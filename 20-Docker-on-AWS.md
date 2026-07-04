# Docker Notes
# Chapter 20 - Docker on AWS

> 📘 **Level:** Beginner to Intermediate
> ⏱️ **Estimated Reading Time:** 60–75 minutes
> 🛠️ **Practice Time:** 4–5 hours

---

# 📚 Table of Contents

1. Why Run Docker on AWS?
2. AWS Services for Docker
3. Docker Deployment Options
4. Docker with Amazon EC2
5. Docker with Amazon ECR
6. Docker with Amazon ECS
7. Docker with Amazon EKS
8. CI/CD Workflow
9. Useful Commands
10. Best Practices
11. Summary
12. Interview Questions
13. Practice Exercises
14. Mini Project
15. Further Reading

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Docker deployment on AWS
- Store Docker images in Amazon ECR
- Deploy containers using Amazon ECS
- Run Kubernetes workloads using Amazon EKS
- Build Docker-based CI/CD pipelines on AWS

---

# 📖 Why Run Docker on AWS?

AWS provides scalable and reliable infrastructure for running Docker containers.

Benefits:

- ✅ High Availability
- ✅ Auto Scaling
- ✅ Load Balancing
- ✅ Secure Image Storage
- ✅ Managed Container Services
- ✅ Easy Monitoring

---

# ☁️ AWS Services for Docker

| AWS Service | Purpose |
|-------------|----------|
| EC2 | Run Docker manually |
| ECR | Store Docker images |
| ECS | Managed container service |
| EKS | Managed Kubernetes |
| ALB | Load balance containers |
| CloudWatch | Monitor containers |
| IAM | Access management |
| CodePipeline | CI/CD automation |

---

# 🏗️ Docker Deployment Options

```text
Docker Image
      │
      ▼
Amazon ECR
      │
      ▼
 ┌───────────────┐
 │ ECS or EKS    │
 └───────────────┘
      │
      ▼
Application Running
```

---

# 🖥️ Docker on Amazon EC2

Install Docker on an EC2 instance.

Example:

```bash
sudo yum update -y

sudo yum install docker -y

sudo systemctl start docker

sudo systemctl enable docker
```

Run a container:

```bash
docker run -d -p 80:80 nginx
```

Suitable for:

- Learning
- Development
- Small applications

---

# 📦 Amazon ECR (Elastic Container Registry)

Amazon ECR is a managed Docker image registry.

Workflow:

```text
Build Image

↓

Tag Image

↓

Push to Amazon ECR

↓

Deploy from ECR
```

Commands:

Login:

```bash
aws ecr get-login-password
```

Tag image:

```bash
docker tag myapp:1.0 <ecr-repository>
```

Push image:

```bash
docker push <ecr-repository>
```

---

# 🚀 Amazon ECS (Elastic Container Service)

Amazon ECS is AWS's managed container orchestration service.

Features:

- Managed clusters
- Fargate support
- EC2 support
- Auto Scaling
- Load Balancing

Workflow:

```text
Docker Image

↓

Amazon ECR

↓

Amazon ECS

↓

Running Containers
```

---

# ☸️ Amazon EKS (Elastic Kubernetes Service)

Amazon EKS is a managed Kubernetes service.

Features:

- Kubernetes API
- Managed control plane
- Auto Scaling
- High Availability
- Integration with AWS services

Workflow:

```text
Docker Image

↓

Amazon ECR

↓

Amazon EKS

↓

Pods
```

---

# 🔄 Docker CI/CD on AWS

Typical deployment pipeline:

```text
Developer

↓

Git Push

↓

CodeBuild

↓

Docker Build

↓

Push to ECR

↓

Deploy ECS/EKS
```

AWS Services:

- CodeCommit
- CodeBuild
- CodePipeline
- ECR
- ECS/EKS

---

# 📊 Useful Commands

Build image:

```bash
docker build -t myapp .
```

Run locally:

```bash
docker run myapp
```

Tag image:

```bash
docker tag myapp:latest <ecr-repository>
```

