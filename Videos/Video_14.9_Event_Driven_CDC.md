# Video 14.9: Event-Driven Approach for CDC

## Duration

**10:01**

---

# Overview

This video introduces the concept of an **Event-Driven Approach for Change Data Capture (CDC)**.

An event-driven system responds whenever a specific event occurs. In database systems, events typically occur when data changes through:

- INSERT operations
- UPDATE operations
- DELETE operations

Instead of repeatedly querying a database to check for changes, CDC solutions monitor events and react immediately when changes occur.

---

# Learning Objectives

After completing this video, you should be able to:

- Define event-driven architecture.
- Explain Change Data Capture (CDC).
- Understand database events.
- Identify common CDC use cases.
- Explain how CDC propagates changes to downstream systems.
- Understand why CDC is important in modern data engineering architectures.

---

# What Is Event-Driven Processing?

An event-driven system executes logic when an event occurs.

General flow:

```text
Event Occurs
      ↓
Event Detected
      ↓
Application Triggered
      ↓
Action Performed
```

Examples:

- New customer record created
- Employee status updated
- Order submitted
- Sensor reading received
- Payment processed

---

# What Is an Event?

An event is a change or activity that occurs within a system.

Examples:

### Insert

```sql
INSERT INTO customers
VALUES (1,'John Smith');
```

Event:

```text
New customer created
```

---

### Update

```sql
UPDATE customers
SET city = 'San Diego'
WHERE customer_id = 1;
```

Event:

```text
Customer record updated
```

---

### Delete

```sql
DELETE FROM customers
WHERE customer_id = 1;
```

Event:

```text
Customer record deleted
```

---

# What Is Change Data Capture (CDC)?

Change Data Capture (CDC) is a technique used to identify and capture changes made to a database.

CDC tracks:

```text
INSERT
UPDATE
DELETE
```

operations.

Purpose:

```text
Capture changes once
Propagate changes everywhere
```

---

# Traditional Approach

Without CDC:

```text
Application
      ↓
Repeatedly Queries Database
      ↓
Checks For Changes
```

Problems:

- High database load
- Unnecessary polling
- Latency
- Increased costs

---

# Event-Driven CDC Approach

With CDC:

```text
Database Change
      ↓
CDC Captures Event
      ↓
Message Generated
      ↓
Other Systems Updated
```

Benefits:

- Real-time updates
- Reduced polling
- Better scalability
- Lower resource consumption

---

# Example Workflow

Imagine a customer database.

New record:

```sql
INSERT INTO customers
VALUES (101,'John');
```

CDC detects:

```text
INSERT event
```

CDC publishes:

```json
{
  "operation": "INSERT",
  "customer_id": 101,
  "name": "John"
}
```

Downstream systems receive the update automatically.

---

# Event Propagation

CDC often sends changes to other systems.

Example architecture:

```text
Database
    ↓
CDC Tool
    ↓
Message Queue
    ↓
Applications
    ↓
Analytics Systems
```

Examples:

- Kafka
- Debezium
- Event Hubs
- Kinesis

---

# Why Use CDC?

CDC eliminates the need for continuous polling.

Instead of:

```text
Did anything change?
Did anything change?
Did anything change?
```

the database notifies systems when changes occur.

Advantages:

### Real-Time Data

Updates occur immediately.

### Reduced Database Load

No constant queries.

### Improved Scalability

Supports many downstream consumers.

### Better Performance

Less resource consumption.

---

# CDC Example for E-Commerce

Customer places order:

```text
Order Created
```

Event generated:

```text
INSERT order
```

CDC captures change.

Updates:

- Order service
- Inventory system
- Shipping system
- Analytics platform

Automatically.

---

# CDC Example for Utilities

Relevant to utility companies such as SoCalGas.

Examples:

### Work Order Created

```text
SAP Work Order
```

CDC event:

```text
INSERT
```

Updates:

- Reporting systems
- Mobile applications
- Analytics platforms

---

### Asset Status Updates

```text
Asset Inspection Completed
```

CDC event:

```text
UPDATE
```

Automatically delivered downstream.

---

# CDC Example for Fleet Management

Vehicle telemetry arrives:

```text
Mileage Updated
Fuel Reading Updated
```

Database changes trigger:

```text
CDC Events
```

Updates:

- Fleet dashboards
- Alerting systems
- Analytics databases

without manual synchronization.

---

# Database Event Detection

Common detection methods:

### Triggers

Database trigger executes after a change.

Example:

```sql
AFTER INSERT
```

---

### Transaction Logs

Reads database transaction logs.

Examples:

```text
MySQL Binlog
PostgreSQL WAL
SQL Server Transaction Log
```

This is the preferred enterprise solution.

---

# Event-Driven Architecture

General flow:

```text
Application
      ↓
Database Change
      ↓
CDC
      ↓
Event Stream
      ↓
Consumers
```

Benefits:

- Decoupled systems
- Scalability
- Reliability
- Near real-time processing

---

# Debezium

Debezium is a CDC platform discussed later in the module.

Purpose:

```text
Capture database changes
Convert them to events
Publish events
```

Debezium commonly integrates with:

```text
Kafka
MySQL
PostgreSQL
SQL Server
MongoDB
```

---

# Data Engineering Use Cases

CDC is widely used in data engineering.

Examples:

### Data Warehousing

```text
Operational Database
        ↓
CDC
        ↓
Data Warehouse
```

---

### Data Lakes

Incremental ingestion instead of full reloads.

---

### Real-Time Analytics

Fresh data available immediately.

---

### Monitoring Systems

Automatic updates across systems.

---

### Event Streaming

Publish database changes directly to streaming platforms.

---

# Advantages of CDC

## Near Real-Time Processing

Changes become available almost immediately.

---

## Lower Overhead

Avoids constant polling.

---

## Incremental Updates

Only changed data is processed.

---

## Improved Data Freshness

Reduces latency.

---

## Scalability

Supports large enterprise environments.

---

# Challenges

## Complexity

Requires specialized tools.

---

## Event Ordering

Events must remain in the proper sequence.

---

## Error Handling

Failed event delivery must be managed.

---

## Infrastructure Requirements

Often requires:

```text
Kafka
Debezium
Message brokers
```

---

# Key Terms

## Event

An action or change occurring within a system.

---

## CDC

Change Data Capture.

A process used to identify and capture database changes.

---

## Event-Driven Architecture

An architecture where actions occur in response to events.

---

## Transaction Log

Database log containing all changes made to data.

---

## Debezium

Open-source CDC platform that monitors database changes and publishes events.

---

## Consumer

An application receiving CDC events.

---

# Key Takeaways

- Event-driven systems react when events occur.
- CDC captures database changes such as INSERT, UPDATE, and DELETE operations.
- CDC reduces the need for database polling.
- Event-driven architectures improve scalability and efficiency.
- CDC is widely used in data engineering, analytics, and microservices.
- Debezium is a popular CDC platform that captures database changes and publishes events.
- CDC enables near real-time data integration and synchronization across systems.

---

# Personal Notes

- CDC solves the common problem of keeping multiple systems synchronized.
- Instead of repeatedly querying databases, systems react to events.
- Debezium appears to be a key technology connecting operational databases with event-streaming platforms.
- CDC is highly relevant for data engineering because it supports incremental processing and real-time analytics.
- This approach can be useful for SAP, operational reporting, fleet management, and utility asset-management systems where near real-time updates are important.