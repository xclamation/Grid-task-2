# Simple frontend-backend app

This project is a simple web application that consists of a backend API built with Go and a frontend built with React. The application is deployed using Docker and Kubernetes.
I attempted to launch this project using Kubernetes Services but couldn't find a free solution, so I decided to run the service locally using minikube.

## Prerequisites

- Docker
- Minikube

## Getting Started
1. Navigate to the project directory where Dockerfile.backend is located:

```bash
cd /project/directory
```

2. Build the Docker images for the backend and frontend applications:
```bash
docker build -t backend-image -f Dockerfile.backend .
docker build -t frontend-image -f frontend/Dockerfile.frontend frontend/
```
  
3. Start Minikube:
```bash
minikube start
```

3. Load the Docker images into Minikube:
```bash
minikube cache add backend-image
minikube cache add frontend-image
```

4. Create the Kubernetes deployments and services for the backend and frontend applications:
```bash
kubectl apply -f backend/k8s/backend-deployment.yml
kubectl apply -f backend/k8s/backend-service.yml
kubectl apply -f frontend/k8s/frontend-deployment.yml
kubectl apply -f frontend/k8s/frontend-service.yml
```

5. Verify that the deployments and services are running:
```bash
kubectl get deployments
kubectl get services
```

6. Access the application using the IP address of the frontend service:
```bash
minikube service frontend-service --url
```
