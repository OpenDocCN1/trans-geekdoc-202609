
and ease of setup are essential.

Figure 9.2 shows the typical inference flow in a FastAPI-based deployment, starting from a client request to model inference and response delivery:

![](img/036cc5d5719121241c605ad59a82949c_608_0.png)

**Figure 9.2**: FastAPI-based model serving workflow

**Example**: FastAPI-based model serving

The following code demonstrates deploying a TorchScript model as a RESTful API using FastAPI, enabling real-time predictions from client applications:

```
from fastapi import FastAPI
import torch
from pydantic import BaseModel
class Input(BaseModel):
    features: list

app = FastAPI()
model = torch.jit.load("model_scripted.pt")

@app.post("/predict")
def predict(input: Input):
    input_tensor = torch.tensor([input.features])
    output = model(input_tensor)
    return {"prediction": output.tolist()}
```

## Key advantages

This deployment approach offers a lightweight, real-time interface ideal for rapid development, testing, and seamless integration with client applications:

- Quick and lightweight setup for development environments and local testing.
- Supports real-time inference with minimal latency.
- Seamlessly integrates with front end clients and back services via REST APIs.

## AI tool assistance

AI coding assistants enhance the FastAPI deployment workflow by automating routing logic, improving schema validation, and resolving common implementation issues:

- GitHub Copilot:
    - Autocompletes API routing and request/response logic.
    - Validates input schemas using pydantic models.
    - Suggests exception handling for common edge cases.
- ChatGPT:
    - Assists in designing asynchronous endpoints and JSON-compatible responses.
    - Recommends input validation patterns and helps troubleshoot API errors.
    - Generates complete scaffolding for FastAPI-based deployment pipelines.

> Note: Local API deployment is ideal for proof of concepts (POCs), internal tools, and integration demos before scaling to cloud or containerized environments.

## Containerized deployment with Docker

As machine learning solutions transition from development to production, consistency, portability, and reproducibility become top priorities. Docker provides a powerful and standardized way to package the entire application into a lightweight, portable container image, including the model, dependencies, and serving logic.

This ensures the model behaves identically across environments on a developer's laptop, a virtual machine in the cloud, or within a large-scale orchestration platform like Kubernetes.

## Example: Dockerfile for model deployment

The following Dockerfile demonstrates how to containerize a FastAPI-based ML model server, ensuring consistent deployment across different environments.

```
FROM python:3.10-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY .
CMD ["uvicorn", "app:app", "-host", "0.0.0.0", "-port", "8000"]
```

## Build and run the container

Use the following commands to build the Docker image and launch the containerized ML API on your local or cloud environment:

```bash
docker build -t ml-api .
docker run -p 8000:8000 ml-api
```

## Deployment targets

This containerized setup is versatile and suitable for deployment across on-premise servers, cloud virtual machines, and scalable Kubernetes environments:

- On-premise servers with fixed infrastructure.
- Cloud VMs such as AWS EC2, Google Compute Engine, or Azure VMs.
- Kubernetes clusters for scalable, orchestrated deployments in production.

## AI tool assistance

AI-powered assistants streamline Docker-based deployments by generating optimized Dockerfiles, resolving build issues, and automating environment configuration steps:

- GitHub Copilot:
    - Suggests best practices for writing efficient Dockerfiles.
    - Recommends minimal base images (e.g., python:3.10-slim) and caching strategies.
    - Automatically completes environment setup and CMD instructions.
- ChatGPT:
    - Generates multi-stage Dockerfiles for reduced image size.
    - Helps write docker-compose.yml files for multi-container setups.
    - Diagnoses build failures, version mismatches, and dependency issues.

> **Note:** Docker enhances reproducibility, simplifies CI/CD integration, and enables seamless migration across cloud and on-premise platforms.

## Model serving

Model serving enhances reproducibility, simplifies CI/CD integration, and enables seamless migration across cloud and on-premise platforms. TorchServe is a flexible, scalable, and-ready tool for machine learning models to be served in production.

The following steps demonstrate the workflow for using TorchServe:

1. Archive the model:
   Use `torch-archiver` to create a model archive file.
2. Start the server:
   Use `torchserve` to launch the model server.
3. Make a request:
   Use `curl` or a client to send data to the model.
