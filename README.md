# Observability-for-Containerized-Applications-with-EKS
Monitoring and Logging Stack

This project demonstrates how to deploy a complete observability stack on **Amazon EKS**, including a simple **frontend-backend Node.js application** with **Prometheus**, **Grafana**, **Loki**, and **Fluent Bit**.

It’s designed for DevOps Platform Engineers to learn EKS architecture, Kubernetes networking, centralized logging, and performance monitoring.

## 🧱 Architecture Overview

                     Internet
                             │
                  [ ALB Ingress Controller ]
                             │
         ┌───────────────────┴───────────────────┐
         │                                       │
    Frontend Service                         Backend Service
    (Node.js App on port 3000)         (Node.js App on port 5000)
         │                                       │
     Pods (Frontend)                       Pods (Backend)
         │                                       │
         └──────────────┐        ┌───────────────┘
                        ▼        ▼
                ┌────────────────────────────┐
                │   Fluent Bit (log collector) │
                └──────────────┬──────────────┘
                               │
               ┌───────────────┴───────────────┐
               ▼                               ▼
           [ Loki ]                     [ Prometheus ]
                                               │
                                               ▼
                                        ┌──────────┐
                                        │ Grafana  │
                                        └──────────┘




---

## 🔧 Technologies Used

| Category                | Tool            | Purpose                            |
|-------------------------|------------------|-----------------------------------|
| Container Orchestration | Amazon EKS       | Kubernetes Cluster                |
| Monitoring              | Prometheus       | Collect system & app metrics      |
| Visualization           | Grafana          | Dashboards for metrics & logs     |
| Logging                 | Fluent Bit       | Lightweight log shipping          |
| Log Storage             | Loki             | Centralized logging backend       |
| App Layer               | Node.js (2 apps) | Simple frontend/backend demo      |
| Networking              | ALB Ingress      | Exposes app via LoadBalancer      |
----------------------------------------------------------------------------------
---

## 📦 Application Overview

I used a simple **frontend-backend Node.js app**:
- **Frontend** fetches a message from the backend and displays it.
- **Backend** returns JSON (`{ message: "Hello from Backend!" }`).

---

## 📁 Folder Structure
eks-observability-app/
│
├── app/
│ ├── frontend/ # Node.js frontend (port 3000)
│ └── backend/ # Node.js backend (port 5000)
│
├── k8s/
│ ├── frontend-deployment.yaml
│ ├── backend-deployment.yaml
│ ├── service-frontend.yaml
│ ├── service-backend.yaml
│ └── ingress.yaml
│
├── monitoring/
│ ├── prometheus/
│ ├── grafana/
│ ├── loki/
│ └── fluentbit/
│
├── screenshots/
│ └── grafana-dashboard.png
│
├── README.md

