# Anantha

Most oceanographic data is locked behind NetCDF files, specialized tooling, and domain expertise. Anantha removes that barrier — researchers and analysts can query 23 years of ARGO float data in plain language and get back visualizations, forecasts, and anomaly reports.

Built for Smart India Hackathon 2025. Live at [anantha.live](https://anantha.live).

---

## What It Does

You type a question. Anantha figures out whether it needs SQL, vector search, or LLM reasoning — or all three — and returns structured, traceable results. No query language required.

The system handles:
- **Natural language to structured queries** — intent extraction, constraint parsing, schema-aware SQL generation
- **Hybrid retrieval** — semantic vector search (ChromaDB) combined with PostgreSQL for precise data access
- **Predictive modeling** — LSTM and transformer-based forecasting, anomaly detection, and trend analysis
- **Multimodal input** — documents, images, unstructured `.nc` files processed in a unified interface
- **Interactive output** — 2D/3D visualizations, float trajectory maps, depth-time plots, BGC comparisons

---

## Architecture

```
User Query
    │
    ▼
FastAPI + Redis (session & queue)
    │
    ▼
LLM Query Parser (intent, constraints, structure)
    │
    ├── SQL path → PostgreSQL (structured float data)
    ├── Vector path → ChromaDB (semantic retrieval)
    └── LLM path → Knowledge base reasoning
    │
    ▼
LSTM / Transformer (forecasting & anomaly detection)
    │
    ▼
LLM-orchestrated output → visualizations + tabular API
    │
    ▼
Reinforcement feedback loop (adaptive refinement)
```

---

## Stack

**Backend** · FastAPI · PostgreSQL · Redis  
**AI & Retrieval** · ChromaDB · LangChain · RAG · LSTM · Transformers  
**Data** · xarray · NetCDF · ARGO Float datasets (2002–2025, 50GB+)  
**Visualization** · Plotly · Leaflet  
**Deployment** · Google Cloud · Firebase

---

## Getting Started

```bash
git clone https://github.com/ryash14/Anantha.git
cd Anantha
pip install -r requirements.txt
```

Configure your environment:

```env
DATABASE_URL=your_postgresql_url
CHROMA_PATH=./chroma_db
GOOGLE_API_KEY=your_google_api_key
REDIS_URL=your_redis_url
```

Run the server:

```bash
uvicorn main:app --reload
```

---

## Data

Anantha ingests ARGO float data in NetCDF format via `xarray`, processes it into PostgreSQL and ChromaDB, and keeps it current through automated ETL jobs. Historical data beyond the active window is archived in cold storage with summary indices maintained for fast retrieval.

---

## Developed at

Smart India Hackathon 2025 · Problem Statement 25040  
Team Sirius (ID: 99896)
