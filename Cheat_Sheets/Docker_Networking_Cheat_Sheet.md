# Docker Networking Cheat Sheet

## Create Network

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

# Create Container on Network

```bash
docker run \
--network CDCFinalAssignment \
imagename
```

---

# Example

```bash
docker run --name mysqlserver \
--network CDCFinalAssignment \
mysqlimg
```

---

# Verify Running Containers

```bash
docker ps
```

---

# Stop Container

```bash
docker stop container_name
```

---

# Enter Container

```bash
docker exec -it container_name bash
```

---

# Architecture Example

```text
CDCFinalAssignment
│
├── mysqlserver
│
└── debeziumserver
```

---

# Benefits of Docker Networks

- Container Communication
- Service Discovery
- Isolation
- Security

---

# Common Commands

```bash
docker ps
docker stop
docker rm
docker network ls
docker network inspect
docker exec
```

---

# Module 14 Takeaway

Docker networking allowed MySQL and Debezium containers to communicate in Activities 14.3, 14.4, and Final Assignment 14.1.