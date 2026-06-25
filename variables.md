# Variables in Java

## 1. What is a Variable?
A variable is a name given to a memory location where a value can be stored and changed during program execution. In simple words, it is a labeled box that holds data.

### Why Java uses variables
Programs need to store information such as age, marks, price, name, or status. Variables make it possible to keep this data, use it later, update it, and pass it around in a program.

### Example
```java
int age = 21;
String name = "Raj";
double price = 499.50;
```
Here, `age`, `name`, and `price` are variables.

### Story example
Imagine a school register. Each student has a box with their details written on it. If the student’s marks change, you update the same box instead of creating a new register every time. That is how a variable works in a program.

***

## 2. Why Variables Are Needed
Variables are needed because programs constantly work with changing data. Without variables, we would have to write values directly everywhere, which makes code difficult to read and change.

### Main reasons
- To store data.
- To reuse data.
- To change values when needed.
- To make programs readable.
- To keep calculations organized.

### Example
```java
int marks = 80;
int bonus = 5;
int total = marks + bonus;
```
Here, `marks`, `bonus`, and `total` help us work with values clearly.

### Story example
Think of a bank account. The balance keeps changing as money is deposited or withdrawn. A variable is like that balance: it holds the current value and can be updated anytime.

***

## 3. Variable Declaration
Declaration means telling Java that a variable exists and what type of data it will store.

### Syntax
```java
dataType variableName;
```

### Example
```java
int age;
String city;
double salary;
```
This tells Java that `age` will store an integer, `city` will store text, and `salary` will store decimal values.

### Important point
At declaration, the variable name is created, but no value is assigned yet.

### Story example
Before keeping items in a drawer, you first label the drawer. Declaration is like creating the labeled drawer.

***

## 4. Variable Initialization
Initialization means giving a variable its first value.

### Syntax
```java
dataType variableName = value;
```

### Example
```java
int age = 21;
String city = "Chennai";
double salary = 35000.0;
```

### Declaration and initialization together
You can declare and initialize in one line.

### Example
```java
int marks = 90;
```

### Declaration and initialization separately
```java
int marks;
marks = 90;
```

### Story example
After labeling the drawer, you place the first item inside it. That first item is the initial value.

***

## 5. Variable Reassignment
Reassignment means changing the value of an already initialized variable.

### Example
```java
int score = 50;
score = 75;
```
The variable `score` first holds 50 and later holds 75.

### Another example
```java
String name = "Asha";
name = "Meena";
```

### Important point
The variable name stays the same, but the stored value changes.

### Story example
A classroom notice board may show today’s schedule. Tomorrow, the same board is reused with a new schedule. The board stays the same; the content changes.

***

## 6. Variable Naming Rules
Java has rules for writing variable names.

### Rules
- A variable name must start with a letter, `_`, or `$`.
- It cannot start with a number.
- It cannot contain spaces.
- It cannot be a Java keyword.
- Case matters in Java.

### Valid names
```java
int age;
int _count;
int $value;
int totalMarks;
```

### Invalid names
```java
int 1age;
int class;
int my age;
```

### Story example
A name tag should be readable and valid. You cannot write something that breaks the rules of the system. Variable names also must follow Java’s system rules.

***

## 7. camelCase Naming Convention
camelCase is the standard style for variable names in Java. The first word starts with a lowercase letter, and every new word starts with a capital letter.

### Examples
- `studentName`
- `totalMarks`
- `accountBalance`
- `isValid`

### Why camelCase is useful
It makes code easier to read and understand. It also matches Java coding style.

### Good practice
Choose names that clearly show meaning.

### Example
- Good: `monthlySalary`
- Weak: `ms`

### Story example
Imagine a file label like “studentFeeAmount” instead of “sfa”. The longer one is easier to understand quickly. That is why camelCase and meaningful names matter.

***

## 8. Local Variables
Local variables are declared inside a method, constructor, or block. They can be used only inside that area.

### Example
```java
void display() {
    int x = 10;
    System.out.println(x);
}
```
Here, `x` is a local variable.

### Key features
- Visible only inside the block where they are declared.
- Must be initialized before use.
- Do not get default values.

### Story example
A notebook used during one class period is local to that class. Once the class ends, that notebook is no longer used. Local variables work in a similar way.

***

## 9. Instance Variables
Instance variables are declared inside a class but outside methods. They belong to an object.

### Example
```java
class Student {
    String name;
    int age;
}
```
Every `Student` object can have its own `name` and `age`.

