# Video 14.14: Application Architecture

## Duration

**01:25**

---

# Overview

In this video, Dr. Sanchez reviews the complete architecture developed throughout Module 14.

The architecture combines:

- Docker containers
- MySQL
- Spring Boot
- Debezium
- Change Data Capture (CDC)

The application demonstrates how multiple containers can work together to support near real-time monitoring of database changes.

---

# Learning Objectives

After completing this video, you should be able to:

- Describe the architecture of the Debezium application.
- Explain the role of each container.
- Understand how Docker networking enables communication.
- Explain how Debezium captures database changes.
- Describe how Spring Boot integrates with Debezium.

---

# Architecture Overview

The completed solution contains multiple components running inside Docker.

```text
myCDCNetwork
│
├── mysqlserver
│
└── debeziumserver
```

Each container has a specific responsibility.

---

# MySQL Container

Container:

```text
mysqlserver
```

Purpose:

- Store application data
- Process database transactions
- Generate binlog events
- Act as the CDC source system

Database:

```text
customerdb
```

Table:

```text
customer
```

Example record:

```text
John Doe
jd@example.com
```

---

# Debezium Container

Container:

```text
debeziumserver
```

Purpose:

- Run the Spring Boot application
- Host the Debezium connector
- Read MySQL binlogs
- Generate CDC events

This container continuously monitors the MySQL database.

---

# Docker Network

Network:

```text
myCDCNetwork
```

Purpose:

- Connect containers together
- Enable inter-container communication
- Allow Debezium to access MySQL

Without this network:

```text
mysqlserver
```

and

```text
debeziumserver
```

would not be able to communicate.

---

# Complete Application Flow

```text
User
 │
 ▼

MySQL Workbench
 │
 ▼

customerdb
 │
 ▼

MySQL Binlog
 │
 ▼

Debezium Connector
 │
 ▼

Spring Boot Application
 │
 ▼

CDC Event Output
```

---

# Database Changes

Examples:

```sql
INSERT
```

```sql
UPDATE
```

```sql
DELETE
```

These operations are written to the MySQL binary log.

---

# MySQL Binary Log

The binlog records:

```text
Database Activity
```

Examples:

```text
Row Inserted
Row Updated
Row Deleted
```

Debezium reads the binlog directly.

---

# Initial Snapshot

When Debezium starts:

```text
No previous offset found
```

It performs a snapshot.

Purpose:

```text
Capture Existing Data
```

Example:

```text
John Doe
```

is captured before streaming begins.

---

# Streaming Mode

After the snapshot:

```text
Starting streaming
```

appears.

Debezium then continuously listens for changes.

Example:

```sql
INSERT INTO customerdb.customer
VALUES (
    2,
    'Peter Parker',
    'pp@example.com'
);
```

---

# CDC Event Generation

Debezium creates an event:

```text
Key = Struct{id=2}
```

Payload:

```text
fullname=Peter Parker
email=pp@example.com
```

Operation:

```text
op=c
```

Meaning:

```text
CREATE
```

---

# Spring Boot's Role

The Spring Boot application provides:

- Application framework
- Dependency management
- Runtime environment
- Debezium integration

Startup command:

```bash
mvn spring-boot:run
```

Startup message:

```text
Started TvApplication
```

indicates successful execution.

---

# Why This Architecture Is Useful

Traditional approach:

```text
Application
      ↓
Repeated Database Queries
      ↓
Check For Changes
```

Problems:

- Excess database load
- Slower response
- Scalability concerns

---

# Event-Driven Approach

Using Debezium:

```text
Database Change
       ↓
Binlog Entry
       ↓
Debezium
       ↓
Event Generated
       ↓
Application Consumes Event
```

Benefits:

- Near real-time processing
- Lower overhead
- Better scalability

---

# Data Engineering Relevance

This architecture resembles modern production systems.

Examples:

## Real-Time Analytics

```text
Database
   ↓
Debezium
   ↓
Analytics Platform
```

---

## Event Streaming

```text
MySQL
   ↓
Debezium
   ↓
Kafka
```

---

## Data Warehousing

```text
Operational DB
      ↓
CDC
      ↓
Warehouse
```

---

## Microservices

```text
Service A
   ↓
Database
   ↓
Debezium
   ↓
Service B
```

---

# Key Components Summary

| Component | Purpose |
|------------|------------|
| MySQL | Stores operational data |
| Binlog | Tracks database changes |
| Debezium | Captures CDC events |
| Spring Boot | Runs the application |
| Docker | Provides containerization |
| Docker Network | Enables communication |

---

# Architecture Diagram

```text
              myCDCNetwork
                     │
     ┌───────────────┴───────────────┐
     │                               │
     ▼                               ▼

┌─────────────┐               ┌──────────────┐
│ mysqlserver │               │debeziumserver│
│ customerdb  │──────────────▶│ Spring Boot  │
│   Binlogs   │               │  Debezium    │
└─────────────┘               └──────────────┘
                                      │
                                      ▼
                               CDC Events
```

---

# Key Takeaways

- Module 14 combines Docker, MySQL, Spring Boot, and Debezium into a complete CDC solution.
- MySQL serves as the source database.
- Debezium monitors MySQL binlogs for changes.
- Spring Boot hosts the Debezium application.
- Docker networking enables communication between containers.
- CDC events are generated automatically when database changes occur.
- Event-driven CDC is more efficient than periodic database polling.
- This architecture is representative of modern data engineering and real-time data integration solutions.

---

# Personal Notes

- This video serves as a summary of the entire Debezium implementation.
- The architecture demonstrates a complete end-to-end CDC workflow.
- Debezium's snapshot and streaming modes ensure both existing and new data are captured.
- Docker networking is a critical component that enables communication between services.
- The solution closely resembles architectures used in enterprise data platforms for real-time analytics and event streaming.

---

# Completion Status

```text
✅ Completed
```