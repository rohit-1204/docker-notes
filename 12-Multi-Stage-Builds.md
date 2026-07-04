# Docker Notes
# Chapter 12 - Multi-Stage Builds

> 📘 **Level:** Intermediate
> ⏱️ **Estimated Reading Time:** 60–90 minutes
> 🛠️ **Practice Time:** 4–5 hours

---

# 📚 Table of Contents

1. What are Multi-Stage Builds?
2. Why Use Multi-Stage Builds?
3. Build Process
4. Single Stage vs Multi-Stage
5. Build Stages
6. COPY --from
7. Example (Go)
8. Example (Node.js)
9. Example (Java)
10. Best Practices
11. Summary
12. Interview Questions
13. Practice Exercises
14. Mini Project
15. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Multi-Stage Builds
- Reduce Docker image size
- Separate build and runtime environments
- Improve security
- Create production-ready Docker images

---

# 📖 What are Multi-Stage Builds?

A **Multi-Stage Build** allows you to use multiple `FROM` instructions in a single Dockerfile.

The first stage builds the application, while the final stage contains only the files required to run it.

This results in:

- ✅ Smaller images
- ✅ Faster deployments
- ✅ Better security
- ✅ Cleaner Dockerfiles

---

# 💡 Why Use Multi-Stage Builds?

### Single Stage Build

```text
Source Code
      │
      ▼
Compiler
      │
Libraries
      │
Tools
      │
Application
      │
Large Docker Image ❌
```

Problems:

- Large image size
- Build tools included
- More security risks

---

### Multi-Stage Build

```text
Build Stage
      │
Compile Application
      │
      ▼
Runtime Stage
      │
Copy Binary
      │
Small Docker Image ✅
```

Benefits:

- Smaller images
- Faster startup
- Reduced attack surface
- Easier maintenance

---

# 🏗️ Multi-Stage Build Process

```text
Source Code
      │
      ▼
Build Stage
      │
Compile
      │
      ▼
Copy Output
      │
      ▼
Runtime Stage
      │
      ▼
Production Image
```

---

# 🆚 Single Stage vs Multi-Stage

| Single Stage | Multi-Stage |
|--------------|-------------|
| Large Image | Small Image |
| Build Tools Included | Only Runtime Files |
| Slower Deployment | Faster Deployment |
| Less Secure | More Secure |
| Difficult to Maintain | Cleaner Structure |

---

# 📝 Basic Multi-Stage Dockerfile

```dockerfile
# Build Stage
FROM golang:1.22 AS builder

WORKDIR /app

COPY . .

RUN go build -o app

# Runtime Stage
FROM alpine:latest

WORKDIR /app

COPY --from=builder /app/app .

CMD ["./app"]
```

---

# 📦 COPY --from

The `COPY --from` instruction copies files from a previous build stage.

Syntax:

```dockerfile
COPY --from=<stage-name> <source> <destination>
```

Example:

```dockerfile
COPY --from=builder /app/app /app/app
```

---

# 🟦 Example: Go Application

```dockerfile
FROM golang:1.22 AS builder

WORKDIR /src

COPY . .

RUN go build -o server

FROM alpine

COPY --from=builder /src/server .

CMD ["./server"]
```

---

# 🟩 Example: Node.js Application

```dockerfile
FROM node:20 AS builder

WORKDIR /app

COPY . .

RUN npm install

RUN npm run build

FROM nginx:latest

COPY --from=builder /app/dist /usr/share/nginx/html
```

---

# ☕ Example: Java Application

```dockerfile
FROM maven:3.9 AS builder

WORKDIR /app

COPY . .

RUN mvn package

FROM eclipse-temurin:21-jre

COPY --from=builder /app/target/app.jar app.jar

CMD ["java","-jar","app.jar"]
```

---

# 🚀 Build the Image

```bash
docker build -t myapp:v1 .
```

---

# ▶️ Run the Container

```bash
docker run myapp:v1
```

