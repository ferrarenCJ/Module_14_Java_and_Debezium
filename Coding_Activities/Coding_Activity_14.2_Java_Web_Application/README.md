# Coding Activity 14.2: Developing a Web Application in Java

## Objective

The objective of this activity is to develop a simple web application using Java and Spring Boot, deploy it within a Docker container, and verify that it is accessible through a web browser.

---

## Purpose

This activity introduces the foundations of modern Java web development using Spring Boot. Students learn how to:

- Create a Spring Boot project.
- Deploy a Java application inside a Docker container.
- Configure and run a web server.
- Handle HTTP requests using REST endpoints.
- Test web applications through a browser.
- Integrate Java, Maven, Docker, and Spring Boot into a single workflow.

These skills are commonly used in enterprise software development, cloud-native applications, microservices, and data engineering platforms.

---

## Learning Outcome

- Develop a web application in Java.

---

# Activity Overview

The activity walks through the complete lifecycle of a simple Spring Boot application:

1. Create a Java/Maven Docker container.
2. Install required tools.
3. Generate a Spring Boot project.
4. Upload the project into the container.
5. Modify application code.
6. Build and run the application.
7. Validate the application using a web browser.

---

# Technologies Used

## Docker

Provides an isolated runtime environment.

## Java 17

Programming language used to build the application.

## Maven

Dependency and build management tool.

## Spring Boot

Java framework used to create web applications and REST APIs.

---

# Step 1: Create Java Docker Container

Create a Java Maven container:

```bash
docker run --name javamaven -dti --rm -p 8080:8080 maven:3.9-eclipse-temurin-17 bash
```

### Purpose

- Creates a container named `javamaven`
- Uses Java 17
- Uses Maven 3.9
- Maps web traffic to port 8080

### Screenshot Required

✅ Java container created on port 8080

---

# Step 2: Open Container CLI and Update Packages

Connect to the container:

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

### Purpose

- Update package lists
- Install a text editor for modifying source files

### Screenshot Required

✅ Updated container CLI

---

# Step 3: Create Spring Boot Project

Navigate to:

```text
https://start.spring.io
```

Configure:

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

Generate:

```text
demo.zip
```

### Screenshot Required

✅ Spring Initializr configuration

---

# Step 4: Extract Project

Unzip:

```text
demo.zip
```

Verify:

```text
demo/
├── pom.xml
├── mvnw
├── mvnw.cmd
└── src/
```

### Screenshot Required

✅ Extracted project structure

---

# Step 5: Navigate to Project Directory

Open local terminal.

Example:

```powershell
cd Downloads
```

or

```bash
cd ~/Downloads
```

### Screenshot Required

✅ Terminal showing current folder

---

# Step 6: Upload Project to Container

Upload project:

```bash
docker cp demo javamaven:/home/
```

### Purpose

Copies Spring Boot project into the Docker container.

### Screenshot Required

✅ Successful docker cp command

---

# Step 7: Verify Upload

Inside the container:

```bash
cd /home/demo
ls
```

Expected files:

```text
pom.xml
src
mvnw
mvnw.cmd
```

### Screenshot Required

✅ Uploaded files visible inside container

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

### Screenshot Required

✅ DemoApplication.java file

---

# Step 9: Update Application Code

Open:

```bash
nano DemoApplication.java
```

Replace contents with:

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
    public String hello(@RequestParam(value = "name", defaultValue = "World") String name)
    {
        return String.format("Hello %s!", name);
    }
}
```

Verify:

```bash
cat DemoApplication.java
```

### Screenshot Required

✅ Updated source code

---

# Step 10: Run Application

Navigate:

```bash
cd /home/demo
```

Run:

```bash
mvn spring-boot:run
```

Wait for output showing:

```text
Started DemoApplication
```

### Screenshot Required

✅ Application running successfully

---

# Step 11: Test Application

## Test 1

Navigate to:

```text
http://localhost:8080/hello
```

Expected output:

```text
Hello World!
```

### Screenshot Required

✅ Browser showing Hello World!

---

## Test 2

Navigate to:

```text
http://localhost:8080/hello?name=John
```

Expected output:

```text
Hello John!
```

### Screenshot Required

✅ Browser showing Hello John!

---

# File Structure

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

# Key Commands Used

### Create Container

```bash
docker run --name javamaven -dti --rm -p 8080:8080 maven:3.9-eclipse-temurin-17 bash
```

### Enter Container

```bash
docker exec -it javamaven bash
```

### Install Nano

```bash
apt-get update
apt-get install -y nano
```

### Upload Project

```bash
docker cp demo javamaven:/home/
```

### Run Application

```bash
mvn spring-boot:run
```

---

# Key Concepts Learned

## Spring Boot

Java framework for rapidly building web applications.

## REST Controller

Handles incoming HTTP requests.

```java
@RestController
```

## GET Endpoint

Responds to browser requests.

```java
@GetMapping("/hello")
```

## Query Parameters

Allows user input through the URL.

Example:

```text
?name=John
```

## Maven

Manages dependencies and application builds.

## Docker

Provides a portable runtime environment.

---

# Data Engineering Relevance

Spring Boot is frequently used by data engineers to:

- Build REST APIs
- Expose data services
- Create ingestion endpoints
- Support metadata platforms
- Develop microservices
- Interface with databases and data pipelines

Examples include:

```text
Fleet APIs
Metadata Services
Reporting Services
Data Quality APIs
Monitoring Applications
```

---

# Submission Checklist

- [ ] Step 1: Java container created
- [ ] Step 2: Container updated
- [ ] Step 3: Spring Initializr configured
- [ ] Step 4: Project extracted
- [ ] Step 5: Terminal in correct folder
- [ ] Step 6: docker cp executed
- [ ] Step 7: Upload verified
- [ ] Step 8: DemoApplication.java visible
- [ ] Step 9: Updated code verified
- [ ] Step 10: Application running
- [ ] Step 11a: Hello World page
- [ ] Step 11b: Hello John page

---

# Completion Status

```text
☐ Not Started
☐ In Progress
☐ Completed
```