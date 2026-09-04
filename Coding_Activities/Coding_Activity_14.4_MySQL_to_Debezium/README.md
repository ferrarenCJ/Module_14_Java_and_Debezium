# Coding Activity 14.4: Connecting MySQL to Debezium

## Objective

The objective of this activity is to connect a MySQL database running in Docker to a Debezium-based Change Data Capture (CDC) application. Debezium monitors database changes and automatically captures INSERT, UPDATE, and DELETE operations.

---

## Learning Outcome

- Connect a database to Debezium.

---

## Purpose

In Module 13, CDC was implemented through periodic database queries. This activity demonstrates a more advanced event-driven approach using Debezium.

Debezium monitors the MySQL binary log and immediately detects database changes, reducing the need for polling and enabling near real-time data integration.

---

## Activity Summary

In this activity:

1. Verified the MySQL container was running.
2. Verified the Docker network.
3. Extracted the Debezium project.
4. Built the Debezium Docker image.
5. Created the Debezium container.
6. Connected Debezium to MySQL through Docker networking.
7. Started the Spring Boot Debezium application.
8. Inserted a customer record using MySQL Workbench.
9. Verified Debezium automatically detected the database change.

---

## Docker Architecture

```text
myCDCNetwork
│
├── mysqlserver
│      │
│      ▼
│   customerdb
│
└── debeziumserver
        │
        ▼
   Debezium CDC
        │
        ▼
   Change Events
```

---

## Commands Used

### Verify Network

```bash
docker network ls
```

### Build Debezium Image

```bash
docker build -t debeziumactivity14_4 .
```

### Create Debezium Container

```bash
docker run -it --rm --name debeziumserver --network myCDCNetwork debeziumactivity14_4 bash
```

### Start Application

```bash
mvn spring-boot:run
```

---

## MySQL Query Executed

```sql
INSERT INTO customerdb.customer
VALUES (
    2,
    'Peter Parker',
    'pp@example.com'
);
```

---

## CDC Event Detected

Debezium detected:

```text
Key = 'Struct{id=2}'
```

and:

```text
fullname=Peter Parker
email=pp@example.com
```

Operation:

```text
op=c
```

Meaning:

```text
c = CREATE (INSERT)
```

---

## Screenshots Included

- Step 1: MySQL Container Running
- Step 2: Docker Network Verification
- Step 3: Debezium Project Extracted
- Step 4: Debezium Docker Image Build
- Step 5: Debezium Container Created
- Step 6: Both Containers Running
- Step 7: Debezium Application Running
- Step 8: MySQL Workbench Insert
- Step 9: Debezium Detected New Record

---

## Key Takeaways

- Debezium provides real-time CDC capabilities.
- Docker networking allows containers to communicate.
- MySQL binary logs are used to detect changes.
- CDC events can be consumed by downstream applications.
- Event-driven CDC is more efficient than periodic polling.
- Debezium simplifies enterprise data synchronization.

---

## Completion Status

```text
✅ Completed
```