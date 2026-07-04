# Docker Notes
# Chapter 03 - Installing Docker

> 📘 **Level:** Beginner
> ⏱️ **Estimated Reading Time:** 45–60 minutes
> 🛠️ **Practice Time:** 2–3 hours

---

# 📚 Table of Contents

1. Introduction
2. System Requirements
3. Install Docker on Ubuntu
4. Install Docker on Amazon Linux
5. Install Docker on Windows
6. Install Docker on macOS
7. Verify Installation
8. Docker Service Management
9. Run Docker Without sudo
10. Install Docker Compose
11. Common Installation Issues
12. Best Practices
13. Summary
14. Interview Questions
15. Practice Exercises
16. Mini Project
17. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Install Docker on different operating systems
- Manage the Docker service
- Run Docker without `sudo`
- Verify the installation
- Install Docker Compose

---

# 📖 Introduction

Docker can be installed on Linux, Windows, and macOS.

For DevOps engineers, **Ubuntu** and **Amazon Linux** are the most commonly used operating systems.

---

# 💻 System Requirements

Minimum Requirements:

- 64-bit Operating System
- 2 GB RAM (4 GB Recommended)
- Internet Connection
- Administrator/Sudo Access

Supported Platforms:

- Ubuntu
- Debian
- CentOS
- Fedora
- Amazon Linux
- Windows
- macOS

---

# 🐧 Install Docker on Ubuntu

## Step 1: Update Packages

```bash
sudo apt update
```

---

## Step 2: Install Docker

```bash
sudo apt install docker.io -y
```

---

## Step 3: Start Docker

```bash
sudo systemctl start docker
```

---

## Step 4: Enable Docker at Boot

```bash
sudo systemctl enable docker
```

---

## Step 5: Verify Installation

```bash
docker --version
```

Example Output:

```text
Docker version 28.x.x
```

---

# ☁️ Install Docker on Amazon Linux

Update the system:

```bash
sudo yum update -y
```

Install Docker:

```bash
sudo yum install docker -y
```

Start Docker:

```bash
sudo systemctl start docker
```

Enable Docker:

```bash
sudo systemctl enable docker
```

Verify:

```bash
docker --version
```

---

# 🪟 Install Docker on Windows

1. Download Docker Desktop
2. Run the installer
3. Enable WSL2 (if prompted)
4. Restart the system
5. Open Docker Desktop

Verify:

```bash
docker --version
```

---

# 🍎 Install Docker on macOS

1. Download Docker Desktop
2. Install the application
3. Launch Docker Desktop
4. Wait for Docker Engine to start

Verify:

```bash
docker --version
```

---

# ✅ Verify Docker Installation

Check Docker Version:

```bash
docker --version
```

Docker Information:

```bash
docker info
```

Run Test Container:

```bash
docker run hello-world
```

Expected Output:

```text
Hello from Docker!
```

---

# ⚙️ Docker Service Management

Start Docker:

```bash
sudo systemctl start docker
```

Stop Docker:

```bash
sudo systemctl stop docker
```

Restart Docker:

```bash
sudo systemctl restart docker
```

Check Status:

```bash
sudo systemctl status docker
```

Enable on Boot:

```bash
sudo systemctl enable docker
```

Disable on Boot:

```bash
sudo systemctl disable docker
```

---

# 👤 Run Docker Without sudo

Add your user to the Docker group:

```bash
sudo usermod -aG docker $USER
```

Apply changes:

```bash
newgrp docker
```

Verify:

```bash
docker ps
```

---

# 📦 Install Docker Compose

Download Compose:

```bash
sudo apt install docker-compose-v2 -y
```

Verify:

```bash
docker compose version
```

---

# 🚨 Common Installation Issues

### Permission Denied

Solution:

```bash
sudo usermod -aG docker $USER
```

---

### Docker Service Not Running

Solution:

```bash
sudo systemctl start docker
```

---

### Command Not Found

Verify Docker installation:

```bash
docker --version
```

---

### Hello World Fails

Check Docker service:

```bash
sudo systemctl status docker
```

---

# 🏗️ Installation Flow

```text
Install Docker
      │
      ▼
Start Docker Service
      │
      ▼
Enable Docker
      │
      ▼
Verify Installation
      │
      ▼
Run Hello World
      │
      ▼
Ready to Use Docker
```

---

# 🏆 Best Practices

- ✅ Keep Docker updated
- ✅ Enable Docker on boot
- ✅ Use Docker without `sudo`
- ✅ Verify installation after updates
- ✅ Remove unused images regularly
- ✅ Install Docker Compose

---

# 📝 Key Takeaways

- Docker supports Linux, Windows, and macOS.
- Ubuntu is the most popular platform for Docker.
- Docker runs as a system service.
- Verify installation using `docker --version`.
- Install Docker Compose for multi-container applications.

---

# 📋 Summary

In this chapter, you learned:

- Docker Installation
- Docker Service Management
- Docker Verification
- Docker Compose Installation
- Common Installation Issues
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. How do you install Docker on Ubuntu?
2. How do you verify Docker installation?
3. What is Docker Desktop?
4. Why is Docker Compose used?
5. How do you start Docker?

---

## Intermediate

6. How do you run Docker without `sudo`?
7. How do you enable Docker on system boot?
8. Explain the Docker service lifecycle.
9. How do you troubleshoot Docker installation?
10. Difference between Docker Engine and Docker Desktop?

---

# 🎯 Practice Exercises

## Exercise 1

Install Docker on Ubuntu.

---

## Exercise 2

Verify Docker installation.

```bash
docker --version
```

---

## Exercise 3

Run the Hello World container.

```bash
docker run hello-world
```

---

## Exercise 4

Run Docker without `sudo`.

---

## Exercise 5

Install Docker Compose.

```bash
docker compose version
```

---

# 🧩 Mini Project

Create a file named:

```text
docker-installation-guide.md
```

Include:

- Installation Steps
- Docker Service Commands
- Docker Compose Installation
- Verification Commands
- Troubleshooting Tips

Commit to Git:

```bash
git add .
git commit -m "Add Docker installation guide"
```

---

# 📚 Further Reading

- Docker Installation Guide
- Docker Desktop Documentation
- Docker Compose Documentation
- Docker CLI Reference

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [02 - Docker Architecture](02-Docker-Architecture.md) | [Docker Roadmap](README.md) | [04 - Docker Images](04-Docker-Images.md) |

---

# 🚀 What's Next?

In **Chapter 04 – Docker Images**, you'll learn:

- 🖼️ What are Docker Images?
- 📦 Image Layers
- 🔍 Search & Pull Images
- 🏷️ Image Tags
- 🛠️ Build Custom Images
- 📤 Push Images to Docker Hub
- 🧹 Remove Images
- ⚡ Image Best Practices
