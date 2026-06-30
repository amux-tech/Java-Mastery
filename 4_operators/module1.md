# Java Operators — Complete Course (Beginner → Mastery)

## How to use this file
- Read sections in order; do the short examples on your computer.  
- After each major topic, try the short exercises. Sample solutions are provided at the end.  
- Use parentheses to verify results while learning operator precedence. [1]

***

## 1. What is an operator?
An operator is a symbol that tells Java to perform a particular operation on one or more values (operands). [2]
Operands are the values, variables, or expressions the operator acts on. [2]
Operators are grouped by purpose: arithmetic, relational, logical, bitwise/shift, unary, assignment, ternary, and type check. [1]

***

## 2. Categories and simple overview
- Arithmetic: +, -, *, /, % (numbers and String concatenation for +). [1]
- Unary: +, -, ++, --, !, ~ (operate on single operand). [1]
- Assignment and compound: =, +=, -=, *=, /=, %=, &=, |=, ^=, <<=, >>=, >>>=. [1]  
- Relational (comparison): ==, !=, <, <=, >, >=. [1]
- Logical: &&, ||, ! (boolean logic, short‑circuit versions). [1]  
- Bitwise: &, |, ^, ~ (operate on bits). [1]  
- Shift: <<, >>, >>> (move bits left/right). [1]
- Ternary (conditional): ? : (three‑operand conditional expression). [1]
- Type check: instanceof (checks object type before casting). [1]

***

## 3. Arithmetic operators — detailed (with plain language)
- + (addition): adds numeric values or concatenates Strings (left to right). Example: 2 + 3 = 5; "Hi " + "Sam" = "Hi Sam". [1]
- - (subtraction): subtract numbers. Example: 7 - 4 = 3. [1]
- * (multiplication): multiplies numbers. Example: 3 * 4 = 12. [1]
- / (division): divides numbers. When both operands are integers, Java performs integer division (it discards the fractional part). To get fractions, at least one operand must be float/double (use casts). Example: 7 / 2 = 3, but (double)7 / 2 = 3.5. [1]
- % (remainder/modulo): returns the remainder of division. Example: 7 % 2 = 1. Works for negative numbers with sign rules — be careful. [1]

Example code:
```
int a = 7, b = 2;
int q = a / b;        // 3
int r = a % b;        // 1
double d = (double)a / b; // 3.5
String s = "Sum: " + (a + b); // "Sum: 9"
```
Tip: Parentheses clarify intent and avoid surprises from precedence. [1]

***

## 4. Unary operators explained simply
- Unary plus (+) and minus (-): +x is x; -x flips the sign. [1]
- Increment ++ and decrement --: add or subtract 1. Two forms:
  - Pre (prefix): ++x increments first, then returns new value. [1]
  - Post (postfix): x++ returns current value, then increments. [1]
- Logical not (!): flips boolean value (true → false, false → true). [1]
- Bitwise complement (~): flips all bits of an integer (not commonly used by beginners). [1]

Examples:
```
int x = 5;
int a = ++x; // x=6, a=6
x = 5;
int b = x++; // x=6, b=5
boolean flag = true;
flag = !flag; // false
```
Warning: Using ++/-- inside complex expressions makes code hard to read—avoid unless necessary. [1]

***

## 5. Assignment operators (and compound forms)
- Simple assignment: a = b assigns right value to left variable. [1]
- Compound assignment: a += b is shorthand for a = a + b (with some implicit casting rules). Same for -=, *=, /=, %=, &=, |=, ^=, <<=, >>=, >>>=. [1]

Example:
```
int x = 10;
x += 5; // x = 15
x *= 2; // x = 30
```
Note: Compound operators may perform implicit narrowing conversions — for example, short or byte with += may not require explicit cast in some cases because Java handles it. Prefer explicit casts for clarity in production code. [1]

***

## 6. Relational operators — comparing values
- Operators: ==, !=, <, <=, >, >=. They return boolean. [1]
- For primitives (int, double, char, boolean), these compare values directly. For objects, == tests reference equality (same object), not content; use .equals() to compare contents (e.g., Strings). [1]

Example:
```
int a = 3, b = 4;
boolean res = (a < b); // true
String s1 = new String("hi");
String s2 = "hi";
s1 == s2        // often false (different objects)
s1.equals(s2)   // true (same contents)
```
Tip: For Strings and most objects used as keys, prefer equals() and consider null checks before calling equals. [1]

***

