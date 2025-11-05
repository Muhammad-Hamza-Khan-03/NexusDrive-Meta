# 🚚 NexusDrive — Intelligent Delivery ETA & Risk Analytics Platform

> **Modular AI system** for real-time **delivery ETA prediction**, **delay risk classification**, and **data-driven logistics optimization**, powered by **Airflow**, **FastAPI**, **MLflow**, and **React + Vite**.

---

## Repository Ecosystem

| Component | Description | Repository |
|------------|-------------|-------------|
| 🧩 **ETL Pipeline** | Airflow-based data ingestion & enrichment pipeline. | [NexusDrive-ETL-pipeline-Airflow](https://github.com/Muhammad-Hamza-Khan-03/NexusDrive-ETL-pipeline-Airflow) |
| 🤖 **Model Training & FastAPI Service** | ML pipelines for ETA & delay prediction, served via FastAPI microservice. | [NexusDrive](https://github.com/Muhammad-Hamza-Khan-03/NexusDrive) |
| 💻 **Frontend Dashboard** | Vite + React-based analytics dashboard with live data visualization. | [NexusDrive-Web-frontend](https://github.com/Muhammad-Hamza-Khan-03/NexusDrive-Web-frontend) |

---

## System Architecture

```mermaid
graph TD
    A[ETL Pipeline - Airflow] -->|Stores Clean Data| B[(Minio)]
    B --> C[ML Model + FastAPI]
    C -->|REST APIs| D[ Frontend (React + Vite)]
    C -->|Model Tracking| E[MLflow]
    C -->|Cache Results| F[(⚡ Redis)]
    D -->|Trigger Inference / Visualize Results| C
```

---

## ⚙️ Tech Stack Overview

| Layer       | Technologies                                      |
|-------------|--------------------------------------------------|
| **ETL**     | Apache Airflow, Pandas, S3/MinIO, PostgreSQL     |
| **Model API** | FastAPI, Scikit-learn, Redis, MLflow, Docker    |
| **Frontend** | React, TypeScript, Vite, Tailwind CSS, ShadCN UI |
| **Deployment** | Docker, Docker Compose, Cloudflare Pages       |

---

## End-to-End Workflow

### Data Ingestion (ETL):
- Airflow fetches and aligns Delivery, Weather, and Traffic data.
- Enriched datasets stored in PostgreSQL.

### Model Training & Serving (ML + API):
- Regression model predicts ETA.
- Classification model predicts delay risk.
- MLflow tracks all model versions and metrics.
- FastAPI serves models via `/predict_eta` and `/classify_delay`.

### Frontend Visualization:
- React dashboard connects to FastAPI endpoints.
- Displays real-time predictions, historical trends, and risk analytics.

---

## Dockerized Components

| Service          | Description                                  | Command                                   |
|-------------------|----------------------------------------------|-------------------------------------------|
| **ETL Container** | Airflow scheduler, webserver, and workers.   | `docker-compose up` (in ETL repo)        |
| **API Container** | FastAPI + Redis microservice.               | `docker-compose up` (in NexusDrive repo) |
| **Frontend**      | Vite static build (deployed on Cloudflare). | `npm run build / deploy`                 |

---

##  How Components Interact

| Step | Action                                                                 |
|------|------------------------------------------------------------------------|
| 1    | ETL pipeline extracts data → transforms → loads into PostgreSQL        |
| 2    | Model service consumes cleaned data → trains → exports models          |
| 3    | API exposes prediction endpoints for ETA & delay                       |
| 4    | Frontend consumes these APIs → visualizes predictions & risks          |
| 5    | Redis caches repeat queries → improves latency                         |
| 6    | MLflow monitors model metrics & experiments                            |

---

##  Quick Setup (for Multi-Repo Users)

```bash
# Clone all NexusDrive modules
git clone https://github.com/Muhammad-Hamza-Khan-03/NexusDrive-ETL-pipeline-Airflow
git clone https://github.com/Muhammad-Hamza-Khan-03/NexusDrive
git clone https://github.com/Muhammad-Hamza-Khan-03/NexusDrive-Web-frontend
```

Each module has its own `README.md` with setup and Docker instructions.  
Follow them sequentially:
1. Start the ETL pipeline.
2. Run the Model & FastAPI container.
3. Launch the Frontend dashboard.

---

## 🌍 Integration Diagram (High-Level Data Flow)

```mermaid
graph TD
    A[ETL Pipeline - Airflow] -->|"Stores Clean Data"| B[(Minio)]
    B --> C[ML Model + FastAPI]
    C -->|"REST APIs"| D[Frontend (React + Vite)]
    C -->|"Model Tracking"| E[MLflow]
    C -->|"Cache Results"| F[(Redis)]
    D -->|"Trigger Inference / Visualize Results"| C

---
```
## Example Use Case

- A logistics company wants to predict ETA for each delivery.
- The ETL system automatically enriches the data with weather & traffic.
- The FastAPI service returns ETA and delay risk predictions.
- The React dashboard visualizes performance metrics, risk heatmaps, and delivery analytics in real time.

---

## 🔗 Related Repositories

- **ETL Pipeline**: [NexusDrive-ETL-pipeline-Airflow](https://github.com/Muhammad-Hamza-Khan-03/NexusDrive-ETL-pipeline-Airflow)
- **Model & API Service**: [NexusDrive](https://github.com/Muhammad-Hamza-Khan-03/NexusDrive)
- **Frontend Dashboard**: [NexusDrive-Web-frontend](https://github.com/Muhammad-Hamza-Khan-03/NexusDrive-Web-frontend)

---

## 🧑‍💻 Author

**Hamza Khan**  
AI & Full-Stack Engineer | MLOps Enthusiast  
📧 hamzakhan102003@gmail.com  

🌐 [LinkedIn](https://www.linkedin.com/in/muhammad-hamza-khan-03/)

---

⭐ **Support**  
If you find NexusDrive helpful, please ⭐ star the repositories and share your feedback!  
Together we can build smarter, more efficient delivery systems.
