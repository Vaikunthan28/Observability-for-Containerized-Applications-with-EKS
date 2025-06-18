# Observability-for-Containerized-Applications-with-EKS
Monitoring and Logging Stack

This project demonstrates how to deploy a complete observability stack on **Amazon EKS**, including a simple **frontend-backend Node.js application** with **Prometheus**, **Grafana**, **Loki**, and **Fluent Bit**.

It’s designed for DevOps Platform Engineers to learn EKS architecture, Kubernetes networking, centralized logging, and performance monitoring.

## 🧱 Architecture Overview

                    Internet
                       │
                [ ALB Ingress Controller ]
                       │
     ┌─────────────────┴─────────────────┐
     │                                   │
Frontend Service                   Backend Service

<pre> ``` Internet | [ ALB Ingress Controller ] | ┌─────────────────┴─────────────────┐ | | Frontend Service Backend Service (Node.js App on port 3000) (Node.js App on port 5000) | | Pods (Frontend) Pods (Backend) | | └────────────┬──────────────────────┘ | Fluent Bit (log collection) | ┌─────────────┴──────────────┐ | | [ Loki ] [ Prometheus ] | [ Grafana ] ``` </pre>