Push image:

```bash
docker push <ecr-repository>
```

Pull image:

```bash
docker pull <ecr-repository>
```

---

# 🏗️ Docker on AWS Workflow

```text
Write Application
        │
        ▼
Build Docker Image
        │
        ▼
Push to Amazon ECR
        │
        ▼
Deploy to ECS / EKS
        │
        ▼
Monitor with CloudWatch
```

---

# 🏆 Best Practices

- ✅ Store images in Amazon ECR
- ✅ Use ECS Fargate for serverless containers
- ✅ Use EKS for Kubernetes workloads
- ✅ Scan container images
- ✅ Enable CloudWatch logging
- ✅ Use IAM roles instead of hardcoded credentials
- ✅ Configure Auto Scaling
- ✅ Keep Docker images small

---

# 🌍 Common Use Cases

| Use Case | AWS Service |
|----------|-------------|
| Store Images | Amazon ECR |
| Run Containers | Amazon ECS |
| Kubernetes | Amazon EKS |
| Virtual Machine | Amazon EC2 |
| Monitoring | CloudWatch |
| CI/CD | CodePipeline |

---

# 📝 Key Takeaways

- Amazon ECR stores Docker images.
- Amazon ECS runs Docker containers without managing Kubernetes.
- Amazon EKS runs Kubernetes workloads.
- EC2 provides full control over Docker.
- AWS integrates Docker with monitoring, security, and CI/CD services.

---

# 📋 Summary

In this chapter, you learned:

- Docker on AWS
- Amazon EC2
- Amazon ECR
- Amazon ECS
- Amazon EKS
- CI/CD Workflow
- Best Practices

---

# ❓ Interview Questions

## Beginner

1. Why run Docker on AWS?
2. What is Amazon ECR?
3. What is Amazon ECS?
4. What is Amazon EKS?
5. Which AWS service stores Docker images?

---

## Intermediate

6. Explain the Docker deployment workflow on AWS.
7. Difference between ECS and EKS?
8. Why use Amazon ECR instead of Docker Hub?
9. Explain Docker deployment using ECS Fargate.
10. How does CloudWatch help Docker deployments?

---

## Advanced

11. Design a production-ready Docker architecture on AWS.
12. Explain a CI/CD pipeline using CodePipeline and ECR.
13. How would you secure Docker containers on AWS?
14. Explain Auto Scaling with ECS.
15. Compare Docker on EC2, ECS, and EKS.

---

# 🎯 Practice Exercises

## Exercise 1

Install Docker on an EC2 instance.

---

## Exercise 2

Build a Docker image.

```bash
docker build -t myapp .
```

---

## Exercise 3

Push the image to Amazon ECR.

---

## Exercise 4

Deploy the image to Amazon ECS.

---

## Exercise 5

Monitor the application using CloudWatch.

---

# 🧩 Mini Project

Create a file named:

```text
docker-on-aws-guide.md
```

Include:

- Docker on AWS Overview
- Amazon EC2
- Amazon ECR
- Amazon ECS
- Amazon EKS
- CI/CD Workflow
- Best Practices

Commit to Git:

```bash
git add .
git commit -m "Add Docker on AWS guide"
```

---

# 📚 Further Reading

- Docker Documentation
- Amazon ECR Documentation
- Amazon ECS Documentation
- Amazon EKS Documentation
- AWS Well-Architected Framework

---

# 📚 Navigation

| ⬅️ Previous | 🏠 Home | ➡️ Next |
|------------|---------|---------|
| [19 - Docker in CI/CD](19-Docker-in-CI-CD.md) | [Docker Roadmap](README.md) | [21 - Docker Interview Questions](21-Docker-Interview-Questions.md) |

---

# 🚀 What's Next?

In **Chapter 21 – Docker Interview Questions**, you'll learn:

- 💼 Beginner Questions
- ⚙️ Intermediate Questions
- 🚀 Advanced & Scenario-Based Questions
- 📝 Common Commands
- 🎯 Interview Tips for DevOps Engineers
