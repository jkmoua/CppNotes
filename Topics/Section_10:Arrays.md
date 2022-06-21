# Arrays

An **array** is a list of variables with a uniform naming mechanism that can be declared in a single line of code. An array is declared as follows
```cpp
int nameOfArray[];
```

The individual variables that make up the array are referred to in a variety of ways. They are either called **indexed variables**, **subscripted variables**, or **elements.**

All of the elements of an array are of the same type called the **base type.**

Arrays and regular variables can be declared together. For example,
```cpp
int exampleArray[], exampleInt;
```

The indexes of an array always start with 0 and end with the integer that is one less than the size of the array. 

Some but not all compilers will allow you to specify the size of an array using a variable. For the sake of portability, it is best to just use a literal or constant.

## Arrays in Memory
The locations of the various array indexed variables for a specific array are always placed next to one another in memory. For example, when you declare the array ``int a[6];``, the computer reserves enough memory to hold six variables of type int one after the other. The computer then remembers only the address of the variable indexed 0, but not any of the other indexed variables. When your program needs the address of some other indexed variable in this array, the computer calculates the address for this other indexed variable from the address of ``a[0]``. This implementation of arrays in C++ is responsible for many of the peculiarities of arrays in C++.

On most systems, the result of an illegal array index is that your program will simply do something wrong, possibly disastrously wrong, and will do so without giving you any warning. Consider our array from before 
```cpp
int a[6];
```
Suppose we later write
```cpp
a[i] = 238;
```
And suppose i happens to be 7, the computer would proceed as if a[7] were a legal indexed variable and then place the value '238' at the location in memory where a[7] should be (7 int memory locations after a[0]), but this could be the memory location of another variable for example and thus, the variable value stored at this memory location will have been unintentionally changed without us ever getting a warning or error.

## The Range-Based for loop
C++11 introduces the range-based for loop which simplifies iteration over every element in an array. The syntax for this is
```cpp
for (datatype varname : array)
{
    // varname is set to each successive element in the array
}
```

For example:
```cpp
int arr[] = {20, 30, 40, 50};
for (int x : arr)
    cout << x << " ";
cout << endl;
```
gives us an output of 20 30 40 50.

With this syntax, we can use & to define the variable as pass by reference to pass changes through to the array or ``const`` to indicate that the elements can't change.

Arrays can be initialized with the following syntax:
```cpp
int b[] = {5, 12, 11};
```

## Arrays in Functions
An indexed variable can be an argument to a function in exactly the same way that any variable of the array base type can be an argument.

```cpp
//consider an array
double a[10];

//then it is legal for a function that takes arguments of type double to do
myFunction(a[3]);
```

### Array Formal Parameters and Arguments
An argument to a function may be an entire array, but an argument for an entire array is neither a call-by-value argument nor a call-by-reference argument. It is a new kind of argument known as an **array argument.** When an array argument is plugged in for an array parameter, all that is given to the function is the address in memory of the first indexed variable of the array argument (the one indexed by 0). The array argument does not tell the function the size of the array. Therefore, when you have an array parameter to a function, you normally must also have another formal parameter of type int that gives the size of the array.

An array argument is like a call-by-reference argument in the following way: If the function body changes the array parameter, then when the function is called, that change is actually made to the array argument.
```cpp
//Example syntax
void arrayFunc(double a[], int arraySize);
```

You can include the keyword ``const`` with your array parameter to disallow changes to the array argument.
```cpp
void arrayFunc(const double a[], int arraySize);
```

Functions may not return an array in the same way they can return a value of type ``int`` or ``double``. To acheive this functionality, you return a pointer to the array. This is discussed in the pointers section.

OFten, the exact size needed for an array is not known when a program is written. Thus, it is common to declare an array to be of the largest size the program could possibly need and allow it to use as much or as little of the array as is needed.

## Multidimensional Arrays
Declare a multimensional array as follows
```cpp
char page[30][100];
int matrix[2][3];
double threeDPicture[10][20][30];
```

The most common number of indexes is two. A two-dimensional array can be visualized as a two dimensional table with the first index giving the row and second index giving the column.

In C++, a two-dimensional array is actually an array of arrays.

### Multidimensional Array Parameters
When a multidimensional array parameter is given in a function heading or function declaration, the size of the first dimension is not given, but the remaining dimension sizes must be given in square brackets. Since the first dimension size is not given, you usually need an additional parameter of type int that gives the size of this first dimension. The following is an example of a function declaration with a two-dimensional array parameter p:
```cpp
void getPage(char p[][100], int sizeDimension1)
```

Viewing a two-dimensional array as an array of arrays will help you to understand how C++ handles parameters for multidimensional arrays.

The first dimension is really the index of the array and is treated just like an array index for an ordinary, one-dimensional array. The second dimension is part of the description of the base type, which is an array of characters of size 100 for our example above.

## Vectors
In C++, once your program creates an array, it cannot change the length of the array. **Vectors** serve the same purpose as arrays except that they can change length while the program is running.

You declare a variable, v, for a vector with base type int as follows:
```cpp
vector<int> v;
```

The notation vector<int> is a class name, and so the previous declaration of v as a vector of type vector<int> includes a call to the default constructor for the class vector<int> that creates a vector object that is empty (has no elements).

