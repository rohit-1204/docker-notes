# Docker Notes
# Chapter 17 - Docker Security

> 📘 **Level:** Beginner to Intermediate
> ⏱️ **Estimated Reading Time:** 60–90 minutes
> 🛠️ **Practice Time:** 4–5 hours

---

# 📚 Table of Contents

1. What is Docker Security?
2. Why Docker Security?
3. Docker Security Architecture
4. Running Containers as Non-Root
5. Image Security
6. Docker Secrets
7. Container Isolation
8. Capabilities
9. Read-Only File System
10. Security Scanning
11. Useful Commands
12. Best Practices
13. Summary
14. Interview Questions
15. Practice Exercises
16. Mini Project
17. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Docker Security
- Secure Docker images
- Run containers safely
- Protect sensitive data
- Apply Docker security best practices

---

# 📖 What is Docker Security?

Docker Security is the practice of protecting:

- 🐳 Docker Images
- 📦 Containers
- 🖥️ Docker Host
- 🌐 Networks
- 🔐 Secrets
- 👤 User Access

The goal is to minimize vulnerabilities and secure containerized applications.

---

# 💡 Why Docker Security?

Without Security:

```text
Container

↓

Runs as Root

↓

System Compromise ❌
```

With Security:

```text
Container

↓

Least Privilege

↓

Secure Application ✅
```

Benefits:

- ✅ Better protection
- ✅ Reduced attack surface
- ✅ Secure deployments
- ✅ Compliance support

---

# 🏗️ Docker Security Architecture

```text
Docker Host
      │
      ▼
Docker Engine
      │
      ▼
Container
      │
      ▼
Application
```

Security Layers:

- Docker Host
- Docker Daemon
- Container Runtime
- Application
- Network

---

# 👤 Run Containers as Non-Root

Avoid running applications as the **root** user.

Dockerfile Example:

```dockerfile
FROM nginx

RUN adduser -D appuser

USER appuser
```

Benefits:

- Reduced privileges
- Better security
- Lower risk of host compromise

---

# 📦 Image Security

Use trusted and official images.

Example:

```text
Official Image ✅

nginx

ubuntu

python
```

Avoid:

- Unknown images
- Outdated images
- Unverified repositories

Always keep images updated.

---

# 🔐 Docker Secrets

Use Docker Secrets for sensitive data instead of hardcoding values.

Examples:

- Database passwords
- API keys
- SSL certificates
- Tokens

Benefits:

- Encrypted storage
- Secure access
- Better secret management

---

# 🔒 Container Isolation

Containers should be isolated from each other.

Docker provides isolation using:

- Namespaces
- Control Groups (cgroups)
- Linux Capabilities

Isolation prevents one container from affecting another.

---

# 🛡️ Linux Capabilities

Instead of giving full root access, Docker allows only required capabilities.

Remove unnecessary capabilities:

```bash
docker run \
--cap-drop ALL \
nginx
```

Add only required capabilities:

```bash
docker run \
--cap-add NET_BIND_SERVICE \
nginx
```

---

# 📁 Read-Only File System

Prevent containers from modifying files.

Example:

```bash
docker run \
--read-only \
nginx
```

Benefits:

- Prevent accidental changes
- Protect application files
- Reduce attack surface

---

# 🔍 Security Scanning

Scan Docker images for vulnerabilities.

Docker Scout:

```bash
docker scout quickview nginx
```

Other tools:

- Trivy
- Grype
- Snyk

Scan images regularly before deployment.

---

# 📊 Useful Docker Commands

Run as non-root:

```dockerfile
USER appuser
```

Run with read-only filesystem:

```bash
docker run --read-only nginx
```

Drop capabilities:

```bash
docker run --cap-drop ALL nginx
```

Inspect container:

```bash
docker inspect nginx
```

View running containers:

```bash
docker ps
```

---

# 🏗️ Docker Security Workflow

```text
Use Official Image
        │
        ▼
Scan Image
        │
        ▼
Run as Non-Root
        │
        ▼
Limit Permissions
        │
        ▼
Secure Production Deployment
```

---

# 🏆 Best Practices

- ✅ Use official base images
- ✅ Keep images updated
- ✅ Run containers as non-root
- ✅ Use Docker Secrets for sensitive data
- ✅ Remove unnecessary Linux capabilities
- ✅ Enable read-only file systems where possible
- ✅ Scan images regularly
- ✅ Follow the Principle of Least Privilege
- ✅ Remove unused containers and images
- ✅ Keep Docker Engine updated

---

# 🌍 Common Security Risks

| Risk | Solution |
|------|----------|
| Running as root | Use non-root user |
| Outdated images | Update regularly |
| Hardcoded passwords | Use Docker Secrets |
| Excessive permissions | Drop capabilities |
| Vulnerable images | Scan before deployment |
| Writable filesystem | Use read-only mode |

---

# 📝 Key Takeaways

- Docker Security protects containers and hosts.
- Use trusted images only.
- Run containers as non-root users.
- Store secrets securely.
- Scan images for vulnerabilities.
- Apply least privilege principles.

---

# 📋 Summary

In this chapter, you learned:

- Docker Security
- Non-Root Containers
- Docker Secrets
- Image Security
- Container Isolation
- Linux Capabilities
- Security Scanning
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. What is Docker Security?
2. Why should containers avoid running as root?
3. What are Docker Secrets?
4. What is container isolation?
5. Why should official images be used?

---

## Intermediate

6. Explain Docker Security architecture.
7. What are Linux capabilities?
8. What is a read-only filesystem?
9. How do you scan Docker images?
10. Explain least privilege in Docker.

---

## Advanced

11. How do namespaces and cgroups improve security?
12. Explain Docker Secrets vs Environment Variables.
13. How would you secure Docker in production?
14. What are common Docker security vulnerabilities?
15. Explain container hardening techniques.

---

# 🎯 Practice Exercises

## Exercise 1

Run a container as a non-root user.

---

## Exercise 2

Run a container with a read-only filesystem.

```bash
docker run --read-only nginx
```

---

## Exercise 3

Drop all Linux capabilities.

```bash
docker run --cap-drop ALL nginx
```

---

## Exercise 4

Scan an image.

```bash
docker scout quickview nginx
```

---

## Exercise 5

Inspect container security settings.

```bash
docker inspect nginx
```

---

# 🧩 Mini Project

Create a file named:

```text
docker-security-guide.md
```

Include:

- Docker Security Overview
- Non-Root Containers
- Docker Secrets
- Image Scanning
- Read-Only Filesystem
- Best Practices

Commit to Git:

```bash
git add .
git commit -m "Add Docker Security guide"
```

---

# 📚 Further Reading

- Docker Security Documentation
- Docker Scout Documentation
- Docker Best Practices
- OWASP Docker Security Cheat Sheet

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [16 - Docker Health Checks](16-Docker-Health-Checks.md) | [Docker Roadmap](README.md) | [18 - Docker Best Practices](18-Docker-Best-Practices.md) |

---

# 🚀 What's Next?

In **Chapter 18 – Docker Best Practices**, you'll learn:

- 🏗️ Writing Efficient Dockerfiles
- 📦 Optimizing Image Size
- 🚀 Multi-Stage Builds
- ⚡ Performance Optimization
- 🔒 Production Security Tips
- 📋 Common Mistakes to Avoid
- 🛠️ Docker Production Checklist
