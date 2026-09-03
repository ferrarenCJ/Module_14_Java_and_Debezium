# Video 14.5: Classes and Objects in Java

## Overview

Classes and objects are fundamental concepts in Object-Oriented Programming (OOP) and form the foundation of Java.

A class acts as a blueprint, while an object is an instance created from that blueprint.

---

# Class

A class defines:

- Attributes (data)
- Methods (behavior)

Example:

```java
public class Car {

    String make;
    String model;

}
```

---

# Object

An object is a specific instance of a class.

Example:

```java
Car myCar = new Car();
```

---

# Creating a Class

```java
public class Student {

    String name;
    int age;

}
```

---

# Creating an Object

```java
Student student1 = new Student();

student1.name = "Cliff";
student1.age = 35;
```

---

# Accessing Object Properties

```java
System.out.println(student1.name);
System.out.println(student1.age);
```

Output:

```text
Cliff
35
```

---

# Complete Example

```java
public class Student {

    String name;
    int age;

    public static void main(String[] args) {

        Student student1 = new Student();

        student1.name = "Cliff";
        student1.age = 35;

        System.out.println(student1.name);
        System.out.println(student1.age);
    }

}
```

---

# Why Classes Matter

Classes help:

- Organize code
- Promote reusability
- Support object-oriented design
- Reduce complexity

---

# Class vs Object

| Class | Object |
|---------|---------|
| Blueprint | Instance |
| Defines structure | Contains actual values |
| Template | Real implementation |

### Example

```text
Class = Car

Object 1 = Toyota Camry
Object 2 = Honda Accord
Object 3 = Ford F-150
```

---

# Key Takeaways

- Classes define structure.
- Objects represent real-world entities.
- Multiple objects can be created from a single class.
- Java is built around object-oriented principles.