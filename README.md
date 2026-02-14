# Enhanced Docker Labs for MLOps

This repository features a collection of enhanced Docker labs designed to demonstrate best practices in Machine Learning Operations (MLOps). These labs focus on efficiency, security, and modern Docker architecture, showcasing production-ready implementations for model training and serving.

## Key Enhancements

All labs in this repository have been upgraded with the following production-grade features:

*   **Security First**: Containers run as a non-root user (appuser) to prevent privilege escalation attacks. Minimal base images (python:3.10-slim) reduce surface area for vulnerabilities.
*   **Optimized Builds**: Multi-stage builds separate build-time dependencies from runtime requirements, resulting in smaller image sizes. Docker Layer Caching is leveraged by ordering instructions from least to most frequently changed.
*   **Isolation and Networking**: Services communicate over custom bridge networks, isolated from the host and other containers. .dockerignore files prevent unnecessary local files (like .git, .venv, __pycache__) from contaminating the build context.

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
