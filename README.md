<!-- Banner -->
<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F2027,50:203A43,100:2C5364&height=200&section=header&text=Jose%20Vinicius%20👨‍💻&fontSize=42&fontColor=ffffff&fontAlignY=35&desc=Java%20%7C%20Spring%20Boot%20%7C%20PostgreSQL%20%7C%20Arquitetura%20de%20Software&descSize=16&descAlignY=55" />
</div>

<h2 align="center">👋 Olá! Eu sou o Vinicius</h2>

<p align="center">
  Desenvolvedor com foco em <strong>backend, arquitetura e sistemas distribuídos</strong>, trabalhando principalmente com Java, Spring Boot, PostgreSQL, Redis, mensageria e containers.
</p>

<p align="center">
  Gosto de entender não só <em>como</em> implementar, mas também <strong>por que uma decisão de arquitetura faz sentido</strong> em termos de concorrência, consistência, escalabilidade e operação.
</p>

---

## 🚀 Sobre mim

Minha principal área é backend com Java e Spring. Tenho estudado e construído projetos envolvendo multi-tenancy, cache distribuído, mensageria, observabilidade, WebSocket, concorrência na JVM e infraestrutura com Docker/Kubernetes.

Também curso mestrado e venho trabalhando com Machine Learning/Deep Learning, mantendo esse estudo como uma segunda frente técnica.

---

## 🏗️ Arquitetura e backend

Alguns temas que fazem parte do meu estudo e dos projetos que desenvolvo:

- Java moderno e Spring Boot
- PostgreSQL, transações, MVCC, locks e concorrência
- Redis para sessão e cache
- RabbitMQ e processamento assíncrono
- APIs REST e WebSocket
- Multi-tenancy e isolamento por tenant
- Docker, Traefik e Kubernetes
- Observabilidade com métricas e tracing
- Sistemas distribuídos, idempotência e consistência
- Concorrência na JVM, virtual threads e sincronização

---

## 🧵 JVM & Concorrência — visão visual

Um dos assuntos que mais estudo é como a JVM coordena trabalho concorrente, virtual threads e locks.

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
    V1 -. espera por I/O .-> P[park / unmount]
    P -. libera a carrier .-> S
```

### Deadlock em uma imagem

```mermaid
flowchart LR
    T1[Thread 1] -->|possui| A[Lock A]
    T1 -->|espera| B[Lock B]
    T2[Thread 2] -->|possui| B
    T2 -->|espera| A
```

📚 **[Ver guia visual completo: virtual threads, pinning, race conditions, deadlocks, MVCC e checklist mental →](docs/jvm-concurrency-visual.md)**

---

## 🔨 Projetos em destaque

### SaaS multi-tenant de e-commerce

Projeto de estudo e produto SaaS com lojas separadas por domínio/subdomínio, painel administrativo por tenant, catálogo, pedidos, Redis, PostgreSQL, Traefik e deploy em VPS com Docker Compose. O repositório principal permanece privado enquanto o produto está em evolução.

### [Modern Concurrency in Java](https://github.com/viniciusscience/modern-concurrency-java-book)

Repositório dedicado a experimentos com concorrência em Java, incluindo virtual threads, executors, sincronização, semáforos e diagnóstico de problemas concorrentes.

### [Machine Learning / Deep Learning](https://github.com/viniciusscience/Machine-Learning-Mestrado)

Projetos acadêmicos e experimentos voltados a classificação de imagens e modelos de aprendizado de máquina aplicados ao mestrado.

### [MCP Easy Setup](https://github.com/viniciusscience/mcp-easy-setup)

Extensão para Visual Studio Code que simplifica a configuração de integrações MCP.

<p align="center">
  <a href="https://marketplace.visualstudio.com/items?itemName=Joseviniciusdasilvadesouzadesouza.mcp-easy-setup">
    <img src="https://img.shields.io/badge/VS%20Code-MCP%20Easy%20Setup-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white" />
  </a>
</p>

---

## 🛠️ Tech Stack

<p align="center">
  <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" />
  <img src="https://img.shields.io/badge/Spring%20Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" />
  <img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white" />
  <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white" />
  <img src="https://img.shields.io/badge/RabbitMQ-FF6600?style=for-the-badge&logo=rabbitmq&logoColor=white" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white" />
  <img src="https://img.shields.io/badge/Traefik-24A1C1?style=for-the-badge&logo=traefikproxy&logoColor=white" />
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/VS%20Code%20Extension-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white" />
</p>

---

## 📚 Atualmente estudando

- Arquitetura de software e sistemas distribuídos
- PostgreSQL avançado e concorrência
- Concorrência na JVM e virtual threads
- Observabilidade e operação de serviços
- Machine Learning e Deep Learning
- Integrações MCP e ferramentas para desenvolvedores

---

<div align="center">
  <strong>💻 Backend, arquitetura e engenharia de software com foco em entender o sistema por inteiro.</strong>
</div>

<!-- Footer -->
<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:2C5364,50:203A43,100:0F2027&height=120&section=footer" />
</div>
