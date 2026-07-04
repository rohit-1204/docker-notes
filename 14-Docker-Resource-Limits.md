# Docker Notes
# Chapter 14 - Docker Resource Limits

> 📘 **Level:** Beginner to Intermediate
> ⏱️ **Estimated Reading Time:** 60–75 minutes
> 🛠️ **Practice Time:** 3–4 hours

---

# 📚 Table of Contents

1. What are Docker Resource Limits?
2. Why Resource Limits?
3. CPU Limits
4. Memory Limits
5. Swap Memory
6. Restart Policies
7. Monitoring Resource Usage
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

- Understand Docker resource limits
- Limit CPU and memory usage
- Configure restart policies
- Monitor container resource usage
- Optimize resource allocation

---

# 📖 What are Docker Resource Limits?

Docker allows you to control how much **CPU**, **Memory**, and **Swap Memory** a container can use.

This prevents one container from consuming all the host resources.

---

# 💡 Why Resource Limits?

Without Resource Limits:

```text
Container A
    │
Uses All CPU & Memory
    │
Other Containers Slow Down ❌
```

With Resource Limits:

```text
Container A (Limited)
        │
Container B (Limited)
        │
Container C (Limited)
        │
Stable System ✅
```

Benefits:

- ✅ Prevent resource exhaustion
- ✅ Better performance
- ✅ Fair resource allocation
- ✅ Stable production environment

---

# 🖥️ CPU Limits

Limit CPU usage using the `--cpus` option.

Example:

```bash
docker run --cpus="1" nginx
```

Allow half a CPU:

```bash
docker run --cpus="0.5" nginx
```

Limit to two CPUs:

```bash
docker run --cpus="2" nginx
```

---

# 🧠 Memory Limits

Limit container memory using `--memory`.

Example:

```bash
docker run --memory="512m" nginx
```

Limit to 1 GB:

```bash
docker run --memory="1g" nginx
```

If the container exceeds the limit, Docker may stop it due to an Out Of Memory (OOM) condition.

---

# 💾 Swap Memory

Swap memory provides additional virtual memory.

Example:

```bash
docker run \
--memory="512m" \
--memory-swap="1g" \
nginx
```

Meaning:

- RAM: 512 MB
- RAM + Swap: 1 GB

---

# 🔄 Restart Policies

Restart policies define how Docker handles container failures.

| Policy | Description |
|--------|-------------|
| no | Never restart (default) |
| always | Always restart |
| unless-stopped | Restart unless manually stopped |
| on-failure | Restart only if the container exits with an error |

Example:

```bash
docker run \
--restart always \
nginx
```

---

# 📊 Monitor Resource Usage

Monitor running containers:

```bash
docker stats
```

Example Output:

```text
CONTAINER   CPU %   MEM USAGE   NET I/O

nginx       2.1%    35 MB       1 MB
```

---

# 🔍 Inspect Container Limits

View container configuration:

```bash
docker inspect nginx
```

Look for:

- CPU limits
- Memory limits
- Restart policy

---

# 📊 Useful Docker Commands

Run with CPU limit:

```bash
docker run --cpus="1" nginx
```

Run with memory limit:

```bash
docker run --memory="512m" nginx
```

Run with restart policy:

```bash
docker run --restart always nginx
```

Monitor resources:

```bash
docker stats
```

Inspect container:

```bash
docker inspect nginx
```

---

# 🏗️ Resource Limit Workflow

```text
Create Container
       │
       ▼
Assign CPU & Memory Limits
       │
       ▼
Run Application
       │
       ▼
Monitor with docker stats
       │
       ▼
Stable Resource Usage
```

---

# 🏆 Best Practices

- ✅ Set CPU and memory limits for production containers
- ✅ Use restart policies for critical services
- ✅ Monitor resource usage regularly
- ✅ Avoid unlimited resource allocation
- ✅ Test applications with resource constraints
- ✅ Remove unused containers to free resources
- ✅ Use lightweight base images

---

# 🌍 Common Use Cases

| Application | Recommended Limits |
|-------------|--------------------|
| Nginx | 0.5 CPU, 256 MB RAM |
| Node.js API | 1 CPU, 512 MB RAM |
| Python App | 1 CPU, 512 MB RAM |
| Redis | 1 CPU, 1 GB RAM |
| MySQL | 2 CPU, 2 GB RAM |
| Jenkins | 2 CPU, 4 GB RAM |

> **Note:** These values are example starting points. Actual resource requirements depend on your workload.

---

# 📝 Key Takeaways

- CPU and memory limits prevent resource exhaustion.
- `docker stats` monitors container performance.
- Restart policies improve service availability.
- Swap memory provides additional virtual memory.
- Resource limits are essential for production environments.

---

# 📋 Summary

In this chapter, you learned:

- Docker Resource Limits
- CPU Limits
- Memory Limits
- Swap Memory
- Restart Policies
- Resource Monitoring
- Docker Commands
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. What are Docker resource limits?
2. Why should CPU limits be configured?
3. How do you limit container memory?
4. What is `docker stats`?
5. What is a restart policy?

---

## Intermediate

6. Explain CPU and memory limits.
7. What is swap memory?
8. Difference between `always` and `unless-stopped` restart policies?
9. How do you inspect container resource settings?
10. Why are resource limits important in production?

---

## Advanced

11. How do Docker resource limits use Linux cgroups?
12. How would you size CPU and memory for microservices?
13. How do you troubleshoot high memory usage in containers?
14. What happens when a container exceeds its memory limit?
15. Explain resource management best practices for Kubernetes and Docker.

---

# 🎯 Practice Exercises

## Exercise 1

Run an Nginx container with a CPU limit.

```bash
docker run --cpus="1" nginx
```

---

## Exercise 2

Run a container with a memory limit.

```bash
docker run --memory="512m" nginx
```

---

## Exercise 3

Configure a restart policy.

```bash
docker run --restart always nginx
```

---

## Exercise 4

Monitor running containers.

```bash
docker stats
```

---

## Exercise 5

Inspect the container configuration.

```bash
docker inspect nginx
```

---

# 🧩 Mini Project

Create a file named:

```text
docker-resource-limits-guide.md
```

Include:

- CPU Limits
- Memory Limits
- Swap Memory
- Restart Policies
- Monitoring Commands
- Best Practices

Commit to Git:

```bash
git add .
git commit -m "Add Docker Resource Limits guide"
```

---

# 📚 Further Reading

- Docker Resource Constraints Documentation
- Docker CLI Reference
- Linux cgroups Documentation
- Docker Best Practices

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [13 - Docker Logging](13-Docker-Logging.md) | [Docker Roadmap](README.md) | [15 - Docker Security](15-Docker-Security.md) |

---

# 🚀 What's Next?

In **Chapter 15 – Docker Security**, you'll learn:

- 🔒 Docker Security Fundamentals
- 👤 Running Containers as Non-Root
- 🛡️ Image Vulnerability Scanning
- 🔐 Docker Secrets
- 🚫 Container Isolation
- 📦 Docker Content Trust
- 🛠️ Security Best Practices
- 🚀 Hardening Docker for Production
