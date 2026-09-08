# Java Cheat Sheet

## What is Java?

Java is a class-based, object-oriented programming language commonly used for enterprise applications, web development, mobile applications, and data engineering tools.

Benefits:

- Platform Independent
- Object-Oriented
- Secure
- Scalable
- Strong Community Support

---

# Basic Java Program

```java
public class HelloWorld {

    public static void main(String[] args) {
        System.out.println("Hello World");
    }

}
```

---

# Java Data Types

## Whole Numbers

| Type | Size | Example |
|--------|--------|--------|
| byte | 1 byte | 127 |
| short | 2 bytes | 32000 |
| int | 4 bytes | 100 |
| long | 8 bytes | 100000L |

### Example

```java
int age = 30;
long population = 8000000000L;
```

---

## Decimal Numbers

| Type | Size |
|--------|--------|
| float | 4 bytes |
| double | 8 bytes |

```java
double salary = 55000.75;
```

---

## Character

```java
char grade = 'A';
```

---

## Boolean

```java
boolean active = true;
```

---

## String

```java
String name = "John";
```

---

# Variables

```java
String employeeName = "John Doe";
int employeeId = 1001;
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

Example:

```java
if(age > 18)
```

---

## Logical

```java
&&
||
!
```

---

# If Statement

```java
if(age >= 18) {
    System.out.println("Adult");
}
```

---

# If Else

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
for(int i=1; i<=5; i++) {
    System.out.println(i);
}
```

---

## While Loop

```java
while(counter < 5) {
    counter++;
}
```

---

# Arrays

```java
String[] names = {"John","Mary","Mike"};
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
int total = add(5,10);
```

---

# Classes

A class is a blueprint for objects.

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

Assign values:

```java
emp.id = 1;
emp.firstName = "John";
```

---

# Constructors

```java
public Employee(int id, String name) {
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

# Access Modifiers

```java
public
private
protected
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

# Compile and Run

Compile:

```bash
javac HelloWorld.java
```

Run:

```bash
java HelloWorld
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

---

# Module 14 Takeaway

Java provides the foundation used by Spring Boot and Debezium applications throughout Module 14.