# CDC (Change Data Capture) Reference Notes

## Overview

Change Data Capture (CDC) is a technique used to identify and track changes occurring within a database.

CDC captures:

```text
INSERT
UPDATE
DELETE
```

operations.

---

# Why CDC Matters

Without CDC:

```text
Application
      ↓
Repeated Polling
      ↓
Database
```

Problems:

- High Load
- Slower Processing
- Increased Costs

---

# CDC Solution

```text
Database Change
      ↓
Event Generated
      ↓
Application Processes Event
```

Benefits:

- Real-Time Data
- Better Performance
- Reduced Database Load

---

# CDC Workflow

```text
Database
      ↓
Transaction Log
      ↓
CDC Tool
      ↓
Consumer Application
```

---

# Event-Driven Architecture

CDC supports event-driven systems.

```text
Database Event
       ↓
CDC Event
       ↓
Application
```

---

# Common CDC Tools

## Debezium

Open-source CDC platform.

---

## AWS DMS

Database migration and CDC service.

---

## Oracle GoldenGate

Enterprise CDC solution.

---

# CDC Operations

## Insert

New record created.

```text
Create Event
```

---

## Update

Existing record modified.

```text
Update Event
```

---

## Delete

Record removed.

```text
Delete Event
```

---

# Real-Time Example

Insert:

```sql
INSERT INTO employee
VALUES (
    2,
    'Mary',
    'Doe'
);
```

CDC captures event immediately.

---

# Data Engineering Use Cases

## Analytics