# Required Codio Activity 14.1: Basic Java Programming

## Learning Outcome

- Write basic Java code.

---

# Activity Overview

This Codio activity focused on fundamental Java programming concepts, including:

- Printing output to the console
- Data type casting
- Arrays
- For loops
- User input
- Conditional logic

---

# Question 1: Printing to Screen

## Objective

Print the following string:

```text
This is a data engineering course.
```

## Solution

```java
public class Q1{
    public static void main(String args[]){

        System.out.println("This is a data engineering course.");

    }
}
```

## Concepts

- Java program structure
- `main()` method
- `System.out.println()`

---

# Question 2: Casting Data Types in Java, Part 1

## Objective

- Create integer `var1a`
- Assign value `15`
- Cast to a `double`
- Store result in `var1b`
- Print both variables

## Solution

```java
public class Q2{
    public static void main(String args[]){

        int var1a = 15;
        double var1b = var1a;

        System.out.println(var1a);
        System.out.println(var1b);

    }
}
```

## Output

```text
15
15.0
```

## Concepts

- Integer data type
- Double data type
- Implicit casting

---

# Question 3: Casting Data Types in Java, Part 2

## Objective

- Create String `var2a`
- Assign value `"000"`
- Convert to integer
- Store in `var2b`
- Print both variables

## Solution

```java
public class Q3{
    public static void main(String args[]){

        String var2a = "000";
        int var2b = Integer.valueOf(var2a);

        System.out.println(var2a);
        System.out.println(var2b);

    }
}
```

## Output

```text
000
0
```

## Concepts

- String data type
- Integer conversion
- `Integer.valueOf()`

---

# For Loops in Java, Part 1

## Objective

Iterate through an array and print each element.

## Solution

```java
public class Demo{
    public static void main(String args[]){

        int[] numbers = {1, 2, 3, 4};

        for(int i = 0; i < numbers.length; i++) {
            System.out.println(numbers[i]);
        }

    }
}
```

## Output

```text
1
2
3
4
```

## Concepts

- Arrays
- For loops
- Array indexing
- `length` property

---

# Question 4: For Loops in Java, Part 2

## Objective

Loop through an animal array and print formatted output.

## Solution

```java
String[] animals = {"cat", "dog", "fish", "rabbit"};

for(int i = 0; i < animals.length; i++) {
    System.out.println("Animal #" + i + " is a " + animals[i]);
}
```

## Output

```text
Animal #0 is a cat
Animal #1 is a dog
Animal #2 is a fish
Animal #3 is a rabbit
```

## Concepts

- String arrays
- Concatenation
- Iteration
- Loop counters

---

# Question 5: User Input

## Objective

- Accept user input
- If input is an integer:
  - Multiply by 4
- Otherwise:
  - Print an error message

## Solution

```java
import java.util.Scanner;

public class Q5{
    public static void main(String args[]){

        Scanner input = new Scanner(System.in);

        if(input.hasNextInt()) {
            int num = input.nextInt();
            System.out.println(num * 4);
        }
        else {
            System.out.println("Please enter an integer");
        }

    }
}
```

## Example Outputs

### Integer Input

Input:

```text
2
```

Output:

```text
8
```

### Non-Integer Input

Input:

```text
hello
```

Output:

```text
Please enter an integer
```

## Concepts

- Scanner
- User input validation
- `hasNextInt()`
- `nextInt()`
- Conditional logic (`if/else`)

---

# Key Java Concepts Learned

## Output

```java
System.out.println();
```

## Integer to Double Casting

```java
double value = integerValue;
```

## String to Integer Conversion

```java
Integer.valueOf(stringValue);
```

## Arrays

```java
int[] numbers = {1, 2, 3, 4};
```

## For Loops

```java
for(int i = 0; i < array.length; i++)
```

## User Input

```java
Scanner input = new Scanner(System.in);
```

## Conditional Logic

```java
if(...)
{
}
else
{
}
```

---

# Challenges Encountered

- Question 5 autograder produced shell-script errors.
- Java code executed correctly.
- Manual testing confirmed:
  - Integer inputs were multiplied by 4.
  - Non-integer inputs displayed the correct error message.
- The grading issue appeared to originate from the Codio autograder