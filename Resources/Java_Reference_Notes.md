# Java Reference Notes

## Overview

Java is a class-based, object-oriented programming language widely used for enterprise applications, web services, cloud platforms, and data engineering tools.

Examples:

```text
Spring Boot
Apache Kafka
Debezium
Apache Hadoop
Apache Spark
```

---

# Java Architecture

```text
Java Source Code
        ↓
     Compiler
        ↓
     Bytecode
        ↓
Java Virtual Machine (JVM)
        ↓
   Program Output
```

---

# Java Program Structure

```java
public class Main {

    public static void main(String[] args) {

        System.out.println("Hello World");

    }

}
```

---

# Data Types

## Integer Types

### byte

```java
byte num = 100;
```

Range:

```text
-128 to 127
```

Storage:

```text
1 byte
```

---

### short

```java
short num = 32000;
```

Storage:

```text
2 bytes
```

---

### int

```java
int age = 30;
```

Storage:

```text
4 bytes
```

---

### long

```java
long population = 9000000000L;
```

Storage:

```text
8 bytes
```

---

## Decimal Types

### float

```java
float price = 12.99f;
```

---

### double

```java
double salary = 85000.50;
```

Storage:

```text
8 bytes
```

---

## Character Type

```java
char grade = 'A';
```

Examples:

```text
A
4
#
```

---

## Boolean

```java
boolean active = true;
```

Values:

```text
true
false
```

---

## String

```java
String name = "John Doe";
```

---

# Variables

```java
String firstName = "John";
int age = 30;
double salary = 65000.50;
```

---

# Operators

## Arithmetic

```java
+
-
*
/
%
```

Example:

```java
int total = 10 + 5;
```

---

## Comparison

```java
==
!=
>
<
>=
<=
```

---

## Logical

```java
&&
||
!
```

---

# Conditional Statements

## If Statement

```java
if(age >= 18) {
    System.out.println("Adult");
}
```

---

## If Else

```java
if(score >= 70) {
    System.out.println("Pass");
}
else {
    System.out.println("Fail");
}
```

---

# Loops

## For Loop

```java
for(int i = 0; i < 5; i++) {

    System.out.println(i);

}
```

---

## While Loop

```java
while(counter < 10) {

    counter++;

}
```

---

# Arrays

```java
String[] names = {
    "John",
    "Mary",
    "Mike"
};
```

Access:

```java
names[0]
```

---

# Methods

```java
public static int add(int a, int b) {

    return a + b;

}
```

Usage:

```java
add(5,10);
```

---

# Classes

A class is a blueprint for creating objects.

```java
public class Employee {

    int id;
    String firstName;

}
```

---

# Objects

```java
Employee emp = new Employee();
```

---

# Constructors

```java
public Employee(
    int id,
    String name
) {

    this.id = id;
    this.name = name;

}
```

---

# Packages

```java
package com.company.project;
```

Import:

```java
import java.util.ArrayList;
```

---

# Exception Handling

```java
try {

    int x = 10 / 0;

}
catch(Exception e) {

    System.out.println(e.getMessage());

}
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

# Key Terms

- Class
- Object
- Method
- Constructor
- Package
- Compiler
- Variable
- Exception
- 