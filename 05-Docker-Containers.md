# Docker Notes
# Chapter 05 - Docker Containers

> 📘 **Level:** Beginner
> ⏱️ **Estimated Reading Time:** 60–75 minutes
> 🛠️ **Practice Time:** 3–4 hours

---

# 📚 Table of Contents

1. What is a Docker Container?
2. Image vs Container
3. Container Lifecycle
4. Creating Containers
5. Running Containers
6. Managing Containers
7. Container Logs
8. Executing Commands
9. Container Inspection
10. Container Resource Management
11. Useful Docker Commands
12. Best Practices
13. Summary
14. Interview Questions
15. Practice Exercises
16. Mini Project
17. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Docker Containers
- Create and manage containers
- Monitor container status
- Access containers using the terminal
- Remove and clean up containers

---

# 📖 What is a Docker Container?

A **Docker Container** is a running instance of a Docker Image.

It contains:

- Application
- Runtime
- Libraries
- Dependencies
- Network Configuration

Containers are:

- Lightweight
- Portable
- Isolated
- Fast to start

---

# 🆚 Docker Image vs Docker Container

| Docker Image | Docker Container |
|--------------|------------------|
| Blueprint | Running Instance |
| Read Only | Read & Write |
| Static | Dynamic |
| Used to Create Containers | Executes Applications |

---

# 🔄 Container Lifecycle

```text
Docker Image
      │
      ▼
Create Container
      │
      ▼
Running
      │
      ▼
Stopped
      │
      ▼
Restart
      │
      ▼
Removed
```

---

# 🚀 Create a Container

Run a new Ubuntu container:

```bash
docker run ubuntu
```

Run an Nginx container:

```bash
docker run nginx
```

Run in detached mode:

```bash
docker run -d nginx
```

---

# 🏷️ Name a Container

Assign a custom name:

```bash
docker run --name web-server nginx
```

Verify:

```bash
docker ps
```

---

# 🌐 Run Container with Port Mapping

Expose port **80** from the container to **8080** on the host.

```bash
docker run -d -p 8080:80 nginx
```

Access:

```
http://localhost:8080
```

---

# 📋 List Containers

Running containers:

```bash
docker ps
```

All containers:

```bash
docker ps -a
```

---

# ▶️ Start a Container

```bash
docker start web-server
```

---

# ⏹️ Stop a Container

```bash
docker stop web-server
```

---

# 🔄 Restart a Container

```bash
docker restart web-server
```

---

# ⏸️ Pause a Container

```bash
docker pause web-server
```

Resume:

```bash
docker unpause web-server
```

---

# 🗑️ Remove a Container

Remove a stopped container:

```bash
docker rm web-server
```

Force remove:

```bash
docker rm -f web-server
```

---

# 📝 Rename a Container

```bash
docker rename web-server nginx-prod
```

---

# 📜 View Container Logs

View logs:

```bash
docker logs web-server
```

Follow logs in real time:

```bash
docker logs -f web-server
```

---

# 💻 Execute Commands Inside a Container

Run Bash:

```bash
docker exec -it web-server bash
```

If Bash is unavailable:

```bash
docker exec -it web-server sh
```

Example:

```bash
docker exec -it web-server ls /
```

---

# 🔍 Inspect a Container

View detailed information:

```bash
docker inspect web-server
```

Useful details:

- Container ID
- IP Address
- Mounts
- Networks
- Status

---

# 📊 Monitor Container Usage

View resource usage:

```bash
docker stats
```

Shows:

- CPU Usage
- Memory Usage
- Network I/O
- Disk I/O

---

# 🏗️ Docker Container Workflow

```text
Docker Image
      │
      ▼
docker run
      │
      ▼
Container Created
      │
      ▼
Application Running
      │
      ▼
Stop / Restart
      │
      ▼
Remove Container
```

---

# 💻 Useful Docker Container Commands

Run container:

```bash
docker run nginx
```

Detached mode:

```bash
docker run -d nginx
```

List containers:

```bash
docker ps
```

All containers:

```bash
docker ps -a
```

Start:

```bash
docker start <container>
```

Stop:

```bash
docker stop <container>
```

Restart:

```bash
docker restart <container>
```

Logs:

```bash
docker logs <container>
```

Execute command:

```bash
docker exec -it <container> bash
```

Inspect:

```bash
docker inspect <container>
```

Delete:

```bash
docker rm <container>
```

---

# 🏆 Best Practices

- ✅ Use meaningful container names
- ✅ Run containers in detached mode for services
- ✅ Remove unused containers
- ✅ Monitor resource usage
- ✅ Store persistent data using volumes
- ✅ Use restart policies for production
- ✅ Keep containers lightweight

---

# 🌍 Common Use Cases

| Container | Purpose |
|-----------|----------|
| nginx | Web Server |
| apache | HTTP Server |
| mysql | Database |
| postgres | SQL Database |
| redis | Cache |
| mongo | NoSQL Database |
| node | Node.js Application |
| python | Python Application |

---

# 📝 Key Takeaways

- Containers are running instances of images.
- Multiple containers can use the same image.
- Containers are isolated from each other.
- Use `docker exec` to access a running container.
- Use `docker logs` to troubleshoot applications.

---

# 📋 Summary

In this chapter, you learned:

- Docker Containers
- Container Lifecycle
- Creating Containers
- Managing Containers
- Logs
- Docker Exec
- Docker Inspect
- Docker Stats
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. What is a Docker Container?
2. Difference between Image and Container?
3. How do you create a container?
4. How do you stop a container?
5. How do you remove a container?

---

## Intermediate

6. What does `docker exec` do?
7. Explain detached mode.
8. Difference between `docker run` and `docker start`.
9. How do you inspect a container?
10. Explain the container lifecycle.

---

## Advanced

11. What happens internally when `docker run nginx` is executed?
12. How do containers share the host kernel?
13. Explain container isolation.
14. How do you troubleshoot a failed container?
15. How do you monitor container resource usage?

---

# 🎯 Practice Exercises

## Exercise 1

Run an Ubuntu container.

```bash
docker run ubuntu
```

---

## Exercise 2

Run an Nginx container in detached mode.

```bash
docker run -d --name web-server nginx
```

---

## Exercise 3

View running containers.

```bash
docker ps
```

---

## Exercise 4

Access the container shell.

```bash
docker exec -it web-server bash
```

---

## Exercise 5

Stop and remove the container.

```bash
docker stop web-server
docker rm web-server
```

---

# 🧩 Mini Project

Create a file named:

```text
docker-containers-guide.md
```

Include:

- Docker Containers
- Container Lifecycle
- Docker Commands
- Logs
- Docker Exec
- Best Practices

Commit to Git:

```bash
git add .
git commit -m "Add Docker Containers guide"
```

---

# 📚 Further Reading

- Docker Containers Documentation
- Docker CLI Reference
- Docker Best Practices
- Docker Engine Documentation

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [04 - Docker Images](04-Docker-Images.md) | [Docker Roadmap](README.md) | [06 - Docker Volumes](06-Docker-Volumes.md) |

---

# 🚀 What's Next?

In **Chapter 06 – Docker Volumes**, you'll learn:

- 💾 What are Docker Volumes?
- 📂 Bind Mounts vs Volumes
- 📦 Named & Anonymous Volumes
- 🔄 Data Persistence
- 📤 Backup & Restore Volumes
- 🗑️ Remove Volumes
- 🛠️ Volume Best Practices
