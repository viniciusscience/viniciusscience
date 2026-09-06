# PostgreSQL: tópicos que estudo

Meu foco em PostgreSQL vai além de escrever SELECTs. Tenho estudado como o banco se comporta sob concorrência e carga.

## Tópicos

- MVCC e snapshots de leitura.
- Locks de linha e de tabela.
- Índices e custo de escrita.
- Transações e níveis de isolamento.
- `pg_stat_activity` e diagnóstico de bloqueios.
- Dead tuples, VACUUM e manutenção.
- Advisory locks para coordenação distribuída.
- Conexões, pool e limites operacionais.

## Objetivo

Entender quando um problema deve ser resolvido no banco, na aplicação ou em ambos, evitando adicionar locks ou infraestrutura sem necessidade.
