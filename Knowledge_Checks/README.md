# Module 14 Knowledge Checks

## Overview

The knowledge checks in Module 14 assessed understanding of Java fundamentals, Spring Boot applications, Docker concepts, Change Data Capture (CDC), and Debezium.

These assessments reinforced key concepts through interactive questions and provided immediate feedback to validate learning progress throughout the module.

---

# Folder Structure

```text
Knowledge_Checks
│
├── Drag_and_Drop_14.1_Data_Types.md
├── KC_14.1_Java_Fundamentals.md
├── KC_14.2_Java_Applications.md
└── KC_14.3_Debezium.md
```

---

# Drag and Drop 14.1
## Java Data Types

### Objective

Match Java data types with their corresponding descriptions, storage sizes, and examples.

### Topics Covered

- byte
- short
- int
- long
- float
- double
- char
- boolean
- String

### Key Concepts

#### byte

```text
1 byte
Range: -128 to 127
```

#### short

```text
2 bytes
Range: -32,768 to 32,767
```

#### long

```text
8 bytes
Used for large whole numbers
```

#### double

```text
8 bytes
Used for decimal values
```

#### char

```text
Stores a single character
```

### Learning Outcome

Understand Java primitive and reference data types.

---

# Knowledge Check 14.1
## Java Fundamentals

### Objective

Assess understanding of basic Java programming concepts.

### Topics Covered

- Java Syntax
- Variables
- Data Types
- Classes
- Objects
- Packages
- Compilers

### Key Concepts

#### Classes

Blueprints used to create objects.

#### Objects

Instances of a class.

#### Packages

Used to organize and reference Java code.

#### Compiler

Converts Java source code into executable bytecode.

### Learning Outcome

Understand core Java fundamentals and object-oriented programming concepts.

---

# Knowledge Check 14.2
## Java Applications

### Objective

Assess understanding of Java web application development and Spring Boot.

### Topics Covered

- Spring Boot
- Maven
- Web Applications
- Java Frameworks
- Application Architecture

### Key Concepts

#### Spring Boot

Popular Java framework for developing web applications.

#### Maven

Tool used for dependency management and builds.

#### Application Startup

```bash
mvn spring-boot:run
```

#### Embedded Server

Spring Boot includes an embedded web server such as Tomcat.

### Learning Outcome

Understand how Java applications are built and deployed using Spring Boot.

---

# Knowledge Check 14.3
## Debezium

### Objective

Assess understanding of Debezium, CDC, Docker networking, and related technologies.

### Topics Covered

- Debezium
- CDC
- Docker Networks
- Docker Images
- Connectors
- Supported Databases

### Questions Covered

#### What is Debezium?

Correct Answer:

```text
Debezium is an open-source distributed platform for CDC.
```

---

#### What language is Debezium written in?

Correct Answer:

```text
Java
```

---

#### How do Docker containers communicate?

Correct Answer:

```text
Create a Docker network and add containers to it.
```

---

#### Create Docker Network

Command:

```bash
docker network create netabel
```

---

#### Create Docker Image

Tool:

```text
Dockerfile
```

---

#### Debezium Database Integration

Correct Answer:

```text
Uses connectors
```

---

#### Compatible Databases

```text
MySQL
PostgreSQL
MongoDB
```

Correct Answer:

```text
All of the answer options are correct
```

---

#### Debezium Connector Capability

Correct Answer:

```text
Transforming
```

(Was not listed as a Debezium connector capability in the lesson.)

### Result

```text
8 / 8 Correct
```

### Learning Outcome

Understand CDC concepts and Debezium implementation.

---

# Topics Assessed Across Module 14

## Java

```text
Classes
Objects
Packages
Data Types
Compilers
```

---

## Spring Boot

```text
Frameworks
Web Applications
Maven
Application Deployment
```

---

## Docker

```text
Images
Containers
Networks
Container Communication
```

---

## MySQL

```text
Databases
Tables
Queries
Binlogs
```

---

## Debezium

```text
Connectors
CDC
Snapshots
Monitoring
Masking
Filters
```

---

# Skills Validated

By completing these knowledge checks, the following skills were demonstrated:

### Java Development

Understanding Java syntax and object-oriented concepts.

---

### Application Development

Understanding Spring Boot and Java application architecture.

---

### Docker Administration

Creating networks, images, and containers.

---

### Data Engineering

Understanding Change Data Capture and event-driven architectures.

---

### Debezium Implementation

Configuring and using CDC pipelines.

---

# Module 14 Assessment Summary

| Assessment | Topic | Status |
|------------|---------|---------|
| Drag and Drop 14.1 | Java Data Types | ✅ Completed |
| KC 14.1 | Java Fundamentals | ✅ Completed |
| KC 14.2 | Java Applications | ✅ Completed |
| KC 14.3 | Debezium | ✅ Completed (8/8) |

---

# Key Takeaways

- Java is a foundational language for enterprise applications.
- Spring Boot simplifies Java application development.
- Docker enables portable application deployment.
- Docker networks allow containers to communicate.
- CDC enables near real-time data synchronization.
- Debezium captures database changes efficiently through transaction logs.
- Event-driven architectures are widely used in modern data engineering platforms.

---

# Status

```text
✅ All Module 14 Knowledge Checks Completed
```