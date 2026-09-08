# Module 14: Glossary

## Binlog
MySQL binary log that records changes to database schemas and tables. Debezium reads binlogs to capture database changes for Change Data Capture (CDC).

---

## Buffer
Temporary storage area in computer memory used to hold data for a short period of time during processing.

---

## Byte
A Java data type that stores whole numbers using one byte of memory.

**Range:**

```text
-128 to 127
```

---

## Char (Character)
A Java data type used to store a single character such as a letter, number, or symbol.

**Examples:**

```text
A
4
#
```

---

## Compiler
A program that translates high-level programming code into machine-readable code.

In Java, the compiler converts Java source code into bytecode that can be executed by the Java Virtual Machine (JVM).

---

## Connectors
Processes that move data between systems and databases.

In Debezium, connectors capture database changes from supported databases such as MySQL, PostgreSQL, and MongoDB.

---

## Debezium
An open-source distributed platform for Change Data Capture (CDC).

Debezium monitors database changes such as:

```text
INSERT
UPDATE
DELETE
```

and streams those events to applications.

---

## Double
A Java data type used to store decimal values with high precision.

**Storage:**

```text
8 bytes
```

---

## Filters
A Debezium capability that allows specific rows or datasets to be selected for processing.

Benefits include:

- Reduced processing volume
- Improved performance
- Focused data capture

---

## Java
A class-based, object-oriented programming language commonly used for enterprise applications, web applications, and backend development.

Key features:

- Platform independent
- Object-oriented
- Strongly typed
- Widely used in data engineering tools

---

## Java Classes
Blueprints used to create objects.

Classes define:

- Variables
- Constructors
- Methods
- Behaviors

Example:

```java
public class Employee {
}
```

---

## Java Objects
Instances of classes.

Example:

```java
Employee emp = new Employee();
```

Objects contain actual data and behaviors defined by a class.

---

## Java Packages
Collections of related classes and interfaces that provide organization and modularity within Java applications.

Example:

```java
com.company.project
```

---

## Long
A Java data type used to store large whole numbers.

**Storage:**

```text
8 bytes
```

**Range:**

```text
-9,223,372,036,854,775,808
to
9,223,372,036,854,775,807
```

---

## Masking
A Debezium capability used to hide sensitive information.

Common examples:

```text
Passwords
Credit Card Numbers
Personal Information
```

---

## Modularity
The ability to organize software into reusable components.

Java modules and packages support modularity by allowing code to be reused across applications.

---

## Monitoring
A Debezium capability that provides visibility into connector performance and activity.

Benefits include:

- Health monitoring
- Troubleshooting
- Performance tracking

---

## Nano Text Editor
A command-line text editor used on Linux and Unix systems.

Common operations:

```text
Ctrl + O  Save
Ctrl + X  Exit
Ctrl + W  Search
```

Used in the module to edit:

```text
DebeziumConnectorConfig.java
```

---

## Short
A Java data type used to store small whole numbers.

**Storage:**

```text
2 bytes
```

**Range:**

```text
-32,768 to 32,767
```

---

## Snapshot
A Debezium mechanism used to capture the initial state of a database.

Snapshots are commonly used:

- During application startup
- During recovery operations
- When new tables are added

Example:

```text
John Doe
```

captured before streaming begins.

---

## Spring Boot
A popular Java framework used for building web and enterprise applications.

Benefits:

- Embedded web server
- Auto-configuration
- Dependency management
- Simplified deployment

Common startup command:

```bash
mvn spring-boot:run
```

---

## Streams
Continuous flows of events or data.

In Debezium, database changes are streamed as events, allowing applications to process updates in near real time.

Benefits:

- Faster processing
- Reduced database polling
- Improved scalability

---

# Key Terms for Module 14

```text
Java
Spring Boot
Docker
CDC
Debezium
Connectors
Snapshots
Binlogs
Streams
Monitoring
Masking
Filters
Packages
Classes
Objects
```

---

# Key Takeaways

- Java provides the application framework used throughout the module.
- Spring Boot simplifies Java application development.
- Debezium enables Change Data Capture (CDC).
- MySQL binlogs provide the source of database change events.
- Connectors allow Debezium to work with multiple databases.
- Snapshots establish an initial state before streaming begins.
- Streams enable near real-time event processing.
- CDC is a foundational concept in modern data engineering architectures.