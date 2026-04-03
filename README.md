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

```mermaid
graph TB
    subgraph "CI/CD — GitHub Actions"
        PUSH[Git Push] --> LINT[Lint & Test]
        LINT --> BUILD[Build Docker Images]
        BUILD --> PUSH_REG[Push to GHCR]
    end

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
    PUSH_REG -.->|Deploy| FE
    PUSH_REG -.->|Deploy| BE

    style FE fill:#61DAFB,stroke:#333,color:#000
    style BE fill:#009688,stroke:#333,color:#fff
    style DB fill:#4169E1,stroke:#333,color:#fff
    style PROM fill:#E6522C,stroke:#333,color:#fff
    style GRAF fill:#F46800,stroke:#333,color:#fff
    style PUSH fill:#333,stroke:#fff,color:#fff
    style PUSH_REG fill:#28a745,stroke:#333,color:#fff
```


---

## Tech Stack

| Layer          | Technology        | Purpose                        |
|----------------|-------------------|--------------------------------|
| Frontend       | React + Nginx     | User interface & static serve  |
| Backend        | Python + FastAPI  | REST API                       |
| Database       | PostgreSQL        | Data persistence               |
| Containers     | Docker + Compose  | Service orchestration          |
| CI/CD          | GitHub Actions    | Automated pipeline             |
| Monitoring     | Prometheus        | Metrics collection             |
| Dashboards     | Grafana           | Metrics visualization          |
| Testing        | pytest + Jest     | Unit & integration tests       |


---

## Getting Started

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/) >= 24.0
- [Docker Compose](https://docs.docker.com/compose/install/) >= 2.20
- [Git](https://git-scm.com/)

### Quick Start
```bash
# 1. Clone the repository
git clone https://github.com/MarcosPerezCantero/finops-app
cd finops-app

# 2. Copy environment variables
cp .env.example .env

# 3. Start all services
docker compose up -d

# 4. Open the app
# Frontend:  http://localhost:3000
# Backend:   http://localhost:8000/docs
# Grafana:   http://localhost:3001
```

### Stop Services
```bash
docker compose down
```


---

## Project Structure
```
finops-app/
├── .github/
│   └── workflows/          # GitHub Actions CI/CD
├── backend/
│   ├── app/                # FastAPI application
│   ├── tests/              # pytest tests
│   ├── Dockerfile
│   ├── requirements.txt
│   └── README.md
├── frontend/
│   ├── src/                # React application
│   ├── Dockerfile
│   ├── nginx.conf
│   └── README.md
├── monitoring/
│   ├── prometheus/         # Prometheus config
│   ├── grafana/            # Grafana dashboards
│   └── README.md
├── docs/
│   ├── architecture.md
│   ├── ci-cd-flow.md
│   └── adr/                # Architecture Decision Records
├── docker-compose.yml
├── .env.example
├── CONTRIBUTING.md
├── CHANGELOG.md
└── LICENSE
```


---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on how to contribute to this project.

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

