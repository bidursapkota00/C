# Complete C Programming Course Guide

## Course Duration: 19 Hours

## Table of Contents

1. [User-Defined Functions](#user-defined-functions)
2. [Arrays and Strings](#arrays-and-strings)
3. [Structures](#structures)
4. [Pointers](#pointers)

In C, a macro is a fragment of code defined using the preprocessor directive #define.
Macros allow code substitution before compilation, meaning the compiler sees the replaced text — not the macro itself.

```c
#define PI 3.14159
#define SQUARE(x) ((x) * (x))
```

```c
#include <stdio.h>

//int add(int*, int*);
void add(int*, int*, int*);

int main() {
	int a = 5, b = 10, sum = 0;
	add(&a, &b, &sum);
	printf("Sum is: %d", sum);
	return 0;
}

void add(int *a, int *b, int *sum) {
	*a = 20;
	*sum = *a + *b;
}

/*
int add(int *a, int *b) {
	int sum;
	sum = *a + *b;
	return sum;
}
*/
```

Excellent — “`static`” in **C** is one of those keywords that seems simple at first but actually affects **scope**, **lifetime**, **linkage**, and **memory** depending on where and how it’s used. Let’s go through everything clearly and systematically 👇

---

## 🧩 1️⃣ What `static` means in general

`static` is a **storage class specifier**.
It tells the compiler two main things:

1. **Lifetime:** The variable exists **for the entire program run** (not destroyed after leaving its scope).
2. **Visibility (Scope):** It’s visible only **within the file or function where it’s declared**.

So `static` makes a variable **persistent** but **restricted in visibility**.

---

## 🏠 2️⃣ Static Variables

### (a) **Static Local Variable (Inside a function)**

When declared **inside a function**, a static variable:

- Retains its value **between function calls**.
- Is **initialized only once**, not every time the function runs.
- Has **function scope** (visible only inside that function).
- Is stored in **data segment**, not on stack.

#### Example:

```c
#include <stdio.h>

void counter() {
    static int count = 0;  // initialized only once
    count++;
    printf("Count = %d\n", count);
}

int main() {
    counter();  // Count = 1
    counter();  // Count = 2
    counter();  // Count = 3
    return 0;
}
```

**Explanation:**
`count` is initialized only once and **retains its value** between calls.
If it weren’t static, it would reset to 0 every time the function runs.

---

### (b) **Static Global Variable (Outside any function)**

When declared **outside any function**, it:

- Has **file scope** (visible only in that `.c` file).
- Cannot be accessed from other source files (even with `extern`).
- Lifetime is **the entire program**.

#### Example:

**file1.c**

```c
#include <stdio.h>
static int secret = 42;  // visible only in file1.c

void showSecret() {
    printf("Secret = %d\n", secret);
}
```

**file2.c**

```c
#include <stdio.h>
extern int secret;  // ❌ error: cannot access static variable in another file

int main() {
    showSecret();  // works if showSecret() is not static
}
```

**Explanation:**
`static` here gives **internal linkage**, so `secret` cannot be seen outside `file1.c`.

---

## 🧱 3️⃣ Static Functions

When you declare a function as `static`, it:

- Is **visible only within that file**.
- Cannot be called from another file (even with a prototype).

#### Example:

```c
// file1.c
static void helper() {
    printf("Hidden helper\n");
}

void publicFunc() {
    helper();  // works here
}
```

```c
// file2.c
void publicFunc();
void helper();  // ❌ no access (static in file1.c)
```

This is used to **limit function visibility** and **avoid name collisions** across multiple source files.

---

## 🧮 4️⃣ Static with Arrays and Structures

You can also make arrays or structures static:

```c
void demo() {
    static int arr[3] = {1, 2, 3};
    arr[0]++;
    printf("%d\n", arr[0]);
}
```

The array persists across calls.

---

## ⚙️ 5️⃣ Initialization Rules

- Static variables are **initialized only once**.
- Default initialization is **zero** if no explicit value is provided.
- Initialization must be **constant** (no runtime values).

#### Example:

```c
static int x;         // initialized to 0
static int y = 5;     // explicitly initialized
static int z = func(); // ❌ error: cannot initialize with a function call
```

---

## 🧠 6️⃣ Memory Placement

Static variables are stored in the **data segment** (not stack or heap).

| Variable Type        | Storage      | Lifetime               | Scope          |
| -------------------- | ------------ | ---------------------- | -------------- |
| Auto (default local) | Stack        | Until function returns | Function       |
| Static local         | Data segment | Entire program         | Function       |
| Static global        | Data segment | Entire program         | File           |
| Global (non-static)  | Data segment | Entire program         | Entire program |

---

## 🧰 7️⃣ Use Cases

✅ **Static local variables**

- To keep track of state across function calls.
- For counters, caching, etc.

✅ **Static global variables**

- To hide internal data from other files (encapsulation).

✅ **Static functions**

- To make helper/utility functions private to a module.

---

## ⚠️ 8️⃣ Common Pitfalls

❌ Using static variables in recursive functions → keeps old state unexpectedly.
❌ Overusing static → reduces modularity and testability.
❌ Forgetting `static` on helper functions → may cause name conflicts between files.

---

## 🧭 9️⃣ Quick Summary Table

| Where declared   | Lifetime         | Scope         | Default Value | Example                |
| ---------------- | ---------------- | ------------- | ------------- | ---------------------- |
| Inside function  | Program lifetime | Function only | 0             | `static int count;`    |
| Outside function | Program lifetime | File only     | 0             | `static int total;`    |
| Static function  | N/A              | File only     | N/A           | `static void helper()` |

---

If you’d like, I can also show **a visual memory layout diagram** of where static variables live (stack vs heap vs data segment).
Would you like that?

---

## Module 1: Overview of Computer Software & Programming Languages (3 hours)

### 1.1 System Software

**Definition**: System software is a type of computer program designed to run a computer's hardware and application programs, acting as an interface between the hardware and user applications.

**Types of System Software**:

- **Operating Systems (OS)**

  - Manages computer hardware and software resources
  - Examples: Windows, Linux, macOS, Unix, Android
  - Functions: Process management, memory management, file management, device management

- **Device Drivers**

  - Specialized programs that control specific hardware devices
  - Enable communication between OS and hardware components
  - Examples: Printer drivers, graphics card drivers, network adapter drivers

- **Utility Programs**

  - Tools for system maintenance and optimization
  - Examples: Antivirus software, disk cleaners, backup utilities, file compression tools

- **Language Translators**
  - Compilers: Convert entire source code to machine code
  - Interpreters: Execute code line by line
  - Assemblers: Convert assembly language to machine code

### 1.2 Application Software

**Definition**: Programs designed to perform specific tasks for end-users, built on top of system software.

**Categories**:

- **General Purpose Software**

  - Word processors (MS Word, Google Docs)
  - Spreadsheets (Excel, Google Sheets)
  - Presentation software (PowerPoint, Keynote)
  - Web browsers (Chrome, Firefox, Safari)
  - Media players (VLC, Windows Media Player)

- **Specific Purpose Software**

  - Accounting software (QuickBooks, Tally)
  - Inventory management systems
  - Hotel management systems
  - Hospital information systems

- **Custom Software**
  - Developed for specific organizations
  - Tailored to unique business requirements
  - Examples: Enterprise resource planning (ERP) systems

### 1.3 General Software Features and Recent Trends

**Essential Software Features**:

- User-friendly interface
- Reliability and stability
- Security features
- Scalability
- Performance optimization
- Cross-platform compatibility
- Regular updates and maintenance
- Documentation and support

**Recent Trends in Software Development**:

- **Cloud Computing**

  - Software as a Service (SaaS)
  - Platform as a Service (PaaS)
  - Infrastructure as a Service (IaaS)

- **Artificial Intelligence and Machine Learning**

  - Intelligent automation
  - Predictive analytics
  - Natural language processing

- **Mobile-First Development**

  - Responsive design
  - Progressive web apps
  - Native mobile applications

- **DevOps and Continuous Integration**

  - Automated testing
  - Continuous deployment
  - Agile methodologies

- **Internet of Things (IoT)**

  - Connected devices
  - Smart home applications
  - Industrial automation

- **Blockchain Technology**

  - Decentralized applications
  - Cryptocurrency platforms
  - Smart contracts

- **Low-Code/No-Code Platforms**
  - Visual development environments
  - Rapid application development
  - Citizen developers

### 1.4 Generation of Programming Languages

**First Generation (1GL) - Machine Language**

- Binary code (0s and 1s)
- Directly executed by computer hardware
- Machine-specific
- Difficult to write and debug
- Example: `10110000 01100001`

**Second Generation (2GL) - Assembly Language**

- Uses mnemonics (symbolic codes)
- Requires assembler for translation
- More readable than machine language
- Still hardware-dependent
- Example: `MOV AL, 61h`

**Third Generation (3GL) - High-Level Languages**

- Human-readable syntax
- Platform-independent (mostly)
- Requires compiler or interpreter
- Examples: C, C++, Java, Python, FORTRAN, COBOL
- Features: Variables, control structures, functions

**Fourth Generation (4GL) - Very High-Level Languages**

- Closer to human language
- Focus on what to do rather than how
- Database query languages
- Examples: SQL, MATLAB, R
- Used for specific applications

**Fifth Generation (5GL) - Artificial Intelligence Languages**

- Based on problem-solving using constraints
- Uses visual programming
- Examples: Prolog, Mercury, LISP
- Focus on AI and machine learning

### 1.5 Categorization of High-Level Languages

**Based on Programming Paradigm**:

- **Procedural Languages**

  - Step-by-step instructions
  - Examples: C, Pascal, FORTRAN
  - Focus on procedures and functions

- **Object-Oriented Languages**

  - Based on objects and classes
  - Examples: Java, C++, Python
  - Features: Encapsulation, inheritance, polymorphism

- **Functional Languages**

  - Based on mathematical functions
  - Examples: Haskell, Lisp, Erlang
  - Emphasis on immutability

- **Scripting Languages**

  - Interpreted languages
  - Examples: JavaScript, Python, Perl
  - Used for automation and web development

- **Logic Programming Languages**
  - Based on formal logic
  - Examples: Prolog, Datalog
  - Rule-based programming

**Based on Level of Abstraction**:

- **Low-level**: Assembly language
- **Middle-level**: C (combines low and high-level features)
- **High-level**: Java, Python, JavaScript

**Based on Application Domain**:

- **System Programming**: C, C++
- **Web Development**: JavaScript, PHP, Ruby
- **Data Science**: Python, R
- **Mobile Development**: Swift, Kotlin, Java

---

## Module 2: Problem Solving Using Computer (3 hours)

### 2.1 Problem Analysis

**Definition**: The process of understanding and breaking down a problem into manageable components before developing a solution.

**Steps in Problem Analysis**:

1. **Problem Identification**

   - Clearly define what needs to be solved
   - Understand the requirements
   - Identify constraints and limitations

2. **Input Analysis**

   - Determine what data is required
   - Identify data types and formats
   - Consider data validation requirements

3. **Output Analysis**

   - Define expected results
   - Determine output format
   - Specify presentation requirements

4. **Process Analysis**

   - Identify processing steps
   - Determine computational requirements
   - Consider alternative approaches

5. **Decomposition**
   - Break complex problems into sub-problems
   - Identify relationships between components
   - Determine module interfaces

**Example Problem**: Calculate the area of a circle

- **Input**: Radius of the circle
- **Process**: Apply formula (Area = π × r²)
- **Output**: Area value

### 2.2 Algorithm Development and Flowchart

**Algorithm**:

An algorithm is a step-by-step procedure to solve a problem, written in simple English statements.

**Characteristics of a Good Algorithm**:

- Finiteness: Must terminate after finite steps
- Definiteness: Each step must be clearly defined
- Input: Zero or more inputs
- Output: At least one output
- Effectiveness: Steps must be basic and executable

**Example Algorithm** (Find largest of three numbers):

```
Step 1: Start
Step 2: Input three numbers a, b, c
Step 3: If a > b AND a > c then
        Print "a is largest"
Step 4: Else if b > c then
        Print "b is largest"
Step 5: Else
        Print "c is largest"
Step 6: Stop
```

**Flowchart**:

A flowchart is a graphical representation of an algorithm using standard symbols.

**Standard Flowchart Symbols**:

- **Oval**: Start/End (Terminal)
- **Parallelogram**: Input/Output
- **Rectangle**: Process/Computation
- **Diamond**: Decision/Condition
- **Arrow**: Flow direction
- **Circle**: Connector

**Example Flowchart Description** (Add two numbers):

```
[Start] → [Input A, B] → [Sum = A + B] → [Output Sum] → [End]
```

**Advantages of Flowcharts**:

- Visual representation aids understanding
- Easy to debug and maintain
- Facilitates communication among team members
- Serves as program documentation

### 2.3 Compilation and Execution

**Source Code to Execution Process**:

1. **Writing Source Code**

   - Write program in high-level language
   - Save with appropriate extension (.c for C programs)

2. **Preprocessing**

   - Handles preprocessor directives (#include, #define)
   - Includes header files
   - Performs macro expansion
   - Produces expanded source code

3. **Compilation**

   - Compiler translates source code to assembly language
   - Performs syntax checking
   - Generates object code (.obj or .o files)
   - Reports compilation errors if any

4. **Assembly**

   - Assembler converts assembly code to machine code
   - Creates object files

5. **Linking**

   - Linker combines object files
   - Links library functions
   - Resolves external references
   - Creates executable file (.exe or .out)

6. **Loading**

   - Loader loads executable into memory
   - Allocates memory space

7. **Execution**
   - CPU executes instructions
   - Program runs and produces output

**Types of Errors During Compilation**:

- **Syntax Errors**: Violations of language rules
- **Semantic Errors**: Logically incorrect statements
- **Linker Errors**: Unresolved references

### 2.4 Debugging and Testing

**Debugging**:

The process of identifying, analyzing, and removing errors (bugs) from a program.

**Types of Errors**:

1. **Syntax Errors**

   - Grammatical mistakes in code
   - Detected by compiler
   - Example: Missing semicolon, undeclared variable
   - Easy to fix

2. **Runtime Errors**

   - Occur during program execution
   - Example: Division by zero, array index out of bounds
   - Program crashes or behaves unexpectedly

3. **Logical Errors**
   - Program runs but produces incorrect results
   - Most difficult to detect
   - Example: Wrong formula, incorrect condition
   - Requires thorough testing

**Debugging Techniques**:

- Code review and inspection
- Using print statements to trace execution
- Using debugger tools (breakpoints, step execution)
- Divide and conquer approach
- Rubber duck debugging (explaining code aloud)

**Testing**:

The process of evaluating a program to ensure it works correctly.

**Testing Strategies**:

1. **Unit Testing**

   - Test individual functions/modules
   - Verify each component works correctly

2. **Integration Testing**

   - Test combined modules
   - Verify interfaces work properly

3. **System Testing**

   - Test complete system
   - Verify system meets requirements

4. **Acceptance Testing**
   - Final testing by end-users
   - Verify system meets user needs

**Test Case Design**:

- Normal/valid inputs
- Boundary values
- Invalid inputs
- Edge cases

### 2.5 Programming Documentation

**Definition**: Written material that explains how a program works and how to use it.

**Types of Documentation**:

1. **Internal Documentation (Comments)**

   - Written within the source code
   - Explains purpose and logic
   - Types in C:
     - Single-line: `// This is a comment`
     - Multi-line: `/* This is a multi-line comment */`

2. **External Documentation**

**User Documentation**:

- User manuals
- Installation guides
- Quick reference guides
- FAQs and troubleshooting

**Technical Documentation**:

- System design documents
- Algorithm descriptions
- Data structure documentation
- API documentation

**Program Documentation Should Include**:

- Program name and purpose
- Author and date
- Input requirements
- Output description
- Algorithm/logic explanation
- Variable descriptions
- Function descriptions
- Assumptions and limitations
- Example usage

**Best Practices**:

- Write clear and concise comments
- Update documentation when code changes
- Use meaningful variable names
- Follow consistent formatting
- Document complex logic thoroughly
- Include examples where helpful

---

## Module 3: Introduction to 'C' Programming (4 hours)

### 3.1 Character Set, Keywords, and Data Types

**C Character Set**:

Characters used to write C programs:

1. **Letters**: A-Z, a-z
2. **Digits**: 0-9
3. **Special Characters**:
   - `+ - * / % = < > ! & | ^ ~ ? : ; , . ' " ( ) [ ] { } # \ _`
4. **White Spaces**: Blank space, tab, newline, carriage return

**C Keywords (Reserved Words)**:

32 keywords with predefined meanings (cannot be used as identifiers):

```
auto        break       case        char
const       continue    default     do
double      else        enum        extern
float       for         goto        if
int         long        register    return
short       signed      sizeof      static
struct      switch      typedef     union
unsigned    void        volatile    while
```

**Identifiers**:

Names given to variables, functions, arrays, etc.

**Rules for Identifiers**:

- Must begin with letter or underscore
- Can contain letters, digits, and underscores
- Cannot be a keyword
- Case-sensitive (age and Age are different)
- No spaces allowed
- Maximum 31 characters (standard)

**Valid**: `count`, `_total`, `num1`, `studentName`
**Invalid**: `1count`, `student name`, `int`, `@value`

**Data Types**:

Data types specify the type of data a variable can hold.

**1. Primary (Basic) Data Types**:

| Data Type     | Size         | Range                                    | Format Specifier |
| ------------- | ------------ | ---------------------------------------- | ---------------- |
| char          | 1 byte       | -128 to 127                              | %c               |
| unsigned char | 1 byte       | 0 to 255                                 | %c               |
| int           | 2 or 4 bytes | -32,768 to 32,767 (2 bytes)              | %d               |
| unsigned int  | 2 or 4 bytes | 0 to 65,535 (2 bytes)                    | %u               |
| short int     | 2 bytes      | -32,768 to 32,767                        | %hd              |
| long int      | 4 bytes      | -2,147,483,648 to 2,147,483,647          | %ld              |
| float         | 4 bytes      | 3.4E-38 to 3.4E+38 (6 decimal places)    | %f               |
| double        | 8 bytes      | 1.7E-308 to 1.7E+308 (15 decimal places) | %lf              |
| long double   | 10 bytes     | 3.4E-4932 to 1.1E+4932                   | %Lf              |

**2. Derived Data Types**:

- Arrays
- Pointers
- Structures
- Unions

**3. Enumeration Data Type**:

- User-defined data type (enum)

**4. Void Type**:

- Represents no value

### 3.2 Preprocessor Directives

**Definition**: Instructions to the preprocessor that are processed before compilation begins. Always start with `#`.

**Common Preprocessor Directives**:

**1. #include**

- Includes header files in the program
- Two forms:
  ```c
  #include <stdio.h>    // System header files
  #include "myheader.h" // User-defined header files
  ```

**Common Header Files**:

- `stdio.h` - Standard Input/Output functions
- `conio.h` - Console Input/Output (non-standard)
- `math.h` - Mathematical functions
- `string.h` - String manipulation functions
- `stdlib.h` - Standard library functions
- `time.h` - Date and time functions

**2. #define**

- Defines macros (constants or code snippets)

```c
#define PI 3.14159
#define MAX 100
#define SQUARE(x) ((x) * (x))
```

**3. #undef**

- Undefines a previously defined macro

```c
#undef PI
```

**4. Conditional Directives**

```c
#ifdef MACRO_NAME
    // Code if MACRO_NAME is defined
#endif

#ifndef MACRO_NAME
    // Code if MACRO_NAME is not defined
#endif

#if condition
    // Code if condition is true
#elif another_condition
    // Code if another_condition is true
#else
    // Code if all conditions are false
#endif
```

**Example Program**:

```c
#include <stdio.h>
#define PI 3.14159
#define AREA(r) (PI * (r) * (r))

int main() {
    float radius = 5.0;
    printf("Area = %.2f\n", AREA(radius));
    return 0;
}
```

### 3.3 Constants and Variables

**Constants**:

Fixed values that cannot be changed during program execution.

**Types of Constants**:

**1. Integer Constants**:

```c
123          // Decimal
0123         // Octal (prefix 0)
0x123        // Hexadecimal (prefix 0x)
123L         // Long integer
123U         // Unsigned integer
```

**2. Floating-Point Constants**:

```c
3.14         // Standard form
3.14F        // Float
3.14L        // Long double
3.14E2       // Exponential form (314.0)
```

**3. Character Constants**:

```c
'A'          // Single character
'\n'         // Newline (escape sequence)
'\t'         // Tab
'\\'         // Backslash
'\''         // Single quote
'\"'         // Double quote
```

**4. String Constants**:

```c
"Hello World"
"C Programming"
""           // Empty string
```

**Defining Constants**:

**Method 1: Using #define**

```c
#define MAX 100
#define PI 3.14159
```

**Method 2: Using const keyword**

```c
const int MAX = 100;
const float PI = 3.14159;
```

**Variables**:

Named memory locations that store data values which can change during program execution.

**Variable Declaration**:

```c
data_type variable_name;

int age;
float salary;
char grade;
double distance;
```

**Variable Initialization**:

```c
int age = 25;
float salary = 50000.50;
char grade = 'A';
```

**Multiple Variables**:

```c
int a, b, c;
int x = 5, y = 10, z = 15;
```

**Variable Scope**:

**1. Local Variables**:

- Declared inside a function or block
- Accessible only within that function/block

```c
void func() {
    int x = 10;  // Local variable
}
```

**2. Global Variables**:

- Declared outside all functions
- Accessible throughout the program

```c
int x = 10;  // Global variable

void func() {
    printf("%d", x);  // Can access x
}
```

### 3.4 Operators and Statements

**Operators**:

Symbols that perform operations on operands.

**1. Arithmetic Operators**:

```c
+    Addition           a + b
-    Subtraction        a - b
*    Multiplication     a * b
/    Division           a / b
%    Modulus            a % b (remainder)
```

**2. Relational Operators**:

```c
==   Equal to          a == b
!=   Not equal to      a != b
>    Greater than      a > b
<    Less than         a < b
>=   Greater or equal  a >= b
<=   Less or equal     a <= b
```

**3. Logical Operators**:

```c
&&   Logical AND       (a > b) && (c < d)
||   Logical OR        (a > b) || (c < d)
!    Logical NOT       !(a > b)
```

**4. Assignment Operators**:

```c
=     Simple assignment     a = b
+=    Add and assign        a += b  (a = a + b)
-=    Subtract and assign   a -= b  (a = a - b)
*=    Multiply and assign   a *= b  (a = a * b)
/=    Divide and assign     a /= b  (a = a / b)
%=    Modulus and assign    a %= b  (a = a % b)
```

**5. Increment/Decrement Operators**:

```c
++    Increment    a++ (post), ++a (pre)
--    Decrement    a-- (post), --a (pre)
```

**Difference**:

```c
int a = 5, b;
b = a++;  // b = 5, a = 6 (post-increment)
b = ++a;  // a = 6, b = 6 (pre-increment)
```

**6. Bitwise Operators**:

```c
&     Bitwise AND      a & b
|     Bitwise OR       a | b
^     Bitwise XOR      a ^ b
~     Bitwise NOT      ~a
<<    Left shift       a << 2
>>    Right shift      a >> 2
```

**7. Conditional (Ternary) Operator**:

```c
condition ? expression1 : expression2

max = (a > b) ? a : b;
```

**8. Special Operators**:

```c
sizeof    Returns size of variable      sizeof(int)
,         Comma operator                a = (b = 3, b + 2)
&         Address operator              &a
*         Pointer operator              *ptr
```

**Operator Precedence** (High to Low):

1. `()` `[]` `->` `.`
2. `!` `~` `++` `--` `+` `-` `*` `&` `sizeof` (unary)
3. `*` `/` `%`
4. `+` `-`
5. `<<` `>>`
6. `<` `<=` `>` `>=`
7. `==` `!=`
8. `&`
9. `^`
10. `|`
11. `&&`
12. `||`
13. `?:`
14. `=` `+=` `-=` etc.
15. `,`

**Statements**:

**1. Expression Statement**:

```c
a = b + c;
printf("Hello");
x++;
```

**2. Compound Statement (Block)**:

```c
{
    int x = 10;
    printf("%d", x);
    x++;
}
```

**3. Null Statement**:

```c
;  // Does nothing
```

**Example Program**:

```c
#include <stdio.h>

int main() {
    int a = 10, b = 20, c;

    // Arithmetic operations
    c = a + b;
    printf("Sum: %d\n", c);

    // Relational operation
    if (a < b) {
        printf("a is less than b\n");
    }

    // Logical operation
    if (a > 0 && b > 0) {
        printf("Both are positive\n");
    }

    return 0;
}
```

---

## Module 4: Input and Output (3 hours)

### 4.1 Formatted Input/Output

**Output: printf() Function**

Used to display formatted output to the standard output (screen).

**Syntax**:

```c
printf("format string", argument_list);
```

**Format Specifiers**:

```c
%d or %i    Integer (signed)
%u          Unsigned integer
%f          Float (6 decimal places default)
%lf         Double
%c          Character
%s          String
%x or %X    Hexadecimal
%o          Octal
%p          Pointer address
%%          Print % symbol
```

**Width and Precision Specifiers**:

```c
%5d         Minimum 5 characters wide, right-aligned
%-5d        Minimum 5 characters wide, left-aligned
%05d        Pad with zeros
%.2f        2 decimal places
%8.2f       8 characters wide, 2 decimal places
```

**Examples**:

```c
int num = 42;
float pi = 3.14159;
char ch = 'A';

printf("Integer: %d\n", num);              // Integer: 42
printf("Float: %f\n", pi);                 // Float: 3.141590
printf("Float: %.2f\n", pi);               // Float: 3.14
printf("Character: %c\n", ch);             // Character: A
printf("Width: %5d\n", num);               // Width:    42
printf("Zero-padded: %05d\n", num);        // Zero-padded: 00042
```

**Escape Sequences**:

```c
\n    Newline
\t    Tab
\b    Backspace
\r    Carriage return
\\    Backslash
\'    Single quote
\"    Double quote
\0    Null character
\a    Alert (beep)
```

**Input: scanf() Function**

Used to read formatted input from the standard input (keyboard).

**Syntax**:

```c
scanf("format string", &variable_list);
```

**Important**: Use `&` (address operator) before variable names (except for strings/arrays).

**Examples**:

```c
int age;
float salary;
char grade;

printf("Enter age: ");
scanf("%d", &age);

printf("Enter salary: ");
scanf("%f", &salary);

printf("Enter grade: ");
scanf(" %c", &grade);  // Space before %c to consume whitespace

printf("Age: %d, Salary: %.2f, Grade: %c\n", age, salary, grade);
```

**Reading Multiple Values**:

```c
int a, b, c;
printf("Enter three numbers: ");
scanf("%d %d %d", &a, &b, &c);

// Or with separator
scanf("%d,%d,%d", &a, &b, &c);  // Input: 10,20,30
```

**Reading Strings**:

```c
char name[50];
printf("Enter name: ");
scanf("%s", name);  // No & for strings (reads until whitespace)

// For strings with spaces
scanf("%[^\n]s", name);  // Reads until newline
```

**Common Issues with scanf()**:

- Buffer issues when mixing character and number input
- Use `fflush(stdin)` or consume newline character

```c
int num;
char ch;

scanf("%d", &num);
scanf(" %c", &ch);  // Space before %c consumes leftover newline
```

### 4.2 Character Input/Output

**Character Output: putchar() Function**

Outputs a single character to the screen.

**Syntax**:

```c
putchar(character);
```

**Examples**:

```c
char ch = 'A';
putchar(ch);           // Outputs: A
putchar('B');          // Outputs: B
putchar('\n');         // Outputs: newline
```

**Character Input: getchar() Function**

Reads a single character from the keyboard.

**Syntax**:

```c
char_variable = getchar();
```

**Examples**:

```c
char ch;
printf("Enter a character: ");
ch = getchar();
printf("You entered: ");
putchar(ch);
```

**String Output: puts() Function**

Outputs a string to the screen and automatically adds a newline.

**Syntax**:

```c
puts(string);
```

**Examples**:

```c
char name[] = "John";
puts(name);                    // Outputs: John\n
puts("Hello World");           // Outputs: Hello World\n
```

**String Input: gets() Function**

Reads a line of text (including spaces) until newline.

**Syntax**:

```c
gets(string_variable);
```

**Note**: `gets()` is unsafe and deprecated. Use `fgets()` instead.

**Examples**:

```c
char name[50];

// Using gets() (not recommended)
printf("Enter name: ");
gets(name);

// Using fgets() (recommended)
printf("Enter name: ");
fgets(name, sizeof(name), stdin);
```

**Comparison: printf/scanf vs putchar/getchar vs puts/gets**:

| Function       | Purpose          | Advantages                    |
| -------------- | ---------------- | ----------------------------- |
| printf()       | Formatted output | Flexible, multiple formats    |
| scanf()        | Formatted input  | Read multiple types           |
| putchar()      | Character output | Fast, simple                  |
| getchar()      | Character input  | Fast, simple                  |
| puts()         | String output    | Automatically adds newline    |
| gets()/fgets() | String input     | Reads entire line with spaces |

### 4.3 Programs Using Input/Output Statements

**Program 1: Simple Calculator**

```c
#include <stdio.h>

int main() {
    float num1, num2, result;
    char operator;

    printf("Enter first number: ");
    scanf("%f", &num1);

    printf("Enter operator (+, -, *, /): ");
    scanf(" %c", &operator);

    printf("Enter second number: ");
    scanf("%f", &num2);

    switch(operator) {
        case '+':
            result = num1 + num2;
            break;
        case '-':
            result = num1 - num2;
            break;
        case '*':
            result = num1 * num2;
            break;
        case '/':
            if(num2 != 0)
                result = num1 / num2;
            else {
                printf("Error: Division by zero!\n");
                return 1;
            }
            break;
        default:
            printf("Invalid operator!\n");
            return 1;
    }

    printf("%.2f %c %.2f = %.2f\n", num1, operator, num2, result);
    return 0;
}
```

**Program 2: Temperature Converter**

```c
#include <stdio.h>

int main() {
    float celsius, fahrenheit;

    printf("Temperature Converter\n");
    printf("Enter temperature in Celsius: ");
    scanf("%f", &celsius);

    fahrenheit = (celsius * 9/5) + 32;

    printf("%.2f°C = %.2f°F\n", celsius, fahrenheit);

    return 0;
}
```

**Program 3: Student Information System**

```c
#include <stdio.h>

int main() {
    char name[50];
    int rollNo;
    float marks1, marks2, marks3, average;
    char grade;

    printf("=== Student Information System ===\n\n");

    printf("Enter student name: ");
    fgets(name, sizeof(name), stdin);

    printf("Enter roll number: ");
    scanf("%d", &rollNo);

    printf("Enter marks in three subjects:\n");
    printf("Subject 1: ");
    scanf("%f", &marks1);
    printf("Subject 2: ");
    scanf("%f", &marks2);
    printf("Subject 3: ");
    scanf("%f", &marks3);

    average = (marks1 + marks2 + marks3) / 3;

    if(average >= 90)
        grade = 'A';
    else if(average >= 80)
        grade = 'B';
    else if(average >= 70)
        grade = 'C';
    else if(average >= 60)
        grade = 'D';
    else
        grade = 'F';

    printf("\n=== Student Report ===\n");
    printf("Name: %s", name);
    printf("Roll Number: %d\n", rollNo);
    printf("Marks: %.2f, %.2f, %.2f\n", marks1, marks2, marks3);
    printf("Average: %.2f\n", average);
    printf("Grade: %c\n", grade);

    return 0;
}
```

**Program 4: Area Calculator**

```c
#include <stdio.h>
#define PI 3.14159

int main() {
    int choice;
    float result;

    printf("=== Area Calculator ===\n");
    printf("1. Circle\n");
    printf("2. Rectangle\n");
    printf("3. Triangle\n");
    printf("Enter choice (1-3): ");
    scanf("%d", &choice);

    switch(choice) {
        case 1: {
            float radius;
            printf("Enter radius: ");
            scanf("%f", &radius);
            result = PI * radius * radius;
            printf("Area of circle: %.2f\n", result);
            break;
        }
        case 2: {
            float length, width;
            printf("Enter length: ");
            scanf("%f", &length);
            printf("Enter width: ");
            scanf("%f", &width);
            result = length * width;
            printf("Area of rectangle: %.2f\n", result);
            break;
        }
        case 3: {
            float base, height;
            printf("Enter base: ");
            scanf("%f", &base);
            printf("Enter height: ");
            scanf("%f", &height);
            result = 0.5 * base * height;
            printf("Area of triangle: %.2f\n", result);
            break;
        }
        default:
            printf("Invalid choice!\n");
    }
    return 0;
}
```

**Program 5: Character Type Checker**

```c
#include <stdio.h>

int main() {
    char ch;

    printf("Enter a character: ");
    ch = getchar();

    printf("You entered: ");
    putchar(ch);
    printf("\n");

    if(ch >= 'A' && ch <= 'Z')
        printf("It is an uppercase letter.\n");
    else if(ch >= 'a' && ch <= 'z')
        printf("It is a lowercase letter.\n");
    else if(ch >= '0' && ch <= '9')
        printf("It is a digit.\n");
    else
        printf("It is a special character.\n");

    return 0;
}
```

---

## Module 5: Control Statements (6 hours)

### 5.1 Introduction to Control Statements

**Definition**: Control statements determine the flow of program execution, allowing programs to make decisions and repeat actions.

**Types of Control Statements**:

1. **Sequential Control**: Statements execute in order (default behavior)
2. **Selection/Decision Control**: Execute statements based on conditions
   - if statement
   - if...else statement
   - Nested if...else
   - else if ladder
   - switch statement
3. **Iteration/Loop Control**: Repeat statements multiple times
   - while loop
   - do...while loop
   - for loop
4. **Jump Control**: Transfer control to different parts of program
   - goto statement
   - break statement
   - continue statement
   - return statement

**Need for Control Statements**:

- Make decisions based on conditions
- Repeat operations without writing duplicate code
- Create flexible and interactive programs
- Handle different scenarios dynamically

### 5.2 Decision Control Statements

#### 5.2.1 The goto Statement

**Definition**: Unconditional jump statement that transfers control to a labeled statement.

**Syntax**:

```c
goto label;
...
label:
    statement;
```

**Example 1: Simple goto**

```c
#include <stdio.h>

int main() {
    int num;

    printf("Enter a positive number: ");
    scanf("%d", &num);

    if(num <= 0) {
        printf("Invalid input!\n");
        goto end;
    }

    printf("Square: %d\n", num * num);

    end:
    printf("Program ended.\n");
    return 0;
}
```

**Example 2: goto in loop**

```c
#include <stdio.h>

int main() {
    int i = 1;

    start:
    if(i <= 5) {
        printf("%d ", i);
        i++;
        goto start;
    }

    printf("\n");
    return 0;
}
```

**Disadvantages of goto**:

- Makes code difficult to understand (spaghetti code)
- Hard to debug and maintain
- Can be replaced with structured control statements
- Should be avoided in modern programming

**When goto might be acceptable**:

- Breaking out of deeply nested loops
- Error handling in some cases
- Very specific system-level programming

#### 5.2.2 The if Statement

**Definition**: Executes a block of code only if a condition is true.

**Syntax**:

```c
if(condition) {
    statement(s);
}
```

**Flowchart Logic**:

```
condition → true → execute statements
         ↓ false
         ↓
    next statement
```

**Example 1: Simple if**

```c
#include <stdio.h>

int main() {
    int age;

    printf("Enter your age: ");
    scanf("%d", &age);

    if(age >= 18) {
        printf("You are eligible to vote.\n");
    }

    printf("Program ended.\n");
    return 0;
}
```

**Example 2: Checking positive number**

```c
#include <stdio.h>

int main() {
    int num;

    printf("Enter a number: ");
    scanf("%d", &num);

    if(num > 0) {
        printf("%d is positive.\n", num);
    }

    if(num == 0) {
        printf("Number is zero.\n");
    }

    if(num < 0) {
        printf("%d is negative.\n", num);
    }

    return 0;
}
```

#### 5.2.3 The if...else Statement

**Definition**: Executes one block if condition is true, another block if false.

**Syntax**:

```c
if(condition) {
    statement(s);  // executed if condition is true
}
else {
    statement(s);  // executed if condition is false
}
```

**Example 1: Even or Odd**

```c
#include <stdio.h>

int main() {
    int num;

    printf("Enter a number: ");
    scanf("%d", &num);

    if(num % 2 == 0) {
        printf("%d is even.\n", num);
    }
    else {
        printf("%d is odd.\n", num);
    }

    return 0;
}
```

**Example 2: Voting Eligibility**

```c
#include <stdio.h>

int main() {
    int age;

    printf("Enter your age: ");
    scanf("%d", &age);

    if(age >= 18) {
        printf("You are eligible to vote.\n");
    }
    else {
        printf("You are not eligible to vote.\n");
        printf("Wait for %d more years.\n", 18 - age);
    }

    return 0;
}
```

**Nested if...else**:

**Syntax**:

```c
if(condition1) {
    if(condition2) {
        statement(s);
    }
    else {
        statement(s);
    }
}
else {
    statement(s);
}
```

**Example: Finding largest of three numbers**

```c
#include <stdio.h>

int main() {
    int a, b, c;

    printf("Enter three numbers: ");
    scanf("%d %d %d", &a, &b, &c);

    if(a >= b) {
        if(a >= c) {
            printf("%d is largest.\n", a);
        }
        else {
            printf("%d is largest.\n", c);
        }
    }
    else {
        if(b >= c) {
            printf("%d is largest.\n", b);
        }
        else {
            printf("%d is largest.\n", c);
        }
    }

    return 0;
}
```

**else if Ladder**:

**Syntax**:

```c
if(condition1) {
    statement(s);
}
else if(condition2) {
    statement(s);
}
else if(condition3) {
    statement(s);
}
else {
    statement(s);
}
```

**Example: Grade Calculator**

```c
#include <stdio.h>

int main() {
    float marks;

    printf("Enter marks (0-100): ");
    scanf("%f", &marks);

    if(marks >= 90) {
        printf("Grade: A+\n");
    }
    else if(marks >= 80) {
        printf("Grade: A\n");
    }
    else if(marks >= 70) {
        printf("Grade: B\n");
    }
    else if(marks >= 60) {
        printf("Grade: C\n");
    }
    else if(marks >= 50) {
        printf("Grade: D\n");
    }
    else {
        printf("Grade: F (Fail)\n");
    }

    return 0;
}
```

**Example: Calculator using if...else**

```c
#include <stdio.h>

int main() {
    float num1, num2, result;
    char op;

    printf("Enter expression (e.g., 5 + 3): ");
    scanf("%f %c %f", &num1, &op, &num2);

    if(op == '+') {
        result = num1 + num2;
        printf("%.2f + %.2f = %.2f\n", num1, num2, result);
    }
    else if(op == '-') {
        result = num1 - num2;
        printf("%.2f - %.2f = %.2f\n", num1, num2, result);
    }
    else if(op == '*') {
        result = num1 * num2;
        printf("%.2f * %.2f = %.2f\n", num1, num2, result);
    }
    else if(op == '/') {
        if(num2 != 0) {
            result = num1 / num2;
            printf("%.2f / %.2f = %.2f\n", num1, num2, result);
        }
        else {
            printf("Error: Division by zero!\n");
        }
    }
    else {
        printf("Invalid operator!\n");
    }

    return 0;
}
```

#### 5.2.4 The switch Statement

**Definition**: Multi-way decision statement that tests a variable against multiple constant values.

**Syntax**:

```c
switch(expression) {
    case constant1:
        statement(s);
        break;
    case constant2:
        statement(s);
        break;
    ...
    default:
        statement(s);
}
```

**Rules**:

- Expression must evaluate to integer or character
- Case values must be constants (not variables)
- Case values must be unique
- break statement exits the switch
- default is optional and executes if no case matches
- Multiple cases can share the same code block

**Example 1: Days of Week**

```c
#include <stdio.h>

int main() {
    int day;

    printf("Enter day number (1-7): ");
    scanf("%d", &day);

    switch(day) {
        case 1:
            printf("Monday\n");
            break;
        case 2:
            printf("Tuesday\n");
            break;
        case 3:
            printf("Wednesday\n");
            break;
        case 4:
            printf("Thursday\n");
            break;
        case 5:
            printf("Friday\n");
            break;
        case 6:
            printf("Saturday\n");
            break;
        case 7:
            printf("Sunday\n");
            break;
        default:
            printf("Invalid day number!\n");
    }

    return 0;
}
```

**Example 2: Calculator using switch**

```c
#include <stdio.h>

int main() {
    float num1, num2, result;
    char operator;

    printf("Enter first number: ");
    scanf("%f", &num1);
    printf("Enter operator (+, -, *, /): ");
    scanf(" %c", &operator);
    printf("Enter second number: ");
    scanf("%f", &num2);

    switch(operator) {
        case '+':
            result = num1 + num2;
            printf("%.2f + %.2f = %.2f\n", num1, num2, result);
            break;
        case '-':
            result = num1 - num2;
            printf("%.2f - %.2f = %.2f\n", num1, num2, result);
            break;
        case '*':
            result = num1 * num2;
            printf("%.2f * %.2f = %.2f\n", num1, num2, result);
            break;
        case '/':
            if(num2 != 0) {
                result = num1 / num2;
                printf("%.2f / %.2f = %.2f\n", num1, num2, result);
            }
            else {
                printf("Error: Division by zero!\n");
            }
            break;
        default:
            printf("Invalid operator!\n");
    }

    return 0;
}
```

**Example 3: Grouping Multiple Cases**

```c
#include <stdio.h>

int main() {
    char ch;

    printf("Enter a character: ");
    scanf("%c", &ch);

    switch(ch) {
        case 'a':
        case 'e':
        case 'i':
        case 'o':
        case 'u':
        case 'A':
        case 'E':
        case 'I':
        case 'O':
        case 'U':
            printf("%c is a vowel.\n", ch);
            break;
        default:
            if((ch >= 'a' && ch <= 'z') || (ch >= 'A' && ch <= 'Z')) {
                printf("%c is a consonant.\n", ch);
            }
            else {
                printf("%c is not a letter.\n", ch);
            }
    }

    return 0;
}
```

**Example 4: Menu-Driven Program**

```c
#include <stdio.h>

int main() {
    int choice;
    float num1, num2;

    printf("=== Menu ===\n");
    printf("1. Addition\n");
    printf("2. Subtraction\n");
    printf("3. Multiplication\n");
    printf("4. Division\n");
    printf("5. Exit\n");
    printf("Enter choice: ");
    scanf("%d", &choice);

    switch(choice) {
        case 1:
        case 2:
        case 3:
        case 4:
            printf("Enter two numbers: ");
            scanf("%f %f", &num1, &num2);
            break;
        case 5:
            printf("Exiting...\n");
            return 0;
        default:
            printf("Invalid choice!\n");
            return 1;
    }

    switch(choice) {
        case 1:
            printf("Sum = %.2f\n", num1 + num2);
            break;
        case 2:
            printf("Difference = %.2f\n", num1 - num2);
            break;
        case 3:
            printf("Product = %.2f\n", num1 * num2);
            break;
        case 4:
            if(num2 != 0)
                printf("Quotient = %.2f\n", num1 / num2);
            else
                printf("Cannot divide by zero!\n");
            break;
    }

    return 0;
}
```

**Difference between if...else and switch**:

| if...else                  | switch                             |
| -------------------------- | ---------------------------------- |
| Can test any condition     | Tests only equality                |
| Works with any data type   | Works with int/char only           |
| Can use ranges             | Uses specific values               |
| More flexible              | More readable for multiple choices |
| Slower for many conditions | Faster for many cases              |

### 5.3 Loop Control Statements

#### 5.3.1 The while Loop

**Definition**: Executes a block of code repeatedly as long as a condition is true. Condition is checked before execution (entry-controlled loop).

**Syntax**:

```c
while(condition) {
    statement(s);
    // Update expression
}
```

**Flowchart Logic**:

```
→ check condition → true → execute statements → repeat
                  ↓ false
                  ↓
              exit loop
```

**Example 1: Print numbers 1 to 10**

```c
#include <stdio.h>

int main() {
    int i = 1;

    while(i <= 10) {
        printf("%d ", i);
        i++;
    }
    printf("\n");

    return 0;
}
```

**Example 2: Sum of first N natural numbers**

```c
#include <stdio.h>

int main() {
    int n, i = 1, sum = 0;

    printf("Enter n: ");
    scanf("%d", &n);

    while(i <= n) {
        sum = sum + i;
        i++;
    }

    printf("Sum of first %d numbers = %d\n", n, sum);
    return 0;
}
```

**Example 3: Factorial calculation**

```c
#include <stdio.h>

int main() {
    int n, i = 1;
    long factorial = 1;

    printf("Enter a number: ");
    scanf("%d", &n);

    while(i <= n) {
        factorial = factorial * i;
        i++;
    }

    printf("Factorial of %d = %ld\n", n, factorial);
    return 0;
}
```

**Example 4: Reverse a number**

```c
#include <stdio.h>

int main() {
    int num, reverse = 0, digit;

    printf("Enter a number: ");
    scanf("%d", &num);

    while(num != 0) {
        digit = num % 10;
        reverse = reverse * 10 + digit;
        num = num / 10;
    }

    printf("Reversed number: %d\n", reverse);
    return 0;
}
```

**Example 5: Menu-driven program with while**

```c
#include <stdio.h>

int main() {
    int choice;

    while(1) {  // Infinite loop
        printf("\n=== Menu ===\n");
        printf("1. Say Hello\n");
        printf("2. Display Date\n");
        printf("3. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        if(choice == 1) {
            printf("Hello, World!\n");
        }
        else if(choice == 2) {
            printf("Today is a great day!\n");
        }
        else if(choice == 3) {
            printf("Exiting...\n");
            break;  // Exit the loop
        }
        else {
            printf("Invalid choice!\n");
        }
    }

    return 0;
}
```

#### 5.3.2 The do...while Loop

**Definition**: Executes a block of code at least once, then repeats as long as condition is true. Condition is checked after execution (exit-controlled loop).

**Syntax**:

```c
do {
    statement(s);
    // Update expression
} while(condition);
```

**Key Difference from while**: Executes at least once even if condition is initially false.

**Example 1: Print numbers 1 to 5**

```c
#include <stdio.h>

int main() {
    int i = 1;

    do {
        printf("%d ", i);
        i++;
    } while(i <= 5);

    printf("\n");
    return 0;
}
```

**Example 2: Input validation**

```c
#include <stdio.h>

int main() {
    int num;

    do {
        printf("Enter a positive number: ");
        scanf("%d", &num);

        if(num <= 0) {
            printf("Invalid! Please try again.\n");
        }
    } while(num <= 0);

    printf("You entered: %d\n", num);
    return 0;
}
```

**Example 3: Sum of digits**

```c
#include <stdio.h>

int main() {
    int num, sum = 0, digit;

    printf("Enter a number: ");
    scanf("%d", &num);

    do {
        digit = num % 10;
        sum = sum + digit;
        num = num / 10;
    } while(num != 0);

    printf("Sum of digits: %d\n", sum);
    return 0;
}
```

**Example 4: Menu with do...while**

```c
#include <stdio.h>

int main() {
    int choice;

    do {
        printf("\n=== Calculator Menu ===\n");
        printf("1. Add\n");
        printf("2. Subtract\n");
        printf("3. Multiply\n");
        printf("4. Divide\n");
        printf("5. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        if(choice >= 1 && choice <= 4) {
            float a, b;
            printf("Enter two numbers: ");
            scanf("%f %f", &a, &b);

            switch(choice) {
                case 1: printf("Sum = %.2f\n", a + b); break;
                case 2: printf("Difference = %.2f\n", a - b); break;
                case 3: printf("Product = %.2f\n", a * b); break;
                case 4:
                    if(b != 0)
                        printf("Quotient = %.2f\n", a / b);
                    else
                        printf("Cannot divide by zero!\n");
                    break;
            }
        }
        else if(choice != 5) {
            printf("Invalid choice!\n");
        }
    } while(choice != 5);

    printf("Thank you!\n");
    return 0;
}
```

**Example 5: Palindrome check**

```c
#include <stdio.h>

int main() {
    int num, original, reverse = 0, digit;

    printf("Enter a number: ");
    scanf("%d", &num);
    original = num;

    do {
        digit = num % 10;
        reverse = reverse * 10 + digit;
        num = num / 10;
    } while(num != 0);

    if(original == reverse) {
        printf("%d is a palindrome.\n", original);
    }
    else {
        printf("%d is not a palindrome.\n", original);
    }

    return 0;
}
```

#### 5.3.3 The for Loop

**Definition**: Most commonly used loop when the number of iterations is known. Combines initialization, condition, and update in one line.

**Syntax**:

```c
for(initialization; condition; update) {
    statement(s);
}
```

**Execution Flow**:

1. Initialization (executed once)
2. Condition check
3. If true: execute statements, then update
4. Repeat steps 2-3 until condition is false

**Example 1: Print numbers 1 to 10**

```c
#include <stdio.h>

int main() {
    int i;

    for(i = 1; i <= 10; i++) {
        printf("%d ", i);
    }
    printf("\n");

    return 0;
}
```

**Example 2: Multiplication table**

```c
#include <stdio.h>

int main() {
    int num, i;

    printf("Enter a number: ");
    scanf("%d", &num);

    printf("Multiplication table of %d:\n", num);
    for(i = 1; i <= 10; i++) {
        printf("%d x %d = %d\n", num, i, num * i);
    }

    return 0;
}
```

**Example 3: Factorial using for loop**

```c
#include <stdio.h>

int main() {
    int n, i;
    long factorial = 1;

    printf("Enter a number: ");
    scanf("%d", &n);

    for(i = 1; i <= n; i++) {
        factorial *= i;
    }

    printf("Factorial of %d = %ld\n", n, factorial);
    return 0;
}
```

**Example 4: Prime number check**

```c
#include <stdio.h>

int main() {
    int num, i, isPrime = 1;

    printf("Enter a number: ");
    scanf("%d", &num);

    if(num <= 1) {
        isPrime = 0;
    }
    else {
        for(i = 2; i <= num/2; i++) {
            if(num % i == 0) {
                isPrime = 0;
                break;
            }
        }
    }

    if(isPrime) {
        printf("%d is a prime number.\n", num);
    }
    else {
        printf("%d is not a prime number.\n", num);
    }

    return 0;
}
```

**Example 5: Fibonacci series**

```c
#include <stdio.h>

int main() {
    int n, i, first = 0, second = 1, next;

    printf("Enter number of terms: ");
    scanf("%d", &n);

    printf("Fibonacci Series: ");
    for(i = 0; i < n; i++) {
        if(i <= 1) {
            next = i;
        }
        else {
            next = first + second;
            first = second;
            second = next;
        }
        printf("%d ", next);
    }
    printf("\n");

    return 0;
}
```

**Nested for Loops**:

**Example 1: Pattern printing**

```c
#include <stdio.h>

int main() {
    int i, j, rows;

    printf("Enter number of rows: ");
    scanf("%d", &rows);

    for(i = 1; i <= rows; i++) {
        for(j = 1; j <= i; j++) {
            printf("* ");
        }
        printf("\n");
    }

    return 0;
}
```

**Example 2: Multiplication table (1-10)**

```c
#include <stdio.h>

int main() {
    int i, j;

    for(i = 1; i <= 10; i++) {
        printf("Table of %d:\n", i);
        for(j = 1; j <= 10; j++) {
            printf("%d x %d = %d\n", i, j, i * j);
        }
        printf("\n");
    }

    return 0;
}
```

**break and continue Statements**:

**break**: Exits the loop immediately

```c
#include <stdio.h>

int main() {
    int i;

    for(i = 1; i <= 10; i++) {
        if(i == 6) {
            break;  // Exit loop when i is 6
        }
        printf("%d ", i);
    }
    printf("\n");  // Output: 1 2 3 4 5

    return 0;
}
```

**continue**: Skips current iteration and moves to next

```c
#include <stdio.h>

int main() {
    int i;

    for(i = 1; i <= 10; i++) {
        if(i % 2 == 0) {
            continue;  // Skip even numbers
        }
        printf("%d ", i);
    }
    printf("\n");  // Output: 1 3 5 7 9

    return 0;
}
```

**Comparison of Loops**:

| Feature           | while              | do...while                    | for              |
| ----------------- | ------------------ | ----------------------------- | ---------------- |
| When to use       | Unknown iterations | At least one execution needed | Known iterations |
| Condition check   | Before execution   | After execution               | Before execution |
| Initialization    | Before loop        | Before loop                   | In loop header   |
| Update            | Inside loop        | Inside loop                   | In loop header   |
| Syntax complexity | Simple             | Moderate                      | Compact          |

### Practice Programs

**Program 1: Armstrong Number**

```c
#include <stdio.h>
#include <math.h>

int main() {
    int num, original, remainder, result = 0, n = 0;

    printf("Enter a number: ");
    scanf("%d", &num);
    original = num;

    // Count digits
    while(original != 0) {
        original /= 10;
        n++;
    }

    original = num;

    // Calculate sum of nth power of digits
    while(original != 0) {
        remainder = original % 10;
        result += pow(remainder, n);
        original /= 10;
    }

    if(result == num) {
        printf("%d is an Armstrong number.\n", num);
    }
    else {
        printf("%d is not an Armstrong number.\n", num);
    }

    return 0;
}
```

**Program 2: Pattern Printing**

```c
#include <stdio.h>

int main() {
    int i, j, rows = 5;

    // Pattern 1: Right triangle
    printf("Pattern 1:\n");
    for(i = 1; i <= rows; i++) {
        for(j = 1; j <= i; j++) {
            printf("* ");
        }
        printf("\n");
    }

    // Pattern 2: Inverted triangle
    printf("\nPattern 2:\n");
    for(i = rows; i >= 1; i--) {
        for(j = 1; j <= i; j++) {
            printf("* ");
        }
        printf("\n");
    }

    // Pattern 3: Pyramid
    printf("\nPattern 3:\n");
    for(i = 1; i <= rows; i++) {
        for(j = 1; j <= rows - i; j++) {
            printf(" ");
        }
        for(j = 1; j <= 2 * i - 1; j++) {
            printf("*");
        }
        printf("\n");
    }

    return 0;
}
```

---

## Additional Practice Exercises

### Module 1-2 Exercises

1. Write the algorithm and draw flowchart to find the largest of three numbers
2. Explain the difference between compiler and interpreter
3. Write an algorithm to check if a number is prime
4. Draw a flowchart to calculate factorial of a number

### Module 3 Exercises

1. Write a program to find the size of different data types
2. Create a program using preprocessor directives to calculate area of shapes
3. Write a program to swap two numbers without using a third variable
4. Demonstrate the use of all arithmetic and relational operators

### Module 4 Exercises

1. Write a program to read and display student information (name, roll, marks)
2. Create a program to convert temperature between Celsius, Fahrenheit, and Kelvin
3. Write a program to calculate simple and compound interest
4. Create a program to find the area and perimeter of different shapes

### Module 5 Exercises

1. Write a program to check if a year is a leap year
2. Create a menu-driven calculator with all operations
3. Write a program to print all prime numbers between 1 and 100
4. Create a program to print various patterns using nested loops
5. Write a program to find GCD and LCM of two numbers
6. Create a program to check if a number is perfect, palindrome, or Armstrong

# C Programming - Complete Notes

## User-Defined Functions, Arrays, Strings

---

## User-Defined Functions

### Introduction to Functions

A **function** is a self-contained block of code that performs a specific task. Functions help in:

- **Modularity**: Breaking down complex problems into smaller, manageable parts
- **Reusability**: Writing code once and using it multiple times
- **Maintainability**: Making code easier to debug and update
- **Abstraction**: Hiding implementation details

**Types of Functions:**

1. **Library Functions**: Pre-defined functions (e.g., `printf()`, `scanf()`, `strlen()`)
2. **User-Defined Functions**: Functions created by programmers

### Function Definition and Return Statement

**Syntax:**

```c
return_type function_name(parameter_list) {
    // Function body
    // Statements
    return value; // Optional, depends on return_type
}
```

**Components:**

- **return_type**: Data type of the value returned (int, float, char, void)
- **function_name**: Identifier for the function
- **parameter_list**: Input values (can be empty)
- **Function body**: Code to be executed
- **return statement**: Returns control to the calling function

**Example 1: Simple Function**

```c
int add(int a, int b) {
    int sum = a + b;
    return sum;
}
```

**Example 2: Function with No Return Value**

```c
void displayMessage() {
    printf("Welcome to C Programming!\n");
    // No return statement needed for void
}
```

**Example 3: Function with No Parameters**

```c
int getRandomNumber() {
    return 42;
}
```

**Return Statement Rules:**

- A function can have multiple return statements
- Once a return is executed, function terminates immediately
- void functions don't require return, but can use `return;` to exit early
- Return value must match the declared return_type

### Function Prototypes

A **function prototype** (also called function declaration) tells the compiler about:

- Function name
- Return type
- Number and types of parameters

**Syntax:**

```c
return_type function_name(parameter_types);
```

**Why Use Prototypes?**

- Allows calling functions before they are defined
- Enables type checking by the compiler
- Improves code organization
- Required when function is defined in another file

**Example:**

```c
#include <stdio.h>

// Function prototypes
int multiply(int, int);
void greet(void);
float calculateArea(float);

int main() {
    int result = multiply(5, 3);
    printf("Result: %d\n", result);
    greet();
    printf("Area: %.2f\n", calculateArea(5.5));
    return 0;
}

// Function definitions
int multiply(int x, int y) {
    return x * y;
}

void greet() {
    printf("Hello, User!\n");
}

float calculateArea(float radius) {
    return 3.14159 * radius * radius;
}
```

**Parameter Names in Prototypes:**

```c
// Both are valid
int add(int a, int b);    // With parameter names
int add(int, int);        // Without parameter names (preferred in prototypes)
```

### Function Invocation

**Function Call Syntax:**

```c
function_name(arguments);
```

**Example:**

```c
#include <stdio.h>

int square(int n) {
    return n * n;
}

int main() {
    int num = 5;
    int result = square(num);  // Function invocation
    printf("Square of %d is %d\n", num, result);
    return 0;
}
```

**Types of Function Calls:**

1. **Call by value**
2. **Call by reference**

### Call by Value

In **call by value**, a copy of the actual parameter is passed to the function. Changes made to parameters inside the function do not affect the original variables.

**Characteristics:**

- Original values remain unchanged
- Function works with copies
- Safe but may be inefficient for large data

**Example:**

```c
#include <stdio.h>

void modify(int x) {
    x = 100;
    printf("Inside function: x = %d\n", x);
}

int main() {
    int num = 10;
    printf("Before function call: num = %d\n", num);
    modify(num);
    printf("After function call: num = %d\n", num);
    return 0;
}

/* Output:
Before function call: num = 10
Inside function: x = 100
After function call: num = 10
*/
```

### Call by Reference

In **call by reference**, the address of the actual parameter is passed using pointers. Changes made inside the function affect the original variables.

**Characteristics:**

- Original values can be modified
- Uses pointer notation
- Memory efficient for large data
- Allows multiple return values through parameters

**Example:**

```c
#include <stdio.h>

void swap(int *x, int *y) {
    int temp = *x;
    *x = *y;
    *y = temp;
}

int main() {
    int a = 5, b = 10;
    printf("Before swap: a = %d, b = %d\n", a, b);
    swap(&a, &b);  // Passing addresses
    printf("After swap: a = %d, b = %d\n", a, b);
    return 0;
}

/* Output:
Before swap: a = 5, b = 10
After swap: a = 10, b = 5
*/
```

**Call by Value vs Call by Reference:**

| Aspect                  | Call by Value         | Call by Reference    |
| ----------------------- | --------------------- | -------------------- |
| What is passed          | Copy of value         | Address of variable  |
| Changes affect original | No                    | Yes                  |
| Memory usage            | More (creates copies) | Less (uses pointers) |
| Syntax                  | `func(x)`             | `func(&x)`           |
| Function parameter      | `void func(int x)`    | `void func(int *x)`  |

### Recursive Functions

**Recursion** is a technique where a function calls itself directly or indirectly to solve a problem.

**Components of Recursion:**

1. **Base Case**: Condition to stop recursion
2. **Recursive Case**: Function calls itself with modified parameters

**Example 1: Factorial**

```c
#include <stdio.h>

int factorial(int n) {
    // Base case
    if (n == 0 || n == 1) {
        return 1;
    }
    // Recursive case
    return n * factorial(n - 1);
}

int main() {
    int num = 5;
    printf("Factorial of %d is %d\n", num, factorial(num));
    return 0;
}

/* Execution trace for factorial(5):
factorial(5) = 5 * factorial(4)
factorial(4) = 4 * factorial(3)
factorial(3) = 3 * factorial(2)
factorial(2) = 2 * factorial(1)
factorial(1) = 1 (base case)
Result: 5 * 4 * 3 * 2 * 1 = 120
*/
```

**Example 2: Fibonacci Series**

```c
#include <stdio.h>

int fibonacci(int n) {
    if (n == 0) return 0;
    if (n == 1) return 1;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

int main() {
    int terms = 10;
    printf("Fibonacci series: ");
    for (int i = 0; i < terms; i++) {
        printf("%d ", fibonacci(i));
    }
    return 0;
}
```

**Example 3: Sum of Natural Numbers**

```c
#include <stdio.h>

int sum(int n) {
    if (n == 0) return 0;
    return n + sum(n - 1);
}

int main() {
    printf("Sum of 1 to 10: %d\n", sum(10));
    return 0;
}
```

**Recursion vs Iteration:**

| Aspect      | Recursion                        | Iteration        |
| ----------- | -------------------------------- | ---------------- |
| Readability | More intuitive for some problems | Can be verbose   |
| Memory      | Uses stack memory                | Uses less memory |
| Speed       | Generally slower                 | Generally faster |
| Termination | Base case required               | Loop condition   |

**Important Notes:**

- Always define a proper base case to avoid infinite recursion
- Recursion uses stack memory; too many calls can cause stack overflow
- Some problems are naturally recursive (tree traversal, divide and conquer)

---

## Arrays and Strings

### Defining an Array

An **array** is a collection of elements of the same data type stored in contiguous memory locations.

**Syntax:**

```c
data_type array_name[size];
```

**Characteristics:**

- Fixed size (defined at compile time)
- Elements accessed using index (0 to size-1)
- Stored in contiguous memory
- All elements must be of same type

**Array Declaration Examples:**

```c
int numbers[5];           // Array of 5 integers
float prices[10];         // Array of 10 floats
char name[20];            // Array of 20 characters
```

**Array Initialization:**

```c
// Method 1: During declaration
int arr[5] = {10, 20, 30, 40, 50};

// Method 2: Partial initialization (remaining elements = 0)
int arr[5] = {10, 20};  // arr = {10, 20, 0, 0, 0}

// Method 3: Without specifying size
int arr[] = {1, 2, 3, 4, 5};  // Size automatically = 5

// Method 4: After declaration
int arr[3];
arr[0] = 10;
arr[1] = 20;
arr[2] = 30;
```

**Memory Layout:**

```
If: int arr[5] = {10, 20, 30, 40, 50};
Memory: [10][20][30][40][50]
Index:   0   1   2   3   4
Address: 1000 1004 1008 1012 1016 (assuming 4 bytes per int)
```

### One Dimensional Arrays

A **one-dimensional array** is a linear collection of elements.

**Example 1: Basic Operations**

```c
#include <stdio.h>

int main() {
    int marks[5] = {85, 90, 78, 92, 88};

    // Accessing elements
    printf("First student marks: %d\n", marks[0]);
    printf("Last student marks: %d\n", marks[4]);

    // Modifying elements
    marks[2] = 80;

    // Traversing array
    printf("All marks: ");
    for (int i = 0; i < 5; i++) {
        printf("%d ", marks[i]);
    }

    return 0;
}
```

**Example 2: Finding Maximum Element**

```c
#include <stdio.h>

int main() {
    int arr[] = {45, 23, 78, 12, 90, 56};
    int size = sizeof(arr) / sizeof(arr[0]);
    int max = arr[0];

    for (int i = 1; i < size; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }

    printf("Maximum element: %d\n", max);
    return 0;
}
```

**Example 3: Array Input from User**

```c
#include <stdio.h>

int main() {
    int n, sum = 0;

    printf("Enter number of elements: ");
    scanf("%d", &n);

    int arr[n];  // Variable-length array (C99 feature)

    printf("Enter %d elements:\n", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
        sum += arr[i];
    }

    printf("Sum: %d\n", sum);
    printf("Average: %.2f\n", (float)sum / n);

    return 0;
}
```

**Example 4: Reversing an Array**

```c
#include <stdio.h>

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int size = 5;

    printf("Original array: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }

    // Reverse using two pointers
    for (int i = 0; i < size / 2; i++) {
        int temp = arr[i];
        arr[i] = arr[size - 1 - i];
        arr[size - 1 - i] = temp;
    }

    printf("\nReversed array: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }

    return 0;
}
```

### Multi-dimensional Arrays

**Multi-dimensional arrays** are arrays of arrays, commonly used for matrices and tables.

**Two-Dimensional Array Syntax:**

```c
data_type array_name[rows][columns];
```

**Declaration and Initialization:**

```c
// Method 1: With initialization
int matrix[3][3] = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// Method 2: Linear initialization
int matrix[3][3] = {1, 2, 3, 4, 5, 6, 7, 8, 9};

// Method 3: Partial initialization
int matrix[3][3] = {{1, 2}, {4}};  // Remaining = 0
```

**Memory Representation:**

```
matrix[2][3] stored as: [0][0] [0][1] [0][2] [1][0] [1][1] [1][2]
```

**Example 1: Matrix Input and Display**

```c
#include <stdio.h>

int main() {
    int rows, cols;

    printf("Enter rows and columns: ");
    scanf("%d %d", &rows, &cols);

    int matrix[rows][cols];

    // Input
    printf("Enter matrix elements:\n");
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            scanf("%d", &matrix[i][j]);
        }
    }

    // Display
    printf("Matrix:\n");
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```

**Example 2: Matrix Addition**

```c
#include <stdio.h>

int main() {
    int a[2][2] = {{1, 2}, {3, 4}};
    int b[2][2] = {{5, 6}, {7, 8}};
    int sum[2][2];

    // Addition
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            sum[i][j] = a[i][j] + b[i][j];
        }
    }

    // Display result
    printf("Sum Matrix:\n");
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            printf("%d ", sum[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```

**Example 3: Matrix Multiplication**

```c
#include <stdio.h>

int main() {
    int a[2][2] = {{1, 2}, {3, 4}};
    int b[2][2] = {{5, 6}, {7, 8}};
    int product[2][2] = {0};

    // Multiplication
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            for (int k = 0; k < 2; k++) {
                product[i][j] += a[i][k] * b[k][j];
            }
        }
    }

    printf("Product Matrix:\n");
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            printf("%d ", product[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```

**Example 4: Transpose of Matrix**

```c
#include <stdio.h>

int main() {
    int matrix[3][2] = {{1, 2}, {3, 4}, {5, 6}};
    int transpose[2][3];

    // Finding transpose
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 2; j++) {
            transpose[j][i] = matrix[i][j];
        }
    }

    printf("Original Matrix:\n");
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 2; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }

    printf("Transpose:\n");
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 3; j++) {
            printf("%d ", transpose[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```

### Strings and String Manipulation

A **string** in C is an array of characters terminated by a null character `'\0'`.

**String Declaration:**

```c
// Method 1: Character array
char str[20];

// Method 2: With initialization
char str[] = "Hello";  // Size = 6 (including '\0')

// Method 3: Character by character
char str[] = {'H', 'e', 'l', 'l', 'o', '\0'};

// Method 4: String pointer
char *str = "Hello";  // String literal
```

**String Representation:**

```
String "Hello" in memory:
['H']['e']['l']['l']['o']['\0']
  0    1    2    3    4    5
```

**Example 1: String Input/Output**

```c
#include <stdio.h>

int main() {
    char name[50];

    // Method 1: Using scanf (stops at whitespace)
    printf("Enter name: ");
    scanf("%s", name);  // No & needed for arrays
    printf("Name: %s\n", name);

    // Method 2: Using gets (deprecated, reads whole line)
    // gets(name);  // Unsafe, avoid using

    // Method 3: Using fgets (safe, reads whole line)
    printf("Enter full name: ");
    fgets(name, 50, stdin);
    printf("Full name: %s", name);

    return 0;
}
```

**Standard String Functions (string.h):**

**1. strlen() - String Length**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[] = "Programming";
    int length = strlen(str);
    printf("Length: %d\n", length);  // Output: 11
    return 0;
}
```

**2. strcpy() - String Copy**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char source[] = "Hello";
    char destination[20];

    strcpy(destination, source);
    printf("Destination: %s\n", destination);
    return 0;
}
```

**3. strcat() - String Concatenation**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str1[50] = "Hello ";
    char str2[] = "World";

    strcat(str1, str2);
    printf("Result: %s\n", str1);  // Output: Hello World
    return 0;
}
```

**4. strcmp() - String Comparison**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str1[] = "Apple";
    char str2[] = "Banana";

    int result = strcmp(str1, str2);

    if (result == 0)
        printf("Strings are equal\n");
    else if (result < 0)
        printf("str1 is less than str2\n");
    else
        printf("str1 is greater than str2\n");

    return 0;
}
```

**Custom String Functions:**

**Example 1: String Length (Manual)**

```c
#include <stdio.h>

int stringLength(char str[]) {
    int length = 0;
    while (str[length] != '\0') {
        length++;
    }
    return length;
}

int main() {
    char str[] = "Hello";
    printf("Length: %d\n", stringLength(str));
    return 0;
}
```

**Example 2: String Copy (Manual)**

```c
#include <stdio.h>

void stringCopy(char dest[], char src[]) {
    int i = 0;
    while (src[i] != '\0') {
        dest[i] = src[i];
        i++;
    }
    dest[i] = '\0';
}

int main() {
    char source[] = "Programming";
    char destination[20];
    stringCopy(destination, source);
    printf("Copied string: %s\n", destination);
    return 0;
}
```

**Example 3: String Reverse**

```c
#include <stdio.h>
#include <string.h>

void reverseString(char str[]) {
    int length = strlen(str);
    for (int i = 0; i < length / 2; i++) {
        char temp = str[i];
        str[i] = str[length - 1 - i];
        str[length - 1 - i] = temp;
    }
}

int main() {
    char str[] = "Hello";
    printf("Original: %s\n", str);
    reverseString(str);
    printf("Reversed: %s\n", str);
    return 0;
}
```

**Example 4: Check Palindrome**

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int isPalindrome(char str[]) {
    int left = 0;
    int right = strlen(str) - 1;

    while (left < right) {
        if (tolower(str[left]) != tolower(str[right])) {
            return 0;  // Not a palindrome
        }
        left++;
        right--;
    }
    return 1;  // Is a palindrome
}

int main() {
    char str[] = "Madam";
    if (isPalindrome(str))
        printf("%s is a palindrome\n", str);
    else
        printf("%s is not a palindrome\n", str);
    return 0;
}
```

**Example 5: Count Vowels and Consonants**

```c
#include <stdio.h>
#include <ctype.h>

void countLetters(char str[]) {
    int vowels = 0, consonants = 0;

    for (int i = 0; str[i] != '\0'; i++) {
        char ch = tolower(str[i]);
        if (ch >= 'a' && ch <= 'z') {
            if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u')
                vowels++;
            else
                consonants++;
        }
    }

    printf("Vowels: %d\n", vowels);
    printf("Consonants: %d\n", consonants);
}

int main() {
    char str[] = "Hello World";
    countLetters(str);
    return 0;
}
```

### Passing Array and String to Function

Arrays and strings are passed to functions by reference (address is passed).

**Passing 1D Array:**

```c
#include <stdio.h>

// Method 1: Unsized array
void display(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

// Method 2: Pointer notation
void modify(int *arr, int size) {
    for (int i = 0; i < size; i++) {
        arr[i] *= 2;
    }
}

int main() {
    int numbers[] = {1, 2, 3, 4, 5};
    int size = 5;

    printf("Original: ");
    display(numbers, size);

    modify(numbers, size);

    printf("Modified: ");
    display(numbers, size);

    return 0;
}
```

**Passing 2D Array:**

```c
#include <stdio.h>

// Must specify column size
void displayMatrix(int mat[][3], int rows) {
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < 3; j++) {
            printf("%d ", mat[i][j]);
        }
        printf("\n");
    }
}

int main() {
    int matrix[2][3] = {{1, 2, 3}, {4, 5, 6}};
    displayMatrix(matrix, 2);
    return 0;
}
```

**Passing Strings:**

```c
#include <stdio.h>
#include <string.h>

// Method 1: Character array
void printString(char str[]) {
    printf("String: %s\n", str);
}

// Method 2: Pointer
void toUpperCase(char *str) {
    for (int i = 0; str[i] != '\0'; i++) {
        if (str[i] >= 'a' && str[i] <= 'z') {
            str[i] = str[i] - 32;
        }
    }
}

int main() {
    char text[] = "hello world";
    printString(text);
    toUpperCase(text);
    printString(text);
    return 0;
}
```

**Return Array from Function:**

```c
#include <stdio.h>
#include <stdlib.h>

// Using static array (not recommended for large data)
int* getArray1() {
    static int arr[] = {1, 2, 3, 4, 5};
    return arr;
}

// Using dynamic allocation (recommended)
int* getArray2(int size) {
    int *arr = (int*)malloc(size * sizeof(int));
    for (int i = 0; i < size; i++) {
        arr[i] = i + 1;
    }
    return arr;
}

int main() {
    int *arr1 = getArray1();
    for (int i = 0; i < 5; i++) {
        printf("%d ", arr1[i]);
    }
    printf("\n");

    int *arr2 = getArray2(5);
    for (int i = 0; i < 5; i++) {
        printf("%d ", arr2[i]);
    }
    free(arr2);  // Don't forget to free memory

    return 0;
}
```

**Important Notes:**

- Arrays are always passed by reference
- Changes inside function affect original array
- Array size should be passed separately
- For 2D arrays, column size must be specified
- Strings are character arrays, so same rules apply

---

## Structures

### Introduction to Structures

A **structure** is a user-defined data type in C that allows you to group variables of different data types under a single name. Structures are used to represent records and organize complex data.

**Syntax:**

```c
struct structure_name {
    data_type member1;
    data_type member2;
    // ... more members
};
```

**Example:**

```c
struct Student {
    int roll_no;
    char name[50];
    float marks;
};
```

**Declaring Structure Variables:**

```c
// Method 1: After structure definition
struct Student s1, s2;

// Method 2: During structure definition
struct Student {
    int roll_no;
    char name[50];
    float marks;
} s1, s2;

// Method 3: Using typedef
typedef struct {
    int roll_no;
    char name[50];
    float marks;
} Student;

Student s1, s2;  // No need for 'struct' keyword
```

**Accessing Structure Members:**
Use the dot (`.`) operator to access structure members.

```c
struct Student s1;
s1.roll_no = 101;
strcpy(s1.name, "John");
s1.marks = 85.5;

printf("Roll No: %d\n", s1.roll_no);
printf("Name: %s\n", s1.name);
printf("Marks: %.2f\n", s1.marks);
```

### Processing a Structure

**Initialization:**

```c
// Method 1: Member by member
struct Student s1;
s1.roll_no = 101;
strcpy(s1.name, "Alice");
s1.marks = 92.5;

// Method 2: During declaration
struct Student s2 = {102, "Bob", 88.0};

// Method 3: Designated initializers (C99)
struct Student s3 = {
    .roll_no = 103,
    .name = "Charlie",
    .marks = 95.5
};
```

**Reading and Displaying Structure Data:**

```c
#include <stdio.h>
#include <string.h>

struct Student {
    int roll_no;
    char name[50];
    float marks;
};

int main() {
    struct Student s1;

    // Reading data
    printf("Enter Roll No: ");
    scanf("%d", &s1.roll_no);
    printf("Enter Name: ");
    scanf("%s", s1.name);  // Note: no & for arrays
    printf("Enter Marks: ");
    scanf("%f", &s1.marks);

    // Displaying data
    printf("\nStudent Details:\n");
    printf("Roll No: %d\n", s1.roll_no);
    printf("Name: %s\n", s1.name);
    printf("Marks: %.2f\n", s1.marks);

    return 0;
}
```

```c
#include <stdio.h>
#include <string.h>

struct Student {
    int id;
    char name[50];
    int age;
    float gpa;
};

void inputStudent(struct Student *s) {
    printf("Enter ID: ");
    scanf("%d", &s->id);
    printf("Enter name: ");
    scanf(" %[^\n]", s->name);  // Read string with spaces
    printf("Enter age: ");
    scanf("%d", &s->age);
    printf("Enter GPA: ");
    scanf("%f", &s->gpa);
}

void displayStudent(struct Student s) {
    printf("\n--- Student Details ---\n");
    printf("ID: %d\n", s.id);
    printf("Name: %s\n", s.name);
    printf("Age: %d\n", s.age);
    printf("GPA: %.2f\n", s.gpa);
}

int main() {
    struct Student s1;

    inputStudent(&s1);
    displayStudent(s1);

    return 0
}
```

**Copying Structures:**

```c
struct Student s1 = {101, "Alice", 92.5};
struct Student s2;

// Direct assignment (copies all members)
s2 = s1;
```

**Comparing Structures:**
Structures cannot be compared directly using `==`. You must compare members individually.

```c
if (s1.roll_no == s2.roll_no &&
    strcmp(s1.name, s2.name) == 0 &&
    s1.marks == s2.marks) {
    printf("Structures are equal\n");
}
```

### Arrays of Structures

An array of structures is used to store multiple records of the same type.

**Declaration:**

```c
struct Student students[50];  // Array of 50 students
```

**Example: Complete Program**

```c
#include <stdio.h>
#include <string.h>

struct Student {
    int roll_no;
    char name[50];
    float marks;
};

int main() {
    struct Student students[3];
    int i;

    // Reading data for multiple students
    for (i = 0; i < 3; i++) {
        printf("\nEnter details for student %d:\n", i + 1);
        printf("Roll No: ");
        scanf("%d", &students[i].roll_no);
        printf("Name: ");
        scanf("%s", students[i].name);
        printf("Marks: ");
        scanf("%f", &students[i].marks);
    }

    // Displaying all students
    printf("\n\nStudent Records:\n");
    printf("%-10s %-20s %-10s\n", "Roll No", "Name", "Marks");
    printf("----------------------------------------\n");
    for (i = 0; i < 3; i++) {
        printf("%-10d %-20s %-10.2f\n",
               students[i].roll_no,
               students[i].name,
               students[i].marks);
    }

    // Finding student with highest marks
    int max_index = 0;
    for (i = 1; i < 3; i++) {
        if (students[i].marks > students[max_index].marks) {
            max_index = i;
        }
    }

    printf("\nTopper: %s with %.2f marks\n",
           students[max_index].name,
           students[max_index].marks);

    return 0;
}
```

### Arrays within Structures

Structures can contain arrays as members, allowing you to store multiple values of the same type within a single structure.

**Example:**

```c
struct Employee {
    int emp_id;
    char name[50];
    int daily_hours[7];  // Hours worked for 7 days
    char skills[5][30];  // Up to 5 skills, each 30 chars
};

int main() {
    struct Employee emp;

    emp.emp_id = 501;
    strcpy(emp.name, "David");

    // Setting daily hours
    int hours[] = {8, 7, 9, 8, 8, 0, 0};
    for (int i = 0; i < 7; i++) {
        emp.daily_hours[i] = hours[i];
    }

    // Setting skills
    strcpy(emp.skills[0], "C Programming");
    strcpy(emp.skills[1], "Python");
    strcpy(emp.skills[2], "Data Structures");

    // Calculating total hours
    int total = 0;
    for (int i = 0; i < 7; i++) {
        total += emp.daily_hours[i];
    }

    printf("Employee: %s\n", emp.name);
    printf("Total hours: %d\n", total);
    printf("Skills:\n");
    for (int i = 0; i < 3; i++) {
        printf("  - %s\n", emp.skills[i]);
    }

    return 0;
}
```

**Nested Structures:**

```c
struct Date {
    int day;
    int month;
    int year;
};

struct Employee {
    int emp_id;
    char name[50];
    struct Date joining_date;  // Nested structure
    struct Date birth_date;
};

int main() {
    struct Employee emp;

    emp.emp_id = 101;
    strcpy(emp.name, "Alice");

    // Accessing nested structure members
    emp.joining_date.day = 15;
    emp.joining_date.month = 6;
    emp.joining_date.year = 2020;

    printf("Joining Date: %d/%d/%d\n",
           emp.joining_date.day,
           emp.joining_date.month,
           emp.joining_date.year);

    return 0;
}
```

### Structures and Functions

Structures can be passed to functions and returned from functions in three ways:

#### 1. Pass by Value

The entire structure is copied to the function. Changes inside the function don't affect the original structure.

```c
#include <stdio.h>

struct Point {
    int x;
    int y;
};

// Function that takes structure by value
void displayPoint(struct Point p) {
    printf("Point: (%d, %d)\n", p.x, p.y);
}

// Function that modifies structure (doesn't affect original)
void modifyPoint(struct Point p) {
    p.x = 100;
    p.y = 200;
}

int main() {
    struct Point p1 = {10, 20};

    displayPoint(p1);       // Output: Point: (10, 20)
    modifyPoint(p1);
    displayPoint(p1);       // Output: Point: (10, 20) - unchanged

    return 0;
}
```

#### 2. Pass by Reference (Using Pointers)

A pointer to the structure is passed. Changes inside the function affect the original structure.

```c
// Function that takes structure pointer
void modifyPoint(struct Point *p) {
    p->x = 100;  // Arrow operator for pointer to structure
    p->y = 200;
}

int main() {
    struct Point p1 = {10, 20};

    printf("Before: (%d, %d)\n", p1.x, p1.y);
    modifyPoint(&p1);  // Pass address
    printf("After: (%d, %d)\n", p1.x, p1.y);

    return 0;
}
```

#### 3. Returning Structures from Functions

```c
struct Point createPoint(int x, int y) {
    struct Point p;
    p.x = x;
    p.y = y;
    return p;
}

struct Point addPoints(struct Point p1, struct Point p2) {
    struct Point result;
    result.x = p1.x + p2.x;
    result.y = p1.y + p2.y;
    return result;
}

int main() {
    struct Point p1 = createPoint(10, 20);
    struct Point p2 = createPoint(30, 40);
    struct Point sum = addPoints(p1, p2);

    printf("Sum: (%d, %d)\n", sum.x, sum.y);  // Output: Sum: (40, 60)

    return 0;
}
```

**Complete Example: Student Management**

```c
#include <stdio.h>
#include <string.h>

struct Student {
    int roll_no;
    char name[50];
    float marks;
};

// Function to read student data
void readStudent(struct Student *s) {
    printf("Enter Roll No: ");
    scanf("%d", &s->roll_no);
    printf("Enter Name: ");
    scanf("%s", s->name);
    printf("Enter Marks: ");
    scanf("%f", &s->marks);
}

// Function to display student data
void displayStudent(struct Student s) {
    printf("Roll No: %d, Name: %s, Marks: %.2f\n",
           s.roll_no, s.name, s.marks);
}

// Function to find student with highest marks
struct Student findTopper(struct Student students[], int n) {
    int max_index = 0;
    for (int i = 1; i < n; i++) {
        if (students[i].marks > students[max_index].marks) {
            max_index = i;
        }
    }
    return students[max_index];
}

int main() {
    struct Student students[3];

    for (int i = 0; i < 3; i++) {
        printf("\nEnter details for student %d:\n", i + 1);
        readStudent(&students[i]);
    }

    printf("\nAll Students:\n");
    for (int i = 0; i < 3; i++) {
        displayStudent(students[i]);
    }

    struct Student topper = findTopper(students, 3);
    printf("\nTopper: ");
    displayStudent(topper);

    return 0;
}
```

```c
#include <stdio.h>

struct Student {
    int roll_no;
    char name[50];
    float marks;
};

void readStudents(struct Student *s, int count) {
    for (int i = 0; i < count; i++) {
        printf("\nEnter details for student %d:\n", i + 1);
        printf("Enter Roll No: ");
        scanf("%d", &s[i].roll_no);
        printf("Enter Name: ");
        scanf("%s", s[i].name);
        printf("Enter Marks: ");
        scanf("%f", &s[i].marks);
    }
}

int main() {
    struct Student students[3];

    readStudents(students, 3);

    return 0;
}
```

---

## Pointers

### Introduction to Pointers

A **pointer** is a variable that stores the memory address of another variable. Pointers are one of the most powerful features of C programming.

**Why Use Pointers?**

- Dynamic memory allocation
- Efficient array and string handling
- Pass by reference to functions
- Implement complex data structures (linked lists, trees, etc.)
- Direct hardware manipulation

**Memory Concepts:**

- Every variable is stored at a specific memory address
- Memory addresses are typically represented in hexadecimal
- The size of a pointer depends on the system architecture (4 bytes for 32-bit, 8 bytes for 64-bit)

### Pointer Declaration

**Syntax:**

```c
data_type *pointer_name;
```

**Examples:**

```c
int *ptr;        // Pointer to integer
float *fptr;     // Pointer to float
char *cptr;      // Pointer to character
double *dptr;    // Pointer to double
```

**Address Operator (`&`):**
Returns the memory address of a variable.

```c
int x = 10;
printf("Value of x: %d\n", x);
printf("Address of x: %p\n", &x);  // %p for pointer/address
```

**Dereference Operator (`*`):**
Accesses the value stored at the memory address.

```c
int x = 10;
int *ptr = &x;  // ptr stores address of x

printf("Address stored in ptr: %p\n", ptr);
printf("Value at address (using *ptr): %d\n", *ptr);
```

**Complete Example:**

```c
#include <stdio.h>

int main() {
    int x = 25;
    int *ptr;

    ptr = &x;  // Store address of x in ptr

    printf("Value of x: %d\n", x);
    printf("Address of x: %p\n", &x);
    printf("Value of ptr (address it holds): %p\n", ptr);
    printf("Value pointed to by ptr: %d\n", *ptr);
    printf("Address of ptr itself: %p\n", &ptr);

    // Modifying value through pointer
    *ptr = 50;
    printf("\nAfter *ptr = 50:\n");
    printf("Value of x: %d\n", x);  // x is now 50

    return 0;
}
```

**Pointer Initialization:**

```c
int x = 10;
int *ptr1 = &x;      // Initialize during declaration
int *ptr2;
ptr2 = &x;           // Initialize separately

int *ptr3 = NULL;    // Initialize to NULL (good practice)
```

**NULL Pointer:**
A pointer that doesn't point to any valid memory location.

```c
int *ptr = NULL;

if (ptr == NULL) {
    printf("Pointer is NULL\n");
}

// Always check before dereferencing
if (ptr != NULL) {
    printf("Value: %d\n", *ptr);
}
```

### Pointer Arithmetic

Pointers can be incremented, decremented, and used in arithmetic operations. When you add or subtract from a pointer, it moves by the size of the data type it points to.

**Operations Allowed:**

1. Increment (`++`) and Decrement (`--`)
2. Addition (`+`) and Subtraction (`-`) with integers
3. Subtraction between two pointers of the same type
4. Comparison (`==`, `!=`, `<`, `>`, `<=`, `>=`)

**Example:**

```c
#include <stdio.h>

int main() {
    int arr[] = {10, 20, 30, 40, 50};
    int *ptr = arr;  // Points to first element

    printf("Address of arr[0]: %p, Value: %d\n", ptr, *ptr);

    ptr++;  // Move to next integer (4 bytes ahead on most systems)
    printf("Address of arr[1]: %p, Value: %d\n", ptr, *ptr);

    ptr += 2;  // Move 2 integers ahead
    printf("Address of arr[3]: %p, Value: %d\n", ptr, *ptr);

    ptr--;  // Move back
    printf("Address of arr[2]: %p, Value: %d\n", ptr, *ptr);

    return 0;
}
```

**Size of Data Types:**

```c
int x;
float f;
char c;
double d;

printf("Size of int: %lu bytes\n", sizeof(int));
printf("Size of float: %lu bytes\n", sizeof(float));
printf("Size of char: %lu bytes\n", sizeof(char));
printf("Size of double: %lu bytes\n", sizeof(double));

int *iptr;
float *fptr;
printf("Size of int pointer: %lu bytes\n", sizeof(iptr));
printf("Size of float pointer: %lu bytes\n", sizeof(fptr));
```

**Pointer Subtraction:**

```c
int arr[] = {10, 20, 30, 40, 50};
int *ptr1 = &arr[1];
int *ptr2 = &arr[4];

int difference = ptr2 - ptr1;  // Number of elements between pointers
printf("Difference: %d elements\n", difference);  // Output: 3
```

**Pointer Comparison:**

```c
int arr[] = {10, 20, 30, 40, 50};
int *ptr1 = &arr[1];
int *ptr2 = &arr[3];

if (ptr1 < ptr2) {
    printf("ptr1 comes before ptr2 in memory\n");
}

if (ptr1 == &arr[1]) {
    printf("ptr1 points to arr[1]\n");
}
```

### Pointer and Array

Arrays and pointers are closely related in C. The name of an array is essentially a pointer to its first element.

**Array-Pointer Relationship:**

```c
int arr[] = {10, 20, 30, 40, 50};
int *ptr = arr;  // Same as: int *ptr = &arr[0];

printf("arr: %p\n", arr);
printf("&arr[0]: %p\n", &arr[0]);
printf("ptr: %p\n", ptr);  // All three print the same address
```

**Accessing Array Elements:**

```c
int arr[] = {10, 20, 30, 40, 50};

// Method 1: Array notation
printf("%d\n", arr[2]);

// Method 2: Pointer notation
printf("%d\n", *(arr + 2));

// Method 3: Using separate pointer
int *ptr = arr;
printf("%d\n", ptr[2]);
printf("%d\n", *(ptr + 2));
```

**Equivalence:**

- `arr[i]` is equivalent to `*(arr + i)`
- `&arr[i]` is equivalent to `(arr + i)`
- `ptr[i]` is equivalent to `*(ptr + i)`

**Traversing Array Using Pointers:**

```c
#include <stdio.h>

int main() {
    int arr[] = {10, 20, 30, 40, 50};
    int n = sizeof(arr) / sizeof(arr[0]);
    int *ptr = arr;

    // Method 1: Using pointer arithmetic
    printf("Method 1:\n");
    for (int i = 0; i < n; i++) {
        printf("%d ", *(ptr + i));
    }

    // Method 2: Incrementing pointer
    printf("\n\nMethod 2:\n");
    ptr = arr;  // Reset pointer
    for (int i = 0; i < n; i++) {
        printf("%d ", *ptr);
        ptr++;
    }

    // Method 3: While loop
    printf("\n\nMethod 3:\n");
    ptr = arr;
    int *end = arr + n;
    while (ptr < end) {
        printf("%d ", *ptr);
        ptr++;
    }

    return 0;
}
```

**Array of Pointers:**

```c
int x = 10, y = 20, z = 30;
int *arr[3];  // Array of 3 integer pointers

arr[0] = &x;
arr[1] = &y;
arr[2] = &z;

for (int i = 0; i < 3; i++) {
    printf("Value: %d\n", *arr[i]);
}
```

**2D Arrays and Pointers:**

```c
int arr[3][4] = {
    {1, 2, 3, 4},
    {5, 6, 7, 8},
    {9, 10, 11, 12}
};

// arr[i][j] is equivalent to *(*(arr + i) + j)

// Accessing using pointers
for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 4; j++) {
        printf("%d ", *(*(arr + i) + j));
    }
    printf("\n");
}
```

### Passing Pointers to a Function

Passing pointers to functions allows you to modify the original variable (pass by reference) and work efficiently with arrays.

**Pass by Value vs Pass by Reference:**

**Pass by Value (Cannot modify original):**

```c
void increment(int x) {
    x = x + 1;
}

