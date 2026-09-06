# Multi-tenancy por domínio e tenant_id

Um modelo simples de SaaS multi-tenant pode usar o hostname para descobrir o tenant e `tenant_id` para isolar os dados.

```mermaid
flowchart LR
    B[Browser] --> DNS[DNS]
    DNS --> T[Traefik]
    T --> W[Nginx / React]
    W --> API[Spring Boot]
    API --> H[Resolver Host]
    H --> D[(domains)]
    D --> TENANT[tenant_id]
    TENANT --> Q[Queries com tenant_id]
    Q --> PG[(PostgreSQL)]
```

## Invariável principal

Toda operação de negócio precisa carregar o contexto correto de tenant até a camada de persistência.

## Pontos de atenção

- Nunca confiar em `tenant_id` arbitrário vindo do cliente quando ele pode ser derivado da sessão/domínio.
- Testar acesso cruzado entre tenants.
- Separar cache por tenant.
- Preservar `Host` através do proxy.
- Auditar operações administrativas sensíveis.
- Índices frequentemente precisam começar ou incluir `tenant_id` conforme os padrões de consulta.

## Cache

```mermaid
flowchart LR
    A[Tenant A] --> KA[catalog:A:v10]
    B[Tenant B] --> KB[catalog:B:v4]
    KA --> R[(Redis)]
    KB --> R
```

A invalidacão de um tenant não deve limpar o catálogo dos demais. Isolamento é uma propriedade que deve existir no banco, cache, autorização e observabilidade.
