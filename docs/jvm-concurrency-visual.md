# JVM e Concorrência — visão visual

Este material resume alguns conceitos que estudo na JVM usando diagramas Mermaid renderizados pelo próprio GitHub.

## 1. Como virtual threads usam carrier threads

```mermaid
flowchart LR
    R1[Request A] --> V1[Virtual Thread A]
    R2[Request B] --> V2[Virtual Thread B]
    R3[Request C] --> V3[Virtual Thread C]

    V1 --> S[JVM Scheduler]
    V2 --> S
    V3 --> S

    S --> C1[Carrier Thread 1]
    S --> C2[Carrier Thread 2]

    C1 --> CPU[CPU]
    C2 --> CPU

    V1 -. bloqueia em I/O .-> P1[Unmount / park]
    P1 -. carrier fica livre .-> S
```

A ideia central é que milhares de virtual threads não significam milhares de threads de sistema operacional. Quando uma virtual thread pode ser desmontada durante espera de I/O, a carrier thread pode executar outro trabalho.

## 2. O que é pinning

```mermaid
flowchart TD
    V[Virtual Thread] --> L{Entrou em região que pode fixar?}
    L -- não --> U[Pode desmontar da carrier durante espera]
    U --> F[Carrier fica disponível]

    L -- sim --> P[Virtual Thread fica presa à carrier]
    P --> W[Espera bloqueante]
    W --> B[Carrier também fica ocupada]
    B --> T[Menor throughput sob muita concorrência]
```

Pinning não significa que a aplicação automaticamente está errada. O problema aparece quando muitas tarefas ficam presas por tempo relevante e consomem as poucas carrier threads disponíveis.

## 3. Race condition

```mermaid
sequenceDiagram
    participant T1 as Thread 1
    participant X as contador = 0
    participant T2 as Thread 2

    T1->>X: lê 0
    T2->>X: lê 0
    T1->>X: escreve 1
    T2->>X: escreve 1
    Note over X: esperado = 2 / resultado = 1
```

O incremento `x++` parece uma operação única no código, mas conceitualmente envolve leitura, cálculo e escrita. Se duas threads intercalarem essas etapas sem coordenação, uma atualização pode ser perdida.

## 4. Deadlock clássico

```mermaid
flowchart LR
    T1[Thread 1] -->|possui| LA[Lock A]
    T1 -->|espera| LB[Lock B]

    T2[Thread 2] -->|possui| LB
    T2 -->|espera| LA

    LA -. ciclo de espera .-> T2
    LB -. ciclo de espera .-> T1
```

Forma mental:

```text
Thread 1: tenho A, preciso de B
Thread 2: tenho B, preciso de A

nenhuma consegue avançar
```

Uma prevenção comum é impor uma ordem global de aquisição de locks.

## 5. Concorrência entre aplicação e banco

```mermaid
flowchart TD
    U1[Request 1] --> S1[Spring Service]
    U2[Request 2] --> S2[Spring Service]

    S1 --> TX1[Transaction 1]
    S2 --> TX2[Transaction 2]

    TX1 --> PG[(PostgreSQL)]
    TX2 --> PG

    PG --> MVCC[MVCC / snapshots]
    PG --> LOCKS[Row locks quando necessário]

    MVCC --> READ[Leituras concorrentes]
    LOCKS --> WRITE[Coordenação de writes conflitantes]
```

MVCC reduz contenção de leitura, mas não elimina a necessidade de locks para escritas concorrentes sobre o mesmo dado.

## 6. Checklist mental ao revisar código concorrente

```mermaid
flowchart TD
    A[Existe estado compartilhado?] -->|não| SAFE[Baixo risco de race condition]
    A -->|sim| B[Mais de uma thread pode acessar?]
    B -->|não| SAFE
    B -->|sim| C[Alguma delas escreve?]
    C -->|não| READ[Leitura concorrente geralmente segura]
    C -->|sim| D[Operação é atômica ou sincronizada?]
    D -->|sim| E[Verificar ordem de locks e contenção]
    D -->|não| RISK[Risco de race condition]
    E --> F[Existe espera circular?]
    F -->|sim| DEAD[Possível deadlock]
    F -->|não| OK[Revisar performance e starvation]
```

Esse é o tipo de raciocínio que tento aplicar ao analisar código Java concorrente: primeiro identificar estado compartilhado, depois escrita concorrente, atomicidade, locks e por fim características de progresso do sistema.
