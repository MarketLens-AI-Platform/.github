# Smart eCommerce Intelligence Platform

> **An End-to-End Autonomous eCommerce Intelligence & MLOps Platform**
> From automated multi-platform web scraping to ML-driven behavioral analysis, LLM semantic enrichment, and real-time BI visualization — all orchestrated on Kubernetes.

[![MLOps Pipeline](https://img.shields.io/badge/MLOps-Kubeflow-blue.svg?style=flat-square&logo=kubernetes)](https://kubeflow.org)
[![LLM Backend](https://img.shields.io/badge/LLM-DeepSeek--Chat-orange.svg?style=flat-square)](https://deepseek.com)
[![Architecture](https://img.shields.io/badge/Architecture-Distributed_A2A-green.svg?style=flat-square)]()
[![Flask](https://img.shields.io/badge/Flask-Backend-000000?style=flat-square&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![Academic](https://img.shields.io/badge/FST_Tanger-LSI_2-red.svg?style=flat-square)](https://www.fstt.ac.ma)

---

## Table of Contents

- [Overview & Business Value](#-overview--business-value)
- [System Architecture](#-system-architecture)
- [Microservices Repositories](#-microservices-repositories)
- [MLOps Pipeline (DAG)](#-mlops-pipeline-dag)
- [BI Dashboard](#-bi-dashboard)
- [Deployment & GitOps](#-deployment--gitops)
- [Authors & Contributors](#-authors--contributors)

---

## 🎯 Overview & Business Value

**Smart eCommerce Intelligence** is a production-grade microservices platform that automates the full data lifecycle for e-commerce competitive intelligence: **ingestion → enrichment → modeling → visualization**.

This organization addresses a critical business need — continuously monitoring competitor catalogs, pricing strategies, and product performance across multiple platforms (Shopify, WooCommerce) without manual intervention. It delivers:

| Capability | Description |
|---|---|
| **Automated Ingestion** | Zero-touch A2A scraping agents extract structured product data from heterogeneous e-commerce APIs with Playwright fallback for JS-rendered pages. |
| **Semantic Enrichment** | DeepSeek LLM, exposed through a secure MCP server, transforms raw descriptions into ML-ready features (sentiment, category mapping, attribute extraction). |
| **Predictive Scoring** | Parallel XGBoost (supervised) and K-Means/PCA (unsupervised) pipelines rank products, detect behavioral segments, and surface Top-K opportunities. |
| **Actionable BI** | Real-time dashboard with KPI tracking, cluster visualization, and a LangChain-powered conversational assistant for natural-language data queries. |

---

## 🏗️ System Architecture

The platform is organized into decoupled layers, each independently deployable and observable:

![Architecture Globale](./docs/architecture.png)

### 1. A2A Scraping Layer
Autonomous Agent-to-Agent crawlers target Shopify and WooCommerce storefronts using Storefront APIs, REST APIs, and Playwright for JavaScript-rendered pages.

### 2. LLM Enrichment Layer
DeepSeek-powered semantic processing behind a secure Model Context Protocol (MCP) boundary, transforming raw product text into structured, ML-ready features.

### 3. MLOps Orchestration Layer
Kubernetes-native ML lifecycle management using Kubeflow Pipelines for declarative DAG execution, MinIO for artifact storage, and GHCR-hosted Docker images.

### 4. BI & Presentation Layer
Stateless Flask application serving an interactive analytics interface with Plotly visualizations and a LangChain-powered conversational AI assistant.

---

## 📦 Microservices Repositories

The platform is decomposed into the following independent repositories:

- [**marketlens-ingestion**](https://github.com/MarketLens-AI-Platform/marketlens-ingestion) — Data ingestion layer using Playwright and A2A agents.
- [**marketlens-llm-mcp**](https://github.com/MarketLens-AI-Platform/marketlens-llm-mcp) — AI enrichment layer and FastMCP server.
- [**marketlens-mlops**](https://github.com/MarketLens-AI-Platform/marketlens-mlops) — Kubeflow ML pipelines and model scoring logic.
- [**marketlens-frontend**](https://github.com/MarketLens-AI-Platform/marketlens-frontend) — Real-time BI dashboard and AI assistant UI.
- [**marketlens-gitops**](https://github.com/MarketLens-AI-Platform/marketlens-gitops) — Centralized K8s manifests, ArgoCD config, and infrastructure hub.

---

## ⚙️ MLOps Pipeline (DAG)

The core ML workflow executes as a Directed Acyclic Graph on Kubeflow Pipelines:

![Pipeline DAG](./docs/dag.png)

| Stage | Component | Description |
|---|---|---|
| **Preprocessing** | `preprocessing.py` | Data cleaning, missing-value imputation, and semantic feature engineering. |
| **Supervised Training** | `supervised.py` | XGBoost classifier predicting Top-K probability from pricing and engagement features. |
| **Unsupervised Training** | `unsupervised.py` | K-Means clustering for product segmentation + PCA for dimensionality reduction. |
| **Association Rules** | `association_rules.py` | Apriori algorithm mining frequent itemsets and purchasing rules. |
| **Scoring Engine** | `scoring.py` | Composite scoring unifying model outputs for final recommendations. |

---

## 📊 BI Dashboard

The interactive analytics interface provides operational visibility across the entire pipeline:

![Dashboard BI](./docs/dashboard.png)

- **KPI Cards** — Real-time metrics overview.
- **PCA Projection** — 2D scatter plot of products in reduced feature space.
- **K-Means Clusters** — Distribution of product segments.
- **AI Virtual Assistant** — Conversational interface powered by DeepSeek.

---

## 🚀 Deployment & GitOps

To deploy the entire platform on a Kubernetes cluster, please visit the [**marketlens-gitops**](https://github.com/MarketLens-AI-Platform/marketlens-gitops) repository.

It contains:
- **ArgoCD Application** for automated sync and GitOps-driven deployment.
- **Kustomize Overlays** for managing microservice manifests.
- **Infrastructure Hub** including MinIO stateful storage configuration.
- **Unified Makefile** for local Kubernetes provisioning and status monitoring.

---

## 👨‍💻 Authors & Contributors

This platform was architected and engineered by:

- **Yassine Kamouss** — Cloud Architecture, MLOps Engineering, Kubernetes & Kubeflow
- **Yahya Ahmane** — AI Integration, LLM & Agent Systems

---
Smart eCommerce Intelligence — FST Tanger, LSI 2, Modules: Data Mining & SID, 2025/2026
