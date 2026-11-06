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
