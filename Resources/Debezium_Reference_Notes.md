# Debezium Reference Notes

## Overview

Debezium is an open-source Change Data Capture (CDC) platform.

Debezium captures changes occurring in databases and streams those changes to applications.

Captured operations:

```text
INSERT
UPDATE
DELETE
```

---

# What is CDC?

CDC stands for:

```text
Change Data Capture
```

Purpose:

```text
Detect Database Changes
```

---

# Traditional Approach

```text
Application
      ↓
Repeated Queries
      ↓
Database
```

---

# Debezium Approach

```text
Database Change
      ↓
Binlog
      ↓
Debezium
      ↓
CDC Event
```

---

# Supported Databases

- MySQL
- PostgreSQL
- MongoDB
- SQL Server
- Oracle

---

# Debezium Connectors

Connectors capture changes from specific database technologies.

Example:

```java
io.debezium.connector.mysql.MySqlConnector
```

---

# Connector Capabilities

## Snapshots

Capture current database state.

---

## Filters

Capture selected data.

---

## Masking

Hide sensitive information.

---

## Monitoring

Track connector health and performance.

---

# MySQL and Debezium

MySQL writes changes to:

```text
Binlog
```

Debezium reads:

```text
MySQL Binlogs
```

to generate CDC events.

---

# Event Operations

## Create

```text
op=c
```

---

## Update

```text
op=u
```

---

## Delete

```text
op=d
```

---

## Read

```text
op=r
```

---

# CDC Workflow

```text
INSERT
      ↓
MySQL Binlog
      ↓
Debezium
      ↓
CDC Event
```

---

# Example Event

```text
Key = Struct{id=2}

FirstName=Mary
LastName=Doe
```

---

# Snapshot Example

Initial data:

```text
FirstName=John
```

Detected during startup.

---

# Build Debezium Image

```bash
docker build -t debeziumimg .
```

---

# Create Container

```bash
docker run -dit \
--name debeziumserver \
debeziumimg bash
```

---

# Start Application

```bash
mvn spring-boot:run
```

---

# Troubleshooting

Check containers:

```bash
docker ps
```

Check networks:

```bash
docker network ls
```

Enter container:

```bash
docker exec -it debeziumserver bash
```

---

# Architecture

```text
MySQL
   ↓
Binlog
   ↓
Debezium
   ↓
Spring Boot
   ↓
CDC Output
```

---

# Module 14 Relevance

Debezium was used to:

- Connect to MySQL
- Read binlogs
- Detect database changes
- Perform CDC
- Stream events in real time