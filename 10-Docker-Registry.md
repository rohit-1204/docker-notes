# Docker Notes
# Chapter 10 - Docker Registry

> 📘 **Level:** Beginner to Intermediate
> ⏱️ **Estimated Reading Time:** 60–75 minutes
> 🛠️ **Practice Time:** 3–4 hours

---

# 📚 Table of Contents

1. What is a Docker Registry?
2. Why Use a Registry?
3. Public vs Private Registry
4. Docker Hub
5. Amazon ECR
6. Image Naming Convention
7. Login to Registry
8. Push Images
9. Pull Images
10. Image Tags
11. Registry Workflow
12. Useful Commands
13. Best Practices
14. Summary
15. Interview Questions
16. Practice Exercises
17. Mini Project
18. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Docker Registries
- Push and pull Docker images
- Use Docker Hub and Amazon ECR
- Manage image tags
- Follow registry best practices

---

# 📖 What is a Docker Registry?

A **Docker Registry** is a repository that stores and distributes Docker images.

It allows developers to:

- Store Docker images
- Share images with teams
- Download images
- Maintain version history

Popular Registries:

- Docker Hub
- Amazon ECR
- Google Artifact Registry
- Azure Container Registry
- Harbor (Private Registry)

---

# 💡 Why Use a Docker Registry?

Without a Registry:

```text
Developer

↓

Build Image

↓

Copy Image Manually

↓

Server
```

Problems:

- ❌ Manual transfer
- ❌ Difficult version control
- ❌ Slow deployment

---

With a Registry:

```text
Developer

↓

Build Image

↓

Push to Registry

↓

Production Server

↓

Pull Image
```

Benefits:

- ✅ Centralized storage
- ✅ Easy sharing
- ✅ Version control
- ✅ Faster deployments
- ✅ CI/CD integration

---

# 🌐 Public vs Private Registry

| Public Registry | Private Registry |
|-----------------|------------------|
| Accessible by everyone | Restricted access |
| Suitable for open-source images | Suitable for enterprise applications |
| Example: Docker Hub | Example: Amazon ECR |

---

# 🐳 Docker Hub

Docker Hub is the default public Docker registry.

Features:

- Millions of public images
- Official Docker images
- Free and paid plans
- Easy integration with Docker CLI

Official Images:

- nginx
- ubuntu
- mysql
- redis
- node
- python

Pull an image:

```bash
docker pull nginx
```

---

# ☁️ Amazon ECR (Elastic Container Registry)

Amazon ECR is AWS's managed private container registry.

Features:

- Private repositories
- IAM integration
- Image scanning
- Encryption
- High availability
- AWS integration (ECS, EKS, Lambda)

Typical Workflow:

```text
Build Image

↓

Tag Image

↓

Push to Amazon ECR

↓

Deploy to ECS/EKS
```

---

# 🏷️ Docker Image Naming Convention

Image format:

```text
registry/repository:tag
```

Examples:

```text
nginx:latest

username/myapp:v1

123456789012.dkr.ecr.region.amazonaws.com/myapp:v1
```

---

# 🔑 Login to Docker Hub

Login:

```bash
docker login
```

Logout:

```bash
docker logout
```

---

# 🔑 Login to Amazon ECR

Authenticate using AWS CLI:

```bash
aws ecr get-login-password \
| docker login \
--username AWS \
--password-stdin <ecr-registry-url>
```

---

# 🏷️ Tag an Image

Create a new tag:

```bash
docker tag myapp myusername/myapp:v1
```

For Amazon ECR:

```bash
docker tag myapp:latest \
<ecr-registry-url>/myapp:v1
```

---

# 📤 Push an Image

Push to Docker Hub:

```bash
docker push myusername/myapp:v1
```

Push to Amazon ECR:

```bash
docker push <ecr-registry-url>/myapp:v1
```

---

# 📥 Pull an Image

Pull from Docker Hub:

```bash
docker pull nginx
```

Pull a specific version:

```bash
docker pull nginx:1.25
```

Pull from Amazon ECR:

```bash
docker pull <ecr-registry-url>/myapp:v1
```

---

# 🗑️ Remove Local Images

Delete an image:

