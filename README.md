# Project Name
### Cloud Service Demo
# Files Included
### index.html
### README.md
## Version control allows you to go back if you've messed something up on the newest branch for example
# Docker
### 1. What Docker is: Docker is a platform for packaging an application together with everything it needs to run (code, runtime, libraries, and settings) so it behaves the same on any machine. It relies on OS-level virtualization, so containers share the host’s kernel and start much faster and use less overhead than full virtual machines.
### 2. What a Docker image is: An image is a read-only template that contains the application and its dependencies, built in stacked layers. Images are defined by a Dockerfile and stored in registries such as Docker Hub, and they never change once built.
### 3. What a Docker container is: A container is a running instance of an image. It adds a thin writable layer on top of the image and runs as an isolated process, so you can start, stop, or delete it without affecting the image. One image can produce many containers.
### 4. Docker image has been added to repo to run it, use these commands: 
### - docker build -t cloud-service-demo:1.0
### - docker run -d --name cloud-demo-container -p 8081:80 cloud-service-demo:1.0
# Kubernetes

### 5. What Kubernetes is and why it is used:

Kubernetes is an open-source container orchestration platform used to deploy, manage, and scale containerized applications. While Docker runs individual containers, Kubernetes manages groups of containers across one or more machines. It provides automated deployment, load balancing, self-healing, scaling, and service discovery, making it easier to run applications reliably in cloud environments.

### 6. The purpose of a Pod, Deployment, and Service:

#### Pod

A Pod is the smallest deployable unit in Kubernetes. It contains one or more containers that share networking and storage resources. In this project, the web application runs inside a container located within a Pod.

#### Deployment

A Deployment manages Pods and ensures that the desired number of replicas are running. If a Pod fails, Kubernetes automatically creates a replacement. Deployments also support rolling updates and rollbacks.

#### Service

A Service provides a stable network endpoint for accessing Pods. Since Pods can be created, destroyed, and recreated over time, a Service ensures that users can consistently communicate with the application without needing to know the Pod's address.

### 7. How to start Minikube and make the Docker image available:

Start the local Kubernetes cluster:

```bash
minikube start --driver=docker
```

Verify the cluster is running:

```bash
kubectl get nodes
```

Load the Docker image into the Minikube cluster:

```bash
minikube image load cloud-service-demo:1.0
```

Verify the image is available:

```bash
minikube image ls
```

### 8. How to apply the Deployment and Service YAML files:

Apply the Deployment configuration:

```bash
kubectl apply -f kubernetes/deployment.yaml
```

Check that the Deployment exists:

```bash
kubectl get deployments
```

Check that the Pod is running:

```bash
kubectl get pods
```

Apply the Service configuration:

```bash
kubectl apply -f kubernetes/service.yaml
```

Check that the Service exists:

```bash
kubectl get svc
```

View all Kubernetes resources:

```bash
kubectl get all
```

### 9. How to access the application using kubectl port-forward:

Use port forwarding to expose the Service locally:

```bash
kubectl port-forward service/cloud-service-demo 8080:80
```

Once the command is running, open:

```text
http://localhost:8080
```

### Useful Kubernetes Commands

Check cluster nodes:

```bash
kubectl get nodes
```

Check deployments:

```bash
kubectl get deployments
```

Check pods:

```bash
kubectl get pods
```

Check services:

```bash
kubectl get svc
```

Check all resources:

```bash
kubectl get all
```

View pod details:

```bash
kubectl describe pod <pod-name>
```

View pod logs:

```bash
kubectl logs <pod-name>
```

### Required Commands

```bash
minikube start --driver=docker
minikube image load cloud-service-demo:1.0
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml
kubectl port-forward service/cloud-service-demo 8080:80
```