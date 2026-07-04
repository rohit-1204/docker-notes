# Docker Notes
# Chapter 04 - Docker Images

> 📘 **Level:** Beginner
> ⏱️ **Estimated Reading Time:** 60–75 minutes
> 🛠️ **Practice Time:** 3–4 hours

---

# 📚 Table of Contents

1. What is a Docker Image?
2. Image vs Container
3. Image Layers
4. Docker Image Lifecycle
5. Docker Hub
6. Searching Images
7. Pulling Images
8. Listing Images
9. Image Tags
10. Inspecting Images
11. Removing Images
12. Saving & Loading Images
13. Best Practices
14. Summary
15. Interview Questions
16. Practice Exercises
17. Mini Project
18. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Docker Images
- Pull images from Docker Hub
- Manage image versions using tags
- Inspect, remove, save, and load images
- Follow Docker image best practices

---

# 📖 What is a Docker Image?

A **Docker Image** is a **read-only template** used to create Docker containers.

It contains:

- Application Code
- Runtime
- Libraries
- Dependencies
- Configuration Files

An image is like a blueprint, while a container is the running instance of that blueprint.

---

# 🆚 Image vs Container

| Docker Image | Docker Container |
|--------------|------------------|
| Blueprint | Running Instance |
| Read Only | Read & Write |
| Cannot Execute | Executes Applications |
| Used to Create Containers | Created from Images |

---

# 🏗️ Image Layers

Docker images are built using multiple **read-only layers**.

```text
Application Layer
        │
Dependencies Layer
        │
Runtime Layer
        │
Base OS Layer
```

Benefits:

- Faster downloads
- Better storage efficiency
- Layer caching
- Reusable layers

---

# 🔄 Docker Image Lifecycle

```text
Dockerfile
      │
      ▼
Build Image
      │
      ▼
Store in Registry
      │
      ▼
Pull Image
      │
      ▼
Run Container
      │
      ▼
Delete Image
```

---

# 🌐 Docker Hub

Docker Hub is the default public registry for Docker images.

Popular Images:

- ubuntu
- nginx
- mysql
- redis
- alpine
- node
- python

---

# 🔍 Search Images

Search for an image:

```bash
docker search nginx
```

Example Output:

```text
NAME      DESCRIPTION

nginx     Official nginx image
```

---

# 📥 Pull Images

Download an image:

```bash
docker pull nginx
```

Pull Ubuntu:

```bash
docker pull ubuntu
```

Pull Redis:

```bash
docker pull redis
```

---

# 📋 List Images

Show downloaded images:

```bash
docker images
```

or

```bash
docker image ls
```

Example:

```text
REPOSITORY   TAG      IMAGE ID

nginx        latest   xxxxxx
ubuntu       latest   xxxxxx
```

---

# 🏷️ Image Tags

Tags identify image versions.

Example:

```bash
docker pull nginx:latest
```

Specific version:

```bash
docker pull nginx:1.25
```

List image tags:

```text
nginx:latest

nginx:1.25

ubuntu:22.04
```

---

# 🔎 Inspect Images

Display detailed information:

```bash
docker image inspect nginx
```

Useful Information:

- Image ID
- Architecture
- OS
- Layers
- Creation Date

---

# 📤 Save an Image

Save an image as a tar file.

```bash
docker save nginx -o nginx.tar
```

Useful for:

- Offline transfer
- Backup
- Migration

---

# 📥 Load an Image

Load an image from a tar file.

```bash
docker load -i nginx.tar
```

---

# 🗑️ Remove Images

Remove a single image:

```bash
docker rmi nginx
```

Remove by ID:

```bash
docker rmi <image-id>
```

Remove all unused images:

```bash
docker image prune
```

Remove all unused objects:

```bash
docker system prune
```

---

# 📊 Useful Docker Image Commands

List images:

```bash
docker images
```

Search image:

```bash
docker search ubuntu
```

Download image:

```bash
docker pull ubuntu
```

Inspect image:

```bash
docker image inspect ubuntu
```

Save image:

```bash
docker save ubuntu -o ubuntu.tar
```

Load image:

```bash
docker load -i ubuntu.tar
```

Delete image:

```bash
docker rmi ubuntu
```

---

# 🏗️ Docker Image Workflow

```text
Docker Hub
      │
      ▼
Pull Image
      │
      ▼
Local Image
      │
      ▼
Run Container
      │
      ▼
Application Running
```

---

# 🏆 Best Practices

- ✅ Use Official Images
- ✅ Use Specific Image Tags
- ✅ Keep Images Small
- ✅ Remove Unused Images
- ✅ Use Alpine Images when possible
- ✅ Regularly Update Images
- ✅ Scan Images for Vulnerabilities

---

# 🌍 Common Image Examples

| Image | Purpose |
|--------|---------|
| ubuntu | Linux OS |
| nginx | Web Server |
| apache | HTTP Server |
| mysql | Database |
| postgres | Database |
| redis | Cache |
| mongo | NoSQL Database |
| node | Node.js Runtime |
| python | Python Runtime |
| alpine | Lightweight Linux |

---

# 📝 Key Takeaways

- Images are templates used to create containers.
- Docker Hub is the default image registry.
- Images are made of reusable layers.
- Tags help manage image versions.
- Images can be saved, loaded, and shared.

---

# 📋 Summary

In this chapter, you learned:

- Docker Images
- Image Layers
- Docker Hub
- Pulling Images
- Listing Images
- Image Tags
- Inspecting Images
- Saving & Loading Images
- Removing Images
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. What is a Docker Image?
2. What is Docker Hub?
3. How do you pull an image?
4. What is an image tag?
5. How do you list Docker images?

---

## Intermediate

6. Explain Docker image layers.
7. Difference between Image and Container.
8. How do you inspect an image?
9. Why are image tags important?
10. Explain image caching.

---

## Advanced

11. How are Docker images built?
12. Explain Docker image lifecycle.
13. How do you optimize Docker images?
14. Why should you avoid using the `latest` tag in production?
15. How do Docker image layers improve performance?

---

# 🎯 Practice Exercises

## Exercise 1

Search for the Nginx image.

```bash
docker search nginx
```

---

## Exercise 2

Download the Ubuntu image.

```bash
docker pull ubuntu
```

---

## Exercise 3

List all downloaded images.

```bash
docker images
```

---

## Exercise 4

Inspect an image.

```bash
docker image inspect ubuntu
```

---

## Exercise 5

Save and load an image.

```bash
docker save ubuntu -o ubuntu.tar
docker load -i ubuntu.tar
```

---

# 🧩 Mini Project

Create a Markdown file named:

```text
docker-images-guide.md
```

Include:

- Docker Images
- Docker Hub
- Image Layers
- Docker Commands
- Best Practices

Commit to Git:

```bash
git add .
git commit -m "Add Docker Images guide"
```

---

# 📚 Further Reading

- Docker Images Documentation
- Docker Hub
- Docker CLI Reference
- Docker Best Practices

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [03 - Installing Docker](03-Installing-Docker.md) | [Docker Roadmap](README.md) | [05 - Docker Containers](05-Docker-Containers.md) |

---

# 🚀 What's Next?

In **[Chapter 05 – Docker Containers] (05-Docker-Containers.md)**, you'll learn:

- 📦 What is a Docker Container?
- ▶️ Create & Run Containers
- ⏹️ Start, Stop & Restart Containers
- 📋 List Containers
- 📝 Rename & Remove Containers
- 🔍 Inspect Containers
- 📜 View Logs
- 💻 Execute Commands Inside Containers
- 🛠️ Container Lifecycle
- 🚀 Best Practices
