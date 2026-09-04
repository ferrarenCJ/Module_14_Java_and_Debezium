# Module 14: Wrap-Up

## Module Overview

Module 14 introduced two important technologies used in modern data engineering:

1. **Java**, one of the most widely used programming languages for enterprise applications.
2. **Debezium**, an open-source Change Data Capture (CDC) platform used to monitor and stream database changes.

Throughout the module, students learned how Java, Spring Boot, Docker, and Debezium work together to build event-driven applications capable of monitoring and reacting to database activity in near real time.

---

# Learning Outcomes Achieved

By completing this module, you learned how to:

- Understand the fundamental concepts of Java.
- Develop applications using Spring Boot.
- Run applications inside Docker containers.
- Create Docker networks for container communication.
- Implement event-driven architectures.
- Understand Change Data Capture (CDC).
- Configure MySQL for CDC operations.
- Use Debezium to capture database changes.
- Connect MySQL and Debezium through Docker networking.
- Monitor database events in real time.

---

# Java Fundamentals

The module began with an introduction to Java and its core concepts.

Topics covered included:

## Data Types

Examples:

```java
int
double
String
boolean
```

---

## Classes

Classes define the structure and behavior of objects.

Example:

```java
public class Customer {
}
```

---

## Objects

Objects are instances of classes.

Example:

```java
Customer customer = new Customer();
```

---

## Packages

Packages organize Java code into logical groups.

Example:

```java
com.company.project
```

---

# Spring Boot

Students learned how Spring Boot simplifies Java web application development.

Benefits include:

- Embedded web servers
- Auto-configuration
- Dependency management
- Faster application development

Application startup command:

```bash
mvn spring-boot:run
```

Successful startup message:

```text
Started TvApplication
```

---

# Docker and Containers

The module reinforced Docker concepts by running applications within containers.

Topics included:

- Creating Docker images
- Running Docker containers
- Uploading and downloading files
- Docker networking

Example container deployment:

```bash
docker run
```

---

# Docker Networking

To enable communication between services, a Docker network was created.

Example:

```bash
docker network create myCDCNetwork
```

The network allowed:

```text
mysqlserver
```

and

```text
debeziumserver
```

to communicate with each other.

---

# Event-Driven Architecture

The module introduced event-driven design.

Traditional approach:

```text
Application
      ↓
Repeated Queries
      ↓
Database
```

Event-driven approach:

```text
Database Change
      ↓
Event Generated
      ↓
Application Responds
```

Benefits:

- Lower latency
- Better scalability
- Reduced database load

---

# Change Data Capture (CDC)

CDC provides a mechanism for identifying and distributing database changes.

Operations captured:

```text
INSERT
UPDATE
DELETE
```

Benefits:

- Real-time synchronization
- Incremental processing
- Event-driven workflows

---

# Introduction to Debezium

Debezium was introduced as an open-source CDC platform.

Debezium:

```text
Monitors Databases
Captures Changes
Streams Events
```

Supported databases include:

```text
MySQL
PostgreSQL
MongoDB
SQL Server
Oracle
Cassandra
```

---

# Debezium Connectors

Debezium uses database-specific connectors.

Examples:

```text
MySQL Connector
PostgreSQL Connector
MongoDB Connector
```

Connectors capture database changes using native logging mechanisms.

---

# Debezium Features

Key capabilities include:

## Snapshots

Capture the initial state of a database.

---

## Filters

Process selected records only.

---

## Masking

Protect sensitive information.

---

## Monitoring

Track connector activity and health.

---

# MySQL and CDC

Module 14 focused on MySQL as the CDC source database.

Debezium reads:

```text
MySQL Binary Logs (Binlogs)
```

The binlog contains:

```text
INSERT
UPDATE
DELETE
```

operations.

---

# Coding Activity 14.3

## Setting Up a Docker Network for MySQL

Students:

- Created a Docker network
- Built a custom MySQL image
- Initialized a database
- Started a MySQL container

Key artifacts:

```text
customer.sql
Dockerfile
myCDCNetwork
mysqlserver
```

---

# Coding Activity 14.4

## Connecting MySQL to Debezium

Students:

- Built a Debezium image
- Created a Debezium container
- Started a Spring Boot application
- Connected Debezium to MySQL
- Verified CDC functionality

Containers used:

```text
mysqlserver
debeziumserver
```

---

# CDC Demonstration

Initial record:

```text
John Doe
jd@example.com
```

Detected during:

```text
Snapshot Phase
```

New record inserted:

```sql
INSERT INTO customerdb.customer
VALUES (
    2,
    'Peter Parker',
    'pp@example.com'
);
```

Debezium generated a CDC event:

```text
Key = Struct{id=2}
```

Operation:

```text
op=c
```

Meaning:

```text
Create (Insert)
```

---

# Application Architecture

Final architecture:

```text
myCDCNetwork
│
├── mysqlserver
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

Workflow:

```text
MySQL
   ↓
Binlog
   ↓
Debezium
   ↓
Spring Boot
   ↓
CDC Event Output
```

---

# Knowledge Checks Completed

## Knowledge Check 14.2

Covered:

- Java applications
- Spring Boot
- Web development concepts

---

## Knowledge Check 14.3

Covered:

- 