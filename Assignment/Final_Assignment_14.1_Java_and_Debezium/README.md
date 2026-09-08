# Final Assignment 14.1: Java and Debezium

## Objective

This assignment demonstrates how to build a complete Change Data Capture (CDC) solution using Docker, MySQL, Spring Boot, and Debezium.

The solution uses Docker containers connected through a Docker network. A MySQL database serves as the CDC source, while Debezium monitors database changes and streams CDC events.

---

## Learning Outcomes

- Set up a network for Debezium in Docker.
- Connect a database to Debezium.
- Implement Change Data Capture (CDC).
- Monitor MySQL database changes using Debezium.

---

## Solution Architecture

```text
CDCFinalAssignment
│
├── mysqlmasterdb
│      │
│      ▼
│   employeedb
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

## Components

### Docker Network

```text
CDCFinalAssignment
```

Provides communication between containers.

### MySQL Container

```text
mysqlmasterdb
```

Hosts:

```text
employeedb
```

### Debezium Container

```text
debeziumserver
```

Monitors database changes.

---

## Database Table

```sql
employee
```

Columns:

```text
id
FirstName
LastName
MobileNumber
email
```

Initial Record:

```text
John Doe
```

CDC Test Record:

```text
Mary Doe
```

---

## Major Tasks Completed

1. Created Docker network.
2. Built MySQL Docker image.
3. Enabled MySQL binary logging.
4. Created MySQL container.
5. Built Debezium Docker image.
6. Updated Maven base image.
7. Created Debezium container.
8. Updated Debezium connector configuration.
9. Started Spring Boot CDC application.
10. Inserted employee records.
11. Verified CDC events.

---

## CDC Verification

Initial CDC event:

```text
FirstName=John
```

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

Debezium CDC event:

```text
FirstName=Mary
```

---

## Screenshots Included

- Step 1 through Step 15

All required screenshots have been captured and included in the submission document.

---

## Key Takeaways

- Docker networks enable container communication.
- MySQL binary logging is required for Debezium CDC.
- Debezium monitors MySQL binlogs.
- Spring Boot can host Debezium CDC applications.
- CDC provides near real-time event processing.
- Event-driven architectures scale better than polling solutions.

---

## Completion Status

```text
✅ Completed
```