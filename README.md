# Module 14: Java and Debezium

## Overview

Module 14 introduced Java fundamentals, Spring Boot web applications, Docker container networking, and Change Data Capture (CDC) using Debezium. Through videos, knowledge checks, coding activities, and a final assignment, I learned how to build and deploy a CDC solution that monitors database changes in near real time.

---

## Learning Outcomes

By completing this module, I was able to:

- Understand the core concepts of Java.
- Identify Java classes, objects, packages, and data types.
- Build and run Java applications using Spring Boot.
- Create and manage Docker containers and networks.
- Explain event-driven architectures.
- Understand Change Data Capture (CDC).
- Configure MySQL for CDC.
- Connect MySQL to Debezium.
- Monitor database changes using Debezium.

---

## Topics Covered

### Java Fundamentals

Key concepts included:

- Data Types
- Variables
- Classes
- Objects
- Packages
- Modularity
- Compilers

Example Java data types:

```java
byte
short
long
double
char
```

---

### Spring Boot

Spring Boot was introduced as a popular Java framework for building web applications.

Benefits:

- Simplified configuration
- Embedded web server
- Dependency management
- Faster development

Command used:

```bash
mvn spring-boot:run
```

---

### Docker

The module reinforced Docker concepts including:

- Building images
- Running containers
- Uploading and downloading files
- Docker networking

Example commands:

```bash
docker build
docker run
docker ps
docker network create
```

---

### Event-Driven Architecture

Traditional database polling:

```text
Application
      ↓
Repeated Queries
      ↓
Database
```

Event-driven architecture:

```text
Database Change
      ↓
Event Generated
      ↓
Application Responds
```

Benefits:

- Reduced database load
- Better scalability
- Near real-time processing

---

### Change Data Capture (CDC)

CDC identifies database changes and propagates them to downstream systems.

Captured operations:

```text
INSERT
UPDATE
DELETE
```

Benefits:

- Real-time synchronization
- Incremental processing
- Better performance than polling

---

### Debezium

Debezium is an open-source CDC platform that captures database changes and streams them as events.

Supported databases include:

```text
MySQL
PostgreSQL
MongoDB
SQL Server
Oracle
```

Key capabilities:

- Snapshots
- Filters
- Masking
- Monitoring

---

### MySQL Binlogs

Debezium interacts with MySQL using:

```text
Binary Logs (Binlogs)
```

The binlog records:

```text
INSERT
UPDATE
DELETE
```

operations, allowing Debezium to capture changes without polling.

---

## Coding Activities

### Coding Activity 14.3
### Setting Up a Docker Network for MySQL

Tasks completed:

- Created Docker network
- Built MySQL image
- Initialized MySQL database
- Created and verified container networking

Technologies used:

```text
Docker
MySQL
Docker Networking
```

---

### Coding Activity 14.4
### Connecting MySQL to Debezium

Tasks completed:

- Built Debezium image
- Created Debezium container
- Connected Debezium to MySQL
- Started Spring Boot application
- Verified CDC functionality

CDC verification:

```sql
INSERT INTO customerdb.customer
VALUES (
  2,
  'Peter Parker',
  'pp@example.com'
);
```

Debezium automatically detected the change.

---

## Knowledge Checks

### Knowledge Check 14.2

Topics:

- Java Applications
- Spring Boot
- Web Development

---

### Knowledge Check 14.3

Topics:

- Debezium
- CDC
- Docker Networking
- Connectors
- Docker Images

Result:

```text
8 / 8 Correct
```

---

## Final Assignment 14.1

### Java and Debezium

Built a complete CDC architecture using:

```text
Docker
MySQL
Spring Boot
Debezium
```

Steps completed:

- Created Docker network
- Built MySQL Docker image
- Created MySQL container
- Built Debezium image
- Created Debezium container
- Updated connector configuration
- Installed nano
- Started CDC monitoring
- Inserted new employee records
- Verified CDC events

---

## Final Assignment Architecture

```text
CDCFinalAssignment
│
├── mysqlmasterdb
│      │
│      ▼
│   employeedb
│
└── debeziumserver
        │
        ▼
   Spring Boot
        │
        ▼
     Debezium
        │
        ▼
     CDC Events
```

---

## CDC Demonstration

Initial employee:

```text
John Doe
```

Detected during Debezium snapshot.

Inserted employee:

```sql
INSERT INTO employeedb.employee
VALUES (
    2,
    'Mary',
    'Doe',
    '4351234354',
    'mary@doe.com'
);
```

Debezium output:

```text
FirstName=Mary
LastName=Doe
email=mary@doe.com
```

CDC successfully confirmed.

---

## Key Commands Used

### Docker Network

```bash
docker network create CDCFinalAssignment
```

### Build MySQL Image

```bash
docker build -t mysqlmasterimg .
```

### Create MySQL Container

```bash
docker run --name mysqlmasterdb -p 3306:3306 \
--network CDCFinalAssignment -d mysqlmasterimg
```

### Build Debezium Image

```bash
docker build -t debeziumimg .
```

### Create Debezium Container

```bash
docker run -dit --name debeziumserver \
--network CDCFinalAssignment debeziumimg bash
```

### Start Application

```bash
mvn spring-boot:run
```

---

## Important Concepts Learned

### Java

```text
Classes
Objects
Packages
Data Types
Modularity
```

### Docker

```text
Images
Containers
Networks
Volumes
```

### CDC

```text
Snapshots
Streaming
Change Events
```

### Debezium

```text
Connectors
Binlogs
Monitoring
Masking
Filters
```

---

## Data Engineering Relevance

The concepts learned in this module are used extensively in:

### Real-Time Analytics

```text
Database
   ↓
CDC
   ↓
Analytics
```

### Data Warehousing

```text
Operational Database
         ↓
CDC
         ↓
Warehouse
```

### Event Streaming

```text
MySQL
   ↓
Debezium
   ↓
Kafka
```

### Microservices

```text
Database Change
        ↓
Debezium
        ↓
Service Notifications
```

---

## Key Takeaways

- Java remains one of the most important enterprise programming languages.
- Spring Boot simplifies Java application development.
- Docker enables portable application deployment.
- Docker networking allows container communication.
- CDC provides efficient data synchronization.
- Debezium captures database changes through transaction logs.
- MySQL binlogs support near real-time event processing.
- Event-driven architectures are essential in modern data engineering.
- Debezium is a powerful tool for integrating operational systems with downstream applications.

---

## Module Completion

### Activities Completed

✅ Videos

✅ Resource Readings

✅ Knowledge Check 14.2

✅ Knowledge Check 14.3

✅ Coding Activity 14.3

✅ Coding Activity 14.4

✅ Final Assignment 14.1

✅ Module Discussion

✅ Module Wrap-Up

---

## Status

```text
✅ Module 14 Complete
```