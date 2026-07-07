# Java Interview Questions: Variables & Data Types

## Level 1 (Basic)

### 1. What is a variable in Java?

**Expected Answer:**

A variable is a named memory location used to store data. Every variable
has a data type that determines what kind of value it can store.

**Example:**

``` java
int age = 25;
```

### 2. What are the primitive data types in Java?

There are **8** primitive data types.

```text
    Data Type   Size            Example
    ----------- --------------- ------------
    byte        1 byte          100
    short       2 bytes         1000
    int         4 bytes         100000
    long        8 bytes         100000000L
    float       4 bytes         10.5f
    double      8 bytes         10.5
    char        2 bytes         'A'
    boolean     JVM-dependent   true
```

### 3. Difference between primitive and non-primitive data types?

  Primitive             Non-Primitive
  --------------------- ------------------
  Stores actual value   Stores reference
  Fixed size            Variable size
  Cannot be null        Can be null
  Faster                Slightly slower

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
