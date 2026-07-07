# Java Interview Questions: Variables & Data Types

## Level 1 (Basic)

### 1. What is a variable in Java?

A variable is a named memory location used to store data. Every variable
has a data type that determines what kind of value it can store.

**Example:**

``` java
int age = 25;
```

### What are primitive data types in Java?

**Expected Answer:**

Primitive data types are the **basic built-in data types** provided by Java. They store the **actual value directly in memory** rather than a reference to an object.

Java has **8 primitive data types**.

| Data Type | Size | Default Value | Example |
|-----------|------|---------------|---------|
| `byte` | 1 byte | `0` | `byte age = 25;` |
| `short` | 2 bytes | `0` | `short marks = 1000;` |
| `int` | 4 bytes | `0` | `int salary = 50000;` |
| `long` | 8 bytes | `0L` | `long population = 8000000000L;` |
| `float` | 4 bytes | `0.0f` | `float price = 10.5f;` |
| `double` | 8 bytes | `0.0` | `double pi = 3.14159;` |
| `char` | 2 bytes | `'\u0000'` | `char grade = 'A';` |
| `boolean` | JVM-dependent | `false` | `boolean isActive = true;` |

### Characteristics of Primitive Data Types

- Store the actual value directly.
- Have a fixed size (except `boolean`, whose representation is JVM-dependent).
- Are predefined by Java.
- Cannot be `null`.
- Do not have methods or fields.
- Generally provide better performance than reference types.

### Example

```java
int age = 25;
double salary = 55000.75;
char grade = 'A';
boolean isStudent = true;
```

### Interview Follow-up

**Q:** Why are primitive data types faster than non-primitive data types?

**Answer:**

Primitive data types store values directly in memory and do not require object creation or dereferencing. This makes them more memory-efficient and generally faster to access than reference types.

### Interview Tip

A strong interview answer is:

> "Primitive data types are Java's built-in data types that store actual values directly in memory. Java provides eight primitive types: `byte`, `short`, `int`, `long`, `float`, `double`, `char`, and `boolean`. They are fixed in size, cannot be `null`, and do not have methods because they are not objects."

### 3. What are the non-primitive data types in Java?

**Expected Answer:**

Non-primitive data types are also known as **reference types**. They do not store the actual value directly; instead, they store a reference (memory address) to the object.

Unlike primitive data types, non-primitive types:
- Can store `null`
- Have methods and fields
- Are created from classes, interfaces, arrays, or enums
- Their size is not fixed

**Examples of non-primitive data types:**

```java
String name = "Naveen";

int[] numbers = {1, 2, 3};

ArrayList<String> list = new ArrayList<>();

Scanner sc = new Scanner(System.in);

Employee emp = new Employee();

enum Day {
    MONDAY, TUESDAY
}
```

The main non-primitive data types are:

- String
- Arrays
- Classes
- Objects
- Interfaces
- Enums
- Records (Java 16+)

**Example:**

```java
String name = "Naveen";
Employee emp = new Employee();
int[] numbers = {1, 2, 3};
```

**Interview Follow-up:**

**Q:** Is `String` a primitive data type?

**A:** No. `String` is a class in Java. It is a non-primitive (reference) data type that provides many useful methods such as:

```java
name.length();
name.toUpperCase();
name.substring(0, 3);
```
### 3. Difference between primitive and non-primitive data types?

```text
  Primitive             Non-Primitive
  --------------------- ------------------
  Stores actual value   Stores reference
  Fixed size            Variable size
  Cannot be null        Can be null
  Faster                Slightly slower
```

**Example:**

``` java
int a = 10;
String name = "Naveen";
```

### 4. Why is String not a primitive?

Because it is a class.

It contains methods like:

``` java
name.length();
name.substring();
name.toUpperCase();
```

Primitive types don't have methods.

### 5. Default values of instance variables?

  Type      Default
  --------- ------------------
  int       0
  long      0L
  float     0.0f
  double    0.0
  boolean   false
  char      '`\u0`{=tex}000'
  Object    null

