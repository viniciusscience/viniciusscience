# PostgreSQL: MVCC e Locks

MVCC permite que leituras trabalhem sobre versões dos dados sem bloquear writers na maior parte dos casos, mas isso não elimina locks quando duas transações disputam a mesma escrita.

```mermaid
flowchart LR
    T1[Transaction 1] --> S1[Snapshot A]
    T2[Transaction 2] --> S2[Snapshot B]
    S1 --> P[(PostgreSQL)]
    S2 --> P
    P --> V1[Versão antiga]
    P --> V2[Versão nova]
```

## Leitura

Um `SELECT` comum normalmente lê a versão visível para seu snapshot.

## Escrita concorrente

```mermaid
sequenceDiagram
    participant T1 as TX 1
    participant PG as Linha produto 42
    participant T2 as TX 2
    T1->>PG: UPDATE
    Note over PG: row lock
    T2->>PG: UPDATE
    Note over T2,PG: espera TX 1 terminar
    T1->>PG: COMMIT
    PG-->>T2: pode continuar
```

## Modelo mental

- MVCC resolve principalmente visibilidade de versões.
- Locks coordenam conflitos reais de escrita e DDL.
- `SELECT ... FOR UPDATE` deve ser usado quando a lógica precisa reservar explicitamente uma linha.
- Índices reduzem trabalho de leitura, mas aumentam custo de manutenção em writes.

A decisão correta depende da invariável do negócio, não apenas de "colocar lock por segurança".