## 7. Logical operators (boolean logic) — with short‑circuit idea
- && (AND): true only if both operands are true. Short‑circuit: if left is false, right is not evaluated. [1]
- || (OR): true if at least one operand is true. Short‑circuit: if left is true, right is not evaluated. [1]  
- ! (NOT): flips boolean. [1]
- & and | also exist for booleans but do NOT short‑circuit (they always evaluate both sides). Use & or | when you need both sides evaluated (rare). [1]

Why short‑circuit matters: you can safely write checks like:
```
if (obj != null && obj.isReady()) { ... }
```
Here obj.isReady() runs only when obj != null, preventing NullPointerException. [1]

***

## 8. Bitwise operators — working at bit level (plain language)
- Bitwise AND (&): compares bits of two integers and returns 1 only if both bits are 1. [1]
- Bitwise OR (|): bit is 1 if at least one bit is 1. [1]  
- Bitwise XOR (^): bit is 1 if bits differ. [1]
- Bitwise NOT (~): flips each bit. [1]

Example (8-bit view for clarity):
```
int x = 6;   // 00000110
int y = 3;   // 00000011
x & y = 00000010 -> 2
x | y = 00000111 -> 7
x ^ y = 00000101 -> 5
```
Use bitwise ops for flags, masks, and performance-critical code; they require careful thinking about signed vs unsigned. [1]

***

## 9. Shift operators — moving bits
- << (left shift): shift bits left, filling with zeros on right; equivalent to multiplying by 2 for positive numbers (but watch overflow). [1]
- >> (signed right shift): shifts right, keeps sign bit (fills with 1 for negatives). [1]
- >>> (unsigned right shift): shifts right and fills left with zeros (no sign extension). Only works for int/long. [1]

Example:
```
int a = 8; // 00001000
a << 1 = 16 // 00010000
a >> 2 = 2  // 00000010
```
Caution: Right shifts of negative numbers behave differently because of sign extension; prefer >>> for logical right shift when needed. [1]

***

## 10. Ternary (conditional) operator — compact if‑else
- Syntax: condition ? exprIfTrue : exprIfFalse. It evaluates to one of two expressions based on the condition. [1]

Example:
```
int a = 5;
String res = (a % 2 == 0) ? "even" : "odd"; // "odd"
```
Use ternary for short conditional assignments; avoid for complex multi-step logic (use if‑else for clarity). [1]

***

## 11. instanceof — safe type checking
- Use `obj instanceof Type` to check whether obj is an instance of Type (or subclass). Useful before casting. [1]

Example:
```
Object obj = "hello";
if (obj instanceof String) {
    String s = (String) obj;
}
```
Note: Since Java 16, you can combine instanceof with a pattern variable: `if (obj instanceof String s) { ... }` (check your Java version). [1]

***

## 12. Precedence and associativity — which operator runs first
- Precedence is the rule that determines the order in which operators are evaluated in an expression. [1]
- Associativity decides the direction for operators with the same precedence (left-to-right or right-to-left). Most binary operators are left-to-right; assignment and ternary are right-to-left. [1]

Simplified precedence table (higher to lower):
1. Postfix: expr++, expr-- [1]
2. Unary: ++expr, --expr, +, -, ~, !, casts [1]
3. Multiplicative: *, /, % [1]
4. Additive: +, - [1]
5. Shift: <<, >>, >>> [1]
6. Relational: <, >, <=, >=, instanceof [1]
7. Equality: ==, != [1]
8. Bitwise AND: & [1]
9. Bitwise XOR: ^ [1]
10. Bitwise OR: | [1]  
11. Logical AND: && [1]
12. Logical OR: || [1]  
13. Ternary: ? : [1]
14. Assignment: =, +=, -=, ... [1]

Example showing precedence:
```
int x = 2 + 3 * 4; // 2 + (3*4) = 14
int y = (2 + 3) * 4; // 20
```
When unsure, add parentheses to express intent. [1]

***

## 13. Common pitfalls — clear and simple explanations
- Integer division: 7/2 = 3 (not 3.5) unless you cast. Always check types. [1]
- Using == with objects: compares references, not contents. For Strings, use equals(). [1]
- Pre/post ++ inside complex expressions: can give surprising results; avoid using both in the same expression. [1]
- Implicit casting with compound assignment can hide conversions; explicit casts improve clarity. [1]
- Bitwise shifts on negative numbers: signed right shift (>>) preserves sign; >>> does not. [1]

***

## 14. Readable patterns and best practices
- Keep expressions simple: one operation per line when learning.  
- Use parentheses to make precedence explicit.  
- Prefer descriptive variable names rather than relying on operator tricks (like swapping without a temp).  
- Write unit tests for code that uses bitwise operators or tricky precedence. [1]

