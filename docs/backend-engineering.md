# Backend Engineering

Notas e princípios que guiam meu estudo e trabalho com backend.

## Foco

- APIs REST com contratos claros e versionamento consciente.
- Serviços com responsabilidades bem definidas.
- Transações curtas e consistência explícita.
- Idempotência em operações suscetíveis a retry.
- Observabilidade desde o início.
- Segurança e isolamento entre tenants.

## Stack principal

Java, Spring Boot, PostgreSQL, Redis, RabbitMQ, Docker e Traefik.

## Perguntas que faço antes de implementar

1. Qual é a fonte da verdade?
2. Onde a consistência precisa ser forte e onde pode ser eventual?
3. O que acontece se a requisição repetir?
4. Como o sistema se comporta sob concorrência?
5. Como vou diagnosticar uma falha em produção?

Esse checklist me ajuda a pensar além do happy path e aproximar decisões de código das decisões de arquitetura.
