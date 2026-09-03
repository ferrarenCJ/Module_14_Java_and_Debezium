# Self-Study Drag & Drop Activity 14.1: Data Types, Classes, Objects, and Packages in Java

## Learning Outcome Addressed

- Define elements of the Java programming language.

---

# Activity Result

✅ Completed Successfully

The activity focused on reinforcing the relationships between:

- Object-Oriented Programming
- Classes and Objects
- Java Compilation
- Packages
- Static Data Types
- Primitive Data Types
- Mathematical Operations and Type Precision

---

# Completed Answers

| Blank | Answer |
|---------|---------|
| 1 | object-oriented |
| 2 | functions |
| 3 | classes and objects |
| 4 | compiled |
| 5 | interpreted |
| 6 | packages |
| 7 | classes |
| 8 | object |
| 9 | static |
| 10 | cannot |
| 11 | initializing |
| 12 | booleans |
| 13 | one |
| 14 | longs and doubles |
| 15 | eight |
| 16 | mathematical operation |
| 17 | more precise |

---

# Completed Paragraph

Java is a(n) **object-oriented** programming language. This means instead of designing software around **functions**, Java utilizes **classes and objects** to structure the programming logic. Similar to C and C++, Java is also a(n) **compiled** programming language, making it faster to run than **interpreted** languages, such as Python.

In order to modularize code and make it more readable, programmers often use **packages** to import **classes** defined in other directories. Once this is imported, the programmer can instantiate a(n) **object** and use it throughout the code.

Java also has **static** data types, meaning that once memory is reserved for a specific variable, that space is attached to a data type and **cannot** be changed without **initializing** a new variable.

**Booleans** are the smallest data type in Java, with just **one** bit(s) of memory required per instance. On the other hand, **longs and doubles** are the largest data types, which each require **eight** byte(s) of memory.

When a(n) **mathematical operation** is performed, the result will always inherit the **more precise** data type from the parent variables used in the equation.

---

# Key Concepts Reinforced

## Object-Oriented Programming

Java is an object-oriented language that organizes programs using:

- Classes
- Objects
- Methods
- Attributes

---

## Compilation

Java source code is compiled into bytecode before execution.

```text
.java
  ↓
javac
  ↓
.class
  ↓
JVM
```

Java is therefore a compiled language, unlike Python which is typically interpreted.

---

## Packages

Packages provide:

- Code organization
- Modularity
- Reusability
- Namespace management

Example:

```java
import java.util.Scanner;
```

---

## Classes and Objects

A class serves as a blueprint.

Example:

```java
public class Car {
    String make;
}
```

An object is an instance of that class.

```java
Car myCar = new Car();
```

---

## Static Typing

Java uses static typing.

Example:

```java
int age = 35;
```

Once declared, a variable's type cannot change without creating a new variable.

---

## Primitive Data Types

Smallest:

```java
boolean
```

Storage:

```text
1 bit
```

Largest primitive types discussed:

```java
long
double
```

Storage:

```text
8 bytes
```

---

## Type Precision

When Java performs mathematical calculations, the result inherits the most precise data type involved.

Example:

```java
2 / 3
```

Output:

```text
0
```

Example:

```java
2.0 / 3
```

Output:

```text
0.6666667
```

Because `double` is more precise than `int`, the result becomes a `double`.

---

# Personal Notes

- Java emphasizes structure and strong typing.
- Packages help manage large applications.
- Classes define behavior and structure.
- Objects represent real instances of classes.
- Java compilation creates platform-independent bytecode.
- Mathematical operations inherit the most precise data type used in the expression.