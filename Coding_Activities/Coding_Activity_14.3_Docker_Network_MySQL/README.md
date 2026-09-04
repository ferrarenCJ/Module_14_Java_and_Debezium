# Coding Activity 14.3: Setting Up a Docker Network for MySQL

## Objective

The objective of this activity is to create a Docker network and configure a MySQL container to participate in a Change Data Capture (CDC) architecture. This activity demonstrates how Docker containers communicate through a shared network and how databases can be initialized automatically during container creation.

---

## Learning Outcome

- Set up a network for Debezium in Docker.

---

## Purpose

Debezium relies on multiple containers communicating with each other to capture and distribute database changes.

This activity prepares the foundation for future Debezium exercises by:

- Creating a Docker network
- Creating a custom MySQL image
- Initializing a database automatically
- Connecting a MySQL container to a Docker network
- Preparing the environment for CDC implementations

---

## Activity Summary

In this activity:

1. Created a Docker network named `myCDCNetwork`.
2. Created a working folder named `Activity14_3`.
3. Created a database initialization script.
4. Created a custom MySQL Docker image.
5. Initialized a customer database.
6. Created a MySQL container.
7. Connected the container to the Docker network.
8. Verified successful execution in Docker Desktop.

---

## Files Created

### customer.sql

```sql
CREATE DATABASE IF NOT EXISTS customerdb;

USE customerdb;

DROP TABLE IF EXISTS `customer`;

CREATE TABLE `customer` (
   `id` int not null,
   `fullname` varchar(255) default null,
   `email` varchar(255) default null,
   PRIMARY KEY (`id`)
);

INSERT INTO customerdb.customer
VALUES (1, 'John Doe', 'jd@example.com');
```

### Dockerfile

```dockerfile
FROM mysql:8.0

ENV MYSQL_DATABASE=customerdb \
    MYSQL_ROOT_PASSWORD=MyNewPass

ADD customer.sql /docker-entrypoint-initdb.d

EXPOSE 3306
```

---

## Commands Used

### Create Docker Network

```bash
docker network create myCDCNetwork
```

### Verify Network

```bash
docker network ls
```

### Build Docker Image

```bash
docker build -t mysqlactivity14_3 .
```

### Run MySQL Container

```bash
docker run --rm --name mysqlserver -p 3306:3306 --network myCDCNetwork -d mysqlactivity14_3
```

### Verify Running Container

```bash
docker ps
```

---

## Architecture

```text
Docker Network: myCDCNetwork

        ┌──────────────┐
        │ mysqlserver  │
        │   MySQL 8    │
        └──────┬───────┘
               │
               ▼

       Future Debezium
       Connectors & Apps
```

---

## Folder Structure

```text
Activity14_3/
├── customer.sql
└── Dockerfile
```

---

## Screenshots Collected

- Step 1: Create Docker Network
- Step 2: Open Folder in VS Code
- Step 3: customer.sql File
- Step 4: Dockerfile
- Step 5: No Running Containers
- Step 6: Build MySQL Image
- Step 7: Create MySQL Container
- Step 8: Docker Desktop Showing Running Container

---

## Key Takeaways

- Docker networks allow containers to communicate.
- Containers can be attached to custom networks.
- MySQL databases can be initialized during container startup.
- Docker images can include SQL scripts for automated database creation.
- Container networking provides the foundation for CDC architectures using Debezium.

---

## Completion Status

```text
✅ Completed
```