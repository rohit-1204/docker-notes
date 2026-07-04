# Docker Notes
# Chapter 06 - Docker Volumes

> 📘 **Level:** Beginner to Intermediate
> ⏱️ **Estimated Reading Time:** 60–75 minutes
> 🛠️ **Practice Time:** 3–4 hours

---

# 📚 Table of Contents

1. What are Docker Volumes?
2. Why Use Volumes?
3. Types of Docker Storage
4. Named Volumes
5. Anonymous Volumes
6. Bind Mounts
7. Volume Lifecycle
8. Managing Volumes
9. Backup & Restore Volumes
10. Useful Docker Commands
11. Best Practices
12. Summary
13. Interview Questions
14. Practice Exercises
15. Mini Project
16. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Docker Volumes
- Store persistent container data
- Use Named Volumes and Bind Mounts
- Backup and restore Docker data
- Manage Docker volumes efficiently

---

# 📖 What are Docker Volumes?

A **Docker Volume** is a storage mechanism that allows data to persist even after a container is removed.

Without volumes:

```text
Container
     │
     ▼
Application Data
     │
Container Deleted
     │
❌ Data Lost
```

With volumes:

```text
Container
     │
     ▼
Docker Volume
     │
Container Deleted
     │
✅ Data Remains
```

---

# 💡 Why Use Docker Volumes?

Benefits:

- ✅ Persistent storage
- ✅ Share data between containers
- ✅ Easy backup and restore
- ✅ Better performance
- ✅ Decouples data from containers

---

# 📦 Types of Docker Storage

Docker supports three storage options:

| Storage Type | Description |
|--------------|-------------|
| Named Volume | Managed by Docker |
| Bind Mount | Uses Host Directory |
| Anonymous Volume | Temporary Docker Volume |

---

# 📁 Named Volumes

Docker manages the storage location.

Create a volume:

```bash
docker volume create my-volume
```

Use the volume:

```bash
docker run -d \
-v my-volume:/usr/share/nginx/html \
nginx
```

---

# 📂 Anonymous Volumes

Created automatically by Docker.

Example:

```bash
docker run -v /app/data nginx
```

Docker assigns a random volume name.

Anonymous volumes are useful for temporary storage.

---

# 📄 Bind Mounts

Bind mounts map a host directory into a container.

```bash
docker run -d \
-v /home/user/html:/usr/share/nginx/html \
nginx
```

Flow:

```text
Host Directory
       │
       ▼
Bind Mount
       │
       ▼
Docker Container
```

Changes made on the host are immediately visible inside the container.

---

# 🔄 Volume Lifecycle

```text
Create Volume
      │
      ▼
Attach to Container
      │
      ▼
Store Data
      │
      ▼
Container Removed
      │
      ▼
Volume Still Exists
      │
      ▼
Delete Volume (Optional)
```

---

# 📋 List Volumes

```bash
docker volume ls
```

---

# 🔍 Inspect a Volume

```bash
docker volume inspect my-volume
```

Shows:

- Mount Point
- Driver
- Labels
- Name

---

# 🗑️ Remove a Volume

Remove a specific volume:

```bash
docker volume rm my-volume
```

Remove unused volumes:

```bash
docker volume prune
```

---

# 💾 Backup a Volume

Create a backup archive:

```bash
docker run --rm \
-v my-volume:/data \
-v $(pwd):/backup \
ubuntu tar czf /backup/backup.tar.gz /data
```

---

# 📥 Restore a Volume

Restore data from the backup:

```bash
docker run --rm \
-v my-volume:/data \
-v $(pwd):/backup \
ubuntu tar xzf /backup/backup.tar.gz -C /
```

---

# 📊 Useful Docker Volume Commands

Create Volume:

```bash
docker volume create my-volume
```

List Volumes:

```bash
docker volume ls
```

Inspect Volume:

```bash
docker volume inspect my-volume
```

Delete Volume:

