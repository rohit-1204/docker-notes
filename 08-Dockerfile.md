# Docker Notes
# Chapter 08 - Dockerfile

> 📘 **Level:** Beginner to Intermediate
> ⏱️ **Estimated Reading Time:** 90–120 minutes
> 🛠️ **Practice Time:** 5–6 hours

---

# 📚 Table of Contents

1. What is a Dockerfile?
2. Why Use Dockerfile?
3. Docker Build Process
4. Dockerfile Structure
5. Common Instructions
6. COPY vs ADD
7. CMD vs ENTRYPOINT
8. ENV & ARG
9. WORKDIR
10. EXPOSE
11. USER
12. Building an Image
13. Docker Build Cache
14. Best Practices
15. Summary
16. Interview Questions
17. Practice Exercises
18. Mini Project
19. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Dockerfiles
- Build custom Docker images
- Use common Dockerfile instructions
- Optimize image size
- Follow Docker best practices

---

# 📖 What is a Dockerfile?

A **Dockerfile** is a text file containing a list of instructions used to automatically build a Docker image.

Instead of manually creating containers, Docker executes these instructions one by one.

Example:

```text
Dockerfile
      │
      ▼
docker build
      │
      ▼
Docker Image
      │
      ▼
Docker Container
```

---

# 💡 Why Use Dockerfile?

Benefits:

- ✅ Automates image creation
- ✅ Reproducible builds
- ✅ Easy version control
- ✅ Consistent deployments
- ✅ Supports CI/CD pipelines

---

# 🏗️ Docker Build Process

```text
Dockerfile
      │
      ▼
docker build
      │
      ▼
Docker Image
      │
      ▼
docker run
      │
      ▼
Container
```

---

# 📄 Basic Dockerfile

```dockerfile
FROM ubuntu:22.04

RUN apt update

CMD ["echo", "Hello Docker"]
```

Build:

```bash
docker build -t myimage .
```

Run:

```bash
docker run myimage
```

---

# 📦 Common Dockerfile Instructions

| Instruction | Purpose |
|-------------|----------|
| FROM | Base Image |
| RUN | Execute Commands |
| COPY | Copy Files |
| ADD | Copy Files & URLs |
| CMD | Default Command |
| ENTRYPOINT | Main Executable |
| ENV | Environment Variables |
| ARG | Build Variables |
| WORKDIR | Working Directory |
| EXPOSE | Document Port |
| USER | Run as Specific User |

---

# 🏗️ FROM

Defines the base image.

```dockerfile
FROM ubuntu:22.04
```

Examples:

```dockerfile
FROM nginx

FROM python:3.12

FROM node:20
```

Every Dockerfile should begin with a `FROM` instruction.

---

# ⚙️ RUN

Executes commands while building the image.

```dockerfile
RUN apt update
RUN apt install -y nginx
```

Multiple commands:

```dockerfile
RUN apt update && \
    apt install -y nginx
```

---

# 📂 COPY

Copies files from the local machine into the image.

```dockerfile
COPY app.py /app/
```

Copy an entire folder:

```dockerfile
COPY . /app
```

---

# ➕ ADD

Similar to COPY, but can also:

- Extract compressed archives
- Download files from URLs

```dockerfile
ADD app.tar.gz /app
```

Use `COPY` unless you specifically need ADD features.

---

# 📋 COPY vs ADD

| COPY | ADD |
|------|-----|
| Copies Local Files | Copies Local Files |
| Simple & Predictable | Supports URLs |
| No Extraction | Auto Extracts Archives |
| Recommended | Use Only When Needed |

---

# ▶️ CMD

Defines the default command when the container starts.

```dockerfile
CMD ["nginx", "-g", "daemon off;"]
```

Only the **last CMD** in the Dockerfile is used.

---

# 🚀 ENTRYPOINT

Defines the main executable for the container.

```dockerfile
ENTRYPOINT ["python3"]
```

Run:

```bash
docker run myimage app.py
```

Result:

```text
python3 app.py
```

---

# 📋 CMD vs ENTRYPOINT

| CMD | ENTRYPOINT |
|------|------------|
| Default Command | Fixed Command |
| Easily Overridden | Harder to Override |
| Optional | Main Executable |

Example:

```dockerfile
ENTRYPOINT ["python3"]

CMD ["app.py"]
```

Running:

```bash
docker run myimage
```

Executes:

```text
python3 app.py
```

---

# 🌍 ENV

Sets environment variables.

```dockerfile
ENV APP_ENV=production
```

Example:

```dockerfile
ENV PORT=8080
```

---

# 🔧 ARG

Defines build-time variables.

```dockerfile
ARG VERSION=1.0
```

Build:

```bash
docker build --build-arg VERSION=2.0 .
```

Difference:

| ENV | ARG |
|-----|-----|
| Available at Runtime | Only During Build |
| Stored in Image | Not Available After Build |

