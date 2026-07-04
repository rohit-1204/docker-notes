# Docker Notes
# Chapter 11 - Docker Hub

> 📘 **Level:** Beginner
> ⏱️ **Estimated Reading Time:** 45–60 minutes
> 🛠️ **Practice Time:** 2–3 hours

---

# 📚 Table of Contents

1. What is Docker Hub?
2. Why Use Docker Hub?
3. Docker Hub Features
4. Create a Docker Hub Account
5. Login to Docker Hub
6. Docker Image Naming
7. Push Images
8. Pull Images
9. Manage Repositories
10. Useful Commands
11. Best Practices
12. Summary
13. Interview Questions
14. Practice Exercises
15. Mini Project
16. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Docker Hub
- Create repositories
- Push and pull Docker images
- Manage image versions
- Share images with others

---

# 📖 What is Docker Hub?

**Docker Hub** is the official cloud-based registry provided by Docker.

It allows you to:

- 📦 Store Docker images
- 📤 Push custom images
- 📥 Pull existing images
- 🤝 Share images with teams
- 🔄 Manage image versions

---

# 💡 Why Use Docker Hub?

Without Docker Hub:

```text
Developer

↓

Build Image

↓

Copy Image Manually

↓

Production Server
```

Problems:

- ❌ Manual transfers
- ❌ No version control
- ❌ Difficult collaboration

---

With Docker Hub:

```text
Developer

↓

Build Image

↓

Push Image

↓

Docker Hub

↓

Production Server

↓

Pull Image
```

Benefits:

- ✅ Centralized image storage
- ✅ Easy sharing
- ✅ Version control
- ✅ CI/CD integration
- ✅ Global accessibility

---

# 🏗️ Docker Hub Architecture

```text
Developer PC
      │
docker push
      │
      ▼
 Docker Hub
      │
docker pull
      │
      ▼
Production Server
```

---

# 🌟 Docker Hub Features

- 📦 Public repositories
- 🔒 Private repositories
- 🏷️ Image versioning
- 🔍 Search official images
- 🤝 Team collaboration
- 🔄 Automated builds (GitHub integration)
- 🛡️ Security scanning (paid plans)

---

# 👤 Create a Docker Hub Account

1. Visit **https://hub.docker.com**
2. Click **Sign Up**
3. Create your account
4. Verify your email
5. Login to Docker Hub

---

# 🔑 Login to Docker Hub

Login:

```bash
docker login
```

Example:

```text
Username: johndoe

Password: ********
```

Verify:

```bash
docker info
```

---

# 🏷️ Docker Image Naming

Format:

```text
username/repository:tag
```

Examples:

```text
john/myapp:v1

john/nginx:latest

company/backend:v2
```

---

# 📦 Create a Repository

On Docker Hub:

```
Repositories

↓

Create Repository

↓

Repository Name

↓

Public / Private

↓

Create
```

Example:

```
john/myapp
```

---

# 📤 Push an Image

Step 1: Build the image

```bash
docker build -t myapp .
```

Step 2: Tag the image

```bash
docker tag myapp john/myapp:v1
```

Step 3: Push

```bash
docker push john/myapp:v1
```

---

# 📥 Pull an Image

Pull latest version:

```bash
docker pull nginx
```

Pull custom image:

```bash
docker pull john/myapp:v1
```

---

# 🏷️ Image Tags

Tags represent image versions.

Examples:

```text
latest

v1

v1.0

v2

stable

production
```

Create another tag:

```bash
docker tag myapp john/myapp:latest
```

---

# 🔍 Search Images

Search Docker Hub:

```bash
docker search nginx
```

Example:

```text
NAME

nginx

mysql

redis
```

---

# 📋 List Local Images

```bash
docker images
```

---

# 🚪 Logout

Logout from Docker Hub:

```bash
docker logout
```

---

# 🏗️ Docker Hub Workflow

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
Login
       │
       ▼
Push Image
       │
       ▼
Docker Hub
       │
       ▼
Pull Anywhere
```

---

# 📊 Useful Docker Hub Commands

Login:

```bash
docker login
```

Logout:

```bash
docker logout
```

Search Images:

```bash
docker search nginx
```

Pull Image:

```bash
docker pull nginx
```

Tag Image:

```bash
docker tag myapp john/myapp:v1
```

Push Image:

```bash
docker push john/myapp:v1
```

List Images:

```bash
docker images
```

---

# 🏆 Best Practices

- ✅ Use meaningful repository names
- ✅ Tag every release
- ✅ Avoid using `latest` in production
- ✅ Keep repositories organized
- ✅ Remove unused images
- ✅ Push only tested images
- ✅ Use private repositories for sensitive applications

---

# 🌍 Common Use Cases

| Use Case | Example |
|----------|---------|
| Store application images | Web apps |
| Share images with teams | Development |
| CI/CD deployments | Jenkins, GitHub Actions |
| Kubernetes deployments | Pull images from Docker Hub |
| Learning & Testing | Official Images |

---

# 📝 Key Takeaways

- Docker Hub is the official Docker registry.
- Images are stored in repositories.
- Images should be tagged before pushing.
- Public and private repositories are supported.
- Docker Hub integrates with CI/CD pipelines.

---

# 📋 Summary

In this chapter, you learned:

- Docker Hub
- Repository Management
- Image Tagging
- Push & Pull Operations
- Docker Hub Commands
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. What is Docker Hub?
2. What is a Docker repository?
3. How do you login to Docker Hub?
4. How do you push an image?
5. How do you pull an image?

---

## Intermediate

6. Difference between Docker Hub and Docker Registry.
7. Why are image tags important?
8. Explain Docker Hub workflow.
9. What are public and private repositories?
10. How do you organize Docker repositories?

---

## Advanced

11. How does Docker Hub integrate with CI/CD?
12. Why should production images use version tags?
13. How would you secure Docker Hub repositories?
14. Explain Docker image versioning strategy.
15. What are the limitations of Docker Hub?

---

# 🎯 Practice Exercises

## Exercise 1

Login to Docker Hub.

```bash
docker login
```

---

## Exercise 2

Search for the Ubuntu image.

```bash
docker search ubuntu
```

---

## Exercise 3

Build and tag an image.

```bash
docker build -t myapp .
docker tag myapp username/myapp:v1
```

---

## Exercise 4

Push the image.

```bash
docker push username/myapp:v1
```

---

## Exercise 5

Pull the image on another machine.

```bash
docker pull username/myapp:v1
```

---

# 🧩 Mini Project

Create a Markdown file named:

```text
docker-hub-guide.md
```

Include:

- Docker Hub Overview
- Repository Management
- Image Tagging
- Push & Pull Commands
- Best Practices

Commit to Git:

```bash
git add .
git commit -m "Add Docker Hub guide"
```

---

# 📚 Further Reading

- Docker Hub Documentation
- Docker CLI Reference
- Docker Image Best Practices
- Docker Official Images

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [10 - Docker Registry](10-Docker-Registry.md) | [Docker Roadmap](README.md) | [12 - Docker Swarm](12-Docker-Swarm.md) |

---

# 🚀 What's Next?

In **Chapter 12 – Docker Swarm**, you'll learn:

- 🐝 What is Docker Swarm?
- 👑 Manager & Worker Nodes
- ⚖️ Load Balancing
- 📈 Scaling Services
- 🔄 Rolling Updates
- 🛡️ High Availability
- 🚀 Swarm Deployment
- 🛠️ Swarm Commands
- ☸️ Comparison with Kubernetes
