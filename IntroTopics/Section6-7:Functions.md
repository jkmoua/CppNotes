# Functions
A **function** is a block of code which only runs when called. Functions may return a value or may perform some other action without returning a value. We use functions to break our programs down into smaller parts.

**function call** = **function invocation**

If your program uses a predefined function from some library, then it must contain an **include directive** that names that library.

**Top-down programming** or **stepwise refinement** - defining the solution at the highest level of functionality and breaking it down further and further into small routines that can be easily documented and coded.

A **function prototype (function declaration)** must appear before a call to the function. It is typically placed before main at the top of the program. It lets the compiler know that it's okay if there is a call to a function because one will be defined later on.
```cpp
Type_Returned_Or_void FunctionName (Parameter_List);
```

## Parameters

Function **arguments** are the real values passed to the function. When the function call is executed, the arguments are plugged in for the parameters.

Function **parameters** are the names listed in the function's definition. A parameter (of any sort) is a kind of blank or placeholder that is filled in with something when the function is called.

When writing a function always look at the situation from the perspective of the function you are writing.

Think of parameter passing as communication, not as a sharing of variables.

**Pass-by-value** - only the value of the arguments is plugged into the function.

**Pass-by-reference** - The argument is a variable, and the variable itself is a plugged in. Therefore, the variable's value can be changed by the function invocation.
Pass-by-reference parameters are indicated by the appending the ampersand sign to the parameter type
```cpp
void getInput(double& variableOne, int& variableTwo);
```

If you want a function to change the value of a variable then use pass-by-reference. Otherwise, use pass-by-value.

The choice between pass-by-value and pass-by-reference is made for each individual parameter, not just once for each function. For example, you can have a function declaration like this
```cpp
void functionName(int& par1, int par2, double& par3);
```

Functions should be self-contained modules that are designed separately from the rest of the program. Therefore, choose parameter names that most closely represent them in the context of the function. The arguments that a function will take may well be variables in another function. So long as all variables and parameters have meaningful names that represent them in their context.

## Commenting - Preconditions and Postconditions
A good way to write function declaration comments is break it down into two kinds of information. First, state what is assumed to be true when the function is called. The function should not be used and cannot be expected to perform correctly unless the **precondition** holds. The **postcondition** describes the effect of the function call; that is, the postcondition tells what will be true after the function is executed in a situation in which the precondition holds.

### Procedural Abstraction
When applied to a function definition, the principle of procedural abstraction means that your function should be written so that it can be used like a black box. This means that the programmer who uses the function should not need to look at the body of the function definition to see how the function works. The function declaration and the accompanying comment should be all the programmer needs to know in order to use the function. To ensure that your function definitions have this important property, you should strictly adhere to the following rules:
-  The function declaration comment should tell the programmer any and all conditions that are required of the arguments to the function and should describe the result of a function invocation.
-   All variables used in the function body should be declared in the function body. (The parameters do not need to be declared, because they are listed in the function heading.)

## Random Numbers, rand() and srand()
The C++ library with header file `<cstdlib>` contains a random number function named rand. When your program invokes rand, the function returns an integer in the range 0 to RAND_MAX, inclusive. RAND_MAX is a defined integer constant whose definition is also in the library with header file `<cstdlib>`. The exact value of RAND_MAX is system-dependent but will always be at least 32767 (the maximum two-byte positive integer).

To get a random number in the range 0 to 10, use ``rand() % 11`` For 0 to 100, ``rand() % 101`` etc

rand does not generate truly random numbers. If you could return the computer to the state it was in when the sequence of calls to rand began, you would get the same sequence of “random numbers.”

The function ``srand()`` takes one positive integer argument, which is the **seed** and sets it for the function ``rand.`` If you start the random number generator with the same seed, over and over, then each time it will produce the same (random-looking) sequence of numbers.

For a random probability instead of a random integer, the following generates a pseudorandom floating-point value between 0.0 and 1.0:
```cpp
(RAND_MAX - rand( ))/static_cast<double>(RAND_MAX)
```

Using `#include <ctime>` with the statement `srand(static_cast<unsigned>(time(nullptr)));` will use the clock time to initialize the random number generator which will allow you to get a different sequence of random numbers each time the program is run.

## Overloading
If you have two or more function definitions for the same function name, that is called overloading. When you overload a function name, the function definitions must have different numbers of formal parameters or some formal parameters of different types. When there is a function call, the compiler uses the function definition whose number of formal parameters and types of formal parameters match the arguments in the function call.

Each function definition has its own prototype.

Any two function definitions that have the same function name must use different numbers of formal parameters or have one or more parameters of different types (or both). You cannot overload based solely on const or solely on call-by-value versus call-by-reference parameters.

Overloading Example:
```cpp
double avg(double n1, double n2)
{
  return (n1 + n2) / 2.0;
}

double avg(double n1, double n2, double, n3)
{
  return (n1 + n2 + n3) / 3.0;
}
```

The rules that the compiler uses for resolving which of multiple overloaded definitions of a function name to apply to a given function call are as follows:
1. Exact match: If the number and types of arguments exactly match a definition (without any automatic type conversion), then that is the definition used.
2. Match using automatic type conversion: If there is no exact match but there is a match using automatic type conversion, then that match is used.

You can specify a default argument for one or more call-by-value parameters in a function. If the corresponding argument is omitted, then it is replaced by the default argument.

Example:
```cpp
void showVolume(int length, int width = 1, int height = 1);
```

A default argument is only given the first time the function is declared (or defined, if that occurs first).

You may have more than one default argument, but all the default argument positions must be in the rightmost positions. If you have more than one default argument, then when the function is invoked, you must omit arguments starting from the right. In the example above, there is no way to omit the second argument in an invocation of showVolume without also omitting the third argument.

## Testing and Debugging Functions
An **assertion** is a statement that is either true or false. Assertions are used to document and check the correctness of programs. The ``assert`` macro is used like a void function that takes one call-by-value parameter of type bool.

You can check that the precondition holds for a function invocation, as shown by the following example:
```cpp
assert((0 < currentCoin) && (currentCoin < 100)
      && (0 <= currentAmountLeft) && (currentAmountLeft < 100));
computeCoin(currentCoin, number, currentAmountLeft);
```
If the precondition is not satisfied, your program will end and an error message will be output.

The assert macro is defined in the library cassert, so any program that uses the assert macro must contain the following: ``#include <cassert>``

If you insert ``#define NDEBUG`` in your program after it is fully debugged, all assert invocations in your program will be turned off. If you later change your program and need to debug it again, you can turn the assert invocations back on by deleting the ``#define NDEBUG`` line (or commenting it out).

**Driver programs** are special programs written to test individual functions outside of the program they are intended for. All driver programs need to do is obtain reasonable values for the function arguments in as simple a way as possible—typically from the user—then execute the function and show the result.

**Stubs** are simplified versions of missing or untested functions which allow you to test programs without needing these complete and tested functions yet. They do not need to perform the correct calculations, but they will deliver values that suffice for testing, and they are simple enough that you can have confidence in their performance.

A common approach is to use driver programs to test some basic functions, such as input and output, and then use a program with stubs to test the remaining functions. The stubs are replaced by functions one at a time: One stub is replaced by a complete function and tested; once that function is fully tested, another stub is replaced by a full function definition, and so forth, until the final program is produced.

Every function should be tested in a program in which every other function in that program has already been fully tested and debugged.
