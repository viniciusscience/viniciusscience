# Deadlock Playbook

Deadlock acontece quando existe um ciclo de espera entre recursos que nunca é quebrado.

```mermaid
flowchart LR
    T1[Thread 1] -->|segura| A[Lock A]
    T1 -->|espera| B[Lock B]
    T2[Thread 2] -->|segura| B
    T2 -->|espera| A
```

## As quatro condições clássicas

1. Exclusão mútua.
2. Hold and wait.
3. Sem preempção automática.
4. Espera circular.

## Estratégias de prevenção

- Definir ordem global para aquisição de locks.
- Reduzir o número de locks mantidos simultaneamente.
- Usar timeout/`tryLock` quando fizer sentido.
- Evitar chamadas lentas enquanto um lock está retido.
- Coletar thread dump/JFR quando houver suspeita em produção.

## Diagnóstico mental

```mermaid
flowchart TD
    A[Aplicação parou de progredir?] --> B[Existem threads BLOCKED/WAITING?]
    B --> C[Quais locks cada thread possui?]
    C --> D[Quais locks cada thread espera?]
    D --> E{Existe ciclo?}
    E -- sim --> F[Deadlock provável]
    E -- não --> G[Investigar starvation, I/O ou pool esgotado]
```

A pergunta principal não é apenas "qual thread está parada?", mas sim "qual recurso ela espera e quem está segurando esse recurso?".
