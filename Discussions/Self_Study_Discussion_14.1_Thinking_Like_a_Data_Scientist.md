# Self-Study Discussion 14.1: Thinking Like a Data Scientist - Java and Debezium

One resource that helped me in this module was the **Debezium Documentation**.

**Resource:** Debezium Documentation  
**Link:** https://debezium.io/documentation/reference/stable/

It helped me understand Change Data Capture (CDC), MySQL binlogs, snapshots, and Debezium event processing. This was especially useful during Coding Activity 14.4 and Final Assignment 14.1 when connecting MySQL and Debezium.

Another helpful resource was the **Spring Boot Documentation**.

**Resource:** Spring Boot Documentation  
**Link:** https://spring.io/projects/spring-boot

It helped me understand the Spring Boot application structure and how to run the project using:

```bash
mvn spring-boot:run
```

### Tip

When troubleshooting Docker and Debezium, always verify your containers and network first:

```bash
docker ps
docker network ls
```

This helped me quickly identify configuration and connectivity issues during the assignments.