int main() {
    int a = 10;
    increment(a);
    printf("%d\n", a);  // Output: 10 (unchanged)
    return 0;
}
```

**Pass by Reference (Can modify original):**

```c
void increment(int *x) {
    *x = *x + 1;
}

int main() {
    int a = 10;
    increment(&a);  // Pass address
    printf("%d\n", a);  // Output: 11 (modified)
    return 0;
}
```

**Swapping Two Numbers:**

```c
void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int x = 10, y = 20;
    printf("Before: x = %d, y = %d\n", x, y);

    swap(&x, &y);

    printf("After: x = %d, y = %d\n", x, y);
    return 0;
}
```

**Passing Arrays to Functions:**
When you pass an array to a function, you're actually passing a pointer to the first element.

```c
// All three declarations are equivalent
void printArray(int arr[], int size);
void printArray(int *arr, int size);
void printArray(int arr[10], int size);  // Size in [] is ignored

void printArray(int *arr, int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int numbers[] = {1, 2, 3, 4, 5};
    int size = sizeof(numbers) / sizeof(numbers[0]);

    printArray(numbers, size);
    return 0;
}
```

**Modifying Array Elements:**

```c
void doubleElements(int *arr, int size) {
    for (int i = 0; i < size; i++) {
        arr[i] *= 2;  // Modifies original array
    }
}

