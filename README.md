# VectorFlow | AI-Powered Document Intelligence Platform

VectorFlow is a high-performance backend system built to process, embed, and query large-scale document data using **Retrieval-Augmented Generation (RAG)**. It demonstrates a modern microservices approach to handling AI workloads, featuring asynchronous task queues, vector embeddings, and automated DevOps pipelines.

---

## 🚀 Core Features
* **Asynchronous Processing:** Heavy PDF/Text processing offloaded to background workers using **Redis** and **BullMQ**.
* **Semantic Search:** Integration with **Vector Databases** (Pinecone/ChromaDB) for context-aware data retrieval.
* **Real-time Streaming:** AI responses delivered via **Server-Sent Events (SSE)** for a snappy UI experience.
* **Enterprise-Grade DevOps:** Fully containerized with **Docker**, orchestrated with **Kubernetes**, and deployed via **GitHub Actions**.

## 🛠 Tech Stack
* **Runtime:** Node.js (TypeScript)
* **Framework:** Express.js
* **Database:** PostgreSQL (Metadata) + Pinecone (Vector Store)
* **ORM:** Prisma
* **Message Broker:** Redis + BullMQ
* **AI Orchestration:** LangChain.js / OpenAI SDK
* **Infrastructure:** Docker, Kubernetes, Terraform

---

## 🏗 System Architecture
VectorFlow follows a decoupled architecture to ensure the API remains responsive while the AI worker handles computationally expensive tasks.



1.  **API Layer:** Handles authentication and file uploads.
2.  **Job Queue:** Manages ingestion tasks to prevent API bottlenecks.
3.  **Worker Service:** Performs document "chunking" and generates embeddings.
4.  **Retrieval Layer:** Queries the Vector DB to provide context to the LLM.

---

## 🚦 Getting Started (Local Development)

### Prerequisites
* Node.js v18+
* Docker & Docker Compose
* OpenAI API Key

### Installation
1.  **Clone the repo:**
    ```bash
    git clone [https://github.com/lordemmag-devops/vector-flow.git](https://github.com/lordemmag-devops/vector-flow.git)
    cd vector-flow
    ```

2.  **Install dependencies:**
    ```bash
    npm install
    ```

3.  **Set up environment variables:**
    ```bash
    cp .env.example .env
    ```

4.  **Spin up the infrastructure:**
    ```bash
    docker-compose up -d
    ```

5.  **Run migrations and start the dev server:**
    ```bash
    npx prisma migrate dev
    npm run dev
    ```

---

## 📈 DevOps & Observability
This project includes a complete monitoring stack using **Prometheus** and **Grafana** to track:
* API Latency
* Worker Job Success/Failure rates
* Memory usage of the Node.js event loop
