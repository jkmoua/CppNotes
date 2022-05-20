# Introduction

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

