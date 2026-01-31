Stage 1: Build the RAG API (FastAPI)
![RAG API Response](./screenshots/api-main.png)
![Swagger UI](./screenshots/api-add-endpoint.png)
![Ollama Integration](./screenshots/api-python-ollama.png)
![Embedding Process](./screenshots/api-embeddings.png)
![RAG Flow](./screenshots/api-rag-flow.png)


Implemented /query and /add endpoints using FastAPI

Stored document embeddings using ChromaDB for semantic retrieval

Integrated a local language model using Ollama

Tested the API using Swagger UI and curl

Stage 2: Containerisation with Docker
![Docker Build](./screenshots/docker-build-success.png)
![Docker Container Running](./screenshots/docker-container-running.png)
![Docker Local API](./screenshots/docker-local-api.png)
![Docker Hub Push](./screenshots/dockerhub-push.png)
![Docker Hub Pull](./screenshots/dockerhub-pull.png)


Created a Dockerfile to package the application and dependencies

Built and ran the container locally

Published the image to Docker Hub

Verified the image could be pulled and run in a clean environment

Stage 3: Kubernetes Deployment
![Kubernetes Pods](./screenshots/k8s-pods.png)
![Kubernetes Service](./screenshots/k8s-service.png)
![API via Kubernetes](./screenshots/k8s-api-response.png)


Deployed the Docker image to a local Kubernetes cluster using Minikube

Used a Deployment to manage Pods declaratively

Exposed the application using a NodePort Service

Verified request flow from local machine to Pods via the Service

Stage 4: Self-Healing and Reliability
![Kubernetes Self-Healing](./screenshots/k8s-self-healing.png)
![New Pod Created Automatically](./screenshots/k8s-new-pod.png)


Manually deleted running Pods

Observed Kubernetes automatically create replacement Pods

Confirmed the Service continued routing traffic without changes

Stage 5: CI/CD with GitHub Actions
![CI Workflow Overview](./screenshots/ci-overview.png)
![CI Trigger on Git Push](./screenshots/ci-git-push.png)
![CI Data Regression Detection](./screenshots/ci-multi-docs.png)


Created a GitHub Actions workflow triggered on every push

Rebuilt embeddings and ran semantic tests in CI

Introduced a mock LLM mode to make tests deterministic

Observed CI failures when knowledge-base changes broke expected behaviour
