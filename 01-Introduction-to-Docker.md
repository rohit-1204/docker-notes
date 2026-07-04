# Docker Notes
# Chapter 01 - Introduction to Docker

> 📘 **Level:** Beginner
> ⏱️ **Estimated Reading Time:** 45–60 minutes
> 🛠️ **Practice Time:** 2–3 hours

---

# 📚 Table of Contents

1. What is Docker?
2. Why Docker?
3. Problems Before Docker
4. What is Containerization?
5. Virtual Machines vs Containers
6. Docker Advantages
7. Docker Use Cases
8. Docker Components
9. Docker Workflow
10. Docker Architecture
11. Docker Terminology
12. Docker Editions
13. Installing Docker
14. First Docker Container
15. Basic Docker Commands
16. Best Practices
17. Summary
18. Interview Questions
19. Practice Exercises
20. Mini Project
21. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Docker fundamentals
- Learn why Docker is widely used
- Understand containerization
- Differentiate between Virtual Machines and Containers
- Run your first Docker container
- Learn basic Docker commands

---

# 📖 What is Docker?

**Docker** is an open-source platform that allows developers to package, ship, and run applications inside lightweight, portable units called **containers**.

A container includes:

- Application Code
- Runtime
- Libraries
- Dependencies
- Configuration Files

This ensures the application behaves the same across all environments.

---

# 💡 Why Docker?

Before Docker, developers often faced the problem:

> "It works on my machine, but not on yours."

Docker solves this by packaging everything an application needs into a single container.

Benefits:

- ✅ Consistent environments
- ✅ Fast deployments
- ✅ Easy scaling
- ✅ Portability
- ✅ Efficient resource usage

---

# ❌ Problems Before Docker

Traditional deployments had several issues:

- Different operating systems
- Missing libraries
- Dependency conflicts
- Manual installations
- Slow deployments
- Difficult scaling

These problems made application deployment unreliable.

---

# 📦 What is Containerization?

Containerization is the process of packaging an application with all its dependencies into a container.

```text
Application
      │
      ▼
Container
      │
      ▼
Runs Anywhere
```

Containers provide isolated environments while sharing the host operating system kernel.

---

# 🖥️ Virtual Machines vs Containers

| Virtual Machine | Docker Container |
|-----------------|------------------|
| Includes Full OS | Shares Host OS |
| Heavy | Lightweight |
| Slow Startup | Fast Startup |
| More Resource Usage | Less Resource Usage |
| Hypervisor Required | Docker Engine Required |

---

# 🚀 Docker Advantages

- Lightweight
- Portable
- Fast startup
- Easy deployment
- Better resource utilization
- Isolation
- Scalability
- Version control for images
- Simplified CI/CD integration

---

# 🌍 Common Docker Use Cases

Docker is commonly used for:

- Web Applications
- Microservices
- API Services
- CI/CD Pipelines
- Testing Environments
- Development Environments
- Cloud Deployments
- Kubernetes Workloads

---

# 🧩 Docker Components

| Component | Description |
|-----------|-------------|
| Docker Engine | Runs containers |
| Docker Image | Blueprint for containers |
| Docker Container | Running instance of an image |
| Docker Hub | Public image repository |
| Docker Registry | Stores Docker images |
| Docker CLI | Command-line interface |
| Docker Daemon | Background service managing containers |

---

# 🔄 Docker Workflow

```text
Write Dockerfile
        │
        ▼
Build Docker Image
        │
        ▼
Store Image
(Docker Hub / Registry)
        │
        ▼
Run Container
        │
        ▼
Application Running
```

---

# 🏗️ Docker Architecture

```text
        Docker CLI
             │
             ▼
      Docker Daemon
             │
     ┌───────┴────────┐
     ▼                ▼
 Docker Images   Docker Containers
             │
             ▼
        Docker Registry
```

---

# 📖 Docker Terminology

### Docker Image

A read-only template used to create containers.

---

### Docker Container

A running instance of a Docker image.

---

### Dockerfile

A text file containing instructions to build a Docker image.

---

### Docker Hub

A public repository for Docker images.

---

### Docker Registry

A storage service for Docker images.

---

### Docker Engine

The core software that creates and manages containers.