### Key features
- Belong to objects.
- Each object gets its own copy.
- Stored with the object.
- Get default values if not initialized.

### Story example
Think of each student having their own personal profile card. One student’s card can show one name and age, and another student’s card can show different values. That is how instance variables work.

***

## 10. Static Variables
Static variables belong to the class, not to individual objects. Only one copy exists for the whole class.

### Example
```java
class Student {
    static String collegeName = "ABC College";
}
```
All students share the same `collegeName`.

### Key features
- Shared by all objects.
- One copy for the class.
- Useful for common data.

### Story example
A school name board at the entrance belongs to the school, not to one student. Every student sees the same school name. That is similar to a static variable.

***

## 11. Variable Scope
Scope means the part of the program where a variable can be accessed.

### Main idea
A variable can only be used inside the region where it is visible. Outside that area, Java does not allow access.

### Types of scope
- Block scope.
- Method scope.
- Class scope.

### Story example
A key may open only one room, not the entire building. Scope works like that: a variable is usable only in its allowed area.

***

## 12. Block Scope
A block is a section of code inside `{ }`. Variables declared inside a block exist only inside that block.

### Example
```java
if (true) {
    int x = 10;
    System.out.println(x);
}
```
The variable `x` cannot be used outside the `if` block.

### Another example
```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```
`i` is available only inside the loop.

### Story example
A temporary pass used only inside one room is useful only for that room. Once you leave the room, the pass is no longer valid. That is block scope.

***

## 13. Method Scope
Variables declared inside a method are available only in that method.

### Example
```java
void calculate() {
    int result = 100;
    System.out.println(result);
}
```
`result` exists only in `calculate()`.

### Important point
Another method cannot directly use `result` because it is outside its scope.

### Story example
A recipe written on one page is used only while cooking that dish. Another recipe page has its own ingredients. That is method scope.

***

## 14. Class Scope
Variables declared inside a class but outside methods are part of class scope. These are usually instance variables or static variables.

### Example
```java
class Car {
    String model;
    static int wheels = 4;
}
```

### Important point
Class scope does not mean the same access for every variable. Instance variables belong to objects, and static variables belong to the class.

### Story example
A building has shared items like the building name and also personal items like each resident’s room number. Both are part of the building, but they behave differently.

***

## 15. Variable Lifetime
Lifetime means how long a variable exists in memory.

### Main idea
Some variables live only during a method call. Some live as long as the object exists. Some live as long as the class is loaded.

### Types
- Local variable lifetime.
- Instance variable lifetime.
- Static variable lifetime.

### Story example
A working note may exist only for one meeting, a personal notebook may exist as long as the person keeps it, and a school notice board may remain for many years. These are different lifetimes.

***

## 16. Local Variable Lifetime
A local variable exists only while the method or block is running.

### Example
```java
void test() {
    int a = 5;
}
```
When `test()` finishes, `a` is gone.

### Important point
Local variables do not continue after the method ends.

### Story example
A kitchen timer used for one cooking task is useful only for that task. Once the task ends, the timer is no longer needed.

***

## 17. Instance Variable Lifetime
An instance variable lives as long as the object is alive.

### Example
```java
Student s = new Student();
```
The object exists on the heap, and its instance variables stay alive with it.

### Important point
If the object is no longer reachable, its data can be removed by garbage collection later.

### Story example
A student’s profile stays useful as long as the student record exists in the system. If the record is deleted, the stored details are no longer needed.

***

## 18. Static Variable Lifetime
A static variable lives as long as the class is loaded in the JVM.

### Example
```java
class Demo {
    static int count = 0;
}
```

### Important point
There is one shared copy for the class, not one per object.

### Story example
A common school timetable is kept for the entire school year. It remains available for everyone until the school updates it.

***

## 19. Variable Memory Concepts
Java uses memory to store data while a program runs. The two important memory areas are stack and heap.

### Basic idea
- Stack is mainly used for method calls and local variables.
- Heap is used for objects created using `new`.

### Story example
Think of stack as a temporary desk where you keep active papers during work, and heap as a storage room where objects are kept.

***

## 20. Variable Storage
Storage means where the variable’s data is kept during execution.

### Basic view
- Primitive local variables are often associated with stack behavior.
- Objects are stored in the heap.
- Reference variables store a link to objects.

### Example
```java
Person p = new Person();
```
`p` is a reference variable, and the `Person` object is on the heap.

### Story example
A phone contact list entry is not the person itself. It is only a reference to that person’s details. That is similar to a reference variable.

***

