# Coding Activity 14.3: Setting Up a Docker Network for MySQL

## Activity Information

### Module

Module 14: Java and Debezium

### Activity

Required Coding Activity 14.3: Setting Up a Docker Network for MySQL

### Learning Outcome

- Set up a network for Debezium in Docker.

---

# Objective

Learn how to create a Docker network and deploy a MySQL container that can communicate with other containers in a Change Data Capture (CDC) environment.

---

# Why This Activity Matters

Debezium architectures typically contain multiple services:

```text
MySQL
Debezium
Kafka
Applications
```

These services often run in separate Docker containers.

For Change Data Capture to work correctly:

```text
Containers must communicate.
```

Docker networking provides that communication layer.

---

# Docker Networks

A Docker network is a virtual network used by containers.

Example:

```text
Container A
      │
      ▼
Docker Network
      ▲
      │
Container B
```

Containers attached to the same network can interact with each other.

---

# Step 1: Create Docker Network

Command:

```bash
docker network create myCDCNetwork
```

Purpose:

- Creates a dedicated network.
- Allows future containers to communicate.
- Provides the infrastructure required for Debezium.

Verify:

```bash
docker network ls
```

Expected:

```text
myCDCNetwork
```

---

# Step 2: Create Activity Folder

Created:

```text
Activity14_3
```

Opened in:

```text
Visual Studio Code
```

Purpose:

- Store project files.
- Organize Docker resources.

---

# Step 3: Create customer.sql

Purpose:

- Create a new database.
- Create a customer table.
- Insert sample data automatically.

SQL Script:

```sql
CREATE DATABASE IF NOT EXISTS customerdb;

USE customerdb;

DROP TABLE IF EXISTS customer;

CREATE TABLE customer (
   id int not null,
   fullname varchar(255),
   email varchar(255),
   PRIMARY KEY (id)
);

INSERT INTO customerdb.customer
VALUES (1, 'John Doe', 'jd@example.com');
```

---

# Database Structure

## Database

```text
customerdb
```

## Table

```text
customer
```

## Columns

| Column | Type |
|----------|----------|
| id | int |
| fullname | varchar(255) |
| email | varchar(255) |

---

# Seed Data

```text
ID: 1
Name: John Doe
Email: jd@example.com
```

This record is automatically inserted when the container initializes.

---

# Step 4: Create Dockerfile

Dockerfile:

```dockerfile
FROM mysql:8.0

ENV MYSQL_DATABASE=customerdb \
    MYSQL_ROOT_PASSWORD=MyNewPass

ADD customer.sql /docker-entrypoint-initdb.d

EXPOSE 3306
```

Purpose:

- Start from the official MySQL image.
- Create database configuration.
- Execute SQL initialization script.
- Expose MySQL port.

---

# Dockerfile Breakdown

## Base Image

```dockerfile
FROM mysql:8.0
```

Uses MySQL version 8.

---

## Environment Variables

```dockerfile
ENV MYSQL_DATABASE=customerdb
```

Creates:

```text
customerdb
```

during initialization.

```dockerfile
MYSQL_ROOT_PASSWORD=MyNewPass
```

Sets the root password.

---

## Initialization Script

```dockerfile
ADD customer.sql /docker-entrypoint-initdb.d
```

Copies:

```text
customer.sql
```

into:

```text
/docker-entrypoint-initdb.d
```

MySQL automatically executes scripts from this folder during startup.

---

## Port Configuration

```dockerfile
EXPOSE 3306
```

Makes MySQL available on:

```text
3306
```

---

# Step 5: Verify No Running Containers

Command:

```bash
docker ps
```

Purpose:

- Avoid port conflicts.
- Ensure clean execution.

Expected:

```text
No running containers
```

---

# Step 6: Build MySQL Image

Command:

```bash
docker build -t mysqlactivity14_3 .
```

Purpose:

- Create a custom image.
- Bundle MySQL and initialization scripts.

Result:

```text
mysqlactivity14_3
```

image created successfully.

---

# Step 7: Run MySQL Container

Command:

```bash
docker run --rm \
--name mysqlserver \
-p 3306:3306 \
--network myCDCNetwork \
-d mysqlactivity14_3
```

Purpose:

- Create the MySQL container.
- Attach container to network.
- Enable access through port 3306.

---

# Command Breakdown

## Automatic Cleanup

```bash
--rm
```

Removes the container after shutdown.

---

## Container Name

```bash
--name mysqlserver
```

Assigns:

```text
mysqlserver
```

as the container name.

---

## Port Mapping

```bash
-p 3306:3306
```

Maps:

```text
Host Port 3306
        ↓
Container Port 3306
```

---

## Network Assignment

```bash
--network myCDCNetwork
```

Connects the container to:

```text
myCDCNetwork
```

---

# Step 8: Verify Container Running

Verification:

```bash
docker ps
```

Docker Desktop also shows:

```text
mysqlserver
```

running successfully.

---

# Architecture After Completion

```text
myCDCNetwork
      │
      ▼
 ┌─────────────┐
 │ mysqlserver │
 │  MySQL 8.0  │
 └─────────────┘
```

Future components:

```text
Debezium
Kafka
Spring Boot
```

will connect to this same network.

---

# Data Engineering Relevance

Docker networking is a common requirement for:

### CDC

```text
MySQL
 ↓
Debezium
 ↓
Kafka
```

---

### Data Pipelines

Containers exchange data over shared networks.

---

### Microservices

Applications communicate using Docker networking.

---

### Event-Driven Architectures

Services react to CDC events generated by databases.

---

# Lessons Learned

- Docker networks enable container communication.
- Containers can be isolated while still sharing network access.
- MySQL databases can be initialized automatically.
- Docker images can contain SQL initialization scripts.
- Custom networks simplify multi-container architectures.
- Debezium environments rely heavily on inter-container communication.

---

# Key Takeaways

- Docker networks are essential for CDC systems.
- MySQL can be deployed and initialized entirely through Docker.
- SQL scripts can automate database creation and data loading.
- Docker networking forms the foundation of Debezium architectures.
- This environment will be reused in upcoming Debezium activities.

---

# Completion Status

```text
✅ Completed
```