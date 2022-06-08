# Functions

**function call** = **function invocation**

If your program uses a predefined function from some library, then it must contain an **include directive** that names that library.

**Top-down programming** or **stepwise refinement** - Defining the solution at the highest level of functionality and breaking it down further and further into small routines that can be easily documented and coded.

A **function prototype** is placed at the top of the program and it lets the compiler know that it's okay if there is a call to a function because one will be defined later on.

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

The choice between pass-by-value and pass-by-reference is made for each individual parameter, not just once for each function.

Functions should be self-contained modules that are designed separately from the rest of the program. Therefore, choose parameter names that most closely represent them in the context of the function. The arguments that a function will take may well be variables in another function. So long as all variables and parameters have meaningful names that represent them in their context.

## Random Numbers, the rand() function
The C++ library with header file <cstdlib> contains a random number function named rand. When your program invokes rand, the function returns an integer in the range 0 to RAND_MAX, inclusive. RAND_MAX is a defined integer constant whose definition is also in the library with header file <cstdlib>. The exact value of RAND_MAX is system-dependent but will always be at least 32767 (the maximum two-byte positive integer).