## 21. Stack Memory
Stack memory is used for method execution and local variables.

### Features
- Fast.
- Automatically managed.
- Memory is released when the method ends.

### Example
```java
void run() {
    int a = 10;
}
```

### What happens
When `run()` starts, a stack frame is created. When `run()` ends, that frame disappears.

### Story example
A chef uses a small working table for the current dish. Once the dish is done, the table is cleared for the next dish. That is stack memory.

***

## 22. Heap Memory
Heap memory is used for objects created with `new`.

### Features
- Used for object storage.
- Shared among all parts of the program.
- Objects remain until no longer needed and collected.

### Example
```java
Student s = new Student();
```

### Story example
A warehouse stores boxes that belong to different customers. The boxes stay there until they are no longer needed. That is similar to heap memory.

***

## 23. Primitive Variables
Primitive variables store actual values directly.

### Java primitive types
- `byte`
- `short`
- `int`
- `long`
- `float`
- `double`
- `char`
- `boolean`

### Examples
```java
byte b = 10;
short s = 200;
int age = 21;
long population = 8000000000L;
float rate = 4.5f;
double price = 99.99;
char grade = 'A';
boolean active = true;
```

### What each type means
- `byte`: very small whole numbers.
- `short`: small whole numbers.
- `int`: common whole numbers.
- `long`: larger whole numbers.
- `float`: decimal values with less precision.
- `double`: decimal values with more precision.
- `char`: a single character.
- `boolean`: true or false.

### Story example
A calculator with fixed buttons can store different kinds of simple values: number, decimal, letter, or yes/no. Primitive variables are like that simple set of buttons.

***

## 24. Reference Variables
Reference variables store the reference to an object, not the object itself.

### Example
```java
Student s = new Student();
```
Here, `s` refers to the `Student` object.

### Important point
The object lives on the heap, while the reference variable points to it.

### Another example
```java
Student s1 = new Student();
Student s2 = s1;
```
Now both `s1` and `s2` point to the same object.

### Story example
A map pin does not contain the building itself. It only points to the building’s location. A reference variable works in a similar way.

***

## 25. Primitive vs Reference Variables
Primitive variables and reference variables behave differently.

| Primitive | Reference |
|---|---|
| Stores actual value | Stores reference to object |
| Simple data types | Object-related data |
| Examples: `int`, `double`, `boolean` | Examples: classes, arrays, `String` |
| Copying gives a new value | Copying gives another reference |

### Example
```java
int a = 10;
int b = a;
```
Here, `b` gets a copy of the value 10.

```java
Student s1 = new Student();
Student s2 = s1;
```
Here, `s2` points to the same object as `s1`.

### Story example
If you copy a coin, the original and copy are separate. But if you copy a room key pointer, both refer to the same room. Primitive variables act more like the coin; reference variables act more like the key pointer.

***

## 26. Default Values of Variables
Default values are automatic values given by Java to instance and static variables when no value is assigned.

### Default values
- `byte`, `short`, `int`, `long` → `0`
- `float`, `double` → `0.0`
- `char` → `'\u0000'`
- `boolean` → `false`
- reference types → `null`

### Example
```java
class Demo {
    int x;
    boolean flag;
    String name;
}
```
Here, `x` becomes `0`, `flag` becomes `false`, and `name` becomes `null`.

### Important point
Local variables do not get default values. They must be initialized before use.

### Story example
A new notebook page may already have printed headings, but the blank spaces are empty until you write in them. Instance and static variables get default values; local variables do not.

***

## 27. Variable Shadowing
Shadowing happens when a local variable or parameter has the same name as an instance variable.

### Example
```java
class Student {
    int age = 20;

    void show() {
        int age = 10;
        System.out.println(age);
    }
}
```
Inside `show()`, the local `age` hides the instance `age`.

### What happens
Java uses the nearest variable name it finds first. So the local one is used inside the method.

### Story example
If two people in the same room have the same name, and you call that name, you may first notice the person standing nearest to you. Shadowing works in a similar way.

***

## 28. The `this` Keyword
`this` refers to the current object.

### Example
```java
class Student {
    int age;

    Student(int age) {
        this.age = age;
    }
}
```
Here, `this.age` means the instance variable, and `age` means the parameter.

### Why it is useful
It removes confusion when names are the same.

### Other use
It can also be used to call current class methods or constructors in some cases.

### Story example
If someone says “my book,” they mean the book that belongs to them. In Java, `this` means “the current object.”

***

## 29. `final` Variables
A `final` variable cannot be reassigned after it has been given a value.

