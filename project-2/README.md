# Time Service Application

This repository contains a simple Python application that serves the current time in Toronto. The application is containerized using Docker and can be deployed to a Kubernetes cluster.

## Prerequisites

- Docker
- Kubernetes cluster (e.g., Minikube)

## Building and Running the Docker Container

1. **Build the Docker image:**

   Navigate to the directory containing the `Dockerfile` and `app.py`.

   ```sh
   cd app/ && docker build -t time-service .
2. **Run the Docker container:**

    ```sh
    docker run -p 3030:3030 time-service
The application should now be accessible at http://localhost:3030.

## Deploying to Kubernetes

1. **Start Minikube with:**

    ```sh
    minikube start
2. **Apply the Deployment and Service manifests:**

    ```sh
    kubectl apply -f deployment.yaml
    kubectl apply -f service.yaml
3. **Verify the deployment:**

    Check if the deployment and service are created successfully:

    ```sh
    kubectl get deployments
    kubectl get pods
    kubectl get services
Since we exposed the service using NodePort, we can access application using any Kubernetes cluster nodes' IP addresses on the specified nodePort. 
Since we are using minikube on local cluster , we can identify IP address via following command: 

    
    minikube ip
    
The application should now be accessible at http://minikube-ip:30000.

## Troubleshooting

If you encounter issues connecting to the Kubernetes API server, make sure cluster is running. You can see log of the pod with the following command:

    kubectl logs <pod-name>
    
If using Minikube, you can restart Minikube with:

    minikube delete
    minikube start