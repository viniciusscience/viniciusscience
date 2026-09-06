# Sistemas Distribuídos: consistência e falhas

Quando uma operação atravessa processos, máquinas ou serviços diferentes, falhas parciais passam a fazer parte do desenho.

```mermaid
flowchart LR
    C[Cliente] --> API[API]
    API --> DB[(PostgreSQL)]
    API --> MQ[RabbitMQ]
    MQ --> W[Worker]
    W --> EXT[Serviço externo]
```

## Perguntas importantes

- O que acontece se o banco confirmar e a publicação na fila falhar?
- A mensagem pode ser entregue duas vezes?
- O consumidor é idempotente?
- Existe retry? Com backoff?
- Como distinguir operação lenta de operação perdida?
- Qual componente é a fonte da verdade?

## Idempotência

```mermaid
flowchart TD
    M[Mensagem recebida] --> K[Extrair idempotency key]
    K --> E{Já processada?}
    E -- sim --> R[Retornar sem repetir efeito]
    E -- não --> P[Processar]
    P --> S[Registrar conclusão]
```

## Regra prática

Não assumir exatamente uma vez. Em muitos sistemas é mais seguro desenhar para pelo menos uma vez + processamento idempotente.

Consistência distribuída é principalmente decidir quais estados intermediários são aceitáveis, como recuperar falhas e como provar o que aconteceu depois.
