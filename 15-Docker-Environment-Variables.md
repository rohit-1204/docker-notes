# Docker Notes
# Chapter 15 - Docker Environment Variables

> 📘 **Level:** Beginner
> ⏱️ **Estimated Reading Time:** 45–60 minutes
> 🛠️ **Practice Time:** 2–3 hours

---

# 📚 Table of Contents

1. What are Environment Variables?
2. Why Use Environment Variables?
3. Passing Environment Variables
4. Using .env Files
5. Environment Variables in Dockerfile
6. Environment Variables in Docker Compose
7. Useful Commands
8. Best Practices
9. Summary
10. Interview Questions
11. Practice Exercises
12. Mini Project
13. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Docker Environment Variables
- Pass variables to containers
- Use `.env` files
- Configure variables in Docker Compose
- Follow best practices

---

# 📖 What are Environment Variables?

Environment Variables are **key-value pairs** used to configure an application without changing its source code.

Examples:

- Database URL
- API Keys
- Username
- Password
- Application Mode
- Port Number

---

# 💡 Why Use Environment Variables?

Without Environment Variables:

```text
Application

↓

Hardcoded Configuration

↓

Code Changes Required ❌
```

With Environment Variables:

```text
Application

↓

Environment Variables

↓

Flexible Configuration ✅
```

Benefits:

- ✅ Easy configuration
- ✅ Secure settings management
- ✅ Different configs for Dev/Test/Prod
- ✅ No code modification

---

# 🏗️ Docker Environment Variable Flow

```text
Docker Run

↓

Environment Variables

↓

Container

↓

Application Reads Variables
```

---

# 🔑 Pass Environment Variables

Use the `-e` option.

Example:

```bash
docker run -e APP_ENV=production nginx
```

Multiple variables:

```bash
docker run \
-e APP_ENV=production \
-e PORT=8080 \
nginx
```

---

# 📄 Using an .env File

Create a file named:

```text
.env
```

Example:

```text
APP_ENV=production
PORT=8080
DB_HOST=mysql
```

Run the container:

```bash
docker run --env-file .env nginx
```

---

# 📝 Environment Variables in Dockerfile

Define default variables using the `ENV` instruction.

Example:

```dockerfile
FROM nginx

ENV APP_ENV=production
ENV PORT=80
```

Build:

```bash
docker build -t myapp .
```

Run:

```bash
docker run myapp
```

---

# 🐳 Environment Variables in Docker Compose

Example:

```yaml
version: "3.9"

services:

  web:
    image: nginx

    environment:
      APP_ENV: production
      PORT: 80
```

Using an `.env` file:

```yaml
services:
  web:
    env_file:
      - .env
```

---

# 🔍 View Environment Variables

Display variables inside a container:

```bash
docker exec nginx env
```

Or:

```bash
docker exec nginx printenv
```

---

# 📊 Useful Docker Commands

Run with variable:

```bash
docker run -e APP_ENV=production nginx
```

Run using `.env` file:

```bash
docker run --env-file .env nginx
```

View variables:

```bash
docker exec nginx env
```

Inspect container:

```bash
docker inspect nginx
```

---

# 🏗️ Environment Variable Workflow

```text
Create Variables
       │
       ▼
Pass to Container
       │
       ▼
Container Starts
       │
       ▼
Application Reads Variables
```

---

# 🏆 Best Practices

- ✅ Use environment variables for configuration
- ✅ Store secrets securely (Docker Secrets, Vault, AWS Secrets Manager)
- ✅ Keep `.env` files out of Git using `.gitignore`
- ✅ Use descriptive variable names
- ✅ Use different values for Development, Testing, and Production
- ❌ Do not hardcode passwords or API keys

---

# 🌍 Common Use Cases

| Variable | Example |
|----------|----------|
| APP_ENV | production |
| PORT | 8080 |
| DB_HOST | mysql |
| DB_USER | admin |
| DB_PASSWORD | password |
| API_KEY | xxxxxxxxx |

---

# 📝 Key Takeaways

- Environment Variables configure applications.
- Use `-e` to pass variables.
- `.env` files simplify configuration.
- Docker Compose supports environment variables.
- Avoid storing secrets directly in images.

---

# 📋 Summary

In this chapter, you learned:

- Docker Environment Variables
- Passing Variables
- `.env` Files
- Dockerfile ENV
- Docker Compose Environment
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. What are Environment Variables?
2. Why do we use them?
3. How do you pass an environment variable?
4. What is an `.env` file?
5. What does the `ENV` instruction do?

---

## Intermediate

6. Difference between `ENV` and `-e`?
7. How do you use environment variables in Docker Compose?
8. Why shouldn't secrets be hardcoded?
9. How do you view environment variables inside a container?
10. Explain the benefits of `.env` files.

---

## Advanced

11. How would you manage secrets in production?
12. Explain environment management across Dev, QA, and Production.
13. How do Kubernetes ConfigMaps and Secrets compare with Docker environment variables?
14. What are the security risks of environment variables?
15. How would you design a secure configuration strategy?

---

# 🎯 Practice Exercises

## Exercise 1

Run a container with an environment variable.

```bash
docker run -e APP_ENV=production nginx
```

---

## Exercise 2

Create an `.env` file.

```text
APP_ENV=development
PORT=8080
```

---

## Exercise 3

Run a container using the `.env` file.

```bash
docker run --env-file .env nginx
```

---

## Exercise 4

View environment variables inside the container.

```bash
docker exec <container-name> env
```

---

## Exercise 5

Create a Dockerfile using the `ENV` instruction.

---

# 🧩 Mini Project

Create a file named:

```text
docker-environment-variables-guide.md
```

Include:

- Environment Variables Overview
- Docker Run Examples
- `.env` File Usage
- Dockerfile ENV
- Docker Compose Environment
- Best Practices

Commit to Git:

```bash
git add .
git commit -m "Add Docker Environment Variables guide"
```

---

# 📚 Further Reading

- Docker Environment Variables Documentation
- Docker Compose Documentation
- Dockerfile Reference
- Twelve-Factor App Configuration

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [14 - Docker Resource Limits](14-Docker-Resource-Limits.md) | [Docker Roadmap](README.md) | [16 - Docker Best Practices](16-Docker-Best-Practices.md) |

---

# 🚀 What's Next?

In **Chapter 16 – Docker Best Practices**, you'll learn:

- 🏗️ Writing Efficient Dockerfiles
- 📦 Optimizing Image Size
- 🔒 Security Best Practices
- 🚀 Multi-Stage Builds
- ⚡ Performance Optimization
- 🛠️ Production Recommendations
- 📋 Common Mistakes to Avoid
