# Final Assignment 14.1: Java and Debezium

## Assignment Goal

Build a complete CDC environment using:

- Docker
- MySQL
- Spring Boot
- Debezium

The system captures database changes and immediately generates CDC events.

---

# Step 1

Verified no running Docker containers.

Purpose:

```text
Clean execution environment
```

---

# Step 2

Created network:

```bash
docker network create CDCFinalAssignment
```

Purpose:

```text
Container communication
```

---

# Step 3

Created:

```text
Dockerfile
employee.sql
```

Database:

```text
employeedb
```

Table:

```text
employee
```

Initial record:

```text
John Doe
```

---

# Step 4

Built image:

```bash
docker build -t mysqlmasterimg .
```

Result:

```text
mysqlmasterimg
```

---

# Step 5

Created container:

```bash
docker run --rm \
--name mysqlmasterdb \
-p 3306:3306 \
--network CDCFinalAssignment \
-d mysqlmasterimg
```

Result:

```text
mysqlmasterdb
```

---

# Step 6

Verified:

```text
mysqlmasterdb
```

running successfully.

---

# Step 7

Downloaded and extracted:

```text
Debezium Project
```

Purpose:

```text
CDC Application
```

---

# Step 8

Updated Dockerfile:

```dockerfile
FROM maven:3.9-eclipse-temurin-11
```

Built:

```bash
docker build -t debeziumimg .
```

Purpose:

```text
Supported Maven image
```

---

# Step 9

Created Debezium container:

```bash
docker run -dit \
--name debeziumserver \
--network CDCFinalAssignment \
debeziumimg bash
```

Purpose:

```text
Run CDC application
```

---

# Step 10

Installed nano:

```bash
apt-get update
apt-get install -y nano
```

Purpose:

```text
Modify connector configuration
```

---

# Step 11

Updated:

```text
DebeziumConnectorConfig.java
```

Changes:

```text
customerdb  → employeedb
mysqlserver → mysqlmasterdb
```

Purpose:

```text
Point Debezium to new database
```

---

# Step 12

Started application:

```bash
mvn spring-boot:run
```

Output:

```text
FirstName=John
```

Purpose:

```text
Verify initial snapshot
```

---

# Step 13

Connected to MySQL:

```bash
mysql -h localhost \
-u root \
-pMyNewPass \
employeedb
```

Purpose:

```text
Execute test transaction
```

---

# Step 14

Inserted record:

```sql
INSERT INTO employeedb.employee
VALUES (
    2,
    'Mary',
    'Doe',
    '4351234354',
    'mary@doe.com'
);
```

Result:

```text
1 row affected
```

---

# Step 15

Debezium detected:

```text
FirstName=Mary
```

Operation:

```text
op=c
```

Meaning:

```text
Create Event
```

CDC confirmed successful.

---

# CDC Workflow

```text
MySQL Insert
      ↓
Binary Log
      ↓
Debezium Connector
      ↓
CDC Event
      ↓
Spring Boot Output
```

---

# Architecture

```text
CDCFinalAssignment
│
├── mysqlmasterdb
│       │
│       ▼
│    employeedb
│
└── debeziumserver
        │
        ▼
   Spring Boot
        │
        ▼
     Debezium
        │
        ▼
    CDC Events
```

---

# Lessons Learned

- CDC eliminates repetitive polling.
- Debezium relies on transaction logs.
- Docker networking is required for container communication.
- MySQL binlogs provide efficient CDC processing.
- Spring Boot integrates easily with Debezium.
- Event-driven systems support real-time processing.

---

# Key Takeaways

- Successfully built a CDC application.
- Connected MySQL and Debezium through Docker.
- Verified CDC using employee data.
- Demonstrated snapshots and streaming.
- Implemented a production-style CDC architecture.

---

# Completion Status

```text
✅ Final Assignment Completed
```