int main() {
    int numbers[] = {1, 2, 3, 4, 5};
    int size = 5;

    printf("Before: ");
    for (int i = 0; i < size; i++) printf("%d ", numbers[i]);

    doubleElements(numbers, size);

    printf("\nAfter: ");
    for (int i = 0; i < size; i++) printf("%d ", numbers[i]);

    return 0;
}
```

**Returning Multiple Values:**

```c
void getMinMax(int *arr, int size, int *min, int *max) {
    *min = *max = arr[0];

    for (int i = 1; i < size; i++) {
        if (arr[i] < *min) *min = arr[i];
        if (arr[i] > *max) *max = arr[i];
    }
}

int main() {
    int numbers[] = {45, 12, 78, 23, 89, 34};
    int size = 6;
    int min, max;

    getMinMax(numbers, size, &min, &max);

    printf("Min: %d, Max: %d\n", min, max);
    return 0;
}
```

### Pointers and Structures

Pointers to structures are commonly used for dynamic memory allocation and efficient structure manipulation.

**Declaring Pointer to Structure:**

```c
struct Student {
    int roll_no;
    char name[50];
    float marks;
};

struct Student s1;
struct Student *ptr = &s1;
```

**Accessing Structure Members Through Pointer:**

There are two ways to access structure members through a pointer:

```c
// Method 1: Using arrow operator (->)
ptr->roll_no = 101;
strcpy(ptr->name, "Alice");
ptr->marks = 92.5;

