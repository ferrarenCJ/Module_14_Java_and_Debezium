# Module 14 Videos

## Overview

The videos in Module 14 introduced Java programming fundamentals, Spring Boot web applications, Docker container management, Change Data Capture (CDC), and Debezium. The content progressed from foundational Java concepts to implementing a complete CDC solution using MySQL, Docker, Spring Boot, and Debezium.

---

# Folder Structure

```text
Videos
│
├── Video_14.1_Introduction_and_Information.md
├── Video_14.2_Java_Containers.md
├── Video_14.3_Hello_World_in_Java.md
├── Video_14.4_Data_Types_in_Java.md
├── Video_14.5_Classes_and_Objects.md
├── Video_14.6_Packages_in_Java.md
├── Video_14.7_File_Transfers_in_Containers.md
├── Video_14.8_Spring_Boot_Web_Applications.md
├── Video_14.9_Event_Driven_CDC.md
├── Video_14.10_Introduction_to_Debezium.md
├── Video_14.11_Network_Setup_for_Debezium.md
├── Video_14.12_Database_Setup_for_Debezium.md
├── Video_14.13_Debezium_with_Spring_Boot.md
└── Video_14.14_Application_Architecture.md
```

---

# Section 1: Java Fundamentals

## Video 14.1
### Introduction and Information

Introduced the structure and objectives of Module 14.

### Topics Covered

- Java Fundamentals
- Spring Boot
- Docker
- CDC
- Debezium

---

## Video 14.2
### Java Containers

Introduced Java containers and how Java applications organize and store data.

### Key Concepts

```text
Containers
Variables
Memory Management
```

---

## Video 14.3
### Hello World in Java

Created and executed a simple Java application.

Example:

```java
public class HelloWorld {

    public static void main(String[] args) {

        System.out.println("Hello World");

    }

}
```

### Key Concepts

- Java Syntax
- Main Method
- Program Execution

---

## Video 14.4
### Data Types in Java

Introduced Java primitive data types.

### Data Types

```java
byte
short
int
long
float
double
char
boolean
```

### Key Concepts

- Variable Storage
- Numeric Types
- Character Data
- Boolean Values

---

## Video 14.5
### Classes and Objects

Introduced object-oriented programming concepts.

### Key Concepts

#### Class

Blueprint for creating objects.

#### Object

Instance of a class.

Example:

```java
Employee emp = new Employee();
```

---

## Video 14.6
### Packages in Java

Introduced Java packages and modularity.

Example:

```java
package com.company.project;
```

### Key Concepts

- Modularity
- Code Organization
- Package References

---

# Section 2: Spring Boot and Docker

## Video 14.7
### File Transfers in Containers

Demonstrated transferring files between the local machine and Docker containers.

### Commands

Copy into container:

```bash
docker cp file.txt container:/tmp
```

Copy from container:

```bash
docker cp container:/tmp/file.txt .
```

---

## Video 14.8
### Spring Boot Web Applications

Introduced Spring Boot as a framework for building Java web applications.

### Topics Covered

- Spring Boot
- Maven
- Web Applications
- Embedded Servers

### Command

```bash
mvn spring-boot:run
```

### Benefits

- Simplified Development
- Auto Configuration
- Embedded Tomcat

---

# Section 3: Change Data Capture (CDC)

## Video 14.9
### Event-Driven CDC

Introduced event-driven architectures and Change Data Capture.

### Traditional Architecture

```text
Application
      ↓
Repeated Queries
      ↓
Database
```

### Event-Driven Architecture

```text
Database Change
      ↓
CDC Event
      ↓
Application Response
```

### Benefits

- Reduced Polling
- Better Performance
- Real-Time Processing

---

# Section 4: Debezium

## Video 14.10
### Introduction to Debezium

Introduced Debezium as an open-source CDC platform.

### Topics Covered

- Debezium
- CDC
- Connectors
- Event Streaming

### Supported Databases

```text
MySQL
PostgreSQL
MongoDB
SQL Server
Oracle
```

---

## Video 14.11
### Network Setup for Debezium

Created Docker networks to enable communication between containers.

### Command

```bash
docker network create myCDCNetwork
```

### Key Concept

Containers must be connected to the same network to communicate.

---

## Video 14.12
### Database Setup for Debezium

Configured MySQL as the source database for CDC.

### Components

```text
MySQL
Tables
Schemas
Binary Logs
```

### Key Concept

MySQL binary logs (binlogs) provide the CDC source data.

---

## Video 14.13
### Debezium with Spring Boot

Integrated Debezium with a Spring Boot application.

### Topics Covered

- Debezium Connectors
- Snapshots
- Streaming
- Event Processing

### Startup Command

```bash
mvn spring-boot:run
```

### Event Types

```text
c = Create
u = Update
d = Delete
r = Read
```

---

## Video 14.14
### Application Architecture

Reviewed the complete CDC architecture created throughout