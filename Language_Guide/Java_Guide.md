# The Complete Java Programming Guide

A detailed, structured reference to the Java programming language — from fundamentals to intermediate concepts.

---

## Table of Contents

1. [Introduction to Java](#1-introduction-to-java)
2. [Setting Up the Environment](#2-setting-up-the-environment)
3. [Basic Program Structure](#3-basic-program-structure)
4. [Variables and Data Types](#4-variables-and-data-types)
5. [Operators](#5-operators)
6. [Control Flow Statements](#6-control-flow-statements)
7. [Arrays](#7-arrays)
8. [Strings](#8-strings)
9. [Object-Oriented Programming](#9-object-oriented-programming)
10. [Exception Handling](#10-exception-handling)
11. [Collections Framework](#11-collections-framework)
12. [Generics](#12-generics)
13. [Lambda Expressions and Streams](#13-lambda-expressions-and-streams)
14. [Multithreading Basics](#14-multithreading-basics)
15. [File I/O](#15-file-io)
16. [Best Practices](#16-best-practices)

---

## 1. Introduction to Java

Java is a **class-based, object-oriented, statically typed** programming language created by Sun Microsystems (now owned by Oracle) and first released in 1995.

### Key Characteristics

| Feature | Description |
|---|---|
| Platform Independent | Compiles to bytecode that runs on the Java Virtual Machine (JVM) — "Write Once, Run Anywhere" |
| Object-Oriented | Everything (except primitives) is modeled as an object |
| Statically Typed | Variable types are checked at compile time |
| Automatic Memory Management | Garbage collection handles memory cleanup |
| Strongly Typed | Type mismatches are caught by the compiler |
| Multithreaded | Built-in support for concurrent programming |

### How Java Works

```
Source Code (.java) → Compiler (javac) → Bytecode (.class) → JVM → Machine Code
```

The compiler translates human-readable `.java` files into `.class` bytecode files. The JVM then interprets or JIT-compiles that bytecode for the underlying operating system, which is what makes Java portable across platforms.

---

## 2. Setting Up the Environment

To write and run Java programs you need:

1. **JDK (Java Development Kit)** — includes the compiler (`javac`), the runtime (`JRE`), and development tools.
2. **A text editor or IDE** — such as IntelliJ IDEA, Eclipse, VS Code, or NetBeans.

### Compiling and Running

```bash
# Compile
javac HelloWorld.java

# Run
java HelloWorld
```

Check your installed version with:

```bash
java -version
javac -version
```

---

## 3. Basic Program Structure

Every Java application starts execution from a `main` method inside a class.

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

### Breaking It Down

- `public class HelloWorld` — declares a class named `HelloWorld`. The file **must** be named `HelloWorld.java`.
- `public static void main(String[] args)` — the entry point of the program.
  - `public` — accessible from anywhere.
  - `static` — belongs to the class, not an instance.
  - `void` — returns nothing.
  - `String[] args` — command-line arguments.
- `System.out.println(...)` — prints text to the console followed by a newline.

### Comments

```java
// Single-line comment

/*
 * Multi-line
 * comment
 */

/**
 * Javadoc comment — used to generate documentation.
 * @param args command-line arguments
 */
```

---

## 4. Variables and Data Types

Java is statically typed, so every variable must have a declared type.

### Primitive Data Types

| Type | Size | Range / Notes | Example |
|---|---|---|---|
| `byte` | 8-bit | -128 to 127 | `byte b = 10;` |
| `short` | 16-bit | -32,768 to 32,767 | `short s = 1000;` |
| `int` | 32-bit | ~-2.1B to 2.1B | `int i = 42;` |
| `long` | 64-bit | Very large integers | `long l = 100000L;` |
| `float` | 32-bit | Single-precision decimal | `float f = 3.14f;` |
| `double` | 64-bit | Double-precision decimal | `double d = 3.14159;` |
| `char` | 16-bit | Single Unicode character | `char c = 'A';` |
| `boolean` | 1-bit (JVM dependent) | `true` or `false` | `boolean flag = true;` |

### Reference Types

Everything that isn't primitive — `String`, arrays, and objects of any class — is a reference type, stored on the heap and accessed via a reference.

```java
String name = "Alice";
int[] numbers = {1, 2, 3};
```

### Variable Declaration

```java
int age = 25;
final double PI = 3.14159; // final = constant, cannot be reassigned
var count = 10; // type inference (Java 10+), inferred as int
```

### Type Casting

```java
// Widening (implicit) — smaller to larger type
int myInt = 9;
double myDouble = myInt; // 9.0

// Narrowing (explicit) — larger to smaller type, needs a cast
double d = 9.78;
int i = (int) d; // 9 (decimal truncated)
```

---

## 5. Operators

### Arithmetic

```java
int a = 10, b = 3;
System.out.println(a + b); // 13
System.out.println(a - b); // 7
System.out.println(a * b); // 30
System.out.println(a / b); // 3  (integer division)
System.out.println(a % b); // 1  (modulus)
```

### Relational and Logical

```java
a == b   // equal to
a != b   // not equal to
a > b    // greater than
a < b    // less than
a && b   // logical AND
a || b   // logical OR
!a       // logical NOT
```

### Assignment Shortcuts

```java
int x = 5;
x += 3; // x = x + 3
x -= 2; // x = x - 2
x *= 4; // x = x * 4
x /= 2; // x = x / 2
x++;    // increment
x--;    // decrement
```

### Ternary Operator

```java
int max = (a > b) ? a : b;
```

---

## 6. Control Flow Statements

### if / else if / else

```java
int score = 85;

if (score >= 90) {
    System.out.println("Grade: A");
} else if (score >= 75) {
    System.out.println("Grade: B");
} else {
    System.out.println("Grade: C");
}
```

### switch

```java
int day = 3;
String dayName;

switch (day) {
    case 1 -> dayName = "Monday";
    case 2 -> dayName = "Tuesday";
    case 3 -> dayName = "Wednesday";
    default -> dayName = "Unknown";
}
System.out.println(dayName);
```

> The arrow syntax (`->`) is the modern switch expression style (Java 14+). The traditional form uses `case 1: ... break;`.

### Loops

```java
// for loop
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}

// while loop
int i = 0;
while (i < 5) {
    System.out.println(i);
    i++;
}

// do-while loop (executes at least once)
int j = 0;
do {
    System.out.println(j);
    j++;
} while (j < 5);

// enhanced for loop (for-each)
int[] nums = {1, 2, 3};
for (int n : nums) {
    System.out.println(n);
}
```

### break and continue

```java
for (int i = 0; i < 10; i++) {
    if (i == 5) break;    // exits the loop entirely
    if (i % 2 == 0) continue; // skips to next iteration
    System.out.println(i);
}
```

---

## 7. Arrays

Arrays hold a fixed-size, ordered collection of elements of the same type.

```java
// Declaration and initialization
int[] numbers = new int[5];         // default values: 0
int[] values = {10, 20, 30, 40};    // initialized directly

// Accessing and modifying
numbers[0] = 100;
System.out.println(values[2]); // 30

// Length
System.out.println(values.length); // 4

// Multi-dimensional arrays
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6}
};
System.out.println(matrix[1][2]); // 6
```

### Iterating Arrays

```java
for (int i = 0; i < values.length; i++) {
    System.out.println(values[i]);
}

// Using Arrays utility class
import java.util.Arrays;
System.out.println(Arrays.toString(values));
```

---

## 8. Strings

`String` is an immutable reference type in Java — once created, its content cannot change.

```java
String greeting = "Hello";
String name = "World";

// Concatenation
String message = greeting + ", " + name + "!";

// Common methods
message.length();            // length of string
message.toUpperCase();       // "HELLO, WORLD!"
message.toLowerCase();       // "hello, world!"
message.contains("World");   // true
message.replace("Hello", "Hi");
message.substring(0, 5);     // "Hello"
message.trim();              // removes leading/trailing whitespace
message.split(",");          // splits into a String[]
message.equals("Hello");     // content comparison (never use == for Strings)
```

### StringBuilder (Mutable Strings)

Since `String` is immutable, repeated concatenation in a loop is inefficient. Use `StringBuilder` instead:

```java
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 5; i++) {
    sb.append(i).append(", ");
}
System.out.println(sb.toString());
```

---

## 9. Object-Oriented Programming

Java is built around four core OOP principles: **Encapsulation, Inheritance, Polymorphism, and Abstraction.**

### 9.1 Classes and Objects

```java
public class Car {
    // Fields (state)
    private String model;
    private int year;

    // Constructor
    public Car(String model, int year) {
        this.model = model;
        this.year = year;
    }

    // Method (behavior)
    public void displayInfo() {
        System.out.println(year + " " + model);
    }
}

// Creating and using an object
Car myCar = new Car("Tesla Model 3", 2024);
myCar.displayInfo(); // 2024 Tesla Model 3
```

### 9.2 Encapsulation

Encapsulation hides internal state behind getters/setters, protecting data integrity.

```java
public class BankAccount {
    private double balance;

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }
}
```

### 9.3 Inheritance

Inheritance lets a class (subclass) acquire fields and methods from another class (superclass) using `extends`.

```java
public class Animal {
    public void eat() {
        System.out.println("This animal eats food.");
    }
}

public class Dog extends Animal {
    public void bark() {
        System.out.println("The dog barks.");
    }
}

Dog d = new Dog();
d.eat();  // inherited from Animal
d.bark(); // defined in Dog
```

### 9.4 Polymorphism

**Method Overriding** (runtime polymorphism) — a subclass provides its own implementation of a method:

```java
public class Animal {
    public void makeSound() {
        System.out.println("Some generic sound");
    }
}

public class Cat extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Meow");
    }
}

Animal a = new Cat();
a.makeSound(); // "Meow" — determined at runtime
```

**Method Overloading** (compile-time polymorphism) — multiple methods with the same name but different parameters:

```java
public int add(int a, int b) { return a + b; }
public double add(double a, double b) { return a + b; }
public int add(int a, int b, int c) { return a + b + c; }
```

### 9.5 Abstraction

**Abstract classes** can contain both implemented and unimplemented (abstract) methods, and cannot be instantiated directly.

```java
public abstract class Shape {
    abstract double area(); // no body — must be implemented by subclasses

    public void describe() {
        System.out.println("This shape has an area of " + area());
    }
}

public class Circle extends Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    double area() {
        return Math.PI * radius * radius;
    }
}
```

**Interfaces** define a contract of methods a class must implement, supporting multiple inheritance of behavior.

```java
public interface Drivable {
    void drive();
    default void honk() { // default method with a body
        System.out.println("Beep!");
    }
}

public class Truck implements Drivable {
    @Override
    public void drive() {
        System.out.println("The truck is driving.");
    }
}
```

### 9.6 Access Modifiers

| Modifier | Class | Package | Subclass | World |
|---|---|---|---|---|
| `public` | ✅ | ✅ | ✅ | ✅ |
| `protected` | ✅ | ✅ | ✅ | ❌ |
| (default/none) | ✅ | ✅ | ❌ | ❌ |
| `private` | ✅ | ❌ | ❌ | ❌ |

### 9.7 static and final

```java
public class Counter {
    static int count = 0; // shared across all instances

    static void increment() {
        count++;
    }
}

final int MAX_USERS = 100; // cannot be reassigned
```

---

## 10. Exception Handling

Java uses `try-catch-finally` blocks to handle runtime errors gracefully.

```java
try {
    int result = 10 / 0; // throws ArithmeticException
} catch (ArithmeticException e) {
    System.out.println("Error: " + e.getMessage());
} finally {
    System.out.println("This always runs.");
}
```

### Multiple Catch Blocks

```java
try {
    int[] arr = new int[5];
    arr[10] = 1; // ArrayIndexOutOfBoundsException
} catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Array error: " + e.getMessage());
} catch (Exception e) {
    System.out.println("General error: " + e.getMessage());
}
```

### Checked vs Unchecked Exceptions

- **Checked exceptions** (e.g., `IOException`) must be either caught or declared with `throws`.
- **Unchecked exceptions** (e.g., `NullPointerException`, `ArithmeticException`) extend `RuntimeException` and aren't required to be caught.

### Custom Exceptions

```java
public class InsufficientFundsException extends Exception {
    public InsufficientFundsException(String message) {
        super(message);
    }
}

public void withdraw(double amount) throws InsufficientFundsException {
    if (amount > balance) {
        throw new InsufficientFundsException("Not enough funds.");
    }
}
```

### try-with-resources

Automatically closes resources (like file streams) after use:

```java
try (BufferedReader reader = new BufferedReader(new FileReader("file.txt"))) {
    System.out.println(reader.readLine());
} catch (IOException e) {
    e.printStackTrace();
}
```

---

## 11. Collections Framework

The Collections Framework provides ready-made data structures for storing and manipulating groups of objects.

### Overview

| Interface | Common Implementations | Characteristics |
|---|---|---|
| `List` | `ArrayList`, `LinkedList` | Ordered, allows duplicates |
| `Set` | `HashSet`, `TreeSet`, `LinkedHashSet` | No duplicates |
| `Map` | `HashMap`, `TreeMap`, `LinkedHashMap` | Key-value pairs |
| `Queue` | `LinkedList`, `PriorityQueue` | FIFO ordering |

### List

```java
import java.util.ArrayList;
import java.util.List;

List<String> fruits = new ArrayList<>();
fruits.add("Apple");
fruits.add("Banana");
fruits.remove("Apple");
System.out.println(fruits.get(0)); // Banana
System.out.println(fruits.size()); // 1
```

### Set

```java
import java.util.HashSet;
import java.util.Set;

Set<Integer> uniqueNumbers = new HashSet<>();
uniqueNumbers.add(1);
uniqueNumbers.add(2);
uniqueNumbers.add(1); // ignored, duplicate
System.out.println(uniqueNumbers.size()); // 2
```

### Map

```java
import java.util.HashMap;
import java.util.Map;

Map<String, Integer> ages = new HashMap<>();
ages.put("Alice", 30);
ages.put("Bob", 25);

System.out.println(ages.get("Alice")); // 30

for (Map.Entry<String, Integer> entry : ages.entrySet()) {
    System.out.println(entry.getKey() + " is " + entry.getValue());
}
```

### Iterating Collections

```java
for (String fruit : fruits) {
    System.out.println(fruit);
}

// Using an Iterator
Iterator<String> it = fruits.iterator();
while (it.hasNext()) {
    System.out.println(it.next());
}
```

---

## 12. Generics

Generics allow classes, interfaces, and methods to operate on types specified by the caller, enabling type safety without code duplication.

```java
// Generic class
public class Box<T> {
    private T content;

    public void set(T content) {
        this.content = content;
    }

    public T get() {
        return content;
    }
}

Box<String> stringBox = new Box<>();
stringBox.set("Hello");
String value = stringBox.get(); // no casting needed
```

### Generic Methods

```java
public static <T> void printArray(T[] array) {
    for (T item : array) {
        System.out.println(item);
    }
}
```

### Bounded Type Parameters

```java
public static <T extends Number> double sum(T[] numbers) {
    double total = 0;
    for (T num : numbers) {
        total += num.doubleValue();
    }
    return total;
}
```

---

## 13. Lambda Expressions and Streams

Introduced in Java 8, lambdas and streams enable a functional programming style.

### Lambda Expressions

A lambda provides a concise way to implement a functional interface (an interface with a single abstract method).

```java
// Traditional anonymous class
Runnable r1 = new Runnable() {
    @Override
    public void run() {
        System.out.println("Running...");
    }
};

// Equivalent lambda
Runnable r2 = () -> System.out.println("Running...");

// Lambda with parameters
Comparator<Integer> comparator = (a, b) -> a - b;
```

### Streams

Streams process sequences of elements with a pipeline of operations (filter, map, reduce, etc.).

```java
import java.util.List;
import java.util.stream.Collectors;

List<Integer> numbers = List.of(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

List<Integer> evenSquares = numbers.stream()
    .filter(n -> n % 2 == 0)      // keep even numbers
    .map(n -> n * n)              // square them
    .collect(Collectors.toList()); // collect into a list

System.out.println(evenSquares); // [4, 16, 36, 64, 100]

// Sum using reduce
int sum = numbers.stream().reduce(0, Integer::sum);

// forEach
numbers.stream().forEach(System.out::println);
```

---

## 14. Multithreading Basics

Java has built-in support for concurrent execution via threads.

### Creating Threads

```java
// Extending Thread
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running: " + Thread.currentThread().getName());
    }
}

MyThread t1 = new MyThread();
t1.start(); // never call run() directly — use start()

// Implementing Runnable (preferred)
Runnable task = () -> System.out.println("Task running");
Thread t2 = new Thread(task);
t2.start();
```

### Synchronization

Prevents race conditions when multiple threads access shared resources.

```java
public class Counter {
    private int count = 0;

    public synchronized void increment() {
        count++;
    }
}
```

### ExecutorService (Modern Approach)

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

ExecutorService executor = Executors.newFixedThreadPool(2);
executor.submit(() -> System.out.println("Task 1"));
executor.submit(() -> System.out.println("Task 2"));
executor.shutdown();
```

---

## 15. File I/O

Java's `java.io` and `java.nio.file` packages handle reading and writing files.

### Writing to a File

```java
import java.io.FileWriter;
import java.io.IOException;

try (FileWriter writer = new FileWriter("output.txt")) {
    writer.write("Hello, file!");
} catch (IOException e) {
    e.printStackTrace();
}
```

### Reading from a File

```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

try (BufferedReader reader = new BufferedReader(new FileReader("output.txt"))) {
    String line;
    while ((line = reader.readLine()) != null) {
        System.out.println(line);
    }
} catch (IOException e) {
    e.printStackTrace();
}
```

### Using java.nio.file (Modern Approach)

```java
import java.nio.file.*;
import java.util.List;

// Write
Files.write(Paths.get("output.txt"), "Hello NIO".getBytes());

// Read
List<String> lines = Files.readAllLines(Paths.get("output.txt"));
lines.forEach(System.out::println);
```

---

## 16. Best Practices

- **Follow naming conventions**: `PascalCase` for classes, `camelCase` for methods/variables, `UPPER_SNAKE_CASE` for constants.
- **Favor composition over inheritance** where possible to reduce coupling.
- **Always close resources** — prefer try-with-resources over manual `close()` calls.
- **Program to interfaces**, not implementations (e.g., `List<String> list = new ArrayList<>();`).
- **Avoid catching generic `Exception`** unless truly necessary — catch specific exceptions.
- **Use `equals()` and `hashCode()` together** when overriding one for custom objects.
- **Prefer immutability** for objects that don't need to change after creation.
- **Use `StringBuilder`** for heavy string concatenation instead of `+` in loops.
- **Write unit tests** (e.g., with JUnit) to verify behavior as your codebase grows.
- **Keep methods short and focused** — each method should do one thing well.

---

## Next Steps

Once comfortable with these fundamentals, consider exploring:

- **Java Records** (Java 16+) for concise immutable data carriers
- **Sealed classes** (Java 17+) for restricted class hierarchies
- **Spring Framework** for building enterprise and web applications
- **Maven or Gradle** for dependency management and build automation
- **JUnit** for unit testing
- **JDBC** for database connectivity

---

*This guide covers Java's core fundamentals and is a solid foundation for building real-world applications. Practice by writing small programs for each concept before combining them into larger projects.*
