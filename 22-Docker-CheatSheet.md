# Docker Notes
# Chapter 22 - Docker Cheat Sheet

> 📘 **Level:** All Levels
> ⏱️ **Estimated Reading Time:** 30–45 minutes
> 🛠️ **Use Case:** Quick Revision & Daily Reference

---

# 📚 Table of Contents

1. Docker Basics
2. Image Commands
3. Container Commands
4. Volume Commands
5. Network Commands
6. Dockerfile Commands
7. Docker Compose Commands
8. Registry Commands
9. System Commands
10. Useful One-Liners
11. Best Practices
12. Summary

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Quickly recall Docker commands
- Manage images and containers
- Work with volumes and networks
- Use Docker Compose efficiently
- Troubleshoot common Docker issues

---

# 🐳 Docker Basics

Check Docker version:

```bash
docker --version
```

View Docker information:

```bash
docker info
```

Display help:

```bash
docker --help
```

---

# 📦 Image Commands

Build an image:

```bash
docker build -t myapp .
```

List images:

```bash
docker images
```

Pull an image:

```bash
docker pull nginx
```

Push an image:

```bash
docker push myrepo/myapp:v1
```

Tag an image:

```bash
docker tag myapp:v1 myrepo/myapp:v1
```

Remove an image:

```bash
docker rmi myapp:v1
```

---

# 📦 Container Commands

Run a container:

```bash
docker run nginx
```

Run in detached mode:

```bash
docker run -d nginx
```

Run with port mapping:

```bash
docker run -d -p 8080:80 nginx
```

Run with environment variables:

```bash
docker run -e APP_ENV=production nginx
```

List running containers:

```bash
docker ps
```

List all containers:

```bash
docker ps -a
```

Stop a container:

```bash
docker stop <container-id>
```

Start a container:

```bash
docker start <container-id>
```

Restart a container:

```bash
docker restart <container-id>
```

Remove a container:

```bash
docker rm <container-id>
```

View logs:

```bash
docker logs <container-id>
```

Access a running container:

```bash
docker exec -it <container-id> bash
```

Inspect a container:

```bash
docker inspect <container-id>
```

---

# 💾 Volume Commands

Create a volume:

```bash
docker volume create myvolume
```

List volumes:

```bash
docker volume ls
```

Inspect a volume:

```bash
docker volume inspect myvolume
```

Remove a volume:

```bash
docker volume rm myvolume
```

Mount a volume:

```bash
docker run -v myvolume:/data nginx
```

---

# 🌐 Network Commands

List networks:

```bash
docker network ls
```

Create a network:

```bash
docker network create mynetwork
```

Inspect a network:

```bash
docker network inspect mynetwork
```

Connect a container:

```bash
docker network connect mynetwork mycontainer
```

Remove a network:

```bash
docker network rm mynetwork
```

---

# 📝 Dockerfile Commands

| Instruction | Purpose |
|------------|---------|
| FROM | Base image |
| WORKDIR | Working directory |
| COPY | Copy files |
| ADD | Copy files/archive |
| RUN | Execute commands |
| ENV | Set environment variables |
| EXPOSE | Document container port |
| USER | Set user |
| CMD | Default command |
| ENTRYPOINT | Main executable |
| HEALTHCHECK | Container health |
| VOLUME | Define volume |

---

# 🐙 Docker Compose Commands

Start services:

```bash
docker compose up
```

Run in background:

```bash
docker compose up -d
```

Stop services:

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

Build services:

```bash
docker compose build
```

Restart services:

```bash
docker compose restart
```

---

# 📤 Registry Commands

Login:

```bash
docker login
```

Logout:

```bash
docker logout
```

Push image:

```bash
docker push myrepo/myapp:v1
```

Pull image:

```bash
docker pull myrepo/myapp:v1
```

Search images:

```bash
docker search nginx
```

---

# ⚙️ System Commands

View disk usage:

```bash
docker system df
```

Remove unused resources:

```bash
docker system prune
```

Remove everything unused:

```bash
docker system prune -a
```

View events:

```bash
docker events
```

Monitor resources:

```bash
docker stats
```

---

# 🚀 Useful One-Liners

Build and run:

```bash
docker build -t app . && docker run app
```

Remove all stopped containers:

```bash
docker container prune
```

Remove all unused images:

```bash
docker image prune
```

Remove all unused volumes:

```bash
docker volume prune
```

Remove all unused networks:

```bash
docker network prune
```

Stop all running containers:

```bash
docker stop $(docker ps -q)
```

Delete all stopped containers:

```bash
docker rm $(docker ps -aq)
```

---

# 🏆 Best Practices

- ✅ Use official images
- ✅ Tag image versions
- ✅ Keep images small
- ✅ Use Multi-Stage Builds
- ✅ Run containers as non-root
- ✅ Use `.dockerignore`
- ✅ Configure Health Checks
- ✅ Use Docker Secrets
- ✅ Scan images regularly
- ✅ Remove unused resources

---

# 📝 Quick Revision

| Topic | Command |
|--------|---------|
| Build Image | `docker build` |
| Run Container | `docker run` |
| List Images | `docker images` |
| List Containers | `docker ps` |
| View Logs | `docker logs` |
| Execute Command | `docker exec` |
| Stop Container | `docker stop` |
| Remove Container | `docker rm` |
| Docker Compose | `docker compose up` |
| Clean System | `docker system prune` |

---

# 📋 Summary

This cheat sheet covered:

- Docker Basics
- Image Commands
- Container Commands
- Volume Commands
- Network Commands
- Dockerfile Instructions
- Docker Compose Commands
- Registry Commands
- System Commands
- Best Practices

---

# 🎉 Congratulations!

You have completed the **Docker Notes** series. 🎉

You now understand:

- ✅ Docker Fundamentals
- ✅ Images & Containers
- ✅ Volumes & Networking
- ✅ Dockerfile & Compose
- ✅ Security & Health Checks
- ✅ CI/CD Integration
- ✅ Docker on AWS
- ✅ Interview Preparation
- ✅ Daily Docker Commands

You are now ready to start building, deploying, and managing containerized applications with confidence.

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home |
|------------|---------|
| [21 - Docker Interview Questions](21-Docker-Interview-Questions.md) | [Docker Roadmap](README.md) |
