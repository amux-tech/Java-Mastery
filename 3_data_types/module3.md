# Java Data Types Mastery Guide  
## Module 3 — Advanced Types, Internals, Errors, and Mastery Practice

> This module finishes the journey.  
> It explains wrapper classes, reference types, big numbers, bits, memory, common errors, best practices, and interview practice in one final master chapter.

***

## Table of Contents

1. [Questions First](#questions-first)
2. [Wrapper Classes](#wrapper-classes)
3. [Wrapper Internals](#wrapper-internals)
4. [Reference Data Types](#reference-data-types)
5. [Primitive vs Reference Types](#primitive-vs-reference-types)
6. [Big Numbers](#big-numbers)
7. [Bit-Level Concepts](#bit-level-concepts)
8. [Memory Concepts](#memory-concepts)
9. [Default Values Recap](#default-values-recap)
10. [Common Errors](#common-errors)
11. [Best Practices](#best-practices)
12. [Real-World Case Studies](#real-world-case-studies)
13. [Interview Questions](#interview-questions)
14. [Output Prediction Questions](#output-prediction-questions)
15. [Debugging Questions](#debugging-questions)
16. [Coding Exercises](#coding-exercises)
17. [Mini Projects](#mini-projects)
18. [Answers](#answers)
19. [Quick Revision Sheet](#quick-revision-sheet)
20. [Cheat Sheet](#cheat-sheet)
21. [Mind Map](#mind-map)
22. [Common Mistakes](#common-mistakes)
23. [Challenge Problems](#challenge-problems)

***

## Questions First

### Think before reading

1. Why do wrapper classes exist?
2. Why does Java need `Integer` when it already has `int`?
3. What is boxing?
4. What is unboxing?
5. What is autoboxing?
6. What is the Integer cache?
7. Why is `Integer a = 100;` special?
8. What is the difference between `==` and `equals()`?
9. Why is `BigDecimal` used for money?
10. Why do bitwise operators exist?
11. What is the difference between stack and heap?
12. Why do reference types need more care than primitives?
13. What are common mistakes with `null`?
14. Why are default values important?
15. How do these topics help in interviews?

***

## Wrapper Classes

Wrapper classes are object versions of primitive types. Oracle’s autoboxing tutorial explains that the compiler converts between primitives and wrapper classes automatically, and lists the primitive-to-wrapper pairs. [docs.oracle](https://docs.oracle.com/javase/tutorial/java/data/autoboxing.html)

### Why wrapper classes exist

Primitives are simple and fast, but sometimes Java needs an object version.

Wrapper classes solve this.

### Primitive to wrapper table

| Primitive | Wrapper |
|---|---|
| `byte` | `Byte` |
| `short` | `Short` |
| `int` | `Integer` |
| `long` | `Long` |
| `float` | `Float` |
| `double` | `Double` |
| `char` | `Character` |
| `boolean` | `Boolean` |

### Why do we need wrappers?

Because objects can be:

- stored in collections,
- passed where objects are required,
- used with methods,
- allowed to be `null`.

### Simple analogy

- Primitive = a toy in your hand
- Wrapper = a toy inside a box with a label and extra rules

### Example

```java
int a = 10;
Integer b = 10;
```

***

## Wrapper Internals

### Boxing

Boxing means converting a primitive into a wrapper object.

```java
Integer x = Integer.valueOf(10);
```

### Unboxing

Unboxing means converting a wrapper object back into a primitive.

```java
int y = x.intValue();
```

### Autoboxing

Java does boxing automatically.

```java
Integer x = 10;
```

### Auto-unboxing

Java does unboxing automatically.

```java
int y = x;
```

Oracle explains that the compiler performs these automatic conversions between primitives and wrappers. [docs.oracle](https://docs.oracle.com/javase/tutorial/java/data/autoboxing.html)

### Integer cache

Java caches some `Integer` objects, usually from `-128` to `127`, to reuse them and save memory. This cache behavior is widely documented in wrapper discussions and in `Integer.valueOf()`-related explanations. [feco.tistory](https://feco.tistory.com/112)

### Why the cache matters

```java
Integer a = 100;
Integer b = 100;
System.out.println(a == b);
```

This may print `true` because both may refer to the same cached object.

But:

```java
Integer a = 200;
Integer b = 200;
System.out.println(a == b);
```

This may print `false` because values outside the usual cache range may create different objects.

### `==` vs `equals()`

- `==` compares references for wrapper objects
- `equals()` compares values

### Example

```java
Integer a = 100;
Integer b = 100;
System.out.println(a == b);      // often true
System.out.println(a.equals(b)); // true
```

### Null unboxing trap

```java
Integer x = null;
int y = x; // NullPointerException
```

Why? Because Java tries to unbox `null`.

***

## Reference Data Types

Reference types store references to objects, not raw values. The Java Language Specification divides Java types into primitive types and reference types. [docs.oracle](https://docs.oracle.com/javase/specs/jls/se7/html/jls-4.html)

### Examples

- `String`
- arrays
- classes
- interfaces
- enums
- records

### What is an object?

An object is a real thing created from a class.

Example:

```java
String name = "Raj";
int[] numbers = {1, 2, 3};
```

### Why reference types exist

They let Java store complex data:

- names,
- lists,
- records,
- structured objects,
- behavior with data.

### Example

A student object may have:

- name
- age
- marks

That is too much for a primitive type, so Java uses objects.

***

## Primitive vs Reference Types

| Feature | Primitive | Reference |
|---|---|---|
| Stores | Actual value | Reference to object |
| `null` allowed | No | Yes |
| Example | `int` | `String` |
| Copy behavior | Copies value | Copies reference |
| Memory | Simple | Object-based |

### Simple idea

If you copy a primitive, you get a new value.  
If you copy a reference, you point to the same object.

***

## Big Numbers

Sometimes normal types are not enough.

### `BigInteger`

Used for very large whole numbers.

```java
BigInteger a = new BigInteger("12345678901234567890");
```

### `BigDecimal`

Used for precise decimal calculations. Oracle’s `BigDecimal` documentation describes it as an arbitrary-precision number with scale, making it suitable for precise arithmetic. [docs.oracle](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/math/BigDecimal.html)

```java
BigDecimal price = new BigDecimal("99.99");
```

### Why use `BigDecimal` for money?

Because `double` can create precision surprises.

### Example

```java
BigDecimal a = new BigDecimal("0.1");
BigDecimal b = new BigDecimal("0.2");
System.out.println(a.add(b));
```

### Why this matters

For finance, exact decimal behavior is usually more important than speed.

***

## Bit-Level Concepts

Bits are the smallest units of data: `0` and `1`.

### Bytes

A byte is 8 bits.

### Binary

Base 2 number system.

### Hexadecimal

Base 16 number system.

### Bitwise operators

Operate directly on bits.

Examples:

- `&` AND
- `|` OR
- `^` XOR
- `~` NOT
- `<<` left shift
- `>>` signed right shift
- `>>>` unsigned right shift

### Why these exist

They are useful for:

- flags,
- masking,
- low-level data,
- performance-sensitive work.

### Example

```java
int x = 5;   // 0101
int y = 3;   // 0011
System.out.println(x & y); // 1
```

### Shift operator idea

- `<<` moves bits left
- `>>` moves bits right while keeping sign
- `>>>` moves bits right with zeros on the left

***

## Memory Concepts

### Stack

Used for:

- local variables,
- method frames,
- temporary values.

### Heap

Used for:

- objects,
- arrays.

### String pool

A special place where string literals may be stored and reused.

### Primitive storage

Primitives hold actual values.

### Object references

Reference variables hold the “link” to objects.

### Simple diagram

```text
Stack
+----------------------+
| int a = 10           |
| String s -----------+|
+----------------------+|
                        |
Heap / String Pool      |
+----------------------+|
| "Hello"              |
+----------------------+
```

***

## Default Values Recap

### Primitive fields

| Type | Default |
|---|---|
| `byte` | `0` |
| `short` | `0` |
| `int` | `0` |
| `long` | `0L` |
| `float` | `0.0f` |
| `double` | `0.0d` |
| `char` | `'\u0000'` |
| `boolean` | `false` |

### Reference fields

- `null`

### Local variables

- no default value

***

## Common Errors

### Overflow

Value too large for the type.

### Underflow

Value too small or too tiny to represent properly.

### Precision loss

Some decimal digits disappear during conversion.

### `NullPointerException`

Happens when you try to use `null` as if it were an object.

### `NumberFormatException`

Happens when text cannot be converted to a number.

### Casting mistakes

Example:

```java
int x = (int) 3.99; // becomes 3
```

### Wrapper mistakes

```java
Integer x = null;
int y = x; // crash
```

***

## Best Practices

- Use `int` for normal whole numbers.
- Use `long` only when needed.
- Use `double` for general decimal work.
- Use `BigDecimal` for money.
- Use `boolean` for true/false logic.
- Use `char` for one character only.
- Use `String` for text.
- Use wrappers when you need objects or `null`.
- Avoid `==` for wrapper value comparison.
- Initialize variables clearly.
- Keep names simple and meaningful.

***

## Real-World Case Studies

### 1. Banking app
Use `BigDecimal` for balance.

### 2. Shopping cart
Use `int` for quantity and `BigDecimal` for price.

### 3. School marks app
Use `int` for marks and `boolean` for pass/fail.

### 4. Temperature sensor
Use `double` or `float`.

### 5. Product code system
Use `String` or `long` depending on format.

### 6. Login system
Use `boolean` for active/inactive status.

### 7. File processing
Use `byte` for raw data.

### 8. Language app
Use `char` and `String`.

### 9. Large ID system
Use `long` or `BigInteger`.

### 10. Bit flag system
Use bitwise operators.

***

## Interview Questions

1. Why do wrapper classes exist?
2. What is boxing?
3. What is unboxing?
4. What is autoboxing?
5. What is auto-unboxing?
6. What is the Integer cache?
7. Why is `Integer a = 100; Integer b = 100;` sometimes `true` with `==`?
8. Why is `BigDecimal` better for money than `double`?
9. What is the difference between primitive and reference types?
10. What is `NullPointerException`?
11. What is `NumberFormatException`?
12. What does `==` compare for objects?
13. What does `equals()` compare?
14. What is a bitwise operator?
15. Why use shift operators?

***

## Output Prediction Questions

1.
```java
Integer a = 100;
Integer b = 100;
System.out.println(a == b);
```

2.
```java
Integer a = 200;
Integer b = 200;
System.out.println(a == b);
```

3.
```java
Integer x = null;
System.out.println(x);
```

4.
```java
int a = 5;
int b = 3;
System.out.println(a & b);
```

5.
```java
System.out.println(0.1 + 0.2);
```

***

## Debugging Questions

1. Why does this crash?
```java
Integer x = null;
int y = x;
```

2. Why does this not behave like expected?
```java
double total = 0.1 + 0.2;
```

3. Why is this wrong?
```java
char c = "A";
```

4. Why is this risky?
```java
int x = (int) 9999999999L;
```

5. Why is this not safe for money?
```java
double balance = 100.10;
```

***

## Coding Exercises

1. Write a program using all wrapper classes.
2. Write a program showing autoboxing and unboxing.
3. Write a program demonstrating `Integer` cache behavior.
4. Write a program using `BigDecimal` for money addition.
5. Write a program using `byte`, `short`, `int`, and `long`.
6. Write a program using bitwise AND and OR.
7. Write a program showing `char` to numeric conversion.
8. Write a program showing overflow in `byte`.
9. Write a program comparing `equals()` and `==`.
10. Write a program converting `String` to `int`.

***

## Mini Projects

1. Student marks calculator.
2. Simple bank balance app.
3. Temperature converter.
4. Product inventory counter.
5. Login status checker.
6. Bitwise flag demo.
7. Currency calculator using `BigDecimal`.
8. Character code explorer.
9. Number system converter.
10. Wrapper class playground.

***

## Answers

### Answers to the questions first

1. Wrapper classes exist so primitives can be used as objects.
2. Boxing means converting a primitive into a wrapper object.
3. Unboxing means converting a wrapper object into a primitive.
4. Autoboxing is automatic boxing by the compiler.
5. Auto-unboxing is automatic unboxing by the compiler.
6. The Integer cache is a pre-created range of Integer objects reused by Java.
7. `Integer a = 100; Integer b = 100;` may be `true` with `==` because cached objects may be reused.
8. `BigDecimal` is better for money because it gives exact decimal control.
9. Primitive types store values directly; reference types store object references.
10. `NullPointerException` happens when you use `null` like an object.
11. `NumberFormatException` happens when text cannot be parsed as a number.
12. `==` compares references for objects.
13. `equals()` compares values when the class defines it that way.
14. A bitwise operator works directly on binary bits.
15. Shift operators move bits left or right.

### Answers to output prediction

1. `true`
2. `false`
3. `null`
4. `1`
5. `0.30000000000000004`

### Answers to debugging questions

1. Because `null` cannot be unboxed into a primitive.
2. Because floating-point values may not be exact in binary.
3. Because `char` needs single quotes.
4. Because the long value may not fit safely in `int`.
5. Because `double` can create precision issues for money.

***

## Quick Revision Sheet

- Wrapper classes are object forms of primitives.
- Boxing = primitive to object.
- Unboxing = object to primitive.
- Autoboxing and auto-unboxing happen automatically.
- Integer cache often reuses values from `-128` to `127`.
- `BigInteger` is for huge whole numbers.
- `BigDecimal` is for precise decimal values.
- Bitwise operators work on bits.
- Stack stores locals; heap stores objects.
- `null` can cause runtime errors.
- `==` and `equals()` are not the same for objects.

***

## Cheat Sheet

| Topic | Simple Meaning |
|---|---|
| Wrapper | Object version of primitive |
| Boxing | Value → object |
| Unboxing | Object → value |
| Autoboxing | Java does boxing automatically |
| Integer cache | Reused small Integer objects |
| BigInteger | Huge whole numbers |
| BigDecimal | Exact decimal math |
| Bitwise | Works on bits |
| Stack | Method/local memory |
| Heap | Object memory |

***

## Mind Map

```text
Java Data Types Mastery
|
+-- Foundations
|   +-- Variables
|   +-- Scope
|   +-- Default values
|
+-- Primitive types
|   +-- byte
|   +-- short
|   +-- int
|   +-- long
|   +-- float
|   +-- double
|   +-- char
|   +-- boolean
|
+-- Literals
|   +-- decimal
|   +-- binary
|   +-- octal
|   +-- hex
|   +-- scientific notation
|
+-- Conversion
|   +-- widening
|   +-- narrowing
|   +-- promotion
|
+-- Advanced
|   +-- wrappers
|   +-- reference types
|   +-- big numbers
|   +-- bits
|   +-- memory
|   +-- errors
|   +-- best practices
```

***

## Common Mistakes

- Using `==` to compare wrapper values.
- Forgetting `null` can crash unboxing.
- Using `double` for money without care.
- Mixing up `char` and `String`.
- Forgetting `L` and `f` suffixes.
- Thinking all decimal values are exact.
- Using octal without meaning to.
- Using local variables before initialization.

***

## Challenge Problems

1. Explain why `Integer a = 127; Integer b = 127;` may behave differently from `Integer a = 128; Integer b = 128;`.
2. Show why `0.1 + 0.2` is not exactly `0.3`.
3. Explain the difference between a primitive variable, a wrapper variable, and a `String`.
4. Write a method that safely converts a `String` to `int`.
5. Write a money calculator using `BigDecimal`.
6. Show how bitwise operators can store flags.
7. Explain stack vs heap like telling a child.
8. Explain why local variables must be initialized.
9. Explain why `final` is useful.
10. Explain the whole data type system in 10 lines.

***
