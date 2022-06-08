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
The C++ library with header file <cstdlib> contains a random number function named rand. When your program invokes rand, the function returns an integer in the range 0 to RAND_MAX, inclusive. RAND_MAX is a defined integer constant whose definition is also in the library with header file <cstdlib>. The exact value of RAND_MAX is system-dependent but will always be at least 32767 (the maximum two-byte positive integer).
  
To get a random number in the range 0 to 10, use ``rand() % 11`` For 0 to 100, ``rand() % 101`` etc
	
