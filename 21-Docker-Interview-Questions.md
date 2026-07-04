# Docker Notes
# Chapter 21 - Docker Interview Questions

> 📘 **Level:** Beginner to Advanced
> ⏱️ **Estimated Reading Time:** 60–90 minutes
> 🛠️ **Practice Time:** 3–4 hours

---

# 📚 Table of Contents

1. Beginner Questions
2. Intermediate Questions
3. Advanced Questions
4. Scenario-Based Questions
5. Docker Commands
6. Interview Tips
7. Summary
8. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Prepare for Docker interviews
- Answer common Docker questions
- Understand real-world Docker scenarios
- Revise important Docker commands
- Build confidence for DevOps interviews

---

# 📖 Beginner Questions

### 1. What is Docker?

Docker is a platform that packages applications and their dependencies into **containers**, allowing them to run consistently across different environments.

---

### 2. What is a Docker Container?

A container is a lightweight, isolated environment that runs an application along with its dependencies.

---

### 3. What is a Docker Image?

A Docker image is a read-only template used to create containers.

---

### 4. What is the difference between an Image and a Container?

| Image | Container |
|--------|-----------|
| Template | Running instance |
| Read-only | Read/Write |
| Used to create containers | Runs the application |

---

### 5. What is Docker Hub?

Docker Hub is a cloud-based registry used to store and share Docker images.

---

### 6. What is Docker Compose?

Docker Compose is a tool used to define and run multi-container applications using a `docker-compose.yml` file.

---

### 7. What is a Dockerfile?

A Dockerfile is a text file containing instructions to build a Docker image.

---

### 8. What is the purpose of Docker Volumes?

Docker Volumes provide persistent storage for containers.

---

### 9. What is Docker Networking?

Docker Networking enables communication between containers and external systems.

---

### 10. What is Docker Registry?

A Docker Registry stores Docker images.

Examples:

- Docker Hub
- Amazon ECR
- Azure Container Registry
- Google Artifact Registry

---

# ⚙️ Intermediate Questions

### 11. Explain the Docker Architecture.

Docker architecture consists of:

- Docker Client
- Docker Daemon
- Docker Host
- Docker Registry

---

### 12. What is the difference between COPY and ADD?

| COPY | ADD |
|------|-----|
| Copies local files | Can copy local files and extract archives |
| Preferred | Use only when extra features are needed |

---

### 13. What is a Multi-Stage Build?

A Multi-Stage Build uses multiple `FROM` statements to create smaller production images.

---

### 14. What is the difference between CMD and ENTRYPOINT?

| CMD | ENTRYPOINT |
|------|------------|
| Default command | Fixed executable |
| Can be overridden | Runs every time |

---

### 15. What is the purpose of `.dockerignore`?

It excludes unnecessary files from the Docker build context, reducing image size and build time.

---

### 16. What are Docker Health Checks?

Health Checks determine whether a containerized application is functioning correctly.

---

### 17. What are Environment Variables?

Environment variables store configuration values outside the application code.

---

### 18. What are Docker Secrets?

Docker Secrets securely store sensitive information like passwords, API keys, and certificates.

---

### 19. What is the difference between Bind Mounts and Volumes?

| Bind Mount | Volume |
|------------|---------|
| Uses host directory | Managed by Docker |
| Host dependent | Portable |
| Good for development | Good for production |

---

### 20. How do you reduce Docker image size?

- Use Alpine images
- Multi-Stage Builds
- Remove unnecessary packages
- Use `.dockerignore`
- Combine `RUN` commands

---

# 🚀 Advanced Questions

### 21. How does Docker provide container isolation?

Using:

- Linux Namespaces
- Control Groups (cgroups)
- Union File Systems

---

### 22. What is the difference between Docker and Virtual Machines?

| Docker | Virtual Machine |
|--------|-----------------|
| Shares host OS kernel | Has its own OS |
| Lightweight | Heavy |
| Fast startup | Slower startup |
| Lower resource usage | Higher resource usage |