---

# 📁 WORKDIR

Sets the working directory.

```dockerfile
WORKDIR /app
```

Equivalent to:

```bash
cd /app
```

---

# 🌐 EXPOSE

Documents which port the application uses.

```dockerfile
EXPOSE 80
```

Example:

```dockerfile
EXPOSE 8080
```

> **Note:** `EXPOSE` does not publish the port. Use `-p` with `docker run`.

---

# 👤 USER

Runs the container as a non-root user.

```dockerfile
USER appuser
```

Improves security.

---

# 🏗️ Build an Image

Build:

```bash
docker build -t myapp .
```

Build with version tag:

```bash
docker build -t myapp:v1 .
```

---

# ▶️ Run the Image

```bash
docker run myapp
```

With port mapping:

```bash
docker run -d -p 8080:80 myapp
```

---

# ⚡ Docker Build Cache

Docker caches image layers.

Benefits:

- Faster builds
- Reuses unchanged layers
- Saves bandwidth

Rebuild without cache:

```bash
docker build --no-cache -t myapp .
```

---

# 🏗️ Dockerfile Example (Python)

```dockerfile
FROM python:3.12

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt

EXPOSE 5000

CMD ["python", "app.py"]
```

---

# 🏗️ Dockerfile Example (Node.js)

```dockerfile
FROM node:20

WORKDIR /app

COPY . .

RUN npm install

EXPOSE 3000

CMD ["npm", "start"]
```

---

# 🏗️ Dockerfile Workflow

```text
Write Dockerfile
       │
       ▼
docker build
       │
       ▼
Docker Image
       │
       ▼
docker run
       │
       ▼
Application Running
```

---

# 🏆 Best Practices

- ✅ Use official base images
- ✅ Keep images small
- ✅ Combine RUN commands
- ✅ Use COPY instead of ADD
- ✅ Use `.dockerignore`
- ✅ Avoid running as root
- ✅ Use version tags instead of `latest`
- ✅ Place frequently changing instructions near the end

---

# 📝 Key Takeaways

- Dockerfiles automate image creation.
- Every Dockerfile starts with `FROM`.
- `COPY` is preferred over `ADD`.
- `CMD` defines the default command.
- `ENTRYPOINT` defines the main executable.
- `ENV` is for runtime variables.
- `ARG` is for build-time variables.

---

# 📋 Summary

In this chapter, you learned:

- Dockerfile Basics
- Dockerfile Instructions
- COPY vs ADD
- CMD vs ENTRYPOINT
- ENV & ARG
- WORKDIR
- EXPOSE
- USER
- Docker Build Process
- Build Cache
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. What is a Dockerfile?
2. What is the purpose of `FROM`?
3. What does `RUN` do?
4. What is `COPY` used for?
5. What is `CMD`?

---

## Intermediate

6. Difference between `COPY` and `ADD`?
7. Difference between `CMD` and `ENTRYPOINT`?
8. Difference between `ENV` and `ARG`?
9. What is `WORKDIR`?
10. Explain Docker build cache.

---

## Advanced

11. How do you optimize a Dockerfile?
12. Why should you avoid the `latest` tag?
13. How do Docker image layers improve build performance?
14. Why should containers avoid running as root?
15. Explain the Docker image build process.

---

# 🎯 Practice Exercises

## Exercise 1

Create a Dockerfile using Ubuntu.

---

## Exercise 2

Build an image.

```bash
docker build -t demo-app .
```

---

## Exercise 3

Run the image.

```bash
docker run demo-app
```

---

## Exercise 4

Add an environment variable.

```dockerfile
ENV APP_ENV=production
```

---

## Exercise 5

Expose port 8080.

```dockerfile
EXPOSE 8080
```

---

# 🧩 Mini Project

Create a file named:

```text
dockerfile-guide.md
```

Include:

- Dockerfile Overview
- Common Instructions
- COPY vs ADD
- CMD vs ENTRYPOINT
- ENV vs ARG
- Best Practices

Commit to Git:

```bash
git add .
git commit -m "Add Dockerfile guide"
```

---

# 📚 Further Reading

- Dockerfile Reference
- Docker Build Documentation
- Docker Best Practices
- Docker CLI Reference

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [07 - Docker Networking](07-Docker-Networking.md) | [Docker Roadmap](README.md) | [09 - Docker Compose](09-Docker-Compose.md) |

---

# 🚀 What's Next?

In **Chapter 09 – Docker Compose**, you'll learn:

- 🧩 What is Docker Compose?
- 📝 `docker-compose.yml`
- 🏗️ Multi-Container Applications
- 🌐 Networks & Volumes
- ⚙️ Environment Variables
- 🚀 Deploying Applications with Docker Compose
- 🛠️ Compose Commands & Best Practices
