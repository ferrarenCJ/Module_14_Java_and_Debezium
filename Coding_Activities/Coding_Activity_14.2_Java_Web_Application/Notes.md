# Coding Activity 14.2: Developing a Web Application in Java

## Activity Information

### Module

Module 14: Java and Debezium

### Activity

Required Coding Activity 14.2: Developing a Web Application in Java

### Learning Outcome

- Develop a web application in Java.

---

# Objective

Learn how to build, modify, deploy, and test a Java web application using Spring Boot within a Docker container.

This activity demonstrates how Java, Maven, Docker, and Spring Boot work together to create modern web applications and APIs.

---

# Purpose

The purpose of this activity is to gain practical experience developing a web application using industry-standard tools and frameworks.

Students learn how to:

- Generate a Spring Boot project
- Deploy code into a Docker container
- Modify Java application code
- Build and execute the application
- Expose web endpoints
- Test HTTP requests through a browser

---

# Technologies Used

## Java 17

Programming language used to create the application.

---

## Maven

Build automation and dependency management tool.

Responsibilities:

- Download dependencies
- Build applications
- Manage libraries
- Execute Spring Boot projects

---

## Docker

Provides a portable and isolated environment for application execution.

Benefits:

- Consistent runtime environment
- Portability
- Easy deployment

---

## Spring Boot

Java framework used to create:

- Web applications
- REST APIs
- Microservices

---

# Step 1: Create Java Docker Container

Command:

```bash
docker run --name javamaven -dti --rm -p 8080:8080 maven:3.9-eclipse-temurin-17 bash
```

## Purpose

Creates a Docker container configured with:

- Java 17
- Maven 3.9
- Port 8080 access

Container name:

```text
javamaven
```

Port mapping:

```text
Host:8080 → Container:8080
```

---

# Step 2: Update Container

Connect:

```bash
docker exec -it javamaven bash
```

Update packages:

```bash
apt-get update
```

Install Nano:

```bash
apt-get install -y nano
```

## Purpose

Installs a text editor for modifying source code directly within the container.

---

# Step 3: Generate Spring Boot Project

Website:

```text
https://start.spring.io
```

Configuration:

```text
Project: Maven
Language: Java
Spring Boot: 3.x
Group: com.example
Artifact: demo
Packaging: Jar
Java: 17
Dependency: Spring Web
```

Downloaded File:

```text
demo.zip
```

## Purpose

Creates a complete Spring Boot project structure with the required dependencies.

---

# Step 4: Extract Project

Extract:

```text
demo.zip
```

Resulting structure:

```text
demo/
├── pom.xml
├── mvnw
├── mvnw.cmd
└── src/
```

## Purpose

Prepares project files for deployment into Docker.

---

# Step 5: Navigate to Project Folder

Example:

```powershell
cd Downloads
```

Verify:

```powershell
dir
```

Expected:

```text
demo
```

## Purpose

Ensures the upload command executes from the correct local folder.

---

# Step 6: Upload Project into Container

Command:

```bash
docker cp demo javamaven:/home/
```

## Purpose

Transfers the Spring Boot project from the local machine into the Docker container.

Result:

```text
/home/demo
```

exists inside the container.

---

# Step 7: Verify Upload

Navigate:

```bash
cd /home/demo
```

Verify:

```bash
ls
```

Expected:

```text
pom.xml
src
mvnw
mvnw.cmd
```

## Purpose

Confirms files copied successfully.

---

# Step 8: Locate DemoApplication.java

Navigate:

```bash
cd /home/demo/src/main/java/com/example/demo
```

Verify:

```bash
ls
```

Expected:

```text
DemoApplication.java
```

## Purpose

Locate the Spring Boot application entry point.

---

# Step 9: Modify Application Code

Updated file:

```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@SpringBootApplication
@RestController
public class DemoApplication {

    public static void main(String[] args)
    {
        SpringApplication.run(DemoApplication.class, args);
    }

    @GetMapping("/hello")
    public String hello(
        @RequestParam(
            value = "name",
            defaultValue = "World"
        ) String name)
    {
        return String.format("Hello %s!", name);
    }
}
```

Verify:

```bash
cat DemoApplication.java
```

## Purpose

Create a REST endpoint:

```text
/hello
```

Add support for:

```text
?name=
```

URL parameters.

---

# Spring Boot Annotations

## @SpringBootApplication

Starts the Spring Boot application.

```java
@SpringBootApplication
```

---

## @RestController

Marks the class as a web controller.

```java
@RestController
```

---

## @GetMapping

Creates a web endpoint.

```java
@GetMapping("/hello")
```

---

## @RequestParam

Accepts URL parameters.

Example:

```text
?name=John
```

---

# Step 10: Run Application

Navigate:

```bash
cd /home/demo
```

Execute:

```bash
mvn spring-boot:run
```

Expected output:

```text
Started DemoApplication
```

and

```text
Tomcat started on port(s): 8080
```

## Purpose

Compiles and launches the Spring Boot web server.

---

# Step 11: Browser Testing

## Test 1

URL:

```text
http://localhost:8080/hello
```

Output:

```text
Hello World!
```

---

## Test 2

URL:

```text
http://localhost:8080/hello?name=John
```

Output:

```text
Hello John!
```

---

# Request Flow

```text
Browser Request
        ↓
Spring Boot Endpoint
        ↓
@GetMapping("/hello")
        ↓
hello() Method
        ↓
Response Returned
        ↓
Browser Displays Result
```

---

# Project Structure

```text
demo/
├── pom.xml
├── mvnw
├── mvnw.cmd
└── src/
    └── main/
        └── java/
            └── com/
                └── example/
                    └── demo/
                        └── DemoApplication.java
```

---

# Commands Used

## Create Container

```bash
docker run --name javamaven -dti --rm -p 8080:8080 maven:3.9-eclipse-temurin-17 bash
```

---

## Open Container

```bash
docker exec -it javamaven bash
```

---

## Update Packages

```bash
apt-get update
```

---

## Install Nano

```bash
apt-get install -y nano
```

---

## Upload Files

```bash
docker cp demo javamaven:/home/
```

---

## Verify Upload

```bash
ls
```

---

## View Source Code

```bash
cat DemoApplication.java
```

---

## Run Application

```bash
mvn spring-boot:run
```

---

# Data Engineering Relevance

Spring Boot is widely used in enterprise data platforms.

Common use cases include:

### REST APIs

Expose data through HTTP endpoints.

Example:

```text
/api/customers
/api/orders
/api/assets
```

---

### Data Services

Provide access to processed and curated datasets.

---

### Metadata Management

Expose metadata catalogs and governance information.

---

### Monitoring Systems

Provide health checks and monitoring endpoints.

---

### Microservices

Support distributed architectures in cloud platforms.

---

# Lessons Learned

- Spring Boot simplifies Java web development.
- Maven manages Java dependencies automatically.
- Docker provides a consistent runtime environment.
- REST endpoints can be created using annotations.
- URL parameters make applications dynamic.
- Web applications can be built and deployed with relatively small amounts of Java code.
- Spring Boot is heavily used in enterprise and data engineering environments.

---

# Challenges Encountered

- Understanding Docker-to-local file transfers.
- Learning Spring Boot project structure.
- Editing source code within a container.
- Waiting for Maven to download dependencies during the first application startup.

---

# Key Takeaways

- Spring Boot is one of the most important Java frameworks.
- Docker allows Java applications to run consistently across environments.
- Maven simplifies dependency management.
- APIs can be created quickly using Spring Boot annotations.
- Java, Docker, Maven, and Spring Boot form a powerful foundation for enterprise application development.

---

# Completion Status

```text
✅ Completed
```