```bash
docker volume rm my-volume
```

Delete Unused Volumes:

```bash
docker volume prune
```

---

# 🏗️ Docker Volume Workflow

```text
Create Volume
      │
      ▼
Run Container
      │
      ▼
Attach Volume
      │
      ▼
Store Data
      │
      ▼
Stop Container
      │
      ▼
Data Still Available
```

---

# 🆚 Bind Mount vs Volume

| Bind Mount | Docker Volume |
|------------|---------------|
| Uses Host Path | Managed by Docker |
| Good for Development | Best for Production |
| Easy File Editing | Better Isolation |
| Depends on Host Structure | Portable |

---

# 🏆 Best Practices

- ✅ Use Named Volumes for production
- ✅ Use Bind Mounts during development
- ✅ Backup important volumes regularly
- ✅ Remove unused volumes
- ✅ Store databases on volumes
- ✅ Never store critical data only inside containers

---

# 🌍 Common Use Cases

| Application | Volume Usage |
|-------------|--------------|
| MySQL | Database Storage |
| PostgreSQL | Persistent Database |
| MongoDB | Data Files |
| Nginx | Website Content |
| WordPress | Uploads |
| Jenkins | Configuration & Jobs |

---

# 📝 Key Takeaways

- Volumes provide persistent storage.
- Named Volumes are managed by Docker.
- Bind Mounts use directories from the host.
- Volumes remain even after containers are deleted.
- Regular backups are important for production workloads.

---

# 📋 Summary

In this chapter, you learned:

- Docker Volumes
- Named Volumes
- Anonymous Volumes
- Bind Mounts
- Volume Lifecycle
- Volume Commands
- Backup & Restore
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. What is a Docker Volume?
2. Why are volumes used?
3. Difference between Volume and Bind Mount?
4. How do you create a Docker Volume?
5. How do you list all Docker Volumes?

---

## Intermediate

6. Explain Docker Volume lifecycle.
7. What is an Anonymous Volume?
8. How do you inspect a volume?
9. How do you back up a Docker Volume?
10. When should you use Bind Mounts?

---

## Advanced

11. Explain Docker storage architecture.
12. How do Docker Volumes improve performance?
13. Why are volumes preferred for databases?
14. How do you migrate Docker volumes?
15. Explain production storage best practices.

---

# 🎯 Practice Exercises

## Exercise 1

Create a volume.

```bash
docker volume create my-volume
```

---

## Exercise 2

List all volumes.

```bash
docker volume ls
```

---

## Exercise 3

Run an Nginx container using the volume.

```bash
docker run -d \
--name nginx-volume \
-v my-volume:/usr/share/nginx/html \
nginx
```

---

## Exercise 4

Inspect the volume.

```bash
docker volume inspect my-volume
```

---

## Exercise 5

Delete the container and verify the volume still exists.

```bash
docker rm -f nginx-volume
docker volume ls
```

---

# 🧩 Mini Project

Create a file named:

```text
docker-volumes-guide.md
```

Include:

- Docker Volumes
- Bind Mounts
- Named Volumes
- Backup & Restore
- Docker Commands
- Best Practices

Commit to Git:

```bash
git add .
git commit -m "Add Docker Volumes guide"
```

---

# 📚 Further Reading

- Docker Volumes Documentation
- Docker Storage Drivers
- Docker CLI Reference
- Docker Best Practices

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [05 - Docker Containers](05-Docker-Containers.md) | [Docker Roadmap](README.md) | [07 - Docker Networking](07-Docker-Networking.md) |

---

# 🚀 What's Next?

In **Chapter 07 – Docker Networking**, you'll learn:

- 🌐 Docker Network Basics
- 🔌 Bridge Network
- 🏠 Host Network
- 🚫 None Network
- 🌍 Overlay Network
- 📡 Port Mapping
- 🔍 Network Inspection
- 🛠️ Custom Networks
- 🚀 Networking Best Practices
