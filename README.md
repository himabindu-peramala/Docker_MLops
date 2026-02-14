# Enhanced Docker Labs for MLOps

This repository features a collection of enhanced Docker labs designed to demonstrate best practices in Machine Learning Operations (MLOps). These labs focus on efficiency, security, and modern Docker architecture, showcasing production-ready implementations for model training and serving.

## Key Enhancements

All labs in this repository have been upgraded with the following production-grade features:

*   **Security Hardening**:
    *   Implemented **non-root execution** (`appuser`) to enforce least-privilege principles.
    *   Switched to **slim base images** to minimize vulnerability surface area.

*   **Performance Optimization**:
    *   Leveraged **multi-stage builds** to reduce final image size by excluding build tools.
    *   Optimized **Docker layer caching** for faster rebuilds during development.

*   **Modern Architecture**:
    *   **Microservices**: Decoupled training and serving logic into independent, scalable containers.
    *   **Networking**: Configured custom isolated bridge networks for secure service-to-service communication.
    *   **Resilience**: Added resource limits (CPU/RAM) and automatic restart policies.

---

## Lab 1: Simple Model Training

**Objective**: Containerize a basic machine learning training script.

### Features
*   **Slim Image**: Reduced image size by using python:3.10-slim.
*   **User Permissions**: Script executes as appuser, not root.
*   **Reproducibility**: Dependencies are locked and installed securely.

### Quick Start

1.  Navigate to the Lab1 directory:
    cd Lab1

2.  Build the image:
    docker build -t lab1 .

3.  Run the container:
    docker run --rm lab1

---

## Lab 2: MLOps Pipeline (Training and Serving)

**Objective**: Orchestrate a complete ML pipeline with separate services for training and serving.

### Architecture
*   **Service 1 (Training)**: Trains a model and saves the artifact to a shared volume.
*   **Service 2 (Serving)**: A Flask API that loads the model and serves predictions.
*   **Shared Volume**: Simulates a model registry/artifact store.

### Features
*   **Microservices Pattern**: Decoupled training and serving logic into separate containers.
*   **Resource Limits**: CPU and Memory limits configured in docker-compose.yml to prevent resource hogging.
*   **Restart Policies**: Services automatically restart on failure (except training, which runs once).

### Quick Start

1.  Navigate to the Lab2 directory:
    cd Lab2

2.  Start the pipeline:
    docker compose up --build

3.  Once running, access the inference endpoint at http://localhost:80

---

## Prerequisites

*   Docker Desktop installed and running.
*   Basic understanding of terminal commands.
