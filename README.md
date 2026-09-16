<!-- Banner -->
<div align="center">
  <img src="./assets/profile-banner.svg" alt="Jose Vinicius — Software Engineering, Java, Spring Boot, Computer Vision e Deep Learning" width="100%" />
</div>

<h2 align="center">👋 Olá! Eu sou o Vinicius</h2>

<p align="center">
  <strong>Software Engineer</strong> com foco em backend, arquitetura e sistemas distribuídos.<br/>
  Mestrando em <strong>Computação Aplicada</strong>, com pesquisa em <strong>Visão Computacional e Deep Learning</strong>.
</p>

<p align="center">
  Java • Spring Boot • PostgreSQL • Sistemas Distribuídos • Computer Vision • Deep Learning
</p>

---

## 🚀 Sobre mim

Minha principal atuação profissional é backend com Java e Spring Boot, trabalhando e estudando temas como arquitetura de software, PostgreSQL, multi-tenancy, mensageria, observabilidade, concorrência na JVM e infraestrutura com containers.

No mestrado em Computação Aplicada, desenvolvo uma segunda frente técnica voltada a Inteligência Artificial, especialmente **Visão Computacional e Deep Learning**, conectando engenharia de software com pesquisa aplicada.

Gosto de entender não apenas *como* implementar uma solução, mas **por que uma decisão técnica faz sentido** em termos de concorrência, consistência, escalabilidade, desempenho e operação.

---

## 🔬 Pesquisa — Computer Vision & Deep Learning

Minha pesquisa de mestrado envolve o **desenvolvimento de modelos de aprendizagem profunda para identificação de grandes peixes migratórios capturados pela pesca oceânica brasileira**.

Atualmente venho explorando:

- Classificação de imagens com redes neurais convolucionais (CNNs)
- Transfer Learning e Fine-Tuning
- ConvNeXt e ResNet
- Preparação, organização e análise de datasets de imagens
- Data augmentation e estratégias para reduzir overfitting
- Avaliação de modelos com accuracy, top-k accuracy e matrizes de confusão
- TensorFlow / Keras para treinamento e experimentação
- Visão computacional aplicada a imagens e, futuramente, vídeo

<p align="center">
  <img src="https://img.shields.io/badge/Research-Computer%20Vision-5C6BC0?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Deep%20Learning-CNNs-FF6F00?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Transfer%20Learning-ConvNeXt%20%7C%20ResNet-7952B3?style=for-the-badge" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white" />
  <img src="https://img.shields.io/badge/Keras-D00000?style=for-the-badge&logo=keras&logoColor=white" />
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white" />
</p>

---

## 🏗️ Arquitetura e Backend

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

## 🧵 JVM & Concorrência — visão animada

Para quem não trabalha com concorrência no dia a dia, a ideia é enxergar o sistema como um fluxo: uma requisição chega, vira trabalho dentro da JVM e disputa recursos para executar.

### Virtual Threads e Carrier Threads

<div align="center">
  <img src="./assets/virtual-threads-animated.svg" alt="Animação mostrando uma requisição passando por Virtual Thread, JVM Scheduler, Carrier Thread, CPU e I/O" width="100%" />
</div>

**Como ler:** a bolinha representa uma requisição. Quando ela entra em I/O, a Virtual Thread pode deixar a carrier livre para outra tarefa continuar usando a CPU.

### Deadlock acontecendo passo a passo

<div align="center">
  <img src="./assets/deadlock-animated.svg" alt="Animação mostrando duas threads entrando em deadlock ao esperar locks uma da outra" width="100%" />
</div>

**Como ler:** Thread A segura o Lock A e espera B. Thread B segura o Lock B e espera A. Quando esse ciclo fecha, nenhuma das duas consegue continuar.

🧪 **[Ver o código do JVM Concurrency Lab interativo](docs/jvm-concurrency-lab.html)** — inclui botões de Play/Reset e cenários de Virtual Threads e Deadlock. O repositório também está preparado para publicar o laboratório via GitHub Pages.

