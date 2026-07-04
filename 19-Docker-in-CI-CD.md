# Docker Notes
# Chapter 19 - Docker in CI/CD

> 📘 **Level:** Beginner to Intermediate
> ⏱️ **Estimated Reading Time:** 60–75 minutes
> 🛠️ **Practice Time:** 3–4 hours

---

# 📚 Table of Contents

1. What is CI/CD?
2. Why Use Docker in CI/CD?
3. CI/CD Workflow
4. Docker Build Stage
5. Docker Test Stage
6. Push Image to Registry
7. Deployment Stage
8. CI/CD Tools
9. Example Pipeline
10. Best Practices
11. Summary
12. Interview Questions
13. Practice Exercises
14. Mini Project
15. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand CI/CD concepts
- Use Docker in CI/CD pipelines
- Build and test Docker images
- Push images to a container registry
- Deploy Dockerized applications

---

# 📖 What is CI/CD?

**CI (Continuous Integration)** is the practice of automatically building and testing code whenever changes are made.

**CD (Continuous Delivery/Deployment)** automates the release of applications to different environments.

Docker makes CI/CD more reliable by ensuring applications run the same way everywhere.

---

# 💡 Why Use Docker in CI/CD?

Without Docker:

```text
Developer

↓

Works on My Machine

↓

Deployment Failure ❌
```

With Docker:

```text
Developer

↓

Build Docker Image

↓

Test Image

↓

Deploy Same Image ✅
```

Benefits:

- ✅ Consistent environments
- ✅ Faster deployments
- ✅ Easy rollback
- ✅ Portable applications
- ✅ Reliable automation

---

# 🏗️ CI/CD Workflow

```text
Developer

↓

Git Push

↓

CI Server

↓

Build Docker Image

↓

Run Tests

↓

Push Image

↓

Deploy Application
```

---

# 📦 Build Docker Image

Example:

```bash
docker build -t myapp:v1 .
```

The CI server builds a new Docker image whenever code changes are pushed.

---

# 🧪 Test Docker Image

Run automated tests inside a container.

Example:

```bash
docker run --rm myapp:v1
```

If the tests fail, the pipeline stops.

---

# 📤 Push Image to Registry

After successful tests, push the image to a registry.

Example:

```bash
docker tag myapp:v1 myrepo/myapp:v1

docker push myrepo/myapp:v1
```

Common registries:

- Docker Hub
- Amazon ECR
- Google Artifact Registry
- GitHub Container Registry
- Azure Container Registry

---

# 🚀 Deploy Application

Deployment environments:

```text
Development

↓

Testing

↓

Staging

↓

Production
```

Deployment methods:

- Docker Compose
- Docker Swarm
- Kubernetes
- Amazon ECS
- Amazon EKS

---

# 🛠️ Popular CI/CD Tools

| Tool | Purpose |
|------|---------|
| Jenkins | CI/CD Automation |
| GitHub Actions | GitHub Workflows |
| GitLab CI/CD | Integrated Pipelines |
| Azure DevOps | Build & Release |
| CircleCI | Cloud CI/CD |
| AWS CodePipeline | AWS CI/CD |

---

# 📄 Example CI/CD Pipeline

```text
Code Commit
      │
      ▼
Build Docker Image
      │
      ▼
Run Tests
      │
      ▼
Security Scan
      │
      ▼
Push to Registry
      │
      ▼
Deploy to Production
```

---

# 📊 Useful Docker Commands

Build image:

```bash
docker build -t myapp:v1 .
```

Run container:

```bash
docker run myapp:v1
```

Tag image:

```bash
docker tag myapp:v1 myrepo/myapp:v1
```

Push image:

```bash
docker push myrepo/myapp:v1
```

Pull image:

```bash
docker pull myrepo/myapp:v1
```

---

# 🏆 Best Practices

- ✅ Automate builds and tests
- ✅ Use version tags instead of `latest`
- ✅ Scan images before deployment
- ✅ Store images in a secure registry
- ✅ Use Multi-Stage Builds
- ✅ Keep CI/CD pipelines fast
- ✅ Roll back using previous image versions
- ✅ Never store secrets in Docker images

---

# 🌍 Common Use Cases

| Scenario | Docker in CI/CD |
|----------|-----------------|
| Build Application | ✅ |
| Automated Testing | ✅ |
| Push to Registry | ✅ |
| Deploy to Kubernetes | ✅ |
| Deploy to ECS | ✅ |
| Rollback Releases | ✅ |

---

# 📝 Key Takeaways

- CI/CD automates software delivery.
- Docker provides consistent build and runtime environments.
- Images are built, tested, pushed, and deployed automatically.
- Container registries store versioned Docker images.
- Automation improves speed and reliability.

---

# 📋 Summary

In this chapter, you learned:

- CI/CD Basics
- Docker in CI/CD
- Image Build
- Testing
- Registry
- Deployment
- CI/CD Tools
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. What is CI/CD?
2. Why is Docker used in CI/CD?
3. What happens after building a Docker image?
4. What is a container registry?
5. Name some CI/CD tools.

---

## Intermediate

6. Explain a Docker CI/CD pipeline.
7. Why should images be versioned?
8. What is the purpose of automated testing?
9. Why should images be scanned before deployment?
10. Explain image promotion across environments.

---

## Advanced

11. Design a CI/CD pipeline using Docker and Kubernetes.
12. How do you implement rollback in Docker deployments?
13. Explain blue-green deployment using Docker.
14. How would you secure a Docker CI/CD pipeline?
15. What are common CI/CD pipeline failures and how would you troubleshoot them?

---

# 🎯 Practice Exercises

## Exercise 1

Build a Docker image.

```bash
docker build -t myapp:v1 .
```

---

## Exercise 2

Run the application.

```bash
docker run myapp:v1
```

---

## Exercise 3

Tag the image.

```bash
docker tag myapp:v1 myrepo/myapp:v1
```

---

## Exercise 4

Push the image to Docker Hub.

```bash
docker push myrepo/myapp:v1
```

---

## Exercise 5

Create a simple CI/CD pipeline using GitHub Actions or Jenkins.

---

# 🧩 Mini Project

Create a file named:

```text
docker-cicd-guide.md
```

Include:

- CI/CD Overview
- Docker Build Process
- Image Testing
- Registry Push
- Deployment Workflow
- Best Practices

Commit to Git:

```bash
git add .
git commit -m "Add Docker CI/CD guide"
```

---

# 📚 Further Reading

- Docker CI Documentation
- Docker Hub Documentation
- GitHub Actions Documentation
- Jenkins Documentation
- Kubernetes Deployment Guide

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [18 - Docker Best Practices](18-Docker-Best-Practices.md) | [Docker Roadmap](README.md) | [20 - Docker Cheat Sheet](20-Docker-Cheat-Sheet.md) |

---

# 🚀 What's Next?

In **Chapter 20 – Docker Cheat Sheet**, you'll learn:

- 🐳 Essential Docker Commands
- 📦 Image Management
- 📁 Volume Commands
- 🌐 Network Commands
- 🛠️ Docker Compose Commands
- ⚡ Troubleshooting Commands
- 🚀 Quick Reference for Daily Use and Interviews
