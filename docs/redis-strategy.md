# Redis: sessão e cache

Uso Redis como ferramenta de aceleração, não como fonte principal de dados de negócio.

## Sessões

Spring Session permite compartilhar estado de autenticação entre futuras réplicas da aplicação sem depender de sticky session.

## Cache

Para catálogo público, prefiro cache-aside com:

- PostgreSQL como source of truth.
- Chaves separadas por tenant.
- Versionamento por tenant para invalidação barata.
- Invalidação após commit da transação.
- TTL como proteção adicional.
- Fallback para PostgreSQL quando o cache não estiver disponível.

## Princípio

Cache melhora latência e reduz carga, mas não deve esconder a regra de consistência do sistema.
