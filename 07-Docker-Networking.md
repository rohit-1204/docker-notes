# Docker Notes
# Chapter 07 - Docker Networking

> 📘 **Level:** Beginner to Intermediate
> ⏱️ **Estimated Reading Time:** 75–90 minutes
> 🛠️ **Practice Time:** 4–5 hours

---

# 📚 Table of Contents

1. Introduction to Docker Networking
2. Why Docker Networking?
3. Docker Network Architecture
4. Types of Docker Networks
5. Bridge Network
6. Host Network
7. None Network
8. Overlay Network
9. Macvlan Network
10. Port Mapping
11. Custom Networks
12. Network Commands
13. DNS in Docker
14. Best Practices
15. Summary
16. Interview Questions
17. Practice Exercises
18. Mini Project
19. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Docker Networking
- Learn different network drivers
- Connect containers together
- Expose applications using port mapping
- Create custom Docker networks
- Understand Docker DNS

---

# 📖 What is Docker Networking?

Docker Networking allows containers to communicate with:

- Other containers
- The Docker Host
- External systems
- The Internet

Every container is connected to a network.

---

# 💡 Why Docker Networking?

Without networking:

```text
Container A

❌ Cannot communicate

Container B
```

With networking:

```text
Container A
      │
      ▼
Docker Network
      │
      ▼
Container B
```

Benefits:

- ✅ Container Communication
- ✅ Service Discovery
- ✅ Isolation
- ✅ Internet Access
- ✅ Secure Communication

---

# 🏗️ Docker Network Architecture

```text
              Docker Host
                    │
      ┌─────────────┼─────────────┐
      ▼             ▼             ▼
 Container A   Container B   Container C
      │             │             │
      └─────────────┼─────────────┘
                    ▼
            Docker Network
```

---

# 🌐 Types of Docker Networks

| Network | Purpose |
|----------|----------|
| Bridge | Default network |
| Host | Shares host network |
| None | No networking |
| Overlay | Multi-host communication |
| Macvlan | Container gets its own MAC/IP |

---

# 🌉 Bridge Network

The **Bridge Network** is the default Docker network.

Features:

- Default for standalone containers
- Containers communicate using IP or container name
- Isolated from host network

List networks:

```bash
docker network ls
```

Run container on bridge:

```bash
docker run -d nginx
```

Inspect bridge network:

```bash
docker network inspect bridge
```

---

# 🏠 Host Network

Containers share the host's network stack.

```text
Host Network

├── Host
└── Container
```

Run container:

```bash
docker run --network host nginx
```

Advantages:

- High performance
- No NAT

Disadvantages:

- Less isolation
- Port conflicts possible

---

# 🚫 None Network

Container has **no network access**.

```bash
docker run --network none ubuntu
```

Use Cases:

- Security testing
- Offline processing
- Isolated workloads

---

# 🌍 Overlay Network

Overlay networks connect containers across multiple Docker hosts.

Used with:

- Docker Swarm
- Multi-node deployments

```text
Host A
   │
Overlay Network
   │
Host B
```

Create overlay network:

```bash
docker network create \
-d overlay my-overlay
```

---

# 🖥️ Macvlan Network

Macvlan gives containers their own MAC address and IP on the physical network.

```text
Router
   │
   ├── Host
   ├── Container 1
   └── Container 2
```

Use Cases:

- Legacy applications
- Network appliances
- Monitoring tools

---

# 🔌 Port Mapping

Port mapping exposes a container port to the host.

Example:

```bash
docker run -d -p 8080:80 nginx
```

Format:

```text
HostPort:ContainerPort
```

Example:

```text
Host Port 8080
      │
      ▼
Container Port 80
```

Access:

```
http://localhost:8080
```

---

# 🌐 Create a Custom Network

Create:

```bash
docker network create my-network
```

Run a container:

```bash
docker run -d \
--network my-network \
--name web nginx
```

Attach another container:

```bash
docker run -it \
--network my-network \
ubuntu
```

Both containers can communicate using container names.

---

# 🔍 Inspect Networks

Inspect a network:

```bash
docker network inspect my-network
```

Shows:

- Connected containers
- Network ID
- Driver
- IP Range
- Gateway

---

# 🗑️ Remove Networks

Delete a network:

```bash
docker network rm my-network
```