### Example
```java
final int MAX_MARKS = 100;
```
`MAX_MARKS` cannot be changed later.

### Important point
For object references, `final` means the reference cannot point to a different object, but the object itself may still change if it is mutable.

### Example
```java
final Student s = new Student();
```
You cannot make `s` point to another `Student` object later.

### Story example
A fixed rule on a notice board cannot be edited once it is locked. That is like a `final` variable.

***

## 30. Variable Type Casting
Type casting means converting one data type into another.

### Why it is needed
Sometimes we need to move from a smaller type to a larger type, or from a larger type to a smaller type.

### Two types
- Implicit casting.
- Explicit casting.

### Story example
A small container can be poured into a bigger one easily, but pouring a big amount into a small container requires care. Casting works in a similar way.

***

## 31. Implicit Casting
Implicit casting happens automatically when Java converts a smaller type to a larger type.

### Example
```java
int a = 10;
double b = a;
```
Java automatically changes `int` to `double`.

### Another example
```java
char c = 'A';
int x = c;
```
The character can be converted to its numeric form automatically.

### Story example
A small cup can be placed inside a bigger cup without effort. Implicit casting is automatic like that.

***

## 32. Explicit Casting
Explicit casting means you manually tell Java to convert one type into another.

### Example
```java
double a = 10.75;
int b = (int) a;
```
Here, `b` becomes `10`.

### Important point
Explicit casting may lose data.

### Another example
```java
int x = 65;
char c = (char) x;
```
The number is converted to a character.

### Story example
If you pour a big bottle into a small cup, some liquid may spill. Explicit casting can also lose part of the value.

***

## 33. Variable-Based Practice
To master variables, practice using them in real code.

### Try these
- Store student marks and calculate total.
- Store product price and apply discount.
- Store employee name and salary.
- Store login status using `boolean`.
- Store a character grade using `char`.

### Example
```java
int english = 88;
int math = 92;
int total = english + math;
double average = total / 2.0;
```

### Story example
A shop owner keeps different notebooks for stock, sales, and customer names. In code, different variables hold different kinds of data.

***

## 34. Memory Diagram Practice
Memory diagrams help you understand how variables and objects connect.

### What to draw
- Primitive variables holding values.
- Reference variables pointing to objects.
- Multiple references pointing to one object.
- Local variables disappearing after the method ends.

### Example
```java
Student s1 = new Student();
Student s2 = s1;
```
Draw one object on the heap and two references pointing to it.

### Story example
A house can be marked on two maps. Both maps point to the same house. That is how multiple references work.

***

## 35. Common Real-World Examples
Variables are everywhere in programming.

### Example 1: Exam system
```java
int marks = 91;
boolean passed = true;
```

### Example 2: Shopping app
```java
double price = 999.99;
double discount = 100.0;
double finalPrice = price - discount;
```

### Example 3: User profile
```java
String username = "raj123";
int loginCount = 5;
```

### Story example
A mobile app changes values all the time: balance, status, cart items, profile name. Variables are what make this possible.

***

## 36. Mastery Order
If you want to become strong in variables, learn in this order:
1. What a variable is.
2. Declaration, initialization, reassignment.
3. Naming rules and camelCase.
4. Local, instance, and static variables.
5. Scope and lifetime.
6. Stack and heap.
7. Primitive and reference variables.
8. Default values, shadowing, `this`, and `final`.
9. Type casting.
10. Practice with code and memory diagrams.

### Story example
Learning variables is like building a house. First you learn the bricks, then the structure, then the wiring, and finally how everything works together.

***

## 37. Final Mastery Notes
Variables are not just syntax. They are the base of how Java stores data, changes values, and manages memory.

### What you should understand deeply
- How variables are declared and used.
- How scope controls visibility.
- How lifetime controls existence.
- How primitives differ from references.
- How memory works with objects.
- How `this`, `final`, and casting affect behavior.

### Simple truth
If you understand variables very well, many later Java topics become easier because they all depend on the same basic idea.

***

## Quick Revision Notes
- Variable = named storage for data.
- Declaration = create the variable.
- Initialization = give first value.
- Reassignment = change value.
- Scope = where variable can be used.
- Lifetime = how long variable exists.
- Local = inside method or block.
- Instance = belongs to object.
- Static = belongs to class.
- Primitive = stores actual value.
- Reference = points to object.
- `this` = current object.
- `final` = cannot be reassigned.
- Implicit casting = automatic conversion.
- Explicit casting = manual conversion.
