# FinOps — Personal Finance Tracker

> A fully containerized personal finance application with a complete DevOps pipeline — from code to production observability.





![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub_Actions-2088FF?logo=githubactions&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Containerized-2496ED?logo=docker&logoColor=white)
![Python](https://img.shields.io/badge/Backend-FastAPI-009688?logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/Frontend-React-61DAFB?logo=react&logoColor=black)
![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-4169E1?logo=postgresql&logoColor=white)
![Prometheus](https://img.shields.io/badge/Metrics-Prometheus-E6522C?logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Dashboard-Grafana-F46800?logo=grafana&logoColor=white)


-------------------------------------------------------------------------------------

## Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [CI/CD Pipeline](#cicd-pipeline)
- [Monitoring](#monitoring)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)


---

## Overview

**FinOps** is a personal finance tracker that allows users to manage expenses and income. The goal of this project is not just the application itself, but to demonstrate a **complete DevOps lifecycle**:

- Containerized microservices (Docker)
- Automated CI/CD pipeline (GitHub Actions)
- Infrastructure as Code (Docker Compose)
- Automated testing (pytest + Jest)
- Observability stack (Prometheus + Grafana)
- Professional documentation


---

## Architecture
````mermaid
graph TB
    subgraph "Docker Network"
        FE[Frontend<br/>React + Nginx<br/>:3000]
        BE[Backend<br/>FastAPI<br/>:8000]
        DB[(PostgreSQL<br/>:5432)]
        PROM[Prometheus<br/>:9090]
        GRAF[Grafana<br/>:3001]
    end

    USER((User)) --> FE
    FE -->|API Calls| BE
    BE -->|Queries| DB
    PROM -->|Scrape /metrics| BE
    GRAF -->|Query| PROM

    style FE fill:#61DAFB,stroke:#333,color:#000
    style BE fill:#009688,stroke:#333,color:#fff
    style DB fill:#4169E1,stroke:#333,color:#fff
    style PROM fill:#E6522C,stroke:#333,color:#fff
    style GRAF fill:#F46800,stroke:#333,color:#fff
```​
```

Esto es **Mermaid**, un lenguaje que escribe diagramas en texto y GitHub los renderiza como imagen automáticamente. Así no necesitas herramientas externas para tener diagramas en tu repo.

Este diagrama muestra cómo se conectan todos los servicios del proyecto: el usuario entra al frontend, que habla con el backend, que consulta la base de datos, y Prometheus recoge métricas que Grafana muestra.

¿Pegado?