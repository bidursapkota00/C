# Complete C Programming Course Guide

## Course Duration: 19 Hours

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