// Method 2: Using dereference and dot operator
(*ptr).roll_no = 101;
strcpy((*ptr).name, "Alice");
(*ptr).marks = 92.5;
```

**Note:** Arrow operator (`->`) is more commonly used and more readable.

**Complete Example:**

```c
#include <stdio.h>
#include <string.h>

struct Student {
    int roll_no;
    char name[50];
    float marks;
};

void readStudent(struct Student *s) {
    printf("Enter Roll No: ");
    scanf("%d", &s->roll_no);
    printf("Enter Name: ");
    scanf("%s", s->name);
    printf("Enter Marks: ");
    scanf("%f", &s->marks);
}

void displayStudent(struct Student *s) {
    printf("\nStudent Details:\n");
    printf("Roll No: %d\n", s->roll_no);
    printf("Name: %s\n", s->name);
    printf("Marks: %.2f\n", s->marks);
}

int main() {
    struct Student s1;
    struct Student *ptr = &s1;

    readStudent(ptr);
    displayStudent(ptr);

    return 0;
}
```

**Array of Structures with Pointers:**

```c
struct Student {
    int roll_no;
    char name[50];
    float marks;
};

int main() {
    struct Student students[3];
    struct Student *ptr;

    // Reading data
    for (ptr = students; ptr < students + 3; ptr++) {
        printf("\nEnter details:\n");
        printf("Roll No: ");
        scanf("%d", &ptr->roll_no);
        printf("Name: ");
        scanf("%s", ptr->name);
        printf("Marks: ");
        scanf("%f", &ptr->marks);
    }

    // Displaying data
    printf("\n\nAll Students:\n");
    for (ptr = students; ptr < students + 3; ptr++) {
        printf("Roll: %d, Name: %s, Marks: %.2f\n",
               ptr->roll_no, ptr->name, ptr->marks);
    }

    return 0;
}
```

**Dynamic Memory Allocation for Structures:**

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct Student {
    int roll_no;
    char name[50];
    float marks;
};

int main() {
    struct Student *ptr;

    // Allocate memory for one student
    ptr = (struct Student *)malloc(sizeof(struct Student));

    if (ptr == NULL) {
        printf("Memory allocation failed\n");
        return 1;
    }

    // Use the allocated memory
    ptr->roll_no = 101;
    strcpy(ptr->name, "John");
    ptr->marks = 88.5;

    printf("Roll No: %d\n", ptr->roll_no);
    printf("Name: %s\n", ptr->name);
    printf("Marks: %.2f\n", ptr->marks);

    // Free the memory
    free(ptr);

    return 0;
}
```

