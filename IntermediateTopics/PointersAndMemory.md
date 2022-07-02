# Pointers

A **pointer** is the memory address of a variable. 

Recall: When a variable is a call-by-reference argument in a function call, the function is given this argument variable in the form of a pointer to the variable

Recall: An array is given to a function (or to anything else, for that matter) by giving a pointer to the first array element.

A variable that can hold pointers to other variables of type _Type_Name_ is declared similar to the way you declare a variable of type _Type_Name_, except that you place an asterisk at the beginning of the variable name. The syntax is as follow:
```cpp
Type_Name *Variable_Name1, *Variable_Name2,...;
// Example
double *pointer1, *pointer2;
```

A pointer is an address, and an address is an integer, but a pointer is not an integer. A pointer is not a value of type int or of any other numeric type.

The ``*`` operator in front of a pointer variable produces the variable to which it points. When used this way, the ``*`` operator is called the **dereferencing operator.** 

The operator ``&`` in front of an ordinary variable produces the address of that variable; that is, it produces a pointer that points to the variable. The ``&`` operator is simply called the **address-of operator.**
```cpp
double *p, v;   // declares a variable v of type double and a 
                // pointer variable p that points to a double vairable
                
p = &v;         // sets the value of p so that p points to the variable v
*p = 9.99;      // *p produces the variable pointed to by p
                // the previous line sets the value of v to 9.99
```

### Using =
```cpp
int *p1, *p2;
p1 = p2;        // This assignment changes p1 so that it points to the same thing
                // which p2 is currently pointing
                
*p1 = *p2       // When you add the asterisk, you are not dealing with the pointers p1 and p2, 
                // but with the variables to which the pointers are pointing.                
```

### The _new_ Operator
The operator ``new`` can be used to create variables that have no identifiers to serve as their names. These nameless variables are referred to via pointers. 
```cpp
int *p1;        // declare a pointer p1 that points to an int variable
p1 = new int;   // creates a new int variable and sets p1 equal to the 
                // address of this new variable
*p1 = 42;       // This new, nameless variable can be referred to as *p1 and you can 
                // do anything with it that you can do any other variable of type int
*p1 = *p1 + 7;
```

Variables that are created using the `new` operator are called **dynamically allocated variables** or simply **dynamic variables**, because they are created and destroyed while the program is running.

When the `new` operator is used to create a dynamic variable of a class type, a constructor for the class is invoked. If you do not specify which constructor to use, the default constructor is invoked. You can specify a different constructor by including arguments.

A similar notation allows you to initialize dynamic variables of nonclass types, as illustrated 
here:
```cpp
int *n;
n = new int(17); // initializes *n to 17
```

With earlier C++ compilers, if there was insufficient available memory to create the `new` variable, then `new` returned a special pointer named ``NULL``. The C++ standard provides that if there is insufficient available memory to create the new variable, then the `new` operator, by default, terminates the program.

A pointer type is a full-fledged type and can be used in the same ways as other types. In particular, you can have a function parameter of a pointer type and you can have a function that returns a pointer type. For example, the following function has a parameter that is a pointer to an int variable and returns a (possibly different) pointer to an int variable:
```cpp
int* findOtherPointer(int* p);
```

## Basic Memory Management
A special area of memory, called the **freestore** or the **heap**, is reserved for dynamically allocated variables. Any new dynamic variable created by a program consumes some of the memory in the freestore.

_NULL_ is a special constant pointer value that is used to give a value to a pointer variable that would not otherwise have a value. _NULL_ can be assigned to a pointer variable of any type. The identifier _NULL_ is defined in a number of libraries, including ``<iostream>``. (The constant _NULL_ is actually the integer 0.)

The fact that _NULL_ is actually the number 0 leads to an ambiguity problem. Consider this overload function:
```cpp
void func(int *p);
void func(int i);
```
Which function will be invoked if we call ``func(NULL)``? Since _NULL_ is the number 0, both are equally valid.

C++11 resolves this problem by introducing a new constant, ``nullptr``. ``nullptr`` is not the integer 0; it is a literal constant used to represent a null pointer. Use ``nullptr`` anywhere you would have used ``NULL`` for a pointer.

### The _delete_ operator
The _**delete**_ operator eliminates a dynamic variable and returns the memory that the dynamic variable occupied to the freestore. The memory can then be reused to create new dynamic variables. After a call to delete, the value of the pointer variable is undefined.
```cpp
delete p;       // eliminates the dynamic variable pointed to by the pointer variable p
```

When you apply delete to a pointer variable, the dynamic variable to which it is pointing is destroyed. At that point, the value of the pointer variable is undefined, which means that you do not know where it is pointing. These undefined pointer variables are called **dangling pointers.**

If p is a dangling pointer and your program applies the dereferencing operator `*` to p (to produce the expression `*p`), the result is unpredictable and usually disastrous.

One way to avoid dangling pointers is to set any dangling pointer variable equal to _NULL_. Then your program can test the pointer variable to see if it is equal to _NULL_ before applying the dereferencing operator `*` to the pointer variable. When you use this technique, you follow a call to delete by code that sets all dangling pointers equal to _NULL_.

### Dynamic Variables and Automatic Variables
Local variables — that is, variables declared within a function definition are sometimes called **automatic variables** because their dynamic properties are controlled automatically for you. They are automatically created when the function in which they are declared is called and automatically destroyed when the function call ends.

Variables declared outside any function or class definition, including outside _main_, are called **global variables.** These global variables are sometimes called **statically allocated variables**, because they are truly static in contrast to dynamic and automatic variables.

### _typedef_
You can use _**typedef**_ to define an alias for any type name or definition. 
```cpp
typedef int* IntPtr;      //creates an alias for the pointer type that points to int variables

// The following two pointer variable declarations are now equivalent
IntPtr p;
int *p;
```

Keep in mind that a typedef does not produce a new type but is simply an alias for the type definition.

A big advantage of _typedef_ is when you define a function with a call-by-reference parameter for a pointer variable. Without the defined pointer type name, you would need to include both an * and an & in the declaration for the function, and the details can get confusing.
```cpp
void sampleFunction(IntPtr& pointerVariable);

// vs

void sampleFunction(int*& pointerVariable);
```

###Pointers as Call-by-Value Parameters
When a call-by-value parameter is of a pointer type, its behavior can occasionally be subtle and troublesome. A pointer has two things associated with it: the pointer value (memory address) and the value stored where p points. A function may change the value of the variable pointed to by a pointer (`*ptr`) while not change the value of `ptr` itself.

## Dynamic Arrays