> Local variables do not get default values.

------------------------------------------------------------------------

# Level 2 (Intermediate)

### 6. What is type casting?

Converting one data type into another.

**Implicit:**

``` java
int a = 10;
double b = a;
```

**Explicit:**

``` java
double d = 10.8;
int a = (int)d;
```

Output:

``` text
10
```

### 7. Why does Java require explicit casting?

Because narrowing conversion may lose data.

``` java
double d = 99.99;
int a = (int)d;
```

Output:

``` text
99
```

Decimal information is lost.

### 8. Difference between widening and narrowing?

**Widening**

``` text
int → long → float → double
```

Automatic.

**Narrowing**

``` text
double → int
```

Requires casting.

### 9. Can boolean be converted to int?

No.

``` java
boolean b = true;
int a = (int)b;
```

Compilation error.

### 10. Why is char 2 bytes?

Java uses Unicode, so `char` stores UTF-16 code units, allowing it to
represent a wide range of characters beyond ASCII.

------------------------------------------------------------------------

# Level 3 (Tricky)

### 11. Output?

``` java
byte b = 127;
b++;
System.out.println(b);
```

**Answer**

``` text
-128
```

Reason: `byte` overflows after 127.

### 12. Output?

``` java
char c = 'A';
System.out.println((int)c);
```

Answer:

``` text
65
```

### 13. Output?

``` java
int x = 10;
double y = x / 4;
System.out.println(y);
```

Answer:

``` text
2.0
```

Reason: `x / 4` performs integer division first (2), then assigns to
`double`.

### 14. Output?

``` java
double y = 10 / 4.0;
System.out.println(y);
```

Answer:

``` text
2.5
```

### 15. Output?

``` java
long a = 100;
int b = (int)a;
```

Compiles?

**Yes**, because of explicit casting.

------------------------------------------------------------------------

# Level 4 (Product Company)

### 16. Why is double preferred over float?

-   Higher precision (64-bit vs 32-bit)
-   Better accuracy for calculations
-   `float` is mainly used when memory is constrained or
    interoperability requires it.

### 17. Why is long written as `100L`?

Without `L`, the literal is treated as an `int`.

``` java
long a = 100L;
```

### 18. Why does this fail?

``` java
int a = 2147483648;
```

Because the value exceeds the maximum `int` value (`2,147,483,647`).

### 19. Difference between `==` and `.equals()`?

-   `==` compares primitive values or object references.
-   `.equals()` compares object content (if the class overrides it
    appropriately).

``` java
String a = new String("Java");
String b = new String("Java");

System.out.println(a == b);      // false
System.out.println(a.equals(b)); // true
```

### 20. Why are wrapper classes needed?

Because Java collections and many APIs work with objects, not
primitives.

``` java
List<Integer> list = new ArrayList<>();
```

You cannot write:

``` java
List<int> list;
```

------------------------------------------------------------------------

# Coding Questions

### Q1

Swap two numbers without using a third variable.

### Q2

Find the data type of:

``` java
10 + 20.5
```

### Q3

Why is this invalid?

``` java
float f = 10.5;
```

### Q4

Explain autoboxing and unboxing with an example.

### Q5

What is the output?

``` java
System.out.println('A' + 1);
```

------------------------------------------------------------------------

# Mini Interview (Answer Without Looking)

1.  What is a variable?
2.  Why are there 8 primitive data types?
3.  Difference between `int` and `Integer`.
4.  Difference between `float` and `double`.
5.  What is widening?
6.  What is narrowing?
7.  Why is `char` 2 bytes?
8.  What are the default values of instance variables?
9.  Why can't local variables be used before initialization?
10. Why are wrapper classes required?

If you can answer these confidently, you'll have a strong foundation for
Java interviews before moving on to operators, control flow, methods,
collections, concurrency, and JVM internals.
