# Docker Reference Notes

## Overview

Docker is a containerization platform that packages applications and their dependencies into portable containers.

Benefits:

- Consistency
- Portability
- Scalability
- Isolation

---

# Core Components

## Docker Image

A read-only template used to create containers.

Example:

```bash
docker build -t myimage .
```

---

## Docker Container

A running instance of an image.

Example:

```bash
docker run myimage
```

---

## Dockerfile

Instructions used to build an image.

Example:

```dockerfile
FROM mysql:8.0

EXPOSE 3306
```

---

# Common Docker Commands

## Build Image

```bash
docker build -t myimage .
```

---

## Run Container

```bash
docker run myimage
```

---

## Run Detached

```bash
docker run -d myimage
```

---

## View Running Containers

```bash
docker ps
```

---

## View All Containers

```bash
docker ps -a
```

---

## Stop Container

```bash
docker stop container_name
```

---

## Remove Container

```bash
docker rm container_name
```

---

## View Images

```bash
docker images
```

---

# Docker Networking

Create network:

```bash
docker network create mynetwork
```

Example:

```bash
docker network create CDCFinalAssignment
```

---

# View Networks

```bash
docker network ls
```

---

# Inspect Network

```bash
docker network inspect CDCFinalAssignment
```

---

# Container Communication

```text
Network
│
├── mysqlserver
│
└── debeziumserver
```

Containers attached to the same network can communicate using container names.

---

# Enter Container

```bash
docker exec -it container_name bash
```

Example:

```bash
docker exec -it mysqlserver bash
```

---

# File Transfers

Copy file into container:

```bash
docker cp file.txt container:/tmp
```

Copy file from container:

```bash
docker cp container:/tmp/file.txt .
```

---

# Docker Architecture

```text
Dockerfile
      ↓
Docker Image
      ↓
Docker Container
```

---

# Module 14 Relevance

Docker was used to:

- Create MySQL images
- Create Debezium images
- Create Docker networks
- Run Spring Boot applications
- Implement CDC environments