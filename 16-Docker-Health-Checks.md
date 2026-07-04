# Docker Notes
# Chapter 16 - Docker Health Checks

> 📘 **Level:** Beginner to Intermediate
> ⏱️ **Estimated Reading Time:** 45–60 minutes
> 🛠️ **Practice Time:** 2–3 hours

---

# 📚 Table of Contents

1. What are Docker Health Checks?
2. Why Health Checks?
3. Health Check Workflow
4. HEALTHCHECK Instruction
5. Health Status
6. Health Check Commands
7. Docker Compose Health Checks
8. Useful Commands
9. Best Practices
10. Summary
11. Interview Questions
12. Practice Exercises
13. Mini Project
14. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Docker Health Checks
- Configure health checks in Dockerfile
- Monitor container health
- View health status
- Follow production best practices

---

# 📖 What are Docker Health Checks?

A **Health Check** allows Docker to determine whether a containerized application is **healthy** and functioning correctly.

Instead of checking only if a container is running, Docker periodically executes a command to verify the application's health.

---

# 💡 Why Health Checks?

Without Health Check:

```text
Container Running

↓

Application Crashed

↓

Docker Shows Running ❌
```

With Health Check:

```text
Container Running

↓

Health Check Fails

↓

Status = Unhealthy ✅
```

Benefits:

- ✅ Detect application failures
- ✅ Improve monitoring
- ✅ Support automatic recovery
- ✅ Better production reliability

---

# 🏗️ Health Check Workflow

```text
Container Starts
       │
       ▼
Run Health Check
       │
       ▼
Application Responds?
   │          │
 Yes         No
 │            │
 ▼            ▼
Healthy   Unhealthy
```

---

# ❤️ HEALTHCHECK Instruction

Add a health check in the Dockerfile.

Example:

```dockerfile
FROM nginx

HEALTHCHECK CMD curl -f http://localhost/ || exit 1
```

Docker periodically executes the command.

- Exit code `0` → Healthy
- Exit code `1` → Unhealthy

---

# ⚙️ HEALTHCHECK Options

Example:

```dockerfile
HEALTHCHECK \
--interval=30s \
--timeout=5s \
--retries=3 \
CMD curl -f http://localhost/ || exit 1
```

Options:

| Option | Description |
|--------|-------------|
| `--interval` | Time between checks |
| `--timeout` | Maximum wait time |
| `--retries` | Failed attempts before unhealthy |
| `--start-period` | Grace period before checks begin |

---

# 📊 Health Status

Docker reports one of the following states:

| Status | Meaning |
|--------|---------|
| starting | Health check is initializing |
| healthy | Application is working |
| unhealthy | Health check has failed |

---

# 🐳 Docker Compose Health Check

Example:

```yaml
version: "3.9"

services:
  web:
    image: nginx

    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost"]
      interval: 30s
      timeout: 5s
      retries: 3
```

---

# 🔍 Check Container Health

View running containers:

```bash
docker ps
```

Inspect container:

```bash
docker inspect <container-name>
```

Look for:

```text
State

↓

Health
```

---

# 📜 Disable Health Check

Run a container without the configured health check:

```bash
docker run --no-healthcheck nginx
```

---

# 📊 Useful Docker Commands

View running containers:

```bash
docker ps
```

Inspect health:

```bash
docker inspect nginx
```

View logs:

```bash
docker logs nginx
```

Monitor resources:

```bash
docker stats
```

---

# 🏗️ Health Check Workflow

```text
Dockerfile
      │
      ▼
HEALTHCHECK
      │
      ▼
Container Starts
      │
      ▼
Periodic Check
      │
      ▼
Healthy / Unhealthy
```

---

# 🏆 Best Practices

- ✅ Add health checks to production containers
- ✅ Use lightweight commands
- ✅ Keep intervals reasonable
- ✅ Avoid long-running health checks
- ✅ Monitor unhealthy containers
- ✅ Combine with restart policies
- ✅ Test health checks before deployment

---

# 🌍 Common Use Cases

| Application | Health Check |
|-------------|--------------|
| Nginx | HTTP request |
| Node.js | `/health` endpoint |
| Spring Boot | `/actuator/health` |
| Python Flask | `/health` route |
| MySQL | `mysqladmin ping` |
| Redis | `redis-cli ping` |

---

# 📝 Key Takeaways

- Health Checks verify application health, not just container status.
- The `HEALTHCHECK` instruction is added in the Dockerfile.
- Docker reports **starting**, **healthy**, or **unhealthy**.
- Health checks improve reliability and monitoring.
- Combine health checks with restart policies for production.

---

# 📋 Summary

In this chapter, you learned:

- Docker Health Checks
- HEALTHCHECK Instruction
- Health Status
- Docker Compose Health Checks
- Useful Commands
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. What is a Docker Health Check?
2. Why are Health Checks important?
3. What does the `HEALTHCHECK` instruction do?
4. What are the possible health states?
5. How do you inspect a container's health?

---

## Intermediate

6. Explain the Health Check workflow.
7. What is the purpose of `--interval` and `--timeout`?
8. How do you configure Health Checks in Docker Compose?
9. Difference between a running container and a healthy container?
10. Why should Health Checks be lightweight?

---

## Advanced

11. How do orchestrators like Kubernetes use health checks?
12. How would you design health endpoints for microservices?
13. Explain Docker Health Checks in production deployments.
14. How do restart policies work with unhealthy containers?
15. What are common Health Check mistakes?

---

# 🎯 Practice Exercises

## Exercise 1

Create a Dockerfile with a health check.

---

## Exercise 2

Build the image.

```bash
docker build -t myapp .
```

---

## Exercise 3

Run the container.

```bash
docker run -d myapp
```

---

## Exercise 4

Inspect the health status.

```bash
docker inspect <container-name>
```

---

## Exercise 5

Create a Docker Compose file with a health check.

---

# 🧩 Mini Project

Create a file named:

```text
docker-health-checks-guide.md
```

Include:

- Health Check Overview
- HEALTHCHECK Instruction
- Docker Compose Configuration
- Health Status
- Best Practices

Commit to Git:

```bash
git add .
git commit -m "Add Docker Health Checks guide"
```

---

# 📚 Further Reading

- Docker HEALTHCHECK Documentation
- Dockerfile Reference
- Docker Compose Documentation
- Container Monitoring Best Practices

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [15 - Docker Environment Variables](15-Docker-Environment-Variables.md) | [Docker Roadmap](README.md) | [17 - Docker Best Practices](17-Docker-Best-Practices.md) |

---

# 🚀 What's Next?

In **Chapter 17 – Docker Best Practices**, you'll learn:

- 🏗️ Writing Efficient Dockerfiles
- 📦 Optimizing Image Size
- 🚀 Multi-Stage Builds
- 🔒 Docker Security Best Practices
- ⚡ Performance Optimization
- 📋 Common Mistakes to Avoid
- 🛠️ Production Deployment Guidelines
