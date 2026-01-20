# Project Goal: 
Demonstrate a high-availability (4-node) NiFi cluster orchestrating multi-source data ingestion (SFTP/API), performing schema-based cleaning via JOLT, and streaming to Confluent Cloud using a centralized Schema Registry.

# NiFi-Confluent-Cloud-POC (AI Agentic Learning)

## Architecture Diagram

```mermaid
graph TD
    subgraph "External Sources"
        A[External APIs]
        B[Internal DBs]
    end

    subgraph "4-Node NiFi Cluster (Data Orchestration)"
        C[Ingest Node 1]
        D[Processing Node 2]
        E[Cleaning Node 3]
        F[Egress Node 4]

        C --> D
        D --> E
        E --> F
    end

    subgraph "Confluent Cloud (Event Streaming)"
        G[Kafka Topic: Agent_Input]
        H[Confluent Schema Registry]
    end

    subgraph "AI Agent Layer"
        I[LangChain/AutoGPT Agent]
        J[Vector DB: Pinecone/Milvus]
    end

    F -- "Avro + Schema ID" --> G
    G --> I
    I --> J
    H -- "Validation" --> F
```


## 🚀 How to Run the POC

### 1. Prerequisites
* **Docker & Docker Compose** installed.
* **GH CLI** (optional, for repo management).
* **Confluent Cloud Account** (for API keys).

### 2. Spin up the 4-Node Cluster
From the project root, run:
```bash
docker-compose up -d
