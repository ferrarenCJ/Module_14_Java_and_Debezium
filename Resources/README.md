# Module 14 Resources

## Overview

This folder contains the supporting materials used throughout **Module 14: Java and Debezium**. These resources provide detailed explanations, reference guides, glossaries, mini-lessons, transcripts, solutions, and module summaries covering Java fundamentals, Spring Boot, Docker, MySQL, Change Data Capture (CDC), and Debezium.

The resources serve as both study materials and future reference documentation for modern data engineering concepts and implementations.

---

# Folder Structure

```text
Resources
│
├── Mini_Lessons
├── Solutions
├── Transcripts
│
├── CDC_Reference_Notes.md
├── Debezium_Reference_Notes.md
├── Docker_Reference_Notes.md
├── Java_Reference_Notes.md
├── Spring_Boot_Reference_Notes.md
│
├── Module_14_Glossary.md
└── Module_14_Wrap_Up.md
```

---

# Mini Lessons

## Purpose

The Mini Lessons provide detailed explanations of core concepts introduced throughout Module 14.

### Topics Covered

```text
Java Fundamentals
Spring Boot
Docker
Event-Driven Architecture
Change Data Capture (CDC)
Debezium
MySQL Binlogs
```

### Learning Benefits

- Reinforce lecture content
- Explain technical concepts
- Prepare for coding activities
- Support assignment completion

---

# Solutions

## Purpose

Contains solution files and completed examples associated with activities and exercises throughout the module.

### Usage

Use these materials to:

- Validate implementations
- Compare approaches
- Review completed work
- Reinforce learning

---

# Transcripts

## Purpose

Contains transcripts from the instructional videos.

### Benefits

- Quick reference
- Searchable content
- Improved accessibility
- Easier note-taking

---

# Reference Notes

The reference notes provide comprehensive documentation for the technologies covered in Module 14.

---

## Java Reference Notes

**File:**

```text
Java_Reference_Notes.md
```

### Topics Covered

- Java Architecture
- Classes
- Objects
- Packages
- Data Types
- Variables
- Methods
- Constructors
- Arrays
- Exception Handling

### Key Concepts

```text
Object-Oriented Programming
Compilation
JVM
Variables
Data Types
```

---

## Spring Boot Reference Notes

**File:**

```text
Spring_Boot_Reference_Notes.md
```

### Topics Covered

- Spring Boot Architecture
- Maven
- Project Structure
- Controllers
- Services
- Dependency Injection
- REST APIs
- Embedded Servers
- Docker Integration

### Key Concepts

```text
Spring Boot
Maven
Controllers
Annotations
Dependency Injection
```

---

## Docker Reference Notes

**File:**

```text
Docker_Reference_Notes.md
```

### Topics Covered

- Images
- Containers
- Dockerfiles
- Networks
- File Transfers
- Container Communication

### Key Concepts

```text
Docker Images
Containers
Docker Networks
Docker CLI
```

---

## Debezium Reference Notes

**File:**

```text
Debezium_Reference_Notes.md
```

### Topics Covered

- Debezium Architecture
- Connectors
- Snapshots
- Event Streaming
- CDC Workflows
- Event Types
- MySQL Integration

### Key Concepts

```text
Debezium
Connectors
Snapshots
Streams
Events
```

---

## CDC Reference Notes

**File:**

```text
CDC_Reference_Notes.md
```

### Topics Covered

- Change Data Capture
- Event-Driven Architectures
- Transaction Logs
- CDC Use Cases
- Data Streaming

### Key Concepts

```text
CDC
Events
Streaming
Synchronization
Analytics
```

---

# Module 14 Glossary

**File:**

```text
Module_14_Glossary.md
```

### Purpose

Provides definitions of key terms introduced during the module.

### Topics Covered

```text
Binlog
Buffer
Byte
Char
Compiler
Connectors
Debezium
Double
Filters
Java Classes
Java Objects
Java Packages
Masking
Monitoring
Nano
Snapshot
Spring Boot
Streams
```

### Benefits

- Quick terminology lookup
- Exam preparation
- Reinforcement of technical vocabulary

---

# Module 14 Wrap-Up

**File:**

```text
Module_14_Wrap_Up.md
```

### Purpose

Summarizes all concepts, activities, technologies, and learning outcomes covered throughout the module.

### Topics Reviewed

```text
Java
Spring Boot
Docker
CDC
Debezium
MySQL
Application Architecture
```

### Benefits

- Module review
- Study guide
- Consolidated learning summary

---

# Major Technologies Covered

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

## Databases

```text
MySQL
Schemas
Tables
Binlogs
```

---

## Data Engineering

```text
CDC
Debezium
Connectors
Snapshots
Streaming
```

---

# Architecture Learned

```text
MySQL
   │
   ▼
 Binlog
   │
   ▼
Debezium
   │
   ▼
Spring Boot
   │
   ▼
CDC Events
```

---

# Learning Outcomes Achieved

By utilizing these resources, the following learning outcomes were achieved:

- Understand Java fundamentals.
- Build Java web applications using Spring Boot.
- Create and manage Docker images and containers.
- Configure Docker networking.
- Understand event-driven architectures.
- Implement Change Data Capture (CDC).
- Configure MySQL for CDC.
- Connect MySQL to Debezium.
- Monitor database changes using CDC events.

---

# Real-World Applications

These technologies are widely used in:

### Data Warehousing

```text
Operational Database
         ↓
CDC
         ↓
Warehouse
```

### Data Lakes

```text
Database
    ↓
CDC
    ↓
Data Lake
```

### Real-Time Analytics

```text
Database
   ↓
Debezium
   ↓
Analytics Platform
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

- Java is a foundational language for enterprise and data engineering platforms.
- Spring Boot simplifies application development and deployment.
- Docker enables consistent and portable environments.
- Docker networking allows services to communicate.
- CDC provides efficient real-time data synchronization.
- Debezium captures database changes from transaction logs.
- Event-driven architectures are widely used in modern data platforms.
- Real-time processing is an important capability in modern data engineering solutions.

---

# Status

```text
✅ Module 14 Resources Complete
```