```bash
docker rmi nginx
```

Delete all unused images:

```bash
docker image prune
```

---

# 🏗️ Registry Workflow

```text
Write Dockerfile
       │
       ▼
Build Image
       │
       ▼
Tag Image
       │
       ▼
Push to Registry
       │
       ▼
Pull on Server
       │
       ▼
Run Container
```

---

# 📊 Useful Docker Registry Commands

Login:

```bash
docker login
```

Logout:

```bash
docker logout
```

Tag Image:

```bash
docker tag myapp myuser/myapp:v1
```

Push Image:

```bash
docker push myuser/myapp:v1
```

Pull Image:

```bash
docker pull myuser/myapp:v1
```

List Local Images:

```bash
docker images
```

Remove Image:

```bash
docker rmi myapp
```

---

# 🏆 Best Practices

- ✅ Use private registries for production
- ✅ Tag images with versions (e.g., `v1.0.0`)
- ✅ Avoid using `latest` in production
- ✅ Remove unused images
- ✅ Scan images for vulnerabilities
- ✅ Use IAM roles and least privilege for ECR access
- ✅ Enable image lifecycle policies in ECR

---

# 🌍 Common Use Cases

| Registry | Use Case |
|-----------|----------|
| Docker Hub | Public images |
| Amazon ECR | AWS deployments |
| Azure Container Registry | Azure workloads |
| Google Artifact Registry | GCP deployments |
| Harbor | On-premises private registry |

---

# 📝 Key Takeaways

- Docker Registry stores Docker images.
- Docker Hub is the default public registry.
- Amazon ECR is a managed private registry on AWS.
- Images should be tagged before pushing.
- Registries are essential for CI/CD pipelines.

---

# 📋 Summary

In this chapter, you learned:

- Docker Registry
- Docker Hub
- Amazon ECR
- Image Tagging
- Push & Pull Operations
- Registry Workflow
- Docker Registry Commands
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. What is a Docker Registry?
2. What is Docker Hub?
3. What is Amazon ECR?
4. How do you push an image?
5. How do you pull an image?

---

## Intermediate

6. Difference between Docker Hub and Amazon ECR.
7. Why are image tags important?
8. Explain the Docker Registry workflow.
9. How do you authenticate with Amazon ECR?
10. Why should you avoid using the `latest` tag?

---

## Advanced

11. How do Docker Registries support CI/CD?
12. How do you secure a private registry?
13. Explain Amazon ECR lifecycle policies.
14. What is image vulnerability scanning?
15. How would you design an enterprise image repository strategy?

---

# 🎯 Practice Exercises

## Exercise 1

Login to Docker Hub.

```bash
docker login
```

---

## Exercise 2

Pull the Nginx image.

```bash
docker pull nginx
```

---

## Exercise 3

Tag the image.

```bash
docker tag nginx myusername/nginx:v1
```

---

## Exercise 4

Push the image to your Docker Hub repository.

```bash
docker push myusername/nginx:v1
```

---

## Exercise 5

Pull the image from Docker Hub.

```bash
docker pull myusername/nginx:v1
```

---

# 🧩 Mini Project

Create a file named:

```text
docker-registry-guide.md
```

Include:

- Docker Registry Overview
- Docker Hub
- Amazon ECR
- Push & Pull Commands
- Image Tagging
- Best Practices

Commit to Git:

```bash
git add .
git commit -m "Add Docker Registry guide"
```

---

# 📚 Further Reading

- Docker Hub Documentation
- Amazon ECR Documentation
- Docker CLI Reference
- OCI Image Specification

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [09 - Docker Compose](09-Docker-Compose.md) | [Docker Roadmap](README.md) | [11 - Docker Swarm](11-Docker-Swarm.md) |

---

# 🚀 What's Next?

In **Chapter 11 – Docker Swarm**, you'll learn:

- 🐝 What is Docker Swarm?
- 🏗️ Swarm Architecture
- 👑 Manager & Worker Nodes
- 🚀 Deploying Services
- ⚖️ Load Balancing
- 📈 Scaling Services
- 🔄 Rolling Updates
- 🛡️ High Availability
- 🛠️ Swarm Commands & Best Practices
