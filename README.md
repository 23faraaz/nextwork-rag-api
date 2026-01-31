
This repository contains a **production-style Retrieval-Augmented Generation (RAG) API** built to demonstrate practical **junior–mid level DevOps skills**. The focus of this project is not advanced theory, but **hands-on execution**: building, packaging, testing, and operating an application across Docker, CI/CD, and Kubernetes.

The project shows how a real service moves from **local development → containerisation → automated testing → Kubernetes deployment**, with emphasis on reproducibility, observability, and failure recovery.

---

## What This Project Demonstrates

This project demonstrates practical DevOps skills relevant to junior and mid-level roles:

* Building and running an API with FastAPI
* Packaging applications into Docker images and publishing them to a registry
* Using GitHub Actions to automate testing on every code change
* Handling non-deterministic AI behaviour in CI using a mock mode
* Deploying containerised applito Kubernetes using Deployments and Services
* Observing Kubernetes self-healing behaviour when Pods fail

All screenshots are included in this repository as evidence that each stage was executed.

---

## High-Level Architecture

```
Client
  ↓
Kubernetes Service (stable endpoint)
  ↓
FastAPI RAG API (Pod – ephemeral)
  ↓
ChromaDB (vector store)
  ↓
Local LLM via Ollama (mocked in CI)
```

---

## Repository Structure

```
.
├── app/                 # FastAPI application
├── docs/                # Knowledge base documents
├── db/                  # Chroma vector store (gitignored)
├── tests/               # Semantic tests
├─I pipeline
├── Dockerfile
├── deployment.yaml
├── service.yaml
├── screenshots/         # Execution evidence
└── README.md
```

---

## Stage 1: Build the RAG API (FastAPI)

![RAG API Response](screenshots/api-main.png)
![Swagger UI](screenshots/api-add-endpoint.png)

* Implemented `/query` and `/add` endpoints using FastAPI
* Stored document embeddings using ChromaDB for semantic retrieval
* Integrated a local language model using Ollama
* Tested the API using Swagger UI and curl

This stage establishes a working ation or deployment.

---

## Stage 2: Containerisation with Docker

![Docker Build](screenshots/docker-build-success.png)
![Docker Container Running](screenshots/docker-container-running.png)
![Docker Hub Push](screenshots/dockerhub-push.png)

* Created a Dockerfile to package the application and dependencies
* Built and ran the container locally
* Published the image to Docker Hub
* Verified the image could be pulled and run in a clean environment

This stage ensures the application is portable and reproducible.

---

## Stage 3: CI/CD with GitHub Actions

![CI Workflow](screenshots/ci-overview.png)
![CI Data Regression](screenshots/ci-multi-docs.png)

* Initialised Git and pushed the project to GitHub
* Created a GitHub Actions workflow to run tests on every push
* Rebuilt embeddings and ran semantic tests in CI
* Introduced a mock LLM mode to make tests deterministic
* Observed CI failing when knowledge base changes broke expected behaviour

This stage demonstrates automated validation and basic data-quality protection.

---

## Stage 4: Kubernetes Deployment

![Kubernetes Pods](screenshots/k8s-pods.png)
![Kubernetes Service](screenshots/k8s-service.png)
![API via Kubernetes](screenshots/k8s-api-response.png)

* Deployed the Docker image to a local Kubernetes cluster using Minikube
* Used a Deployment to manage Pods declaratively
* Exposed the application using a NodePort Service
* Verified request flow from local machine to Pod via the Service

This stage shows how Kubernetes manages application lifecycle and networking.

---

## Stage 5: Self-Healing and Reliability

![Self Healing](screenshots/k8s-self-healing.png)
![New Pod Created](screenshots/k8s-new-pod.png)

* Deleted running Pods manually
* Observed Kubernetes automatically create replacement Pods
* Confirmed the Service continued routing traffic without changes

This demonstrates Kubernetes’ desired-state reconciliation and basic resilience.

---

## How to Run This Project

### Run with Docker

```bash
docker pull 23faraaz/rag-app:latest
docker run -p 8000:8000 23faraaz/rag-app:latest
```

### Deploy to Kubernetes (Minikube)

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
minikube service rag-app-service --url``

---

## Why This Project Matters

This project shows my ability to:

* Work with containerised applications end-to-end
* Use CI to catch failures early rather than manually testing
* Deploy and debug applications running inside Kubernetes
* Understand how Services, Deployments, and Pods interact in practice

Everything included reflects work I personally executed and understand.

---

## Author

Faraaz Mohammed

Junior / Mid-Level DevOps Engineer

