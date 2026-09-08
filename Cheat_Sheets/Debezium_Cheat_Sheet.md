# Debezium Cheat Sheet

## What is Debezium?

Debezium is an open-source Change Data Capture (CDC) platform.

It captures:

```text
INSERT
UPDATE
DELETE
```

events from databases.

---

# Supported Databases

- MySQL
- PostgreSQL
- MongoDB
- SQL Server
- Oracle

---

# CDC Flow

```text
Database Change
       ↓
Binlog
       ↓
Debezium
       ↓
CDC Event
       ↓
Consumer
```

---

# Debezium Features

## Snapshots

Captures initial database state.

---

## Filters

Captures selected records.

---

## Masking

Hides sensitive information.

---

## Monitoring

Tracks connector health.

---

# Event Types

```text
c = Create
u = Update
d = Delete
r = Read
```

---

# MySQL Connector

```java
io.debezium.connector.mysql.MySqlConnector
```

---

# Example Configuration

```java
.with(
 "database.hostname",
 "mysqlmasterdb"
)
```

```java
.with(
 "database.dbname",
 "employeedb"
)
```

---

# Start Application

```bash
mvn spring-boot:run
```

---

# Snapshot Example

```text
FirstName=John
```

---

# CDC Example

```sql
INSERT INTO employee
VALUES (
  2,
  'Mary',
  'Doe'
);
```

Detected by Debezium:

```text
FirstName=Mary
```

---

# Docker Deployment

Build:

```bash
docker build -t debeziumimg .
```

Run:

```bash
docker run -dit \
--name debeziumserver \
debeziumimg bash
```

---

# Final Assignment Architecture

```text
mysqlmasterdb
      ↓
   Binlog
      ↓
Debezium
      ↓
Spring Boot
      ↓
CDC Events
```

---

# Troubleshooting

Check Containers:

```bash
docker ps
```

Check Networks:

```bash
docker network ls
```

Enter Container:

```bash
docker exec -it debeziumserver bash
```

---

# Key Terms

- CDC
- Debezium
- Connector
- Snapshot
- Event Stream
- Binlog
- Monitoring

---

# Module 14 Takeaway

Debezium enables near real-time CDC by reading database transaction logs and streaming changes to applications.