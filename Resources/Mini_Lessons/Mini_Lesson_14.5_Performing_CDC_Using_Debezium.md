# Mini-Lesson 14.5: Performing CDC Using Debezium

## Overview

This lesson explains how Debezium performs **Change Data Capture (CDC)** by monitoring database transaction logs and streaming database changes to applications.

Debezium enables applications to react to changes in databases such as MySQL, PostgreSQL, MongoDB, and SQL Server without continually polling the database.

---

# Learning Objectives

After completing this lesson, you should be able to:

- Explain why CDC is important.
- Describe how Debezium performs CDC.
- Understand Debezium connector capabilities.
- Explain how Debezium uses MySQL binlogs.
- Identify the components of a Debezium event message.
- Understand snapshots and streaming modes.

---

# Why Is CDC Important?

Organizations often have many systems that rely on the same data.

Examples:

```text
Operational Databases
Reporting Systems
Data Warehouses
Data Lakes
Analytics Applications
Microservices
```

When data changes in one system, other systems need to be updated.

Without CDC:

```text
Application
      ↓
Poll Database
      ↓
Check For Changes
      ↓
Update Systems
```

Problems:

- Increased database load
- Unnecessary queries
- Higher latency
- Poor scalability

---

# Debezium and CDC

Debezium is an open-source platform designed for:

```text
Change Data Capture
```

Debezium continuously monitors database changes and streams those changes to downstream applications.

Supported databases include:

```text
MySQL
PostgreSQL
MongoDB
SQL Server
Cassandra
MariaDB
Oracle
```

---

# Event Streaming

Debezium streams database events.

Examples:

```text
INSERT
UPDATE
DELETE
```

Advantages:

### Faster Processing

Changes are available immediately.

---

### Reliable Recovery

Applications can restart without losing events.

---

### Reduced Load

Databases are not repeatedly queried.

---

# Bank Account Analogy

Debezium functions similarly to a bank transaction log.

Example:

```text
Deposit Money
Withdraw Money
Transfer Money
```

Every transaction is recorded.

Likewise:

```text
INSERT
UPDATE
DELETE
```

operations are recorded and tracked.

Debezium reads these transactions and delivers them to applications.

---

# Debezium Connector Capabilities

Debezium connectors provide several important features.

---

# Snapshots

A snapshot captures the current state of a database.

Purpose:

```text
Baseline Data Capture
```

Typical use cases:

- Initial application startup
- Data recovery
- Table reloads
- Schema updates

Example:

```text
customerdb.customer
```

If Debezium starts for the first time:

```text
No previous offset found
```

it performs a snapshot.

---

# Snapshot Benefits

A snapshot allows applications to:

```text
Read Existing Records
Capture Current State
Resume Processing
```

Example:

```text
John Doe
jd@example.com
```

can be captured before streaming begins.

---

# Filters

Debezium supports filtering.

Purpose:

```text
Process Only Required Data
```

Examples:

```text
Specific Databases
Specific Tables
Specific Records
```

Benefits:

- Improved performance
- Reduced processing volume

---

# Masking

Debezium can hide sensitive data.

Examples:

```text
Passwords
Credit Card Numbers
Social Security Numbers
```

Benefits:

```text
Security
Compliance
Privacy Protection
```

---

# Monitoring

Debezium supports monitoring of connector health and activity.

Benefits:

```text
Operational Visibility
Performance Tracking
Issue Detection
```

---

# CDC and MySQL

Debezium integrates particularly well with MySQL.

Reason:

```text
MySQL Binary Log (Binlog)
```

---

# What Is a Binlog?

The MySQL binary log records:

```text
Database Changes
```

Examples:

```sql
INSERT
UPDATE
DELETE
```

Every modification is written to the binlog.

---

# Example

SQL Statement:

```sql
INSERT INTO customer
VALUES (
    2,
    'Peter Parker',
    'pp@example.com'
);
```

MySQL records the operation in:

```text
binlog
```

Debezium reads the binlog and generates an event.

---

# Why Binlogs Are Important

Binlogs enable:

```text
High Performance CDC
```

because Debezium does not need to repeatedly query the database.

Instead:

```text
MySQL Binlog
      ↓
Debezium
      ↓
CDC Event
```

---

# Scaling CDC

Production databases may process:

```text
Thousands
or
Millions
```

of transactions daily.

Debezium can keep pace because:

```text
Transaction Logs
Are Sequential
```

and optimized for reading changes.

---

# Debezium Message Structure

For every captured event, Debezium sends a message.

A message often contains:

```text
Schema
Payload
Metadata
```

---

# Component 1: DDL

DDL refers to the operation being captured.

Examples:

```text
INSERT
SELECT
DROP
CREATE
ALTER
```

Example:

```text
INSERT
```

for a new customer.

---

# Component 2: Database Name

Identifies the source database.

Example:

```text
customerdb
```

---

# Component 3: POS

POS represents:

```text
Binlog Position
```

Example:

```text
binlog.000002
position 378
```

Purpose:

- Track progress
- Allow restart recovery
- Prevent duplicate processing

---

# Component 4: Table Changes

Contains the actual row-level data.

Example:

```text
Customer Table
```

Before:

```text
No Record
```

After:

```text
Peter Parker
pp@example.com
```

---

# Change Events

A change event captures a database modification.

Examples:

```text
INSERT
UPDATE
DELETE
```

---

# Event Key

The key uniquely identifies the row.

Example:

```text
Struct{id=2}
```

The primary key:

```text
id = 2
```

identifies the customer.

---

# Event Value

The value contains event details.

Example:

```text
after={
    id=2,
    fullname=Peter Parker,
    