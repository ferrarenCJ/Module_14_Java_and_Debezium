# Video 14.12: Database Setup for Debezium

## Duration

**03:34**

---

# Overview

This video demonstrates how to create and initialize a MySQL database inside a Docker container and connect that container to a Docker network for use with Debezium.

This setup is a foundational step in building a Change Data Capture (CDC) architecture because Debezium needs access to a database that it can monitor for changes.

---

# Learning Objectives

After completing this video, you should be able to:

- Create a MySQL container in Docker.
- Initialize a database using SQL scripts.
- Configure a MySQL container for CDC.
- Connect a database container to a Docker network.
- Understand the role of MySQL in a Debezium architecture.

---

# Why Database Setup Is Important

Debezium captures changes from a source database.

Before Debezium can monitor data changes, a database must exist and be configured properly.

The database serves as the:

```text
Source System
```

for CDC events.

Database actions such as:

```text
INSERT
UPDATE
DELETE
```

are monitored and captured by Debezium.

---

# MySQL as the Source Database

In this module, MySQL serves as the CDC source database.

Responsibilities include:

- Storing application data
- Processing transactions
- Recording database changes
- Producing events for CDC

Example table:

```text
customer
```

Example data:

```text
John Doe
jd@example.com
```

---

# Docker Network Architecture

The video builds a network architecture similar to:

```text
myCDCNetwork
│
├── mysqlserver
├── Debezium
├── Kafka
└── Spring Boot Application
```

All containers communicate using the shared Docker network.

---

# Creating the Database

The database is initialized using:

```sql
CREATE DATABASE IF NOT EXISTS customerdb;
```

Purpose:

- Automatically create the database
- Eliminate manual setup
- Ensure consistency across environments

---

# Creating a Table

Example:

```sql
CREATE TABLE customer (
    id int not null,
    fullname varchar(255),
    email varchar(255),
    PRIMARY KEY (id)
);
```

Purpose:

- Store customer information
- Provide data for CDC demonstrations

---

# Loading Initial Data

Example:

```sql
INSERT INTO customerdb.customer
VALUES (
    1,
    'John Doe',
    'jd@example.com'
);
```

Purpose:

- Prepopulate the database
- Provide records for CDC testing

---

# Automated Database Initialization

MySQL containers automatically execute SQL scripts stored in:

```text
/docker-entrypoint-initdb.d
```

Example Dockerfile:

```dockerfile
FROM mysql:8.0

ENV MYSQL_DATABASE=customerdb \
    MYSQL_ROOT_PASSWORD=MyNewPass

ADD customer.sql /docker-entrypoint-initdb.d

EXPOSE 3306
```

---

# Dockerfile Components

## Base Image

```dockerfile
FROM mysql:8.0
```

Uses the official MySQL 8 image.

---

## Environment Variables

```dockerfile
MYSQL_DATABASE=customerdb
```

Creates:

```text
customerdb
```

during startup.

---

```dockerfile
MYSQL_ROOT_PASSWORD=MyNewPass
```

Sets the MySQL root password.

---

## Initialization Script

```dockerfile
ADD customer.sql /docker-entrypoint-initdb.d
```

Copies the SQL file into the MySQL initialization folder.

---

## Port Configuration

```dockerfile
EXPOSE 3306
```

Exposes the standard MySQL port.

---

# Building the Docker Image

Command:

```bash
docker build -t mysqlactivity14_3 .
```

Result:

```text
mysqlactivity14_3
```

A custom MySQL image containing:

- MySQL Server
- Database configuration
- Initialization scripts

---

# Running the MySQL Container

Command:

```bash
docker run --rm \
--name mysqlserver \
-p 3306:3306 \
--network myCDCNetwork \
-d mysqlactivity14_3
```

Purpose:

- Start MySQL
- Attach to Docker network
- Make database available to Debezium

---

# Network Communication

Once running:

```text
mysqlserver
```

can communicate with other containers on:

```text
myCDCNetwork
```

Example future architecture:

```text
mysqlserver
      ↓
   Debezium
      ↓
     Kafka
      ↓
Spring Boot
```

---

# CDC Workflow

Database change:

```sql
UPDATE customer
SET email='new@email.com'
WHERE id=1;
```

Flow:

```text
MySQL
   ↓
Debezium
   ↓
Event Generated
   ↓
Consumer Application
```

---

# Data Engineering Relevance

This setup reflects real-world data engineering environments.

Common examples:

### Data Warehousing

```text
MySQL
  ↓
CDC
  ↓
Warehouse
```

---

### Real-Time Analytics

```text
Database
   ↓
Debezium
   ↓
Analytics
```

---

### Event Streaming

```text
MySQL
   ↓
Debezium
   ↓
Kafka
```

---

### Microservices

Database changes are propagated automatically across services.

---

# Key Terms

## MySQL

Open-source relational database management system.

---

## Docker Container

An isolated environment for running applications.

---

## Docker Network

A virtual network that enables container communication.

---

## CDC

Change Data Capture.

A process used to identify and distribute database 