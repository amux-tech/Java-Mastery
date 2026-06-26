# Java Data Types Mastery Guide  
## Module 2 — Primitive Types, Literals, and Conversion

> This module teaches the “number and character world” of Java.  
> You will learn how Java stores small numbers, big numbers, decimal numbers, letters, true/false values, and how Java changes one type into another.

***

## Table of Contents

1. [Questions First](#questions-first)
2. [Big Picture](#big-picture)
3. [Primitive Types Overview](#primitive-types-overview)
4. [All 8 Primitive Types](#all-8-primitive-types)
5. [Literals](#literals)
6. [Binary, Octal, Hexadecimal](#binary-octal-hexadecimal)
7. [Numeric Separators and Scientific Notation](#numeric-separators-and-scientific-notation)
8. [Type Conversion](#type-conversion)
9. [Type Promotion](#type-promotion)
10. [Integer Internals](#integer-internals)
11. [Floating-Point Internals](#floating-point-internals)
12. [Character Internals](#character-internals)
13. [Internal Working](#internal-working)
14. [Real Project Example](#real-project-example)
15. [Common Mistakes](#common-mistakes)
16. [Interview Questions](#interview-questions)
17. [Practice Questions](#practice-questions)
18. [Answers](#answers)
19. [Quick Revision Sheet](#quick-revision-sheet)
20. [Cheat Sheet](#cheat-sheet)
21. [Mind Map](#mind-map)

***

## Questions First

### Think before reading

1. Why does Java have 8 primitive types?
2. Why is `int` the most common integer type?
3. Why do `long` and `float` need suffixes?
4. Why can `012` be dangerous?
5. Why does `3.14` become `double` by default?
6. Why do decimal numbers sometimes give surprising results?
7. Why is `char` not the same as `String`?
8. What happens when one type is changed into another type?
9. Why does Java sometimes automatically convert a value?
10. Why do some numbers overflow?

***

## Big Picture

Primitive types are Java’s simplest built-in types. They store the actual value directly. Oracle’s Java tutorial describes the primitive set and notes that `byte`, `short`, `int`, `long`, `float`, `double`, `char`, and `boolean` are the primitive types used in Java. [docs.oracle](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)

### What this module covers

- all primitive types,
- how literals work,
- how number systems work,
- how Java converts types,
- how Java promotes types in expressions,
- how integers and decimals behave inside the computer.

### Simple idea

Java must store different kinds of values in different ways:

- tiny whole number
- big whole number
- decimal number
- one character
- true/false

***

## Primitive Types Overview

| Type | Size | Default Value | Wrapper Class | Main Use |
|---|---:|---|---|---|
| `byte` | 8-bit | `0` | `Byte` | very small integers |
| `short` | 16-bit | `0` | `Short` | small integers |
| `int` | 32-bit | `0` | `Integer` | general whole numbers |
| `long` | 64-bit | `0L` | `Long` | very large whole numbers |
| `float` | 32-bit | `0.0f` | `Float` | decimal values with lower precision |
| `double` | 64-bit | `0.0d` | `Double` | normal decimal values |
| `char` | 16-bit | `'\u0000'` | `Character` | one character |
| `boolean` | logical type | `false` | `Boolean` | true/false decisions |

> Default values above are the standard field defaults; local variables must be initialized before use.

***

## All 8 Primitive Types

### 1) `byte`

A `byte` is a tiny whole number type.

- Range: `-128` to `127`
- Size: 8 bits
- Use: small counts, binary data, memory-sensitive arrays

#### Why created?
To save memory when values are very small.

#### Example
```java
byte b = 100;
```

#### Common trap
```java
byte b = 128; // error
```

***

### 2) `short`

A `short` is a small whole number type.

- Range: `-32,768` to `32,767`
- Size: 16 bits
- Use: small numeric storage

#### Why created?
To give more range than `byte`, but less space than `int`.

#### Example
```java
short s = 2000;
```

***

### 3) `int`

An `int` is the default whole-number type in Java.

- Range: `-2,147,483,648` to `2,147,483,647`
- Size: 32 bits
- Use: counters, indexes, age, loops, scores

#### Why created?
It gives a very good balance of speed and range.

#### Example
```java
int age = 25;
```

***

### 4) `long`

A `long` is a large whole-number type.

- Range: very large positive and negative values
- Size: 64 bits
- Use: IDs, timestamps, huge counts

#### Why created?
To store values that do not fit in `int`.

#### Example
```java
long distance = 5000000000L;
```

#### Important
Use `L` at the end.

***

### 5) `float`

A `float` is a decimal type with lower precision.

- Size: 32 bits
- Use: graphics, memory-saving decimal storage

#### Why created?
To store decimal values with less memory.

#### Example
```java
float price = 12.5f;
```

#### Important
Use `f` at the end.

***

### 6) `double`

A `double` is a decimal type with better precision.

- Size: 64 bits
- Use: most decimal calculations

#### Why created?
To store decimal values more accurately than `float`.

#### Example
```java
double pi = 3.14159;
```

***

### 7) `char`

A `char` stores one Unicode character.

- Size: 16 bits
- Use: letters, symbols, single characters

#### Why created?
To store one character compactly.

#### Example
```java
char grade = 'A';
```

#### Rule
Use single quotes.

***

### 8) `boolean`

A `boolean` stores only two values:

- `true`
- `false`

#### Why created?
To represent decisions and conditions.

#### Example
```java
boolean active = true;
```

***

## Literals

A literal is a value written directly in code. Java’s literal forms include numeric, string, boolean, and character forms. [docs.oracle](https://docs.oracle.com/cd/E19798-01/821-1841/bnbuv/index.html)

### Integer literals
```java
int a = 10;
```

### Long literals
```java
long b = 10L;
```

### Float literals
```java
float c = 3.14f;
```

### Double literals
```java
double d = 3.14;
```

### Character literals
```java
char e = 'J';
```

### Boolean literals
```java
boolean f = true;
```

### String literals
```java
String g = "Java";
```

***

## Binary, Octal, Hexadecimal

Java lets you write integers in different number systems.

### Binary
Base 2

```java
int x = 0b1010;
```

### Octal
Base 8

```java
int y = 012;
```

### Hexadecimal
Base 16

```java
int z = 0x10;
```

### Simple comparison

| Form | Example | Decimal Value |
|---|---|---:|
| Binary | `0b1010` | 10 |
| Octal | `012` | 10 |
| Decimal | `10` | 10 |
| Hex | `0xA` | 10 |

### Warning
`012` is not twelve. It is octal.

***

## Numeric Separators and Scientific Notation

### Numeric separators

Underscores make big numbers easier to read.

```java
int million = 1_000_000;
long card = 1234_5678_9012_3456L;
```

### Scientific notation

Used for very large or very small decimal numbers.

```java
double a = 1.5e3;   // 1500.0
double b = 2.0E-4;  // 0.0002
```

### Why useful?
Because long digit lists are hard for the eyes.

***

## Type Conversion

Type conversion means changing one data type into another.

### Widening conversion
Smaller type to larger type.

```java
int x = 10;
double y = x;
```

This is usually automatic.

### Narrowing conversion
Larger type to smaller type.

```java
double x = 10.5;
int y = (int) x;
```

This needs casting.

### Precision loss
Some data may be lost when converting to a smaller or less precise type.

### Data loss
Part of the value may disappear.

### Overflow
Value becomes too large for the destination type.

### Underflow
Value becomes too small in magnitude to be represented properly, especially in floating-point work.

### Simple rule
- widening = safe
- narrowing = risky

***

## Type Promotion

Type promotion happens when Java automatically changes small numeric types into bigger ones during calculations.

### Example

```java
byte a = 10;
byte b = 20;
int c = a + b;
```

Why `int`?  
Because Java promotes smaller integer types during arithmetic.

### Unary promotion
For one value.

```java
byte a = 10;
int b = +a;
```

### Binary numeric promotion
For two values in expressions.

```java
int x = 5 + 2.5;
```

Java promotes the smaller/less precise value to make the operation work.

### Method argument promotion
Java may promote values when passing arguments to methods.

### Operator behavior
Arithmetic operators often promote values to `int`, `long`, `float`, or `double` depending on the expression.

***

## Integer Internals

Integers are stored in binary. Java uses signed values and two’s complement for integer representation.

### Two’s complement idea
It is a binary system that lets Java represent negative numbers.

### Example
`5` in binary is easy.  
Negative numbers are stored using two’s complement rules.

### Overflow
When an integer goes beyond its max value, it wraps around.

```java
byte b = 127;
b++;
System.out.println(b);
```

Output:
```text
-128
```

### Why this happens
The bit pattern rolls over.

***

## Floating-Point Internals

Java floating-point types follow IEEE 754 rules. Oracle’s Java docs describe `float` and `double` as floating-point types. [w3schools](https://www.w3schools.com/java/java_data_types.asp)

### Why decimals can be surprising
Some decimal numbers cannot be stored exactly in binary.

### Example
```java
System.out.println(0.1 + 0.2);
```

This may not print exactly `0.3`.

### Important ideas

- precision
- rounding
- NaN
- infinity
- positive zero
- negative zero

### NaN
Means “Not a Number”.

### Infinity
Happens when a number is too large to fit.

### Positive and negative zero
They are special floating-point values with subtle differences.

***

## Character Internals

A `char` in Java is a 16-bit Unicode code unit.

### Why this matters
Java supports many world languages and symbols.

### ASCII
Old 7-bit character set for English letters and symbols.

### Unicode
Much larger character system for many languages.

### UTF-16
Java `char` uses UTF-16 code units.

### Code point
A numeric value assigned to a character.

### Escape sequences
Special written forms like:

```java
'\n'
'\t'
'\\'
'\''
```

***

## Internal Working

Java source code is compiled into bytecode. The JVM then runs the bytecode and uses type rules to store and convert values.

### Example

```java
int a = 10;
double b = a;
```

- `10` is stored as an `int`
- `b` becomes `10.0`

### Why this matters
You can predict output and spot type errors early.

***

## Real Project Example

Imagine a shopping app.

```java
int quantity = 3;
long orderId = 5000000000L;
float taxRate = 5.5f;
double price = 499.99;
char rating = 'A';
boolean inStock = true;
String productName = "Keyboard";
```

### Meaning
- `quantity` = count
- `orderId` = big ID
- `taxRate` = small decimal
- `price` = money estimate
- `rating` = one letter
- `inStock` = yes/no
- `productName` = text

***

## Common Mistakes

- Forgetting `L` for `long`
- Forgetting `f` for `float`
- Using `char` with double quotes
- Thinking `012` means twelve
- Using `float` for money
- Assuming decimals are exact
- Forgetting narrowing casts
- Expecting `byte + byte` to stay `byte`

***

## Interview Questions

1. How many primitive types are there?
2. Why is `int` used most often?
3. What is the range of `byte`?
4. Why does `long` need `L`?
5. Why does `float` need `f`?
6. What is the difference between `char` and `String`?
7. What is widening conversion?
8. What is narrowing conversion?
9. What is overflow?
10. What is two’s complement?
11. Why does `byte + byte` become `int`?
12. What is IEEE 754?
13. What is NaN?
14. What is scientific notation?
15. What are escape sequences?

***

## Practice Questions

### Predict output

1.
```java
byte b = 127;
b++;
System.out.println(b);
```

2.
```java
int x = 10;
double y = x;
System.out.println(y);
```

3.
```java
System.out.println(0b1010);
```

4.
```java
System.out.println(012);
```

5.
```java
System.out.println(1.5e3);
```

### Explain in simple words

6. Why is `3.14` a `double` by default?
7. Why does `float` need `f`?
8. Why is `char` not the same as `String`?
9. Why can decimals be imprecise?
10. Why is `int` the default whole number type?

***

## Answers

### Answers to the questions first

1. Java has 8 primitive types.
2. `int` is used most often because it gives a good balance of speed and range.
3. `byte` range is `-128` to `127`.
4. `long` needs `L` because integer literals are `int` by default.
5. `float` needs `f` because decimal literals are `double` by default.
6. `char` stores one character; `String` stores text as an object.
7. Widening conversion means changing a smaller type into a larger type safely.
8. Narrowing conversion means changing a larger type into a smaller type, which may lose data.
9. Overflow happens when a value is too large for the type.
10. Two’s complement is the binary system Java uses for signed integers.
11. `byte + byte` becomes `int` because Java promotes smaller integer types in arithmetic.
12. IEEE 754 is the standard for floating-point representation.
13. NaN means Not a Number.
14. Scientific notation is a compact way to write very large or very small decimal values.
15. Escape sequences are special character forms like `\n` and `\t`.

### Answers to practice questions

1. Output:
```text
-128
```

2. Output:
```text
10.0
```

3. Output:
```text
10
```

4. Output:
```text
10
```

5. Output:
```text
1500.0
```

6. `3.14` is `double` by default because Java treats decimal literals as double unless told otherwise.
7. `float` needs `f` so Java knows the literal is a float.
8. `char` is one character; `String` is many characters wrapped in an object.
9. Decimals can be imprecise because many decimal fractions cannot be stored exactly in binary.
10. `int` is default because it is the standard general-purpose integer type.

***

## Quick Revision Sheet

- Primitive types store simple values directly.
- Java has 8 primitive types.
- `int` is the default integer type.
- `double` is the default decimal type.
- `long` uses `L`.
- `float` uses `f`.
- `char` uses single quotes.
- `boolean` uses `true` or `false`.
- Binary, octal, and hex are just different number systems.
- Widening conversion is safe.
- Narrowing conversion may lose data.
- Integer overflow wraps around.
- Floating-point values can be imprecise.

***

## Cheat Sheet

| Concept | Example | Meaning |
|---|---|---|
| `byte` | `byte b = 10;` | tiny integer |
| `short` | `short s = 20;` | small integer |
| `int` | `int i = 30;` | normal integer |
| `long` | `long l = 40L;` | large integer |
| `float` | `float f = 3.5f;` | small precision decimal |
| `double` | `double d = 3.5;` | normal decimal |
| `char` | `char c = 'A';` | one character |
| `boolean` | `boolean ok = true;` | true/false |
| binary | `0b1010` | base 2 |
| octal | `012` | base 8 |
| hex | `0x10` | base 16 |

***

## Mind Map

```text
Primitive Data Types
|
+-- Integers
|   +-- byte
|   +-- short
|   +-- int
|   +-- long
|
+-- Decimals
|   +-- float
|   +-- double
|
+-- Character
|   +-- char
|
+-- Logic
|   +-- boolean
|
+-- Literals
|   +-- decimal
|   +-- binary
|   +-- octal
|   +-- hex
|   +-- long
|   +-- float
|   +-- double
|   +-- char
|   +-- boolean
|   +-- string
|
+-- Conversion
|   +-- widening
|   +-- narrowing
|
+-- Promotion
|   +-- unary
|   +-- binary
```

***