**Dynamic Array of Structures:**

```c
#include <stdio.h>
#include <stdlib.h>

struct Student {
    int roll_no;
    char name[50];
    float marks;
};

int main() {
    int n;
    struct Student *students;

    printf("Enter number of students: ");
    scanf("%d", &n);

    // Allocate memory for n students
    students = (struct Student *)malloc(n * sizeof(struct Student));

    if (students == NULL) {
        printf("Memory allocation failed\n");
        return 1;
    }

    // Input data
    for (int i = 0; i < n; i++) {
        printf("\nEnter details for student %d:\n", i + 1);
        printf("Roll No: ");
        scanf("%d", &(students + i)->roll_no);
        printf("Name: ");
        scanf("%s", (students + i)->name);
        printf("Marks: ");
        scanf("%f", &(students + i)->marks);
    }

    // Display data
    printf("\n\nAll Students:\n");
    for (int i = 0; i < n; i++) {
        printf("Roll: %d, Name: %s, Marks: %.2f\n",
               (students + i)->roll_no,
               (students + i)->name,
               (students + i)->marks);
    }

    // Free memory
    free(students);

    return 0;
}
```

**Self-Referential Structures (Introduction to Linked Lists):**

```c
struct Node {
    int data;
    struct Node *next;  // Pointer to same structure type
};

int main() {
    struct Node n1, n2, n3;

    n1.data = 10;
    n2.data = 20;
    n3.data = 30;

    n1.next = &n2;
    n2.next = &n3;
    n3.next = NULL;

    // Traversing the linked structure
    struct Node *ptr = &n1;
    while (ptr != NULL) {
        printf("%d -> ", ptr->data);
        ptr = ptr->next;
    }
    printf("NULL\n");

    return 0;
}
```

