# Lab 1: Simple Model Training

This lab demonstrates a simple Python script running inside a Docker container to train a machine learning model.

## Prerequisites

- Docker installed on your machine.
- (Optional) A local virtual environment for development, though the lab runs entirely in Docker.

## How to Run

1.  **Build the Docker Image**:
    Navigate to the `Lab1` directory and build the image:
    ```bash
    docker build -t lab1-training .
    ```

2.  **Run the Container**:
    Run the container to execute the training script:
    ```bash
    docker run --rm lab1-training
    ```
    The `--rm` flag automatically removes the container after it exits.

## Key Features

- **Base Image**: Uses `python:3.10-slim` for a smaller image size.
- **Security**: Runs as a non-root user (`appuser`).
- **Optimization**: Leverages Docker layer caching ensuring faster builds.
