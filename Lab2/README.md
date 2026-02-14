# Lab 2: MLOps Pipeline (Training & Serving)

This lab demonstrates a minimal MLOps pipeline using Docker Compose. It consists of two services:
1.  **Model Training**: Trains a model and saves it to a shared volume.
2.  **Model Serving**: Loads the trained model and serves it via a Flask API.

## Prerequisites

- Docker and Docker Compose installed.

## How to Run

1.  **Start the Pipeline**:
    Navigate to the `Lab2` directory and run:
    ```bash
    docker compose up --build
    ```

2.  **Access the Application**:
    Once the serving container is running (and healthy), access the web interface at:
    [http://localhost:80](http://localhost:80)

3.  **Stop the Pipeline**:
    Press `Ctrl+C` to stop, or run:
    ```bash
    docker compose down
    ```

## Key Features

- **Multi-stage Builds**: separate stages for building environments.
- **Microservices Architecture**: Separate containers for training and serving.
- **Shared Volumes**: Simulates a "Model Registry" by exchanging files between containers.
- **Networking**: Services run on a dedicated isolated bridge network.
- **Security**: Runs as a non-root user.
- **Resource Limits**: CPU and Memory limits configured in `docker-compose.yml`.