---

## Summary

### Key Points - Structures

- Structures group different data types under one name
- Access members using dot (`.`) operator
- Arrays of structures store multiple records
- Structures can contain arrays and nested structures
- Pass structures by value or by pointer to functions
- Use `typedef` to simplify structure declarations

### Key Points - Pointers

- Pointers store memory addresses of variables
- Use `&` to get address, `*` to dereference
- Pointer arithmetic moves by size of data type
- Array names are pointers to first element
- Pass pointers to functions for pass-by-reference
- Use `->` operator for accessing structure members through pointer
- Always initialize pointers and check for NULL

### Best Practices

1. Always initialize pointers before use
2. Check for NULL before dereferencing
3. Free dynamically allocated memory
4. Use meaningful variable names
5. Prefer passing large

# Complete Notes: File Handling in C and FORTRAN Basics

## Table of Contents

1. [Data Files in C](#data-files-in-c)
2. [FORTRAN Programming Basics](#fortran-programming-basics)

---

## Data Files in C

### 1. Introduction to File Handling

File handling is a crucial aspect of programming that allows programs to store data permanently and retrieve it when needed. In C programming, files are used to store data on secondary storage devices like hard disks, enabling data persistence beyond program execution.

**Why File Handling?**

- Permanent storage of data
- Data can be accessed across multiple program executions
- Large volumes of data can be managed efficiently
- Data sharing between different programs

**Types of Files:**

1. **Text Files**: Store data in human-readable ASCII format
2. **Binary Files**: Store data in binary format (0s and 1s)

### 2. Defining, Opening and Closing Files

#### File Pointer

A file pointer is a pointer to a structure of type `FILE` (defined in `stdio.h`) that contains information about the file.

```c
FILE *filePointer;
```

#### Opening a File: `fopen()`

The `fopen()` function is used to open a file and returns a file pointer.

**Syntax:**

```c
FILE *fopen(const char *filename, const char *mode);
```

**File Opening Modes:**

| Mode    | Description        | File Exists                            | File Doesn't Exist |
| ------- | ------------------ | -------------------------------------- | ------------------ |
| `"r"`   | Read only          | Opens file                             | Returns NULL       |
| `"w"`   | Write only         | Truncates to zero length               | Creates new file   |
| `"a"`   | Append             | Opens for appending                    | Creates new file   |
| `"r+"`  | Read and write     | Opens file                             | Returns NULL       |
| `"w+"`  | Read and write     | Truncates to zero length               | Creates new file   |
| `"a+"`  | Read and append    | Opens for reading and appending        | Creates new file   |
| `"rb"`  | Read binary        | Opens binary file                      | Returns NULL       |
| `"wb"`  | Write binary       | Truncates binary file                  | Creates new file   |
| `"ab"`  | Append binary      | Opens binary for appending             | Creates new file   |
| `"rb+"` | Read/write binary  | Opens binary file                      | Returns NULL       |
| `"wb+"` | Read/write binary  | Truncates binary file                  | Creates new file   |
| `"ab+"` | Read/append binary | Opens binary for reading and appending | Creates new file   |

**Example:**

```c
FILE *fp;
fp = fopen("data.txt", "r");
if (fp == NULL) {
    printf("Error opening file!\n");
    exit(1);
}
```

#### Closing a File: `fclose()`

The `fclose()` function closes an open file and flushes any buffered data.

**Syntax:**

```c
int fclose(FILE *filePointer);
```

**Returns:**

- 0 on success
- EOF (End of File) on error

**Example:**

```c
fclose(fp);
```

**Why Close Files?**

- Frees system resources
- Ensures all buffered data is written to disk
- Prevents data corruption
- Avoids running out of file descriptors

### 3. Input/Output Operations on Files

#### Character Input/Output

**a) `fgetc()` - Read a character**

```c
int fgetc(FILE *stream);
```

Reads and returns the next character from the file. Returns EOF on end of file or error.

**Example:**

```c
FILE *fp = fopen("file.txt", "r");
char ch;
while ((ch = fgetc(fp)) != EOF) {
    printf("%c", ch);
}
fclose(fp);
```

**b) `fputc()` - Write a character**

