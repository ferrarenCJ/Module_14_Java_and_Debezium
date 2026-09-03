# Video 14.4: Data Types in Java

## Overview

Data types define the kind of values that can be stored in variables within a Java program.

Java is a strongly typed language, meaning every variable must have a declared data type before it can be used.

---

# Primitive Data Types

Java provides eight primitive data types.

## Boolean

Stores true or false values.

```java
boolean isActive = true;
```

---

## Byte

Stores small integer values.

```java
byte age = 25;
```

Range:

```text
-128 to 127
```

---

## Short

Stores larger integers than byte.

```java
short population = 32000;
```

---

## Int

Most commonly used integer type.

```java
int salary = 50000;
```

---

## Long

Stores very large integers.

```java
long distance = 999999999L;
```

---

## Float

Stores decimal values with single precision.

```java
float temperature = 72.5f;
```

---

## Double

Stores decimal values with double precision.

```java
double pi = 3.14159;
```

---

## Char

Stores a single character.

```java
char grade = 'A';
```

---

# Example

```java
public class DataTypes {

    public static void main(String[] args) {

        boolean active = true;
        int age = 30;
        double salary = 50000.50;
        char grade = 'A';

        System.out.println(active);
        System.out.println(age);
        System.out.println(salary);
        System.out.println(grade);

    }

}
```

---

# Key Takeaways

- Java requires explicit data types.
- Primitive types improve performance and memory usage.
- Choosing the correct data type is important.
- Double is commonly used for decimal values.
- Int is the standard integer type.
