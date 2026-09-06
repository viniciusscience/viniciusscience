# Observabilidade: do sintoma à causa

Observabilidade não é só ter dashboards. O objetivo é reduzir o tempo entre perceber um sintoma e encontrar a causa.

```mermaid
flowchart LR
    U[Usuário] --> T[Traefik]
    T --> API[Spring Boot]
    API --> DB[(PostgreSQL)]
    API --> REDIS[(Redis)]
    API --> MQ[RabbitMQ]

    T -. métricas .-> P[Prometheus]
    API -. métricas/traces .-> P
    DB -. métricas .-> P
    P --> G[Grafana]
```

## Sinais principais

- Latência p50/p95/p99.
- Taxa de erro.
- Throughput/RPS.
- Saturação de CPU, memória, conexões e filas.
- Tempo de queries e locks no banco.
- Cache hit/miss.
- Tamanho e idade de filas.

## Fluxo de diagnóstico

```mermaid
flowchart TD
    A[Endpoint lento] --> B[É geral ou um endpoint?]
    B --> C[CPU/memória saturadas?]
    C --> D[Pool/conexões saturados?]
    D --> E[Query lenta ou bloqueada?]
    E --> F[Dependência externa lenta?]
    F --> G[Trace/log correlacionado]
    G --> H[Causa provável + evidência]
```

O objetivo é evitar diagnóstico por palpite: cada hipótese deve ser testada com métrica, trace, log ou estado do recurso.