---

# 🏷️ Docker Editions

### Docker Community Edition (CE)

- Free
- Open Source
- Ideal for learning and development

---

### Docker Business

- Enterprise features
- Enhanced security
- Centralized management
- Commercial support

---

# 💻 Installing Docker

Supported Operating Systems:

- Ubuntu
- Debian
- CentOS
- Fedora
- Amazon Linux
- Windows
- macOS

Verify installation:

```bash
docker --version
```

---

# 🚀 Run Your First Container

Run the official Hello World container:

```bash
docker run hello-world
```

Expected output:

```text
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

---

# 💻 Basic Docker Commands

## Check Docker Version

```bash
docker --version
```

---

## View Docker Information

```bash
docker info
```

---

## List Running Containers

```bash
docker ps
```

---

## List All Containers

```bash
docker ps -a
```

---

## List Images

```bash
docker images
```

---

## Pull an Image

```bash
docker pull nginx
```

---

## Run a Container

```bash
docker run nginx
```

---

## Stop a Container

```bash
docker stop <container-id>
```

---

## Remove a Container

```bash
docker rm <container-id>
```

---

## Remove an Image

```bash
docker rmi <image-id>
```

---

# 🏆 Docker Best Practices

- ✅ Use official Docker images
- ✅ Keep images small
- ✅ Remove unused containers and images
- ✅ Use image tags
- ✅ Store images in a registry
- ✅ Avoid running containers as root
- ✅ Regularly update images

---

# 🌍 Common Use Cases

| Scenario | Docker |
|----------|--------|
| Local Development | ✅ |
| Testing | ✅ |
| CI/CD Pipelines | ✅ |
| Microservices | ✅ |
| Cloud Deployment | ✅ |
| Kubernetes | ✅ |

---

# 📝 Key Takeaways

- Docker uses containers instead of virtual machines.
- Containers are lightweight and portable.
- Docker packages applications with dependencies.
- Images are used to create containers.
- Docker Hub stores public images.
- Docker simplifies development and deployment.

---

# 📋 Summary

In this chapter, you learned:

- Docker Basics
- Containerization
- Virtual Machines vs Containers
- Docker Components
- Docker Workflow
- Docker Architecture
- Docker Terminology
- Docker Installation
- Basic Docker Commands
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. What is Docker?
2. What is a container?
3. What is Docker Engine?
4. What is Docker Hub?
5. What is a Docker Image?

---

## Intermediate

6. Explain containerization.
7. Difference between Docker Images and Containers.
8. Compare Docker and Virtual Machines.
9. Explain Docker architecture.
10. Why is Docker popular in DevOps?

---

## Advanced

11. How does Docker improve CI/CD?
12. Explain the Docker workflow.
13. How does Docker ensure portability?
14. What are the advantages of containers over virtual machines?
15. What best practices should be followed when using Docker?

---

# 🎯 Practice Exercises

## Exercise 1

Install Docker on your operating system.

---

## Exercise 2

Verify the Docker installation.

```bash
docker --version
```

---

## Exercise 3

Run the Hello World container.

```bash
docker run hello-world
```

---

## Exercise 4

Pull the Nginx image.

```bash
docker pull nginx
```

---

## Exercise 5

List all Docker images and containers.

```bash
docker images
docker ps -a
```

---

# 🧩 Mini Project

Create a Markdown file named:

```text
docker-introduction.md
```

Include:

- What is Docker?
- Docker Architecture
- Containerization
- Docker Components
- VM vs Container Comparison
- Basic Docker Commands

Commit your project:

```bash
git add .
git commit -m "Add Docker introduction notes"
```

---

# 📚 Further Reading

- Docker Documentation
- Docker Hub
- Docker Best Practices Guide
- OCI (Open Container Initiative)
- Docker CLI Reference

---

# 🚀 What's Next?

In **Chapter 02 – Docker Architecture**, you'll learn:

- 🏗️ Docker Engine
- ⚙️ Docker Daemon
- 💻 Docker CLI
- 📦 Images & Containers
- 📂 Docker Registry
- 🔄 Docker Lifecycle
- 🛠️ Docker Engine Workflow
- 🚀 Hands-on Architecture Examples