```c
int fputc(int character, FILE *stream);
```

Writes a character to the file. Returns the character written or EOF on error.

**Example:**

```c
FILE *fp = fopen("output.txt", "w");
fputc('A', fp);
fputc('B', fp);
fclose(fp);
```

**c) `getc()` and `putc()` - Macro versions**
Similar to `fgetc()` and `fputc()` but implemented as macros for efficiency.

```c
int getc(FILE *stream);
int putc(int character, FILE *stream);
```

#### String Input/Output

**a) `fgets()` - Read a string**

```c
char *fgets(char *str, int n, FILE *stream);
```

Reads up to n-1 characters from the file or until newline/EOF is encountered.

**Example:**

```c
FILE *fp = fopen("data.txt", "r");
char buffer[100];
if (fgets(buffer, 100, fp) != NULL) {
    printf("Read: %s", buffer);
}
fclose(fp);
```

**b) `fputs()` - Write a string**

```c
int fputs(const char *str, FILE *stream);
```

Writes a string to the file (does not append newline automatically).

**Example:**

```c
FILE *fp = fopen("output.txt", "w");
fputs("Hello, World!\n", fp);
fputs("Second line\n", fp);
fclose(fp);
```

#### Formatted Input/Output

**a) `fprintf()` - Formatted write**

```c
int fprintf(FILE *stream, const char *format, ...);
```

Similar to `printf()` but writes to a file.

**Example:**

```c
FILE *fp = fopen("data.txt", "w");
int age = 25;
char name[] = "John";
fprintf(fp, "Name: %s, Age: %d\n", name, age);
fclose(fp);
```

**b) `fscanf()` - Formatted read**

```c
int fscanf(FILE *stream, const char *format, ...);
```

Similar to `scanf()` but reads from a file.

**Example:**

```c
FILE *fp = fopen("data.txt", "r");
int age;
char name[50];
fscanf(fp, "Name: %s, Age: %d", name, &age);
printf("Name: %s, Age: %d\n", name, age);
fclose(fp);
```

#### Block Input/Output (Binary Files)

**a) `fread()` - Read block of data**

```c
size_t fread(void *ptr, size_t size, size_t count, FILE *stream);
```

Reads `count` elements of `size` bytes each from the file.

**Example:**

```c
struct Student {
    int id;
    char name[50];
    float marks;
};

FILE *fp = fopen("students.dat", "rb");
struct Student s;
fread(&s, sizeof(struct Student), 1, fp);
fclose(fp);
```

**b) `fwrite()` - Write block of data**

```c
size_t fwrite(const void *ptr, size_t size, size_t count, FILE *stream);
```

Writes `count` elements of `size` bytes each to the file.

**Example:**

```c
struct Student s = {101, "Alice", 85.5};
FILE *fp = fopen("students.dat", "wb");
fwrite(&s, sizeof(struct Student), 1, fp);
fclose(fp);
```

#### File Position Functions

**a) `fseek()` - Move file pointer**

```c
int fseek(FILE *stream, long offset, int origin);
```

**Origin values:**

- `SEEK_SET` (0): Beginning of file
- `SEEK_CUR` (1): Current position
- `SEEK_END` (2): End of file

**Example:**

```c
fseek(fp, 0, SEEK_SET);  // Move to beginning
fseek(fp, 10, SEEK_CUR); // Move 10 bytes forward
fseek(fp, -5, SEEK_END); // Move 5 bytes before end
```

**b) `ftell()` - Get current position**

```c
long ftell(FILE *stream);
```

Returns the current file position or -1L on error.

**Example:**

```c
long position = ftell(fp);
printf("Current position: %ld\n", position);
```

**c) `rewind()` - Reset file pointer**

```c
void rewind(FILE *stream);
```

Moves the file pointer to the beginning of the file.

**Example:**

```c
rewind(fp);  // Equivalent to fseek(fp, 0, SEEK_SET)
```

#### End-of-File Detection

**a) `feof()` - Check for EOF**

```c
int feof(FILE *stream);
```

Returns non-zero if end-of-file is reached.

**Example:**

```c
while (!feof(fp)) {
    char ch = fgetc(fp);
    if (ch != EOF) {
        printf("%c", ch);
    }
}
```

### 4. Error Handling During Input/Output Operations

#### Error Detection Functions

**a) `ferror()` - Check for errors**

```c
int ferror(FILE *stream);
```

Returns non-zero if an error has occurred on the stream.

**Example:**

```c
if (ferror(fp)) {
    printf("Error occurred during file operation\n");
}
```

**b) `clearerr()` - Clear error indicators**

```c
void clearerr(FILE *stream);
```

Clears the end-of-file and error indicators for the stream.

**Example:**

```c
clearerr(fp);
```

**c) `perror()` - Print error message**

```c
void perror(const char *message);
```

Prints the error message followed by the system error description.

**Example:**

```c
FILE *fp = fopen("nonexistent.txt", "r");
if (fp == NULL) {
    perror("Error opening file");
    // Output: Error opening file: No such file or directory
}
```

#### Common File Errors and Handling

**1. File Opening Errors**

```c
FILE *fp = fopen("data.txt", "r");
if (fp == NULL) {
    perror("Error");
    fprintf(stderr, "Failed to open file: data.txt\n");
    exit(EXIT_FAILURE);
}
```

**2. Read/Write Errors**

```c
int result = fwrite(data, size, count, fp);
if (result != count) {
    if (ferror(fp)) {
        fprintf(stderr, "Error writing to file\n");
        clearerr(fp);
    }
}
```

**3. File Closing Errors**

```c
if (fclose(fp) == EOF) {
    perror("Error closing file");
}
```

**4. Buffer Flushing**

```c
int fflush(FILE *stream);
```

Forces any buffered output to be written to the file immediately.

**Example:**

```c
fprintf(fp, "Important data\n");
if (fflush(fp) != 0) {
    perror("Error flushing buffer");
}
```

#### Best Practices for Error Handling

1. **Always check if file opened successfully**

```c
FILE *fp = fopen("file.txt", "r");
if (fp == NULL) {
    fprintf(stderr, "Cannot open file\n");
    return 1;
}
```

2. **Use `errno` for detailed error information**

```c
#include <errno.h>

FILE *fp = fopen("file.txt", "r");
if (fp == NULL) {
    fprintf(stderr, "Error %d: %s\n", errno, strerror(errno));
    return 1;
}
```

3. **Check return values of I/O functions**

```c
size_t written = fwrite(buffer, 1, size, fp);
if (written != size) {
    fprintf(stderr, "Write error: expected %zu, wrote %zu\n", size, written);
}
```

4. **Close files in reverse order of opening**

```c
FILE *fp1 = fopen("file1.txt", "r");
FILE *fp2 = fopen("file2.txt", "w");

// ... operations ...

fclose(fp2);
fclose(fp1);
```

5. **Use `atexit()` for critical cleanup**

```c
void cleanup() {
    if (fp != NULL) {
        fclose(fp);
    }
}

int main() {
    atexit(cleanup);
    fp = fopen("file.txt", "r");
    // ... program code ...
}
```

