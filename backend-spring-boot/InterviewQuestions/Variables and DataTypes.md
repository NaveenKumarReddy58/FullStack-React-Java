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
### Why boolean is JVM dependent

Java only specifies the values of a boolean (true and false), not its size. The JVM decides how to store it based on the underlying hardware and CPU architecture. Since CPUs typically access memory in bytes or larger units rather than single bits, the JVM can choose the most efficient representation. That's why the size of a boolean is JVM-dependent.

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
### What is Implicit Casting?

Implicit casting (also called **widening conversion**) is the automatic conversion of a smaller data type to a larger compatible data type. Java performs this conversion automatically because there is no risk of data loss.

**Example:**

```java
int a = 10;
double b = a;
```

In the above example, `int` is automatically converted to `double` because a `double` can store all `int` values without losing information.

Therefore, no explicit cast is required.

### What is Explicit Casting?

Explicit casting (also called **narrowing conversion**) is the manual conversion of a larger data type to a smaller compatible data type. Since this conversion may result in data loss, the programmer must explicitly tell Java to perform the conversion.

In other words, by writing the cast, you are saying:

> "I understand that some data may be lost, and I'm okay with that."

**Example:**

```java
double d = 10.8;
int a = (int) d;
```

**Output:**

```text
10
```

**Explanation:**

In the above example, `double` has a larger range and can store decimal values, whereas `int` stores only whole numbers. During the conversion, the decimal part (`0.8`) is discarded, so the result becomes `10`.

Therefore, Java requires an explicit cast because there is a possibility of data loss.

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

## Why is `char` 2 bytes in Java?

### Answer

Java uses **Unicode** to represent characters from many languages around the world instead of just English. A Java `char` stores **one UTF-16 code unit**, which occupies **16 bits (2 bytes)**. This allows Java to represent a much wider range of characters than ASCII.

> **Note:** Some Unicode characters, such as many emojis, require **two UTF-16 code units (two `char` values)** because they are outside the Basic Multilingual Plane (BMP).

---

## Does `String` use UTF-16 internally?

### Answer

It depends on the Java version.

- **Java 8 and earlier:** A `String` was internally stored as a `char[]`, so it always used UTF-16 code units.
- **Java 9 and later:** Java introduced **Compact Strings**. If all characters fit in the Latin-1 character set (such as English text), the `String` is stored using a `byte[]` with Latin-1 encoding to save memory. Otherwise, it is stored using UTF-16.

This optimization reduces memory usage while keeping the behavior of `String` the same.

---

## Why doesn't `int` use UTF-16?

### Answer

UTF-16 is a **character encoding** used to represent text, not numbers. An `int` stores a binary numeric value (32 bits) for efficient arithmetic operations. Converting numbers to UTF-16 would require treating them as text, which would waste memory and reduce performance.

---

## Why doesn't `String` always use UTF-16 in modern Java?

### Answer

Starting with Java 9, Java introduced **Compact Strings** to reduce memory usage. If a `String` contains only Latin-1 characters (such as English text), it is stored using one byte per character. If it contains characters outside the Latin-1 range, Java stores it using UTF-16.

This optimization improves memory efficiency without changing how developers use `String`.
------------------------------------------------------------------------

# Level 3 (Tricky)

# Byte and Short Arithmetic Operations in Java

## Can we perform arithmetic operations on byte and short?

Yes, Java allows arithmetic operations on `byte` and `short`.

However, during arithmetic operations, Java automatically promotes `byte`, `short`, and `char` values to `int`.

### Example

```java
byte a = 10;
byte b = 20;

int result = a + b;

System.out.println(result);
```

Output:

```
30
```

Here:

```
byte + byte = int
```

The result of `a + b` is an `int`, not a `byte`.

---

# Why does `byte result = a + b` give an error?

Example:

```java
byte a = 10;
byte b = 20;

byte result = a + b;   // Compilation error
```

### Reason

Java promotes the operands before performing arithmetic.

The compiler treats it as:

```java
int temp = a + b;
byte result = temp;
```

The problem is that an `int` is larger than a `byte`.

```
byte range:
-128 to 127

int range:
-2,147,483,648 to 2,147,483,647
```

Java does not automatically convert an `int` back to a `byte` because data loss can happen.

Example:

```java
int value = 200;

byte b = value;   // Error
```

Because:

```
200 cannot fit inside byte range (-128 to 127)
```

---

# How to store the result back into byte?

Use explicit casting.

Example:

```java
byte a = 10;
byte b = 20;

byte result = (byte)(a + b);

System.out.println(result);
```

Output:

```
30
```

Here we are telling Java:

> Convert this int result into a byte because we know it fits.

---

# What happens when overflow occurs?

Example:

```java
byte a = 100;
byte b = 100;

byte result = (byte)(a + b);

System.out.println(result);
```

Calculation:

```
100 + 100 = 200
```

But byte can store only:

```
-128 to 127
```

So overflow happens.

Binary representation:

```
200 = 11001000
```

In signed byte two's complement:

```
11001000 = -56
```

Output:

```
-56
```

---

# Why does byte increment work?

Example:

```java
byte b = 127;

b++;

System.out.println(b);
```

Output:

```
-128
```

The increment operator is a special case.

Java internally performs:

```java
b = (byte)(b + 1);
```

Binary:

Before increment:

```
127 = 01111111
```

After adding 1:

```
  01111111
+ 00000001
-----------
  10000000
```

`10000000` represents:

```
-128
```

in two's complement.

---

# Why does b = b + 0 give an error?

Example:

```java
byte b = 10;

b = b + 0;   // Compilation error
```

Because:

```
byte + int = int
```

The value `0` is an integer literal, so Java converts:

```
byte + int
```

into:

```
int
```

The result is an `int`, and assigning it back to `byte` requires narrowing conversion.

Correct:

```java
b = (byte)(b + 0);
```

---

# Why does b += 0 work?

Example:

```java
byte b = 10;

b += 0;
```

This works because compound assignment operators automatically perform casting.

It is equivalent to:

```java
b = (byte)(b + 0);
```

---

# Special Case: Constant Values

This works:

```java
byte result = 10 + 20;
```

Output:

```
30
```

Why?

Because `10 + 20` is a compile-time constant.

The compiler calculates:

```
10 + 20 = 30
```

and checks that `30` fits inside byte range.

But this fails:

```java
byte a = 10;
byte b = 20;

byte result = a + b;
```

because the calculation happens at runtime and the result type is `int`.

---

# Interview Answer

**Java allows arithmetic operations on byte and short, but before performing the operation, they are promoted to int. The result of the operation is always int. To store the result back into byte or short, explicit casting is required because narrowing conversion may cause data loss. Compound assignment operators like += automatically perform the cast.**

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