📚 **[Ver guia visual completo: virtual threads, pinning, race conditions, deadlocks, MVCC e checklist mental →](docs/jvm-concurrency-visual.md)**

---

## 🧠 Engineering Notes

Uma coleção curta e visual dos assuntos que venho estudando e aplicando:

| Tema | Nota |
|---|---|
| Backend | [Princípios de backend engineering](docs/backend-engineering.md) |
| JVM | [Virtual threads](docs/virtual-threads.md) |
| Concorrência | [Checklist de concorrência](docs/concurrency-checklist.md) |
| Deadlocks | [Playbook de deadlock](docs/deadlock-playbook.md) |
| PostgreSQL | [MVCC e locks](docs/mvcc-locking.md) |
| PostgreSQL | [Notas de estudo](docs/postgresql-notes.md) |
| Redis | [Sessão e estratégia de cache](docs/redis-strategy.md) |
| Sistemas distribuídos | [Consistência e idempotência](docs/distributed-consistency.md) |
| RabbitMQ | [Fluxo de mensageria](docs/rabbitmq-flow.md) |
| Observabilidade | [Fluxo de diagnóstico](docs/observability-flow.md) |
| Multi-tenancy | [Resolução por domínio e tenant_id](docs/multitenancy-flow.md) |
| Traefik | [Fluxo de roteamento](docs/traefik-request-flow.md) |

---

## 🔨 Projetos em destaque

### 🐟 [Machine Learning / Deep Learning — Mestrado](https://github.com/viniciusscience/Machine-Learning-Mestrado)

Experimentos acadêmicos de Machine Learning e Deep Learning, com foco atual em **classificação de imagens, CNNs, Transfer Learning, ConvNeXt e ResNet** aplicados à pesquisa de identificação de espécies de peixes.

### SaaS multi-tenant de e-commerce

Projeto de estudo e produto SaaS com lojas separadas por domínio/subdomínio, painel administrativo por tenant, catálogo, pedidos, Redis, PostgreSQL, Traefik e deploy em VPS com Docker Compose. O repositório principal permanece privado enquanto o produto está em evolução.

### [Modern Concurrency in Java](https://github.com/viniciusscience/modern-concurrency-java-book)

Repositório dedicado a experimentos com concorrência em Java, incluindo virtual threads, executors, sincronização, semáforos e diagnóstico de problemas concorrentes.

### [MCP Easy Setup](https://github.com/viniciusscience/mcp-easy-setup)

Extensão para Visual Studio Code que simplifica a configuração de integrações MCP.

<p align="center">
  <a href="https://marketplace.visualstudio.com/items?itemName=Joseviniciusdasilvadesouzadesouza.mcp-easy-setup">
    <img src="https://img.shields.io/badge/VS%20Code-MCP%20Easy%20Setup-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white" />
  </a>
</p>

---

## 🛠️ Tech Stack

### Backend & Infra

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

### AI & Computer Vision

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white" />
  <img src="https://img.shields.io/badge/Keras-D00000?style=for-the-badge&logo=keras&logoColor=white" />
  <img src="https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white" />
</p>

### Frontend & Tools

<p align="center">
  <img src="https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/VS%20Code%20Extension-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white" />
</p>

---

## 📚 Atualmente estudando

- Visão Computacional e Deep Learning
- CNNs, Transfer Learning e Fine-Tuning
- ConvNeXt, ResNet e arquiteturas modernas para classificação de imagens
- Arquitetura de software e sistemas distribuídos
- PostgreSQL avançado e concorrência
- Concorrência na JVM e virtual threads
- Observabilidade e operação de serviços

---

<div align="center">
  <strong>💻 Software Engineering • Distributed Systems • Computer Vision • Deep Learning</strong>
</div>

<!-- Footer -->
<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:2C5364,50:203A43,100:0F2027&height=120&section=footer" />
</div>