***

## 15. Worked examples — step by step
1) Post vs Pre increment:
```
int x = 3;
System.out.println(x++); // prints 3, x becomes 4
System.out.println(++x); // x becomes 5, prints 5
```
Explanation: postfix returns old value, prefix returns new value. [1]

2) Short-circuit to avoid NPE:
```
String s = null;
if (s != null && s.length() > 0) { ... } // safe
```
If s is null, second part is not evaluated. [1]

3) Mixing types:
```
int a = 5;
double b = 2.0;
double c = a / b; // 2.5 because one operand is double
```
At least one operand must be floating point for floating division. [1]

***

## 16. Interview‑level tricky questions (with solutions)
1) What prints: 
```
int x = 3;
System.out.println(x++ + ++x);
```
Solution: x++ returns 3 (x→4); ++x makes x 5 and returns 5; 3 + 5 = 8. [1]

2) Why use >>> instead of >>?
Answer: >>> fills left bits with zero (logical shift) and is useful when you want to treat the value as unsigned; >> keeps sign (arithmetic shift). [1]

3) What does `a += b` do when a is a byte?  
Answer: a += b performs an implicit cast that can differ from `a = (byte)(a + b)` semantics in narrow cases; be explicit in production code. [1]

***

## 17. Practice problems (progressive)
Short exercises to test understanding (solutions follow). Try to solve before peeking.

Beginner (10):
1. Compute: 7 / 2 and (double)7 / 2.  
2. What is "a" after: int a=1; a += 2 * 3;  
3. Evaluate: int x=5; x = x++ + ++x; what is x?  
4. What does "~0" evaluate to for a 32-bit int?  
5. Which is true: "abc" == new String("abc") ?  
6. What is result: 1 & 2 ?  (bitwise)  
7. Evaluate: 1 | 2 ?  
8. What prints: System.out.println(true && false || true);  
9. Using ternary: String r = (5%2==0)? "even":"odd"; value of r?  
10. Is `obj instanceof String` safe if obj is null? (true/false)

Intermediate (15):
11. Compute: int a=10; a >>= 2; value?  
12. Evaluate: int x = 2; System.out.println(x+++x); (space matters)  
13. What is difference between & and && when left operand is false and right throws exception?  
14. Predict: int a=5; int b=2; System.out.println(a/b*b);  
15. What happens if you do `double d = 1/2;`?  
16. Explain `x ^= y` meaning.  
17. Show how to swap a and b without a third variable using XOR (and limits).  
18. int v = -1; System.out.println(v >>> 1); what kind of value?  
19. What is precedence between + and << ?  
20. Given boolean b = (3 > 2) & (1/0 == 1); what happens?  
21. Evaluate: byte b = 10; b = (byte)(b * 2); why cast needed?  
22. Explain `a = a++` effect.  
23. If s1 = "a", s2 = "a"; is s1==s2 true? Why?  
24. int x = 1; x = x + (x = 4); what is x? (undefined behavior discussion)  
25. Show how compound assignment handles narrowing (example with short).

Advanced (15):
26. Write expression using shifts to multiply by 8.  
27. Why might `a + b` overflow and how to detect it?  
28. Show how to use bitmask to test if the 3rd bit is set.  
29. What is the result of `Integer.rotateLeft(x, n)` vs `<<`? (conceptually)  
30. Explain operator precedence of ?: vs assignment.  
31. Why is `if (x = 1) {}` invalid in Java?  
32. What does `(~x) + 1` compute for two's complement?  
33. Show a safe equals check for possibly null strings.  
34. Explain short-circuit advantage in performance.  
35. Show effect of mixing long and int in shifts (e.g., 1L << 33).  
36. Why are bitwise ops useful in competitive programming?  
37. Demonstrate how floating point affects + associativity (a+(b+c) != (a+b)+c).  
38. Distinguish between `^` on booleans and integers.  
39. Show how to implement conditional without ?: using logical operators.  
40. Explain Java language guarantee on evaluation order of operands left-to-right.

(Answers at end) [1]

***

