# Video 14.13: Using Debezium with Spring Boot

## Duration

**06:39**

---

# Overview

This video demonstrates how to use **Debezium** within a **Spring Boot** application to monitor changes made to a MySQL database.

The application runs inside a Docker container and uses Debezium's MySQL connector to capture database changes directly from MySQL binary logs. Whenever records are inserted, updated, or deleted, Debezium generates change events that can be consumed by applications in near real-time.

---

# Learning Objectives

After completing this video, you should be able to:

- Explain how Debezium integrates with Spring Boot.
- Understand how a Spring Boot application can monitor database changes.
- Describe Debezium's role in CDC architectures.
- Explain how MySQL binary logs support CDC.
- Understand how Docker networking enables container communication.

---

# What Is Happening in the Architecture?

The architecture demonstrated in this module consists of:

```text
Docker Network
│
├── mysqlserver
│
└── debeziumserver
       │
       ▼
 Spring Boot Application
       │
       ▼
     Debezium
       │
       ▼
   Change Events
```

The Spring Boot application embeds Debezium and continuously monitors the MySQL database.

---

# Why Spring Boot?

Spring Boot simplifies Java application development by providing:

- Auto-configuration
- Embedded web servers
- Dependency management
- Simplified deployment

Benefits:

```text
Less Configuration
Faster Development
Standalone Execution
```

---

# Why Debezium?

Debezium provides:

```text
Change Data Capture (CDC)
```

without requiring applications to repeatedly query databases.

Instead of:

```text
Application
     ↓
Poll Database
     ↓
Check for Changes
```

Debezium supports:

```text
Database Change
      ↓
Debezium Detects Event
      ↓
Application Receives Event
```

---

# Change Data Capture (CDC)

CDC tracks database operations:

```text
INSERT
UPDATE
DELETE
```

Benefits include:

- Near real-time processing
- Reduced database load
- Improved scalability
- Better system synchronization

---

# MySQL and Binary Logs

Debezium connects to MySQL by reading:

```text
Binary Logs (Binlogs)
```

The binary log records:

```text
INSERT
UPDATE
DELETE
```

operations.

Example:

```sql
INSERT INTO customer
VALUES (2,'Peter Parker','pp@example.com');
```

This action is written to the binlog.

Debezium reads the binlog and generates a CDC event.

---

# Spring Boot Startup

When the application starts:

```bash
mvn spring-boot:run
```

Spring Boot initializes:

```text
Embedded Tomcat
Application Context
Debezium Engine
MySQL Connector
```

Typical output:

```text
Started TvApplication
```

---

# Debezium Connector Configuration

The application uses:

```text
io.debezium.connector.mysql.MySqlConnector
```

Configuration includes:

```text
database.hostname = mysqlserver
database.dbname = customerdb
database.port = 3306
database.user = root
```

These settings allow Debezium to connect to MySQL.

---

# Initial Snapshot

When Debezium starts for the first time:

```text
No previous offset found
```

It performs a snapshot.

Purpose:

```text
Read existing rows
Capture table structure
Establish baseline state
```

Example:

```text
customerdb.customer
```

table is scanned.

---

# Snapshot Process

Debezium performs:

```text
Step 1 - Preparing
Step 2 - Determine Tables
Step 3 - Lock Tables
Step 4 - Determine Offset
Step 5 - Read Schema
Step 6 - Persist History
Step 7 - Read Data
```

This creates an initial view of the database.

---

# Existing Record Detection

The initial row:

```text
John Doe
jd@example.com
```

generates:

```text
Key = Struct{id=1}
```

Event:

```text
after={
    id=1,
    fullname=John Doe,
    email=jd@example.com
}
```

This confirms successful CDC setup.

---

# Streaming Mode

After snapshot completion:

```text
Starting streaming
```

appears.

Debezium then continuously monitors:

```text
mysqlserver
```

for changes.

---

# Capturing New Records

Example:

```sql
INSERT INTO customerdb.customer
VALUES (
    2,
    'Peter Parker',
    'pp@example.com'
);
```

Debezium detects:

```text
Key = Struct{id=2}
```

Output:

```text
after={
    id=2,
    fullname=Peter Parker,
    email=pp@example.com
}
```

Operation:

```text
op=c
```

Meaning:

```text
CREATE (INSERT)
```

---

# Docker Networking

Both containers communicate through:

```text
myCDCNetwork
```

Containers:

```text
mysqlserver
debeziumserver
```

Networking allows:

```text
Debezium
      ↓
Access MySQL
      ↓
Read Binlogs
      ↓
Generate Events
```

---

# Debezium Event Structure

Each CDC event contains:

### Key

```text
Struct{id=2}
```

Identifies the affected record.

---

### After Values

```text
fullname=Peter Parker
email=pp@example.com
```

Shows the new row data.

---

### Operation Type

```text
op=c
```

Operation codes:

```text
c = Create
u = Update
d = Delete
r = Read (Snapshot)
```

---

# Data Engineering Relevance

Debezium is commonly used in:

### Event Streaming

```text
MySQL
 ↓
Debezium
 ↓
Kafka
```

---

### Data Warehouses

```text
Operational Database
 ↓
CDC
 ↓
Warehouse
```

---

### Data Lakes

Near real-time ingestion.

---

### Analytics Platforms

Immediate availability of new records.

---

### Microservices

Automatic propagation of changes across services.

---

# Advantages of Using Debezium

## Near Real-Time Processing

Changes become available immediately.

---

## Reduced Polling

Eliminates repeated database queries.

---

## Scalable Architecture

Supports multiple downstream consumers.

---

## Reliable CDC

Uses database 