Delete unused networks:

```bash
docker network prune
```

---

# 🌎 Docker DNS

Docker provides built-in DNS.

Containers on the same custom network can communicate using **container names**.

Example:

```text
web

↓

database
```

Instead of:

```text
172.18.0.3
```

Example:

```bash
ping database
```

---

# 📊 Useful Docker Network Commands

List Networks:

```bash
docker network ls
```

Inspect Network:

```bash
docker network inspect bridge
```

Create Network:

```bash
docker network create my-network
```

Connect Container:

```bash
docker network connect my-network web
```

Disconnect Container:

```bash
docker network disconnect my-network web
```

Delete Network:

```bash
docker network rm my-network
```

Prune Networks:

```bash
docker network prune
```

---

# 🏗️ Docker Networking Workflow

```text
Create Network
       │
       ▼
Run Container A
       │
       ▼
Run Container B
       │
       ▼
Containers Communicate
       │
       ▼
Expose Application
Using Port Mapping
```

---

# 🏆 Best Practices

- ✅ Use custom bridge networks
- ✅ Use container names instead of IP addresses
- ✅ Expose only required ports
- ✅ Remove unused networks
- ✅ Use Overlay for multi-host deployments
- ✅ Use Host networking only when necessary
- ✅ Isolate applications using separate networks

---

# 🌍 Common Use Cases

| Application | Network Type |
|-------------|--------------|
| Nginx Web Server | Bridge |
| MySQL Database | Bridge |
| Redis Cache | Bridge |
| Docker Swarm | Overlay |
| Monitoring Tools | Host |
| Secure Containers | None |

---

# 📝 Key Takeaways

- Every container connects to a Docker network.
- Bridge is the default network.
- Host shares the host's network stack.
- None disables networking.
- Overlay connects containers across multiple hosts.
- Docker provides built-in DNS for service discovery.

---

# 📋 Summary

In this chapter, you learned:

- Docker Networking
- Network Drivers
- Bridge Network
- Host Network
- None Network
- Overlay Network
- Macvlan Network
- Port Mapping
- Custom Networks
- Docker DNS
- Network Commands
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. What is Docker Networking?
2. What is the default Docker network?
3. How do you list Docker networks?
4. What is port mapping?
5. How do containers communicate?

---

## Intermediate

6. Difference between Bridge and Host network?
7. What is an Overlay network?
8. What is Docker DNS?
9. How do you create a custom network?
10. Explain the None network.

---

## Advanced

11. Explain Docker networking architecture.
12. When would you use Host networking?
13. How does Overlay networking work?
14. What is Macvlan?
15. How does Docker perform service discovery?

---

# 🎯 Practice Exercises

## Exercise 1

List all Docker networks.

```bash
docker network ls
```

---

## Exercise 2

Create a custom bridge network.

```bash
docker network create my-network
```

---

## Exercise 3

Run an Nginx container on the custom network.

```bash
docker run -d \
--network my-network \
--name web \
nginx
```

---

## Exercise 4

Inspect the custom network.

```bash
docker network inspect my-network
```

---

## Exercise 5

Expose Nginx using port mapping.

```bash
docker run -d \
-p 8080:80 \
nginx
```

Open:

```
http://localhost:8080
```

---

# 🧩 Mini Project

Create a file named:

```text
docker-networking-guide.md
```

Include:

- Docker Networking
- Network Types
- Port Mapping
- Custom Networks
- Docker DNS
- Best Practices

Commit to Git:

```bash
git add .
git commit -m "Add Docker Networking guide"
```

---

# 📚 Further Reading

- Docker Networking Documentation
- Docker CLI Reference
- Docker Bridge Network Guide
- Docker Overlay Network Guide

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [06 - Docker Volumes](06-Docker-Volumes.md) | [Docker Roadmap](README.md) | [08 - Dockerfile](08-Dockerfile.md) |

---

# 🚀 What's Next?

In **Chapter 08 – Dockerfile**, you'll learn:

- 📝 What is a Dockerfile?
- 🏗️ Dockerfile Instructions
- 📦 Build Custom Images
- 📂 COPY vs ADD
- ⚙️ CMD vs ENTRYPOINT
- 🌍 ENV & ARG
- 🧹 Optimize Dockerfiles
- 🚀 Docker Image Build Best Practices
