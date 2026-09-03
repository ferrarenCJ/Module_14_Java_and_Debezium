# Video 14.3: Hello World! in Java

## Hello World! in Java

**Duration:** 2:54

---

# Overview

In this video, Dr. Sanchez demonstrates how to create and run the traditional "Hello World!" program in Java. The lesson introduces the basic structure of a Java program and explains several core concepts that form the foundation of Java development.

The "Hello World!" example is commonly used as a programmer's first application because it demonstrates the minimum components needed to create and execute a Java program.

---

# Learning Objectives

After completing this video, you should be able to:

- Create a basic Java program.
- Understand the structure of a Java class.
- Identify the purpose of the `main()` method.
- Compile Java source code.
- Execute a Java application.
- Display output to the console.

---

# Hello World Program

```java
public class HelloWorld {

    public static void main(String[] args) {

        System.out.println("Hello World!");

    }

}
```

---

# Program Breakdown

## Class Definition

```java
public class HelloWorld
```

### Explanation

- `public` makes the class accessible from anywhere.
- `class` defines a Java class.
- `HelloWorld` is the class name.

### Important Rule

The filename must match the class name:

```text
HelloWorld.java
```

---

## Main Method

```java
public static void main(String[] args)
```

### Purpose

The `main()` method is the entry point of a Java application.

When a Java program starts, execution begins here.

### Components

#### public

Allows the method to be accessed by the Java runtime.

#### static

Allows the method to be executed without creating an object.

#### void

Indicates that the method returns no value.

#### String[] args

Stores command-line arguments passed to the program.

---

## Output Statement

```java
System.out.println("Hello World!");
```

### Explanation

- `System` is a built-in Java class.
- `out` represents the standard output stream.
- `println()` prints text to the console and moves to a new line.

### Output

```text
Hello World!
```

---

# Creating the Program

Create a new Java file:

```bash
nano HelloWorld.java
```

Add the program code and save the file.

---

# Compiling the Program

Java source code must be compiled before execution.

Compile:

```bash
javac HelloWorld.java
```

This creates:

```text
HelloWorld.class
```

The `.class` file contains Java bytecode.

---

# Running the Program

Execute the compiled application:

```bash
java HelloWorld
```

Output:

```text
Hello World!
```

---

# Java Program Workflow

```text
Write Source Code
        ↓
Compile with javac
        ↓
Generate .class File
        ↓
Run with java
        ↓
Display Output
```

---

# Source Code vs Bytecode

## Source Code

Human-readable code written in:

```text
HelloWorld.java
```

Example:

```java
System.out.println("Hello World!");
```

---

## Bytecode

Generated after compilation:

```text
HelloWorld.class
```

Bytecode runs on the Java Virtual Machine (JVM).

---

# Java Virtual Machine (JVM)

The JVM allows Java programs to run on different operating systems.

Examples:

- Windows
- Linux
- macOS

This supports Java's famous principle:

```text
Write Once, Run Anywhere
```

---

# Key Terms

## Java

An object-oriented programming language used for enterprise, web, and data engineering applications.

## Class

A blueprint that defines properties and behaviors for objects.

## Method

A block of code that performs a specific task.

## Main Method

The starting point of a Java application.

## Compiler

Software that converts source code into bytecode.

## Bytecode

Platform-independent code executed by the JVM.

## JVM (Java Virtual Machine)

The runtime environment that executes Java bytecode.

---

# Key Takeaways

- Every Java application begins with a class.
- The `main()` method serves as the program entry point.
- Java code must be compiled before execution.
- `System.out.println()` displays output to the console.
- Compilation produces a `.class` file.
- The JVM enables Java applications to run on multiple operating systems.
- The "Hello World!" application demonstrates the basic structure of every Java program.

---

# Personal Notes

- Java requires more structure than Python for simple programs.
- The filename must match the class name exactly.
- Java follows a compile-then-run workflow.
- Understanding classes and methods will be important for upcoming Spring Boot lessons.
- The JVM is one of Java's biggest advantages because it allows applications to run across platforms.