## 18. Answers to practice problems (brief)
1. 7/2 = 3; (double)7/2 = 3.5. [1]
2. a = 1 + (2*3) → 7. [1]
3. Evaluate x = x++ + ++x with x starting 5: careful — result 11 (step-by-step: first x++ returns 5 (x→6), ++x → 7, 5+7 = 12; assigned to x yields 12). Note: Always compute stepwise to avoid confusion. [1]
4. ~0 = -1 for 32-bit int (all bits 1). [1]
5. "abc" == new String("abc") is false (different references); use equals() → true. [1]
6. 1 & 2 -> 0. [1]
7. 1 | 2 -> 3. [1]  
8. true && false || true -> (false) || true -> true. [1]  
9. r = "odd". [1]
10. obj instanceof String is false if obj is null (safe test). [1]
11. a=10; a >>= 2 → a = 10 >> 2 = 2. [1]
12. x+++x parses as (x++) + x. If x=2, prints 4. [1]
13. & evaluates both sides and will throw exception if right does; && will not evaluate right if left false. [1]
14. a/b*b uses integer division; a/b = 5 so 5*2 = 10 — shows order and truncation. [1]
15. double d = 1/2; d becomes 0.0 (since 1/2 int division =0, cast after), use 1.0/2 or (double)1/2. [1]
16. x ^= y is x = x ^ y (bitwise XOR assignment). [1]
17. XOR swap: a ^= b; b ^= a; a ^= b; (works for ints but can fail if same variable or overflow concerns). [1]
18. v=-1; v>>>1 is large positive integer (for 32-bit int, 2147483647). [1]
19. + has lower precedence than <<? Actually << has lower precedence than +? Refer to precedence table: multiplicative/additive before shift, so + has lower precedence than shift? Check table: multiplicative(*/%) > additive(+ -) > shift(<< >> >>>). So shift has lower precedence than additive. Use table. [1]
20. (3>2) & (1/0==1) — second expression divides by zero and will throw ArithmeticException because & evaluates both sides. [1]
21. b = (byte)(b * 2); cast needed because b*2 is int by default. [1]
22. a = a++ assigns old value to a; in effect value may remain same; avoid this pattern. [1]
23. s1 = "a", s2 = "a" may be true because of string pool internment; literals often refer to same object. [1]
24. x = x + (x = 4) — evaluation is left-to-right for operands, so RHS (x=4) runs first? Java guarantees left-to-right operand evaluation; result deterministic but confusing — avoid such code. [1]
25. Example: short s = 1; s += 2; no cast needed due to compound assignment; but s = s + 2 requires cast. [1]
26. Multiply by 8: x << 3. [1]
27. Addition overflow: e.g., Integer.MAX_VALUE + 1 wraps to negative; detect using checks like (b > 0 && a > Integer.MAX_VALUE - b). [1]
28. Test 3rd bit (0-based): (x & (1 << 3)) != 0. [1]
29. rotateLeft shifts bits circularly; << fills with zeros. rotateLeft preserves all bits by moving MSBs to LSBs. [1]
30. ?: has lower precedence than most operators but higher than assignment; it associates right-to-left. [1]
31. if (x = 1) invalid because = produces an int, Java requires boolean in if condition. [1]
32. (~x) + 1 computes -x in two's complement. [1]
33. Safe equals: "constant".equals(var) or Objects.equals(var, "constant"). [1]
34. Short-circuit avoids unnecessary computation or exceptions and can improve performance and safety. [1]
35. 1L << 33 shifts a long (64-bit); shifting more than 63 is masked by 0x3F, so be careful. [1]
36. Bitwise ops allow fast operations on sets/flags and low-level optimizations used in contests. [1]
37. Floating point addition is not associative due to rounding errors: (a+b)+c may differ from a+(b+c). [1]
38. ^ on booleans is logical XOR; on integers it's bitwise XOR. [1]
39. Conditional without ?: can be written with if/else and assignments. [1]
40. Java guarantees left-to-right evaluation of operands; this removes many undefined behaviors common in other languages. [1]

(If you want the fully expanded line-by-line reasoning for each numbered answer, I can append that.) [1]

***

## 19. Quick reference cheatsheet (single page)
- Arithmetic: + - * / %  (use cast for floats) [1]
- Increment/decrement: ++x / x++  (prefix vs postfix) [1]
- Relational: < > <= >= == != (primitives vs objects) [1]
- Logical: && || !  (short-circuit) [1]  
- Bitwise: & | ^ ~  (integer-level) [1]  
- Shift: << >> >>>  (left, signed-right, unsigned-right) [1]
- Ternary: cond ? a : b  (expression form) [1]
- Type check: instanceof  (safe casting check) [1]
- Precedence tip: use parentheses for clarity. [1]

***

## 20. Extra resources
- Official Java tutorial on operators for definitions and precedence table. [1]
- Interactive practice (Programiz, GeeksforGeeks) for more examples and quizzes. [3][4]

***
