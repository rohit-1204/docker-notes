# Docker Notes
# Chapter 09 - Docker Compose

> 📘 **Level:** Beginner to Intermediate
> ⏱️ **Estimated Reading Time:** 75–90 minutes
> 🛠️ **Practice Time:** 4–5 hours

---

# 📚 Table of Contents

1. What is Docker Compose?
2. Why Use Docker Compose?
3. Docker Compose Architecture
4. docker-compose.yml
5. Services
6. Networks
7. Volumes
8. Environment Variables
9. Docker Compose Commands
10. Docker Compose Workflow
11. Example Project
12. Best Practices
13. Summary
14. Interview Questions
15. Practice Exercises
16. Mini Project
17. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Docker Compose
- Deploy multi-container applications
- Write a `docker-compose.yml` file
- Manage services, networks, and volumes
- Use Docker Compose commands efficiently

---

# 📖 What is Docker Compose?

**Docker Compose** is a tool used to define and manage **multi-container Docker applications** using a single YAML configuration file.

Instead of running multiple `docker run` commands, you define all services in one file and start them together.

---

# 💡 Why Use Docker Compose?

Without Docker Compose:

```text
docker run nginx

docker run mysql

docker run redis

docker network create

docker volume create
```

With Docker Compose:

```text
docker compose up
```

Benefits:

- ✅ Manage multiple containers
- ✅ Single configuration file
- ✅ Automatic networking
- ✅ Easy scaling
- ✅ Faster deployments

---

# 🏗️ Docker Compose Architecture

```text
docker-compose.yml
         │
         ▼
Docker Compose
         │
 ┌───────┼────────┐
 ▼       ▼        ▼
Web     DB     Redis
```

---

# 📄 docker-compose.yml

A Compose file is written in **YAML**.

Basic structure:

```yaml
services:
  web:
    image: nginx
```

---

# 🧩 Services

Each application is defined as a **service**.

Example:

```yaml
services:
  web:
    image: nginx

  db:
    image: mysql
```

Each service runs inside its own container.

---

# 🌐 Networks

Docker Compose automatically creates a network.

Containers communicate using **service names**.

Example:

```text
web

↓

db
```

No need to use container IP addresses.

Custom network:

```yaml
networks:
  app-network:
```

---

# 💾 Volumes

Volumes provide persistent storage.

Example:

```yaml
volumes:
  db-data:
```

Mount volume:

```yaml
services:
  db:
    image: mysql

    volumes:
      - db-data:/var/lib/mysql
```

---

# 🌍 Environment Variables

Define variables inside Compose.

```yaml
environment:
  MYSQL_ROOT_PASSWORD: password
```

Using an `.env` file:

```yaml
environment:
  APP_ENV: ${APP_ENV}
```

---

# 🏗️ Complete Docker Compose Example

```yaml
version: "3.9"

services:

  web:
    image: nginx
    ports:
      - "8080:80"

  db:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: password

volumes:
  db-data:
```

---

# 🚀 Start Services

Start all services:

```bash
docker compose up
```

Detached mode:

```bash
docker compose up -d
```

---

# ⏹️ Stop Services

```bash
docker compose stop
```

---

# 🔄 Restart Services

```bash
docker compose restart
```

---

# 🗑️ Remove Services

Stop and remove containers:

```bash
docker compose down
```

Remove containers, networks, and volumes:

```bash
docker compose down -v
```

---

# 📋 List Running Services

```bash
docker compose ps
```

---

# 📜 View Logs

```bash
docker compose logs
```

Follow logs:

```bash
docker compose logs -f
```

---

# 🔧 Scale Services

Run multiple instances of a service:

```bash
docker compose up --scale web=3
```

---

# 📊 Useful Docker Compose Commands

Start:

```bash
docker compose up
```

Detached:

```bash
docker compose up -d
```

Stop:

```bash
docker compose stop
```

Restart:

```bash
docker compose restart
```

Remove:

```bash
docker compose down
```

View logs:

```bash
docker compose logs
```

List services:

```bash
docker compose ps
```

Pull latest images:

```bash
docker compose pull
```

---

# 🏗️ Docker Compose Workflow

```text
Write docker-compose.yml
          │
          ▼
docker compose up
          │
          ▼
Containers Created
          │
          ▼
Application Running
          │
          ▼
docker compose down
```

---

# 🌍 Real-World Example

A typical web application consists of:

```text
User
   │
   ▼
Nginx
   │
   ▼
Backend API
   │
   ▼
MySQL Database
```

Docker Compose runs all these services together.

---

# 🏆 Best Practices

- ✅ Keep one service per container
- ✅ Use named volumes
- ✅ Use custom networks
- ✅ Store secrets in environment variables or secret managers
- ✅ Use image version tags
- ✅ Keep Compose files simple
- ✅ Use `.env` files for configuration

---

# 📝 Key Takeaways

- Docker Compose manages multiple containers.
- Applications are defined in a YAML file.
- Services communicate using service names.
- Networks are created automatically.
- Volumes provide persistent storage.

---

# 📋 Summary

In this chapter, you learned:

- Docker Compose
- Compose File Structure
- Services
- Networks
- Volumes
- Environment Variables
- Docker Compose Commands
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. What is Docker Compose?
2. What is `docker-compose.yml`?
3. Why use Docker Compose?
4. How do you start services?
5. How do you stop services?

---

## Intermediate

6. Explain Docker Compose architecture.
7. How do services communicate?
8. What are named volumes?
9. Explain automatic networking.
10. Difference between `docker compose up` and `docker compose down`.

---

## Advanced

11. How do you scale services?
12. Explain Docker Compose workflow.
13. How do you manage environment variables?
14. Why is Docker Compose useful in development?
15. Explain Docker Compose best practices.

---

# 🎯 Practice Exercises

## Exercise 1

Create a simple Compose file with Nginx.

---

## Exercise 2

Start all services.

```bash
docker compose up -d
```

---

## Exercise 3

View running services.

```bash
docker compose ps
```

---

## Exercise 4

View application logs.

```bash
docker compose logs
```

---

## Exercise 5

Stop and remove all services.

```bash
docker compose down
```

---

# 🧩 Mini Project

Create a file named:

```text
docker-compose-guide.md
```

Include:

- Docker Compose Overview
- Compose File Structure
- Services
- Networks
- Volumes
- Docker Compose Commands
- Best Practices

Commit to Git:

```bash
git add .
git commit -m "Add Docker Compose guide"
```

---

# 📚 Further Reading

- Docker Compose Documentation
- Compose File Reference
- Docker CLI Reference
- Docker Best Practices

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [08 - Dockerfile](08-Dockerfile.md) | [Docker Roadmap](README.md) | [10 - Docker Registry](10-Docker-Registry.md) |

---

# 🚀 What's Next?

In **Chapter 10 – Docker Registry**, you'll learn:

- 📦 What is a Docker Registry?
- 🌐 Public vs Private Registries
- 🐳 Docker Hub
- ☁️ Amazon ECR
- 🔑 Login & Authentication
- 📤 Push & Pull Images
- 🛡️ Registry Security
- 🚀 Registry Best Practices
