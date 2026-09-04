# Video 14.8: Spring Boot: A Web Developing Application for Java

## Duration

**09:54**

---

# Overview

Spring Boot is one of the most popular frameworks for Java application development. It simplifies the process of creating web applications by providing preconfigured settings, embedded web servers, and production-ready features.

In this video, Dr. Sanchez demonstrates how to create and run a Spring Boot web application inside a Docker container.

---

# Learning Objectives

After completing this video, you should be able to:

- Understand the purpose of Spring Boot.
- Explain why Spring Boot is widely used in Java development.
- Create a basic Spring Boot application.
- Run a Spring Boot application inside a container.
- Understand how web applications communicate with users through HTTP requests and responses.

---

# What Is Spring Boot?

Spring Boot is a Java framework built on top of the Spring Framework that simplifies web application development.

Benefits include:

- Faster development
- Reduced configuration
- Embedded web servers
- Production-ready features
- Easy deployment

---

# Why Use Spring Boot?

Traditional Java web development often requires significant configuration and setup.

Spring Boot reduces complexity by:

- Automatically configuring components
- Managing dependencies
- Providing built-in web servers
- Simplifying project structure

---

# Common Spring Boot Applications

Spring Boot is commonly used for:

- REST APIs
- Web applications
- Microservices
- Enterprise applications
- Cloud-native systems

Examples include:

```text
E-commerce platforms
Inventory systems
Customer portals
Data platforms
Financial applications
```

---

# Spring Boot Architecture

```text
Client Browser
       |
       V
Spring Boot Application
       |
       V
Business Logic
       |
       V
Database
```

The application receives requests from users and returns responses.

---

# Maven and Dependencies

Spring Boot projects commonly use Maven for dependency management.

Example project structure:

```text
project
│
├── src
│   ├── main
│   │   ├── java
│   │   └── resources
│
├── pom.xml
│
└── target
```

---

# pom.xml

The `pom.xml` file contains:

- Project information
- Dependencies
- Build configuration

Example:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

Purpose:

```text
Adds web application capabilities to the project.
```

---

# Main Spring Boot Application

Typical application entry point:

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication

public class Application {

    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }

}
```

---

# @SpringBootApplication

This annotation:

```java
@SpringBootApplication
```

combines several Spring features.

Responsibilities:

- Component scanning
- Auto-configuration
- Application initialization

---

# Creating a Web Endpoint

Example:

```java
@RestController

public class HomeController {

    @GetMapping("/")

    public String home() {
        return "Hello World";
    }

}
```

---

# Explanation

### @RestController

Marks the class as a web controller.

### @GetMapping

Maps requests to a URL.

Example:

```text
http://localhost:8080/
```

---

# Application Response

Request:

```text
GET /
```

Response:

```text
Hello World
```

---

# Running Spring Boot

Using Maven:

```bash
mvn spring-boot:run
```

Or:

```bash
java -jar app.jar
```

---

# Running in Docker

Docker can host Spring Boot applications inside containers.

Benefits:

- Consistency across environments
- Easier deployment
- Isolation
- Scalability

---

# Typical Docker Workflow

## Build Application

```bash
mvn package
```

Creates:

```text
target/app.jar
```

---

## Create Docker Image

Example Dockerfile:

```dockerfile
FROM openjdk:17

COPY target/app.jar app.jar

ENTRYPOINT ["java","-jar","/app.jar"]
```

---

## Build Image

```bash
docker build -t spring-app .
```

---

## Run Container

```bash
docker run -p 8080:8080 spring-app
```

---

# Port Mapping

Example:

```bash
-p 8080:8080
```

Meaning:

```text
Host Port     Container Port
8080      ->      8080
```

Users can access:

```text
http://localhost:8080
```

---

# Spring Boot and APIs

Spring Boot is heavily used to create REST APIs.

Example:

```java
@GetMapping("/employees")
```

Returns:

```json
[
  {
    "id": 1,
    "name": "John"
  }
]
```

These APIs are commonly consumed by:

- React applications
- Angular applications
- Mobile applications
- Data platforms

---

# Enterprise Use Cases

Spring Boot is frequently used for:

### Banking Systems

```text
Customer accounts
Transactions
Loans
```

### Utilities

```text
Work management
Asset management
Field service applications
```

### E-Commerce

```text
Ordering systems
Inventory management
Payment processing
```

### Data Platforms

```text
Data services
Metadata APIs
Integration services
```

---

# Data Engineering Connection

As a data engineer, Spring Boot can be used to:

- Expose data APIs
- Build microservices
- Manage ingestion endpoints
- Integrate with databases
- Support cloud-native architectures

Examples:

```text
Data quality APIs
Fleet monitoring services
Metadata services
Reporting APIs
```

---

# Relationship to Previous Topics

### Java

Spring Boot is built using Java.

### Classes

Controllers, services, and repositories are Java classes.

### Objects

Spring creates and manages application objects automatically.

### Packages

Spring Boot applications are organized using package structures.

### Containers

Applications can run inside Docker containers.

---

# Key Terms

## Spring Boot

A framework for creating Java applications and web services.

---

## Controller

A class that handles incoming web requests.

---

## Endpoint

A URL through which clients interact with an application.

Example:

```text
/api/customers
```

---

## Maven

A build and dependency-management tool for Java.

---

## Dependency

An external library used by an application.

---

## Docker Container

An isolated runtime environment for an application.

---

# Key Takeaways

- Spring Boot simplifies Java web development.
- Spring Boot automatically configures many application components.
- Controllers process HTTP requests and return responses.
- Maven manages project dependencies.
- Spring Boot applications can run inside Docker containers.
- Spring Boot is widely used for APIs, web applications, and microservices.
- Understanding Spring Boot is important for modern enterprise and data engineering environments.

---

# Personal Notes

- Spring Boot appears to be the Java equivalent of a modern web application framework.
- Most enterprise Java applications are built using Spring Boot.
- The framework handles much of the boilerplate configuration automatically.
- Running Spring Boot inside Docker combines Java development with containerization.
- Spring Boot knowledge will be valuable for understanding backend APIs, microservices, and cloud-native architectures.