---

### 23. Explain Docker Networking modes.

- Bridge
- Host
- None
- Overlay
- Macvlan

---

### 24. How would you secure Docker in production?

- Run as non-root
- Scan images
- Use Docker Secrets
- Keep images updated
- Limit capabilities
- Enable logging
- Use read-only filesystem

---

### 25. Explain Docker in CI/CD.

Typical workflow:

```text
Code

↓

Build Image

↓

Run Tests

↓

Push Registry

↓

Deploy
```

---

### 26. What is Docker Swarm?

Docker Swarm is Docker's native container orchestration platform for managing multiple Docker hosts.

---

### 27. Explain Docker on AWS.

Common AWS services:

- Amazon EC2
- Amazon ECR
- Amazon ECS
- Amazon EKS
- CloudWatch

---

### 28. What is the purpose of image tagging?

Image tags identify different versions of an image.

Example:

```text
myapp:v1

myapp:v2

myapp:latest
```

---

### 29. How do you troubleshoot a failing container?

Steps:

- Check logs
- Inspect container
- Verify environment variables
- Check resource limits
- Verify network connectivity

---

### 30. Explain Docker Best Practices.

- Official images
- Small image size
- Non-root user
- Security scanning
- Health checks
- Resource limits
- Version tags

---

# 💼 Scenario-Based Questions

### 31. A container exits immediately after starting. What would you check?

- Container logs
- Startup command
- Application errors
- Missing environment variables

---

### 32. Your Docker image is very large. How would you reduce its size?

- Use Alpine images
- Multi-Stage Builds
- Remove unnecessary dependencies
- Use `.dockerignore`

---

### 33. The application works locally but fails in production. What would you verify?

- Environment variables
- Network configuration
- Image version
- Volume mounts
- Logs

---

### 34. How do you deploy Docker containers on AWS?

- Build image
- Push to Amazon ECR
- Deploy using Amazon ECS or Amazon EKS

---

### 35. How do you roll back a failed deployment?

- Deploy the previous image version
- Verify application health
- Monitor logs

---

# 🛠️ Common Docker Commands

Build image:

```bash
docker build -t myapp .
```

Run container:

```bash
docker run myapp
```

List containers:

```bash
docker ps
```

List images:

```bash
docker images
```

View logs:

```bash
docker logs <container-name>
```

Inspect container:

```bash
docker inspect <container-name>
```

Stop container:

```bash
docker stop <container-name>
```

Remove container:

```bash
docker rm <container-name>
```

Remove image:

```bash
docker rmi <image-name>
```

---

# 💡 Interview Tips

- ✅ Explain concepts clearly
- ✅ Mention real-world use cases
- ✅ Understand Docker architecture
- ✅ Practice common Docker commands
- ✅ Know Dockerfile instructions
- ✅ Learn Docker Compose basics
- ✅ Understand networking and volumes
- ✅ Know Docker security best practices

---

# 📝 Summary

This chapter covered:

- Beginner Questions
- Intermediate Questions
- Advanced Questions
- Scenario-Based Questions
- Common Docker Commands
- Interview Tips

---

# 📚 Further Reading

- Docker Documentation
- Dockerfile Reference
- Docker Compose Documentation
- Docker Best Practices
- Docker Security Guide

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [20 - Docker on AWS](20-Docker-on-AWS.md) | [Docker Roadmap](README.md) | [22 - Docker Cheat Sheet](22-Docker-Cheat-Sheet.md) |

---

# 🚀 What's Next?

In **Chapter 22 – Docker Cheat Sheet**, you'll get:

- 🐳 Essential Docker Commands
- 📦 Image Commands
- 📁 Volume Commands
- 🌐 Network Commands
- 🛠️ Docker Compose Commands
- ⚡ Troubleshooting Commands
- 📋 Quick Revision for Interviews and Daily Work
