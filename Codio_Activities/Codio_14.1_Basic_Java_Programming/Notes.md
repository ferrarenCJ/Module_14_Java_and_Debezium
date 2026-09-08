# Codio 14.1: Basic Java Programming

## Objective

Learn the basic syntax and structure of a Java program, including variables, data types, classes, methods, and output statements.

---

# Java Overview

Java is a class-based, object-oriented programming language commonly used for:

- Enterprise Applications
- Web Applications
- Mobile Applications
- Data Engineering Platforms

Examples:

```text
Spring Boot
Apache Kafka
Debezium
Hadoop
Spark
```

---

# Java Program Structure

Basic template:

```java
public class Main {

    public static void main(String[] args) {

    }

}
```

Components:

### Class

```java
public class Main
```

Defines the blueprint for the application.

### Main Method

```java
public static void main(String[] args)
```

The entry point of a Java program.

---

# Variables

Variables store data.

Example:

```java
String firstName = "John";
```

```java
int age = 30;
```

```java
double salary = 65000.50;
```

---

# Common Data Types

## String

Stores text.

```java
String name = "John";
```

---

## int

Stores whole numbers.

```java
int age = 30;
```

---

## double

Stores decimal values.

```java
double salary = 65000.50;
```

---

## boolean

Stores true or false.

```java
boolean active = true;
```

---

## char

Stores a single character.

```java
char grade = 'A';
```

---

# Output Statements

Display information using:

```java
System.out.println();
```

Example:

```java
System.out.println("Hello World");
```

Output:

```text
Hello World
```

---

# String Concatenation

Combine text and variables.

Example:

```java
System.out.println("Name: " + firstName);
```

Output:

```text
Name: John
```

---

# Sample Output

```text
Employee Information
--------------------
First Name: John
Last Name: Doe
Age: 30
Salary: $65000.5
```

---

# Compilation

Compile:

```bash
javac Main.java
```

Run:

```bash
java Main
```

---

# Key Concepts Learned

- Java Class Structure
- Main Method
- Variables
- Data Types
- Strings
- Integer Values
- Decimal Values
- Console Output
- Program Execution

---

# Real-World Relevance

Java is widely used in data engineering and enterprise systems.

Examples:

```text
Spring Boot
Debezium
Apache Kafka
Apache Hadoop
Apache Spark
```

Many of the technologies introduced in Module 14 are built using Java.

---

# Key Takeaways

- Every Java application starts with a class.
- The main() method serves as the execution entry point.
- Variables store application data.
- Java provides multiple data types for different purposes.
- System.out.println() displays information to the console.
- Java is a foundational language for many data engineering technologies.

---

# Completion Status

```text
✅ Completed
```
``