# Docker Notes
# Chapter 02 - Docker Architecture

> 📘 **Level:** Beginner
> ⏱️ **Estimated Reading Time:** 60–75 minutes
> 🛠️ **Practice Time:** 2–3 hours

---

# 📚 Table of Contents

1. What is Docker Architecture?
2. Docker Components
3. Docker Client (CLI)
4. Docker Daemon
5. Docker Engine
6. Docker Images
7. Docker Containers
8. Docker Registry
9. Docker Object Lifecycle
10. Docker Architecture Flow
11. Docker Communication
12. Docker Workflow
13. Useful Docker Commands
14. Best Practices
15. Summary
16. Interview Questions
17. Practice Exercises
18. Mini Project
19. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Docker architecture
- Learn how Docker components communicate
- Understand the Docker lifecycle
- Learn the role of Docker Engine
- Understand Docker Images, Containers, and Registries

---

# 📖 What is Docker Architecture?

Docker follows a **Client-Server Architecture**.

It consists of several components working together to build, run, and manage containers.

```text
Docker Client
      │
      ▼
Docker Daemon
      │
      ▼
Docker Engine
      │
      ▼
Images → Containers
```

---

# 🏗️ Docker Components

Docker consists of:

- Docker Client (CLI)
- Docker Daemon
- Docker Engine
- Docker Images
- Docker Containers
- Docker Registry

---

# 💻 Docker Client (CLI)

The Docker Client is the command-line interface used to interact with Docker.

Example commands:

```bash
docker run nginx
docker images
docker ps
docker pull ubuntu
```

The client sends requests to the Docker Daemon.

---

# ⚙️ Docker Daemon

The Docker Daemon (`dockerd`) is a background service responsible for:

- Building images
- Running containers
- Managing networks
- Managing volumes
- Communicating with registries

It listens for Docker API requests from the Docker Client.

---

# 🚀 Docker Engine

Docker Engine is the core software that powers Docker.

It includes:

- Docker Daemon
- REST API
- Docker CLI

Responsibilities:

- Create containers
- Manage images
- Handle networking
- Manage storage
- Pull and push images

---

# 📦 Docker Images

A Docker Image is a read-only template used to create containers.

An image contains:

- Application code
- Runtime
- Libraries
- Dependencies
- Configuration

Example:

```bash
docker pull nginx
```

---

# 📦 Docker Containers

A Container is a running instance of an image.

Example:

```bash
docker run nginx
```

Multiple containers can be created from the same image.

```text
Nginx Image

├── Container 1
├── Container 2
└── Container 3
```

---

# 🌐 Docker Registry

A Docker Registry stores Docker images.

Types:

- Docker Hub (Public)
- Amazon ECR
- Azure Container Registry
- Google Artifact Registry
- Private Registry

Example:

```bash
docker push my-image
docker pull nginx
```

---

# 🔄 Docker Object Lifecycle

```text
Dockerfile

↓

Build Image

↓

Store Image

↓

Run Container

↓

Start

↓

Stop

↓

Restart

↓

Remove
```

---

# 🔗 Docker Communication

Docker components communicate as follows:

```text
User

↓

Docker CLI

↓

Docker REST API

↓

Docker Daemon

↓

Docker Engine

↓

Images / Containers
```

---

# 🔁 Docker Workflow

Step 1

Write a Dockerfile

↓

Step 2

Build an Image

```bash
docker build -t myapp .
```

↓

Step 3

Run a Container

```bash
docker run myapp
```

↓

Step 4

Application Starts

↓

Step 5

Stop or Remove Container

---

# 🏗️ Complete Docker Architecture

```text
                User
                  │
                  ▼
          Docker CLI (Client)
                  │
          Docker REST API
                  │
                  ▼
        Docker Daemon (dockerd)
                  │
      ┌───────────┼───────────┐
      ▼           ▼           ▼
   Images     Containers   Networks
      │
      ▼
 Docker Registry (Docker Hub / ECR)
```

---

# 💻 Useful Docker Commands

## Check Docker Version

```bash
docker --version
```

---

## Display Docker Information

```bash
docker info
```

---

## Pull an Image

```bash
docker pull ubuntu
```

---

## List Images

```bash
docker images
```

---

## Run a Container

```bash
docker run ubuntu
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

# 🏆 Best Practices

- ✅ Use official images whenever possible
- ✅ Remove unused containers
- ✅ Remove unused images
- ✅ Use image tags instead of `latest`
- ✅ Keep Docker Engine updated
- ✅ Store images in a registry
- ✅ Monitor Docker resources

---

# 🌍 Real-World Example

Developer creates an application.

↓

Writes a Dockerfile.

↓

Builds an Image.

↓

Pushes Image to Docker Hub.

↓

Production Server pulls the Image.

↓

Runs Containers.

↓

Application becomes available to users.

---

# 📝 Key Takeaways

- Docker uses a Client-Server architecture.
- Docker CLI communicates with the Docker Daemon.
- Docker Engine manages images and containers.
- Images are templates.
- Containers are running instances of images.
- Registries store Docker images.

---

# 📋 Summary

In this chapter, you learned:

- Docker Architecture
- Docker Client
- Docker Daemon
- Docker Engine
- Docker Images
- Docker Containers
- Docker Registry
- Docker Lifecycle
- Docker Workflow
- Docker Commands

---

# ❓ Interview Questions

## Beginner

1. What is Docker Architecture?
2. What is Docker CLI?
3. What is Docker Daemon?
4. What is Docker Engine?
5. What is Docker Registry?

---

## Intermediate

6. Explain the Docker workflow.
7. Difference between Docker Image and Container.
8. How does Docker Client communicate with Docker Daemon?
9. What is the role of Docker Engine?
10. Explain Docker Registry.

---

## Advanced

11. Explain Docker's Client-Server Architecture.
12. How does Docker manage containers?
13. Explain the Docker object lifecycle.
14. How do Docker images move from development to production?
15. What happens internally when `docker run nginx` is executed?

---

# 🎯 Practice Exercises

## Exercise 1

Verify Docker Engine is running.

```bash
docker info
```

---

## Exercise 2

Pull the Ubuntu image.

```bash
docker pull ubuntu
```

---

## Exercise 3

Run an Ubuntu container.

```bash
docker run ubuntu
```

---

## Exercise 4

List Docker images and containers.

```bash
docker images
docker ps -a
```

---

## Exercise 5

Stop and remove a container.

```bash
docker stop <container-id>
docker rm <container-id>
```

---

# 🧩 Mini Project

Create a Markdown file named:

```text
docker-architecture.md
```

Include:

- Docker Components
- Docker Architecture Diagram
- Docker Workflow
- Docker Lifecycle
- Docker CLI Commands
- Docker Best Practices

Commit it to Git:

```bash
git add .
git commit -m "Add Docker architecture notes"
```

---

# 📚 Further Reading

- Docker Engine Documentation
- Docker CLI Reference
- Docker Architecture Guide
- Docker Hub Documentation
- OCI (Open Container Initiative)

---

# 🚀 What's Next?

In **Chapter 03 – Installing Docker**, you'll learn:

- 🐧 Install Docker on Ubuntu
- 🪟 Install Docker on Windows
- 🍎 Install Docker on macOS
- ⚙️ Configure Docker
- 👤 Manage Docker as a Non-Root User
- 🔄 Start, Stop & Enable Docker Service
- ✅ Verify Docker Installation
- 🛠️ Common Installation Issues
