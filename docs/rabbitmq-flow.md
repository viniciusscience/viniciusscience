# RabbitMQ: fluxo mental

Mensageria desacopla o produtor do consumidor e permite absorver picos, retries e processamento assíncrono.

```mermaid
flowchart LR
    API[Spring Boot API] --> EX[Exchange]
    EX --> Q1[Queue pedidos]
    EX --> Q2[Queue notificações]
    Q1 --> W1[Worker pedidos]
    Q2 --> W2[Worker notificações]
```

## O que a fila resolve

- Desacoplamento temporal.
- Absorção de picos.
- Retry controlado.
- Processamento assíncrono.
- Escala independente de consumidores.

## O que ela não resolve sozinha

- Idempotência.
- Ordem global de eventos.
- Transação entre banco e broker.
- Poison messages.
- Observabilidade de mensagens presas.

## Consumidor robusto

```mermaid
flowchart TD
    M[Mensagem] --> V[Validar]
    V --> I{Já processei?}
    I -- sim --> ACK[ACK]
    I -- não --> P[Processar]
    P --> OK{Sucesso?}
    OK -- sim --> S[Persistir resultado]
    S --> ACK
    OK -- não --> R{Retry ainda permitido?}
    R -- sim --> RETRY[Retry com backoff]
    R -- não --> DLQ[Dead Letter Queue]
```

Prefiro pensar em mensageria como um protocolo de entrega sujeito a duplicidade e falhas, não como uma chamada de método remota garantida.
