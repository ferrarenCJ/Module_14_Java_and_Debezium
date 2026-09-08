# Spring Boot Reference Notes

## Overview

Spring Boot is a Java framework used for building web, enterprise, and microservice applications quickly and efficiently.

Spring Boot reduces the amount of configuration required in traditional Java applications by providing:

- Auto Configuration
- Embedded Web Servers
- Dependency Management
- Production-Ready Features

---

# Why Spring Boot?

Traditional Java applications often require:

```text
Extensive Configuration
Application Server Setup
Complex Build Processes
```

Spring Boot simplifies development through:

```text
Convention Over Configuration
Embedded Servers
Rapid Development
```

---

# Spring Boot Architecture

```text
Java Application
        ↓
Spring Framework
        ↓
Spring Boot
        ↓
Embedded Server
        ↓
Web Application/API
```

---

# Project Structure

```text
myproject
│
├── src
│   ├── main
│   │   ├── java
│   │   └── resources
│   │
│   └── test
│
├── pom.xml
│
└── Dockerfile
```

---

# Main Application Class

Every Spring Boot application starts with:

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class Application {

    public static void main(String[] args) {

        SpringApplication.run(
            Application.class,
            args
        );

    }

}
```

---

# @SpringBootApplication

Primary annotation used to start Spring Boot.

```java
@SpringBootApplication
```

Combines:

```text
@Configuration
@EnableAutoConfiguration
@ComponentScan
```

---

# Running a Spring Boot Application

## Maven Command

```bash
mvn spring-boot:run
```

Example from Module 14:

```bash
mvn spring-boot:run
```

Output:

```text
Started TvApplication
```

---

# Maven

Spring Boot projects commonly use Maven for dependency management.

---

## Compile

```bash
mvn compile
```

---

## Run Tests

```bash
mvn test
```

---

## Package

```bash
mvn package
```

---

## Run Application

```bash
mvn spring-boot:run
```

---

# pom.xml

The Maven configuration file.

Example:

```xml
<project>

    <dependencies>

        <dependency>
            <groupId>
                org.springframework.boot
            </groupId>

            <artifactId>
                spring-boot-starter-web
            </artifactId>

        </dependency>

    </dependencies>

</project>
```

---

# Spring Boot Starters

Spring Boot simplifies dependency management through starter packages.

Examples:

### Web Applications

```xml
spring-boot-starter-web
```

---

### Database Access

```xml
spring-boot-starter-data-jpa
```

---

### Testing

```xml
spring-boot-starter-test
```

---

# Controllers

Controllers handle HTTP requests.

Example:

```java
import org.springframework.web.bind.annotation.*;

@RestController
public class HomeController {

    @GetMapping("/")
    public String home() {

        return "Hello World";

    }

}
```

---

# REST APIs

Spring Boot frequently develops REST APIs.

Example:

```java
@GetMapping("/employees")
```

Returns data.

---

```java
@PostMapping("/employees")
```

Creates data.

---

```java
@PutMapping("/employees")
```

Updates data.

---

```java
@DeleteMapping("/employees")
```

Deletes data.

---

# Dependency Injection

Spring Boot automatically manages objects.

Annotation:

```java
@Autowired
```

Example:

```java
@Autowired
EmployeeService employeeService;
```

Benefits:

```text
Loose Coupling
Reusable Code
Simplified Development
```

---

# Services

Business logic is typically placed within service classes.

Example:

```java
@Service
public class EmployeeService {

}
```

---

# Configuration Files

Application settings are stored in:

```text
application.properties
```

or

```text
application.yml
```

---

## Example

```properties
server.port=8080
```

---

## Database Example

```properties
spring.datasource.url=
jdbc:mysql://localhost:3306/employeedb
```

---

# Embedded Server

Spring Boot includes an embedded server.

Common options:

```text
Tomcat
Jetty
Undertow
```

Default:

```text
Apache Tomcat
```

---

# Build Executable JAR

```bash
mvn package
```

Result:

```text
target/app.jar
```

Run:

```bash
java -jar app.jar
```

---

# Spring Boot and Docker

Build image:

```bash
docker build -t springboot-app .
```

Run container:

```bash
docker run springboot-app
```

---

# Spring Boot and Debezium

Module 14 Architecture:

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

Spring Boot served as the application framework that hosted Debezium.

---

# Module 14 Example

Start application:

```bash
mvn spring-boot:run
```

Output:

```text
Starting embedded Tomcat
```

Then:

```text
Started TvApplication
```

After startup:

```text
FirstName=John
```

CDC monitoring begins.

---

# Benefits of Spring Boot

## Faster Development

Less configuration required.

---

## Embedded Server

No manual server installation.

---

## Production Ready

Built-in monitoring and configuration.

---

## Cloud Friendly

Works well in:

```text
Docker
Kubernetes
AWS
Azure
```

---

# Common Annotations

## Application

```java
@SpringBootApplication
```

---

## Controller

```java
@RestController
```

---

## Service

```java
@Service
```

---

## Dependency Injection

```java
@Autowired
```

---

## Request Mapping

```java
@GetMapping
@PostMapping
@PutMapping
@DeleteMapping
```

---

# Common Spring Boot Commands

Run:

```bash
mvn spring-boot:run
```

Compile:

```bash
mvn compile
```

Test:

```bash
mvn test
```

Package:

```bash
mvn package
```

---

# Key Terms

- Spring Boot
- Maven
- Controller
- Service
- Dependency Injection
- REST API
- Embedded Tomcat
- Annotation
- Application Properties

---

# Module 14 Relevance

Spring Boot was used throughout Module 14 to:

- Host the Debezium CDC application
- Manage dependencies through Maven
- Start and run the CDC service
- Connect to MySQL
- Monitor database changes through Debezium

Understanding Spring Boot is essential for building modern Java-based data engineering and enterprise applications.