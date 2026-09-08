# Module 14 Coding Activities

## Overview

The coding activities in Module 14 provided hands-on experience with Docker, Java, Spring Boot, MySQL, and Debezium. These activities reinforced the concepts introduced throughout the module and culminated in building a complete Change Data Capture (CDC) solution.

---

# Folder Structure

```text
Coding_Activities
│
├── Coding_Activity_14.1_File_Transfers_Containers
├── Coding_Activity_14.2_Java_Web_Application
├── Coding_Activity_14.3_Docker_Network_MySQL
└── Coding_Activity_14.4_MySQL_to_Debezium
```

---

# Coding Activity 14.1
## File Transfers and Containers

### Objective

Learn how to transfer files between a local machine and Docker containers.

### Topics Covered

- Docker Containers
- File Management
- Docker CLI
- Container Access

### Commands Used

Copy file into a container:

```bash
docker cp localfile.txt container:/tmp
```

Copy file from a container:

```bash
docker cp container:/tmp/file.txt .
```

Access container:

```bash
docker exec -it container_name bash
```

### Skills Learned

- Navigating containers
- Managing files in Docker
- Using Docker CLI commands
- Working inside container environments

---

# Coding Activity 14.2
## Java Web Application

### Objective

Run a Java web application using Spring Boot.

### Topics Covered

- Java
- Spring Boot
- Maven
- Web Applications

### Commands Used

Run application:

```bash
mvn spring-boot:run
```

Package application:

```bash
mvn package
```

### Skills Learned

- Spring Boot architecture
- Java application execution
- Maven builds
- Web application deployment

### Key Concept

Spring Boot provides a simplified framework for building and deploying Java applications.

---

# Coding Activity 14.3
## Docker Network and MySQL Setup

### Objective

Create a Docker network and deploy a MySQL database container configured for Change Data Capture (CDC).

### Topics Covered

- Docker Networking
- MySQL
- Docker Images
- Binary Logging

### Components Created

Network:

```text
myCDCNetwork
```

MySQL Image:

```text
mysqlmasterimg
```

MySQL Container:

```text
mysqlserver
```

### Commands Used

Create network:

```bash
docker network create myCDCNetwork
```

Build image:

```bash
docker build -t mysqlmasterimg .
```

Create container:

```bash
docker run \
--name mysqlserver \
--network myCDCNetwork \
-d mysqlmasterimg
```

### Skills Learned

- Creating Docker networks
- Building custom Docker images
- Deploying MySQL in Docker
- Configuring container communication

### Key Concept

Containers must be attached to the same network to communicate with each other.

---

# Coding Activity 14.4
## Connecting MySQL to Debezium

### Objective

Build and configure a Debezium container to monitor MySQL database changes using CDC.

### Topics Covered

- Debezium
- CDC
- Spring Boot
- MySQL Binlogs
- Event Streaming

### Components Created

Debezium Image:

```text
debeziumimg
```

Debezium Container:

```text
debeziumserver
```

### Commands Used

Build Debezium image:

```bash
docker build -t debeziumimg .
```

Create Debezium container:

```bash
docker run -dit \
--name debeziumserver \
--network myCDCNetwork \
debeziumimg bash
```

Run application:

```bash
mvn spring-boot:run
```

### Skills Learned

- Configuring Debezium
- Connecting Debezium to MySQL
- Monitoring database changes
- Running Spring Boot applications
- Capturing CDC events

### CDC Example

Insert:

```sql
INSERT INTO customerdb.customer
VALUES (
    2,
    'Peter Parker',
    'pp@example.com'
);
```

Detected by Debezium:

```text
FirstName=Peter
```

---

# Technologies Used

## Programming

```text
Java
Spring Boot
Maven
```

---

## Containerization

```text
Docker
Docker Images
Docker Containers
Docker Networks
```

---

## Database

```text
MySQL
Binlogs
Tables
Schemas
```

---

## Data Engineering

```text
CDC
Debezium
Connectors
Snapshots
Event Streams
```

---

# Architecture Developed

```text
Docker Network
        │
        ▼

 ┌──────────────┐
 │  MySQL DB    │
 │ mysqlserver  │
 └──────┬───────┘
        │
        ▼
     Binlogs
        │
        ▼
 ┌──────────────┐
 │  Debezium    │
 │debeziumserver│
 └──────┬───────┘
        │
        ▼
  CDC Events
```

---

# Learning Outcomes Achieved

By completing these activities, I learned how to:

- Transfer files to and from Docker containers.
- Build and run Java applications.
- Use Spring Boot and Maven.
- Configure Docker networks.
- Build custom MySQL images.
- Deploy MySQL in Docker.
- Configure Change Data Capture.
- Connect MySQL and Debezium.
- Monitor database changes in real time.

---

# Real-World Applications

These skills are commonly used in:

### Data Warehousing

```text
Source Database
      ↓
CDC
      ↓
Warehouse
```

### Real-Time Analytics

```text
Database
    ↓
Debezium
    ↓
Analytics
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
CDC Event
        ↓
Application Response
```

---

# Key Takeaways

- Docker makes applications portable and reproducible.
- Spring Boot simplifies Java application development.
- Docker networks enable container communication.
- MySQL binlogs provide a source for CDC.
- Debezium captures changes in near real time.
- CDC is a foundational data engineering pattern.
- Event-driven architectures are more scalable than polling-based solutions.

---

# Status

```text
✅ All Module 14 Coding Activities Completed
```