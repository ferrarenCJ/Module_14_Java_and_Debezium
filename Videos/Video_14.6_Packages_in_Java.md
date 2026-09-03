# Video 14.6: Packages in Java

## Overview

Packages are used to organize related Java classes and interfaces.

Packages make large applications easier to manage and reduce code complexity.

---

# Why Use Packages?

Packages help:

- Organize code
- Improve maintainability
- Prevent naming conflicts
- Encourage modular design

---

# Example Package Structure

```text
com.company.app

├── Employee.java
├── Customer.java
└── Main.java
```

---

# Creating a Package

At the top of a Java file:

```java
package com.company.app;
```

---

# Example

```java
package com.company.app;

public class Employee {

    String employeeName;

}
```

---

# Importing Packages

Use the import statement to access classes from another package.

```java
import java.util.Scanner;
```

---

# Example Program

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

    }

}
```

---

# Package Naming Conventions

Package names typically use:

```text
company.project.module
```

Examples:

```text
com.microsoft.azure
com.amazon.aws
edu.mit.dataengineering
```

---

# Java Standard Library Packages

Frequently used packages include:

```java
java.util
java.io
java.lang
java.net
```

Examples:

### Utility Classes

```java
import java.util.ArrayList;
```

### Input/Output

```java
import java.io.File;
```

### Networking

```java
import java.net.URL;
```

---

# Benefits of Packages

- Better organization
- Easier maintenance
- Improved readability
- Reduced duplication
- Easier collaboration among developers

---

# Real-World Example

```text
Package:
com.company.hr

Classes:
Employee
Manager
Department
Payroll
```

This structure keeps related functionality together.

---

# Key Takeaways

- Packages organize related classes.
- Packages create a modular design.
- Import statements allow classes to be reused.
- Package structures become essential as projects grow.
- Most enterprise Java applications use extensive package hierarchies.