## Introduction

Most of C is a subset of C++ which means most C programs are also C++ programs. The opposite is not true!

C++ was developed by Bjarne Stroustrup in the early 1980s to overcome the shortcomings of the C language.

All procedure-like entities in C++ are called **functions**.

Functions  in C++ what other languages may call procedures, methods, functions, or subprograms.

A **computer program** is a sequence of instructions that tells the computer, step by step, what it is we want it to do.

**Statements** are the instructions in a computer program.

C++11 includes a variable type name `auto` that deduces the type of variable based on an expression on the right side of the equal sign.
```cpp
auto x = expression;
```

C++11 also introduced a way to determine the type of a variable or expression using `decltype(expression)` The following code declares y to the same type as (x*3.5). Since (x*3.5) is a double, y is declared as a double.
```cpp
int x = 10;
decltype(x*3.5) y;
```

## Char Variables
**Characters** are things like letters ('a', 'Z'), digits ('1','9','0'), and other symbols that might appear on a screen ('$','+','^').

Computers don't actually store characters, they store numbers. When you store a value in a character variable, what is actually being stored is a code (ASCII) that represents that value.

## Shorthand Assignment Notation

A shorthand notation exists that combines the asignment operator and an arithmetic operator so that a given variable can change its value.

|Example                 |Equivalent to|
|---                     |---  
|`count += 2;`           |`count = count + 2;`|
|`total -= discount;`    |`total = total - discount;`|
|`bonus *= 2;`           |`bonus = bonus * 2`|
|`time /= rushFactor;`   |`time = time / rushFactor`|
|`change %= 100;`        |`change = change % 100;`|
|`amount *= cnt1 + cnt2;`|`amount = amount * (cnt1 + cnt2);`|

## Assignment Compatibility
Although it is usually a bad idea to do so, you can store an `int` value such as 65 in a variable of type `char` and you can store a letter such as 'Z' in a variable of type `int`.
```cpp
char x = 65;
int y = 'Z';
```
C/C++ considers characters to be small integers. Variables of type `char` consume less memory than type `int` so doing arithmetic with variables of type `char` can save some memory.

When assigned to a variable of type `bool` any nonzero integer will be stored as the value `true`. Zero will be stored as the value `false`.

When assigning a `bool` value to an interger variable, `true` will be stored as 1 and `false` will be stored as 0.

A **literal** is a name for one specific value and are often called **constants** in contrast to variables

## Escape sequences
An **escape sequence** tells the compiler that the sequences following a backslash, \, does not have the same meaning as the character appearing by itself.
|Sequences|Meaning|
|---|---|
|`\n`|New line|
|`\r`|Carriage return (Positions the cursor at the start of the current line)|
|`\t`|(Horizontal) Tab (Advances the cursor to the next tab stop)|
|`\a`|Alert(Sounds the alert noise, typically a bell)|
|`\\`|Backslash (Allows you to place a backslash in a quoted expression)|
|`\'`|Single quote (Mostly used to place a single quote inside single quotes)|
|`\"`|Double quote (Mostly used to place a double quote inside a quoted string)|
|`\v`|Vertical tab|
|`\b`|Backspace|
|`\f`|Form feed|
|`\?`|Question mark|

**Raw string literal** Assign the exact string “\t\\t\n” to the variable s like this
```cpp
string s = R"(\t\\t\n)";
```

**Modifiers** modifies(restricts) the variables being declared. Once example is `const`.
```cpp
const int BRANCH_COUNT = 10;
const int WINDOW_COUNT = 10;
```

## Type Cast
The expression `static_cast<double>` is like a function that takes an `int` argument and returns an "equivalent" value of type `double`.
```cpp
static_cast<double>(m);
```

The older form of type casting is shown below. The newer form is encouraged.
```cpp
int(9.3);
double(42);
(double)42;
```

## Precedence Rules
When an expression is evaluated, C++ follows the following rules:
1. Any operations that are inside of parentheses come first.
2. Then come multiplication, division, and modulus, done from left to right. Notice that, contrary to popular belief, multiplication does not come before division.
3. Addition and subtraction, done from left to right, come last.

## Increment and Decrement Operators
The **increment operator**, `++` adds 1 to the value of the variable.

The **decrement operator**, `--` subtracts 1 from the value of the operator.

The expression `n++` evaluates to the value of the variable n, and then the value of the variable n is incremented by 1.

The expression `++n` first increments the value of the variable n and then returns this increased value of n.

Both expressions increase the value of n by 1, but the expressions evaluate to different values. The same functionality also applies to the decrement operator.

The increment and decrement operators cannot be applied to anything other than a single variable.
```cpp
(x*y)++;  //illegal
--(x*y);  //illegal
5++;      //illegal
```

## Console Input/Output
Simple console input is done with the objects `cin`, `cout`, and `cerr`, all of which are 
defined in the library `iostream`.

The symbol "<<" is called the **stream insertion operator** because it is used when we want to insert something into a stream.

The object `cerr` sends its output to the standard error output stream which is normally the console screen. If you do nothing special to change things, then cout and cerr will both send their output to the console screen, so there is no difference between them.

The `cin` statement the >> points in the opposite direction from the << in a `cout` statement. The word `cin` is a stream that represents the keyboard. The symbol ">>" is called the **stream extraction operator.**

### Stream Extraction Operator
**Extraction Operator Rule #1:** The extraction operator always takes ("extracts") one item from its left operand (the input stream "cin" in this example) and places it into its right operand ("num1" in this example).

**Extraction Operator Rule #2:** The extraction operator always begins by skipping any leading whitespace in the input stream.

**Extraction Operator Rule #3:** The extraction operator is always customized according to the type of its right operand, so that it will read exactly one value of that type. It then stops, and anything left in the input stream remains there.

When the user types some input and then presses "enter", pressing "enter" causes two things to happen. First it causes the data just typed to be placed into the input stream. Second, it places a newline character into the input stream.

```cpp
cin.ignore(); //This function consumes exactly one character from the input stream. Can be helpful in consuming a newline character left in the input stream from a user pressing enter
```