---

# 🏗️ Multi-Stage Build Workflow

```text
Dockerfile
      │
      ▼
Build Stage
      │
Compile Source Code
      │
      ▼
Runtime Stage
      │
Copy Application
      │
      ▼
Small Production Image
```

---

# 📊 Useful Commands

Build Image:

```bash
docker build -t myapp:v1 .
```

List Images:

```bash
docker images
```

Run Image:

```bash
docker run myapp:v1
```

Inspect Image:

```bash
docker image inspect myapp:v1
```

Remove Image:

```bash
docker rmi myapp:v1
```

---

# 🏆 Best Practices

- ✅ Use Multi-Stage Builds for production
- ✅ Use lightweight runtime images (Alpine, Distroless)
- ✅ Name build stages using `AS`
- ✅ Copy only required files
- ✅ Remove unnecessary dependencies
- ✅ Use official base images
- ✅ Keep runtime images minimal

---

# 🌍 Common Use Cases

| Application | Multi-Stage Benefit |
|-------------|---------------------|
| Go | Small binary image |
| Java | Remove Maven after build |
| Node.js | Copy only build artifacts |
| React | Deploy static files with Nginx |
| Python | Separate build dependencies |
| .NET | Runtime-only production image |

---

# 📝 Key Takeaways

- Multi-Stage Builds use multiple `FROM` instructions.
- Build tools stay in the build stage.
- Runtime images contain only required files.
- Smaller images improve deployment speed and security.
- `COPY --from` is used to copy files between stages.

---

# 📋 Summary

In this chapter, you learned:

- Multi-Stage Builds
- Build vs Runtime Stage
- COPY --from
- Build Workflow
- Multi-Stage Examples
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. What is a Multi-Stage Build?
2. Why are Multi-Stage Builds used?
3. What does `COPY --from` do?
4. Can a Dockerfile have multiple `FROM` instructions?
5. What is the advantage of smaller images?

---

## Intermediate

6. Difference between Single Stage and Multi-Stage Builds?
7. Why should build tools not be included in production images?
8. How do Multi-Stage Builds improve security?
9. Explain the build workflow.
10. What is the purpose of naming build stages?

---

## Advanced

11. How do Multi-Stage Builds reduce attack surface?
12. Explain how Docker caches build stages.
13. Why are Distroless images often used with Multi-Stage Builds?
14. How would you optimize a production Dockerfile?
15. Explain a real-world Multi-Stage Build for a microservice.

---

# 🎯 Practice Exercises

## Exercise 1

Create a Multi-Stage Dockerfile.

---

## Exercise 2

Build the image.

```bash
docker build -t myapp:v1 .
```

---

## Exercise 3

Run the container.

```bash
docker run myapp:v1
```

---

## Exercise 4

Inspect the image.

```bash
docker image inspect myapp:v1
```

---

## Exercise 5

Compare the image size with a single-stage build.

---

# 🧩 Mini Project

Create a file named:

```text
multi-stage-build-guide.md
```

Include:

- Multi-Stage Build Overview
- COPY --from
- Build Workflow
- Sample Dockerfile
- Best Practices

Commit to Git:

```bash
git add .
git commit -m "Add Multi-Stage Builds guide"
```

---

# 📚 Further Reading

- Docker Multi-Stage Builds Documentation
- Dockerfile Reference
- Docker Best Practices
- OCI Image Specification

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [11 - Docker Hub](11-Docker-Hub.md) | [Docker Roadmap](README.md) | [13 - Docker Security](13-Docker-Security.md) |

---

# 🚀 What's Next?

In **Chapter 13 – Docker Security**, you'll learn:

- 🔒 Docker Security Fundamentals
- 👤 Root vs Non-Root Containers
- 🛡️ Image Scanning
- 🔐 Secrets Management
- 📦 Content Trust
- 🚫 Container Isolation
- 🔍 Security Best Practices
- 🚀 Hardening Docker for Production
