# Video 14.11: Network Setup for Debezium

## Duration

**01:32**

---

# Overview

This video introduces the networking requirements needed for a Debezium-based Change Data Capture (CDC) architecture.

Since Debezium typically works with multiple containers, those containers must be able to communicate with one another over a shared Docker network. Dr. Sanchez demonstrates how Docker networking allows containers to interact and exchange data.

---

# Learning Objectives

After completing this video, you should be able to:

- Understand why container networking is required.
- Explain how Docker containers communicate.
- Create a Docker network.
- Connect multiple containers to the same network.
- Understand the networking requirements for Debezium architectures.

---

# Why Networking Is Required

In a Debezium environment, multiple services typically work together.

Examples:

```text
MySQL Database
Debezium Connector
Spring Boot Application
Kafka
```

These services often run inside separate Docker containers.

For the architecture to function correctly:

```text
Container A
      ↓
Container B
      ↓
Container C
```

must all be able to communicate.

Without networking:

```text
Containers are isolated
```

and communication becomes difficult.

---

# Container Communication

Docker containers can communicate through a shared Docker network.

Example:

```text
Docker Network
│
├── MySQL Container
├── Debezium Container
├── Kafka Container
└── Spring Boot Container
```

Each container can communicate with other containers attached to the same network.

---

# Debezium Architecture

The upcoming activities will use an architecture similar to:

```text
MySQL Database
        ↓
     Debezium
        ↓
       Kafka
        ↓
Spring Boot Application
```

For this architecture to work:

- MySQL must communicate with Debezium.
- Debezium must communicate with Kafka.
- Applications must communicate with Kafka.

Networking enables these connections.

---

# Creating a Docker Network

Create a network:

```bash
docker network create mynetwork
```

Verify:

```bash
docker network ls
```

Example output:

```text
NETWORK ID     NAME
xxxxxxxxxxxx   bridge
xxxxxxxxxxxx   host
xxxxxxxxxxxx   mynetwork
```

---

# Connecting Containers to a Network

Create a container attached to a network:

```bash
docker run --network mynetwork ...
```

Example:

```bash
docker run \
  --name mysql \
  --network mynetwork \
  mysql
```

---

# Existing Containers

Attach an existing container:

```bash
docker network connect mynetwork container_name
```

Example:

```bash
docker network connect mynetwork mysql
```

---

# How Containers Locate Each Other

Containers on the same network can often communicate using container names.

Example:

```text
Container Name: mysql
```

Connection string:

```text
mysql:3306
```

instead of:

```text
192.168.x.x
```

This simplifies configuration.

---

# Example Communication Flow

```text
MySQL Container
        ↓
Database Change
        ↓
Debezium Container
        ↓
CDC Event
        ↓
Consumer Application
```

All communication occurs through the shared Docker network.

---

# Container Networking Benefits

## Isolation

Containers communicate only within approved networks.

---

## Simplicity

Container names can be used instead of IP addresses.

---

## Scalability

Additional containers can easily join the network.

---

## Portability

The same architecture can run on:

- Windows
- macOS
- Linux
- Cloud platforms

---

# Data Engineering Relevance

Container networking is an important skill for data engineers.

Common use cases:

### CDC Architectures

```text
MySQL
  ↓
Debezium
  ↓
Kafka
```

---

### Data Platforms

```text
Applications
      ↓
APIs
      ↓
Databases
```

---

### Microservices

Multiple services communicate through shared networks.

---

### Streaming Systems

```text
Kafka
Spark
Flink
Debezium
```

communicate through container networks.

---

# Key Terms

## Docker Network

A virtual network that enables communication between containers.

---

## Container

An isolated runtime environment containing an application and its dependencies.

---

## Debezium

An open-source CDC platform that captures and publishes database changes.

---

## Connector

A component that captures changes from a source database.

---

## Kafka

A distributed event-streaming platform commonly used with Debezium.

---

# Example Architecture

```text
Docker Network
│
├── mysql
├── debezium
├── kafka
└── springboot
```

Communication:

```text
mysql
   ↓
debezium
   ↓
kafka
   ↓
springboot
```

---

# Key Takeaways

- Containers must communicate for CDC architectures to function.
- Docker networks allow containers to exchange data.
- Debezium environments commonly consist of several interconnected containers.
- Containers attached to the same network can communicate using container names.
- Networking simplifies deployment and management of distributed applications.
- Understanding Docker networking is essential for working with Debezium, Kafka, Spring Boot, and modern data engineering platforms.

---

# Personal Notes

- Container networking is the foundation that allows Debezium architectures to function.
- Debezium alone is not enough; supporting services must also communicate over a network.
- Using container names instead of IP addresses simplifies configuration.
- This concept is similar to how microservices communicate in Kubernetes and cloud environments.
- Understanding Docker networking is important for future work with Kafka, event streaming, CDC pipelines, and distributed data platforms.

---

# Completion Status

```text
✅ Completed
```