# Kcube Talent Finder

**Recruit the Talent with AI: No Manual Hassle, No Complex Processes**

<img width="500" height="500" alt="kcube_talent_finder_case_study" src="https://github.com/user-attachments/assets/3992d511-2113-4146-9bbc-12c2c51121b3" />


Automate SQL and raw data processing with the best practices of **Data Engineering** and **OCR**, powered by AI.  
This project enables businesses to find the right candidates quickly and efficiently without manual filtering.

---

## Problem Statement
Businesses were struggling with **manual recruitment processes**, handling over **60,000 files** (≈15 GB cumulative data) dispersed across SQL databases and raw files of inconsistent formats.  

Challenges included:
- Highly **time-consuming** and **error-prone** manual screening.  
- **Dispersed data** in SQL and unstructured files.  
- **Non-uniform formats** making automation difficult.  

---

## Solution Provided
Kcube AI developed an **AI-powered recruitment solution** that transformed the candidate selection process:  

- Parsed and preprocessed 60K+ raw files using advanced **Data Engineering** pipelines.  
- Applied **OCR techniques** to extract valuable insights from complex documents.  
- Cleaned, structured, and stored all data into a **Vector Database** for efficient AI search.  
- Integrated with **SQL databases** and external file systems.  
- Built an intuitive **Web UI** where employees can simply type prompts to filter candidates instantly.  

---

## Key Features
- AI-driven **semantic search** over structured + unstructured data.  
- **OCR-powered document parsing** for heterogeneous file formats.  
- Integration with multiple data sources (SQL + raw files).  
- **Scalable backend services** with CI/CD automation.  
- **Conversational interface** to query recruitment data.  

---

## Tech Stack
| Technology                | Purpose |
|----------------------------|---------|
| **Azure AI Search**        | Vector database & semantic search |
| **Azure OpenAI**           | Conversational AI & embeddings |
| **React**                  | Web-based user interface |
| **FastAPI**                | Scalable backend services |
| **PostgreSQL**             | Secure structured data storage |
| **OCR & Data Engineering** | Document parsing & preprocessing |
| **GitHub Actions (CI/CD)** | Automated deployment pipeline |

---

## Data Flow Diagram
```mermaid
flowchart TD
  %% -------- DATA SOURCES --------
  subgraph DS[Data Sources]
    SQL[(SQL DBs)]
    FILES[Raw Files]
    APIS[Third Party APIs]
  end

  %% -------- INGESTION --------
  subgraph ING[Ingestion and Orchestration]
    CONNECT[Connectors]
    SCHED[Scheduler and Workers]
    INGEST[Ingestion Service]
  end

  %% -------- PREPROCESSING --------
  subgraph ETL[Preprocessing and ETL]
    OCR[OCR Pipeline]
    PARSE[Document Parsers]
    CLEAN[Normalization and Cleaning]
    PII[PII Redaction]
    META[Metadata Extraction]
    CHUNK[Smart Chunking]
  end

  %% -------- EMBEDDINGS --------
  subgraph IDX[Embedding and Indexing]
    EMB[Embeddings]
    HINDEX[Hybrid Indexer]
  end

  %% -------- STORAGE --------
  subgraph STOR[Storage]
    VDB[(Azure AI Search)]
    PG[(PostgreSQL)]
    BLOB[(Blob Storage)]
  end

  %% -------- SERVING --------
  subgraph SRV[Serving and Retrieval]
    UI[React Web UI]
    API[FastAPI Backend]
    AUTH[Auth and RBAC]
    QP[Query Pipeline]
    RET[Retriever]
    RERANK[Reranking]
    RAG[RAG Composer]
    EXP[Export and Citations]
  end

  %% -------- OPERATIONS --------
  subgraph OPS[Observability and Ops]
    LOGS[Logs]
    METRICS[Metrics]
    GUARD[Guardrails]
    CI[GitHub Actions]
    MON[Monitoring]
    AUDIT[Audit Trail]
  end

  %% -------- FLOWS --------
  SQL --> CONNECT
  FILES --> CONNECT
  APIS --> CONNECT

  CONNECT --> SCHED --> INGEST
  INGEST --> OCR
  INGEST --> PARSE
  OCR --> PARSE
  PARSE --> CLEAN --> PII --> META --> CHUNK

  %% Persist processed artifacts
  CHUNK --> BLOB
  META --> PG

  %% Embeddings and indexing
  CHUNK --> EMB --> HINDEX --> VDB
  PG --> HINDEX

  %% Serving path
  UI --> AUTH --> API
  API --> QP --> RET --> RERANK --> RAG --> EXP --> UI

  %% Retrieval sources
  QP --> PG
  RET --> VDB
  RAG --> BLOB

  %% Ops hooks
  API --> LOGS
  RET --> METRICS
  RAG --> METRICS
  AUTH --> AUDIT
  INGEST --> AUDIT
  CI --> INGEST
  CI --> API
  MON --> UI

```

---

## Live Link
👉 [Kcube AI](https://kcube.ai)

---

## Case Study Visual
![Kcube Talent Finder](./Kcube_Talent_Finder_Case_Study.png)

---

## About Kcube AI
Kcube AI is an **AI-first IT services company** specializing in:  
- AI Web & Mobile Development  
- Data Engineering, AI/ML/NLP Solutions  
- Power Apps & Power BI Integrations  
- Cloud Solutions with Microsoft Azure  

Visit us at: [kcube.ai](https://kcube.ai)
