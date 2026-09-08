# Spring Boot Cheat Sheet

## What is Spring Boot?

Spring Boot is a Java framework used for rapidly developing web and enterprise applications.

Benefits:

- Auto Configuration
- Embedded Server
- Dependency Management
- Rapid Development

---

# Project Structure

```text
project
│
├── src
│   └── main
│       ├── java
│       └── resources
│
├── pom.xml
└── Dockerfile
```

---

# Main Application

```java
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

# Run Application

```bash
mvn spring-boot:run
```

---

# Build Project

```bash
mvn clean package
```

---

# Maven

Common Commands:

```bash
mvn clean
mvn compile
mvn package
mvn test
```

---

# REST Controller

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

# Annotations

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

# Configuration

application.properties

```properties
server.port=8080
```

---

# Dependency Example

pom.xml

```xml
<dependency>
    <groupId>
        org.springframework.boot
    </groupId>
</dependency>
```

---

# Spring Boot + Debezium

Workflow:

```text
Spring Boot
        ↓
Debezium Connector
        ↓
MySQL Database
        ↓
CDC Events
```

---

# Docker Execution

Build:

```bash
docker build -t app .
```

Run:

```bash
docker run app
```

---

# Key Terms

- Spring Boot
- Maven
- Controller
- Dependency Injection
- REST API
- Properties File
- Web Application

---

# Module 14 Takeaway

Spring Boot provides the framework used to host Debezium and process CDC events.