### Complete Example: File Copy with Error Handling

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    FILE *sourceFile, *destFile;
    char ch;

    // Open source file for reading
    sourceFile = fopen("source.txt", "r");
    if (sourceFile == NULL) {
        perror("Error opening source file");
        return EXIT_FAILURE;
    }

    // Open destination file for writing
    destFile = fopen("destination.txt", "w");
    if (destFile == NULL) {
        perror("Error opening destination file");
        fclose(sourceFile);
        return EXIT_FAILURE;
    }

    // Copy contents
    while ((ch = fgetc(sourceFile)) != EOF) {
        if (fputc(ch, destFile) == EOF) {
            fprintf(stderr, "Error writing to destination file\n");
            fclose(sourceFile);
            fclose(destFile);
            return EXIT_FAILURE;
        }
    }

    // Check for read errors
    if (ferror(sourceFile)) {
        fprintf(stderr, "Error reading from source file\n");
        fclose(sourceFile);
        fclose(destFile);
        return EXIT_FAILURE;
    }

    // Close files
    if (fclose(sourceFile) == EOF) {
        perror("Error closing source file");
    }

    if (fclose(destFile) == EOF) {
        perror("Error closing destination file");
        return EXIT_FAILURE;
    }

    printf("File copied successfully!\n");
    return EXIT_SUCCESS;
}
```

### Example: Writing and Reading Student Records

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct Student {
    int rollNo;
    char name[50];
    float marks;
};

void writeStudents() {
    FILE *fp = fopen("students.dat", "wb");
    if (fp == NULL) {
        perror("Error opening file for writing");
        return;
    }

    struct Student students[] = {
        {101, "Alice", 85.5},
        {102, "Bob", 78.0},
        {103, "Charlie", 92.3}
    };

    size_t written = fwrite(students, sizeof(struct Student), 3, fp);
    if (written != 3) {
        fprintf(stderr, "Error: Could not write all records\n");
    } else {
        printf("Successfully wrote %zu records\n", written);
    }

    if (fclose(fp) == EOF) {
        perror("Error closing file");
    }
}

void readStudents() {
    FILE *fp = fopen("students.dat", "rb");
    if (fp == NULL) {
        perror("Error opening file for reading");
        return;
    }

    struct Student s;
    printf("\nStudent Records:\n");
    printf("%-10s %-20s %-10s\n", "Roll No", "Name", "Marks");
    printf("----------------------------------------\n");

    while (fread(&s, sizeof(struct Student), 1, fp) == 1) {
        printf("%-10d %-20s %-10.2f\n", s.rollNo, s.name, s.marks);
    }

    if (ferror(fp)) {
        fprintf(stderr, "Error reading from file\n");
    }

    fclose(fp);
}

int main() {
    writeStudents();
    readStudents();
    return 0;
}
```

---

## FORTRAN Programming Basics

### 1. Introduction to FORTRAN

FORTRAN (FORmula TRANslation) is one of the oldest high-level programming languages, developed by IBM in the 1950s. It is particularly suited for scientific and numerical computation.

**Key Features:**

- Strong mathematical computation capabilities
- Efficient array processing
- Widely used in engineering and scientific applications
- Column-based syntax in older versions (FORTRAN 77)

### 2. Character Set

FORTRAN uses the following character set:

**Letters:** A-Z (uppercase), a-z (lowercase)

**Digits:** 0-9

**Special Characters:**

- `+` (plus)
- `-` (minus)
- `*` (asterisk/multiplication)
- `/` (slash/division)
- `**` (exponentiation)
- `=` (assignment/equality)
- `( )` (parentheses)
- `,` (comma)
- `.` (period/decimal point)
- `'` (apostrophe for strings)
- `:` (colon)
- `!` (exclamation for comments)

**Note:** In FORTRAN 77, lowercase letters are treated the same as uppercase.

### 3. Data Types, Constants and Variables

#### Basic Data Types

**a) INTEGER**
Used for whole numbers without decimal points.

```fortran
INTEGER :: age, count
age = 25
count = 100
```

**b) REAL**
Used for floating-point numbers (numbers with decimal points).

```fortran
REAL :: price, temperature
price = 19.99
temperature = 98.6
```

**c) DOUBLE PRECISION**
Used for double-precision floating-point numbers (more accuracy than REAL).

```fortran
DOUBLE PRECISION :: pi, result
pi = 3.141592653589793D0
```

**d) COMPLEX**
Used for complex numbers (real and imaginary parts).

```fortran
COMPLEX :: z
z = (3.0, 4.0)  ! 3 + 4i
```

**e) LOGICAL**
Used for Boolean values (.TRUE. or .FALSE.).

```fortran
LOGICAL :: flag
flag = .TRUE.
```

**f) CHARACTER**
Used for storing text/strings.

```fortran
CHARACTER(LEN=20) :: name
CHARACTER :: initial
name = "John Doe"
initial = 'J'
```

#### Constants

Constants are fixed values that do not change during program execution.

**Types of Constants:**

1. **Integer Constants:** 123, -45, 0
2. **Real Constants:** 3.14, -0.5, 2.0E3 (2.0 × 10³)
3. **Double Precision Constants:** 3.14159D0, 1.5D-5
4. **Character Constants:** 'Hello', "FORTRAN"
5. **Logical Constants:** .TRUE., .FALSE.

**Named Constants (PARAMETER):**

```fortran
REAL, PARAMETER :: PI = 3.14159
INTEGER, PARAMETER :: MAX_SIZE = 100
```

#### Variables

Variables are named memory locations that can store data values.

**Variable Naming Rules:**

- Must start with a letter
- Can contain letters, digits, and underscores
- Maximum length varies (typically 31 characters in FORTRAN 77)
- Case insensitive

**Variable Declaration:**

```fortran
INTEGER :: i, j, k
REAL :: x, y, z
CHARACTER(LEN=50) :: message
LOGICAL :: isValid
```

**Implicit Typing:**
In FORTRAN 77, variables are implicitly typed:

- Variables starting with I, J, K, L, M, N are INTEGER
- All others are REAL

```fortran
! Implicit typing (not recommended)
I = 10        ! INTEGER by default
X = 5.5       ! REAL by default
```

**Explicit Declaration (Recommended):**

```fortran
IMPLICIT NONE  ! Disables implicit typing
INTEGER :: count
REAL :: average
```

### 4. Arithmetic Operations and Library Functions

#### Arithmetic Operators

| Operator | Operation      | Example   | Result               |
| -------- | -------------- | --------- | -------------------- |
| `+`      | Addition       | 5 + 3     | 8                    |
| `-`      | Subtraction    | 5 - 3     | 2                    |
| `*`      | Multiplication | 5 \* 3    | 15                   |
| `/`      | Division       | 5 / 2     | 2 (integer division) |
| `/`      | Division       | 5.0 / 2.0 | 2.5 (real division)  |
| `**`     | Exponentiation | 2 \*\* 3  | 8                    |

**Example:**

```fortran
INTEGER :: a, b, result
REAL :: x, y, z

a = 10
b = 3
result = a + b     ! 13
result = a - b     ! 7
result = a * b     ! 30
result = a / b     ! 3 (integer division)

x = 10.0
y = 3.0
z = x / y          ! 3.333...
z = x ** 2         ! 100.0
```

#### Operator Precedence

1. `**` (exponentiation) - highest
2. `*`, `/` (multiplication, division)
3. `+`, `-` (addition, subtraction) - lowest

Use parentheses to override precedence:

```fortran
result = (a + b) * c
```

#### Intrinsic (Library) Functions

**Mathematical Functions:**

| Function   | Description         | Example            |
| ---------- | ------------------- | ------------------ |
| `ABS(x)`   | Absolute value      | ABS(-5) = 5        |
| `SQRT(x)`  | Square root         | SQRT(16.0) = 4.0   |
| `EXP(x)`   | Exponential (eˣ)    | EXP(1.0) ≈ 2.718   |
| `LOG(x)`   | Natural logarithm   | LOG(2.718) ≈ 1.0   |
| `LOG10(x)` | Base-10 logarithm   | LOG10(100.0) = 2.0 |
| `SIN(x)`   | Sine (x in radians) | SIN(0.0) = 0.0     |
| `COS(x)`   | Cosine              | COS(0.0) = 1.0     |
| `TAN(x)`   | Tangent             | TAN(0.0) = 0.0     |
| `ASIN(x)`  | Arc sine            | ASIN(0.5)          |
| `ACOS(x)`  | Arc cosine          | ACOS(0.5)          |
| `ATAN(x)`  | Arc tangent         | ATAN(1.0)          |

**Other Useful Functions:**

| Function         | Description         | Example                |
| ---------------- | ------------------- | ---------------------- |
| `INT(x)`         | Convert to integer  | INT(3.7) = 3           |
| `REAL(i)`        | Convert to real     | REAL(5) = 5.0          |
| `MOD(a,b)`       | Modulus (remainder) | MOD(10, 3) = 1         |
| `MAX(a,b,c,...)` | Maximum value       | MAX(5, 2, 9) = 9       |
| `MIN(a,b,c,...)` | Minimum value       | MIN(5, 2, 9) = 2       |
| `SIGN(a,b)`      | Transfer sign       | SIGN(5.0, -1.0) = -5.0 |

**Example:**

```fortran
REAL :: x, y, angle
x = 16.0
y = SQRT(x)           ! y = 4.0

angle = 0.0
y = SIN(angle)        ! y = 0.0

x = -5.5
y = ABS(x)            ! y = 5.5

x = 3.7
y = REAL(INT(x))      ! y = 3.0
```

### 5. Structure of a FORTRAN Program

A typical FORTRAN program has the following structure:

```fortran
      PROGRAM program_name
C     Declaration section
      IMPLICIT NONE
      INTEGER :: variable1
      REAL :: variable2

C     Executable statements
      variable1 = 10
      variable2 = 20.5

C     Output
      PRINT *, 'Hello, FORTRAN!'
      PRINT *, variable1, variable2

C     Program termination
      STOP
      END PROGRAM program_name
```

**Components:**

1. **PROGRAM statement:** Defines the program name
2. **Declaration section:** Variable declarations
3. **Executable statements:** Program logic
4. **END statement:** Marks the end of the program

**Comments:**

- In FORTRAN 77: Use `C` or `*` in column 1
- In FORTRAN 90+: Use `!` anywhere on a line

```fortran
C     This is a comment in FORTRAN 77
      ! This is a comment in FORTRAN 90+
      x = 5  ! Inline comment
```

**Column Format (FORTRAN 77):**

- Columns 1-5: Statement labels
- Column 6: Continuation character
- Columns 7-72: FORTRAN statements
- Columns 73-80: Sequence numbers (optional)

**Example Program:**

```fortran
      PROGRAM circle_area
      IMPLICIT NONE
      REAL :: radius, area
      REAL, PARAMETER :: PI = 3.14159

      PRINT *, 'Enter radius:'
      READ *, radius

      area = PI * radius ** 2

      PRINT *, 'Area of circle:', area

      STOP
      END PROGRAM circle_area
```

### 6. Formatted and Unformatted Input/Output Statements

#### Unformatted I/O (List-Directed I/O)

**Output - PRINT Statement:**

```fortran
PRINT *, 'message', variable1, variable2
```

**Input - READ Statement:**

```fortran
READ *, variable1, variable2
```

**Example:**

```fortran
INTEGER :: age
REAL :: height
PRINT *, 'Enter age and height:'
READ *, age, height
PRINT *, 'Age:', age, 'Height:', height
```

#### Formatted I/O

Formatted I/O provides precise control over the appearance of input and output.

**Output - WRITE Statement:**

```fortran
WRITE(unit, format) variable_list
```

**Input - READ Statement:**

```fortran
READ(unit, format) variable_list
```

**Common Format Specifiers:**

| Specifier | Description                         | Example    |
| --------- | ----------------------------------- | ---------- |
| `I5`      | Integer, 5 columns wide             | 12345      |
| `F8.2`    | Real, 8 columns, 2 decimals         | 123.45     |
| `E12.4`   | Exponential, 12 columns, 4 decimals | 1.2345E+02 |
| `A10`     | Character, 10 columns               | Hello      |
| `X`       | Space                               |            |
| `/`       | New line                            |            |

**Examples:**

```fortran
! Format with statement label
      INTEGER :: num
      REAL :: price

      num = 42
      price = 19.99

      WRITE(*, 100) num, price
100   FORMAT('Number:', I5, 5X, 'Price:', F8.2)
! Output: Number:   42     Price:   19.99
```

```fortran
! Inline format
      WRITE(*, '(A, I3, A, F6.2)') 'Count:', num, ' Price:', price
```

**Reading with Format:**

```fortran
      INTEGER :: year
      REAL :: temperature

      PRINT *, 'Enter year and temperature:'
      READ(*, '(I4, F6.2)') year, temperature
```

**File I/O with Unit Numbers:**

```fortran
      OPEN(UNIT=10, FILE='data.txt', STATUS='NEW')
      WRITE(10, '(I5, F8.2)') num, price
      CLOSE(10)
```

### 7. Control Structures

#### GOTO Statement

The GOTO statement transfers control to a labeled statement (generally discouraged in modern programming).

```fortran
      GOTO label

label statement
```

**Example:**

```fortran
      INTEGER :: i
      i = 1

10    PRINT *, i
      i = i + 1
      IF (i <= 5) GOTO 10

      PRINT *, 'Done'
```

#### Logical IF Statement

Executes a single statement if the condition is true.

**Syntax:**

```fortran
IF (logical_expression) statement
```

**Example:**

```fortran
      INTEGER :: x
      x = 10

      IF (x > 5) PRINT *, 'x is greater than 5'
      IF (x == 10) x = x + 1
```

**Block IF Statement:**

```fortran
      IF (condition) THEN
          statements
      ELSE IF (condition) THEN
          statements
      ELSE
          statements
      END IF
```

**Example:**

```fortran
      INTEGER :: score

      PRINT *, 'Enter score:'
      READ *, score

      IF (score >= 90) THEN
          PRINT *, 'Grade: A'
      ELSE IF (score >= 80) THEN
          PRINT *, 'Grade: B'
      ELSE IF (score >= 70) THEN
          PRINT *, 'Grade: C'
      ELSE
          PRINT *, 'Grade: F'
      END IF
```

**Logical Operators:**

- `.EQ.` or `==` (equal to)
- `.NE.` or `/=` (not equal to)
- `.LT.` or `<` (less than)
- `.LE.` or `<=` (less than or equal)
- `.GT.` or `>` (greater than)
- `.GE.` or `>=` (greater than or equal)
- `.AND.` (logical AND)
- `.OR.` (logical OR)
- `.NOT.` (logical NOT)

**Example:**

```fortran
      IF (x > 0 .AND. x < 100) THEN
          PRINT *, 'x is between 0 and 100'
      END IF
```

#### Arithmetic IF Statement

A three-way branch based on the sign of an arithmetic expression (FORTRAN 77).

**Syntax:**

```fortran
IF (arithmetic_expression) label1, label2, label3
```

- If expression < 0, go to label1
- If expression = 0, go to label2
- If expression > 0, go to label3

**Example:**

```fortran
      INTEGER :: num

      PRINT *, 'Enter a number:'
      READ *, num

      IF (num) 10, 20, 30

10    PRINT *, 'Negative'
      GOTO 40

20    PRINT *, 'Zero'
      GOTO 40

30    PRINT *, 'Positive'

40    CONTINUE
```

#### DO Loops

DO loops provide iteration in FORTRAN.

**Basic DO Loop Syntax:**

```fortran
DO label variable = start, end, step
    statements
label CONTINUE
```

**Modern Syntax (FORTRAN 90+):**

```fortran
DO variable = start, end, step
    statements
END DO
```

**Example:**

```fortran
! Print numbers 1 to 10
      INTEGER :: i

      DO 100 i = 1, 10
          PRINT *, i
100   CONTINUE
```
