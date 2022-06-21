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

On most systems, the result of an illegal array index is that your program will simply do something wrong, possibly disastrously wrong, and will do so without giving you any warning. Consider our array from before ``int a[6];``
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

Often, the exact size needed for an array is not known when a program is written. Thus, it is common to declare an array to be of the largest size the program could possibly need and allow it to use as much or as little of the array as is needed.

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
In C++, once your program creates an array, it cannot change the length of the array. **Vectors** serve the same purpose as arrays except that they can change length while the program is running. Vectors are defined in the library ``vector``, which places them in the ``std`` namespace

You declare a variable, v, for a vector with base type int as follows:
```cpp
#include <vector>
using namespace std;

vector<int> v;
```

The notation ``vector<int>`` is a class name, and so the previous declaration of v as a vector of type ``vector<int>`` includes a call to the default constructor for the class ``vector<int>`` that creates a vector object that is empty (has no elements).

You can read and change elements of vectors in the same way as arrays.
```cpp
v[i] = 42;
```
However, you cannot initialize the ith element using ``v[i]`` like how you would in an array; you can only change an element that has already been given some value. To add an element to a vector for the first time, you normally use the member function ``push_back``.
```cpp
//push_back example
vector<double> sample;
sample.push_back(0.0);
sample.push_back(1.1);
sample.push_back(2.2);
```

The member function ``size()`` can be used to determine how many elements are in a vector. This function returns a value of type ``unsigned int``, not a value of type ``int`` and should be automatically converted to type ``int`` when it needs to be, but some compilers may warn you that you are using an ``unsigned int`` where an ``int`` is required. Because of this, you may apply a type cast to be safe.

### Vector Efficiency
At any point in time a vector has a **capacity,** which is the number of elements for which it currently has memory allocated. The member function ``capacity( )`` can be used to find out the capacity of a vector. Do not confuse the capacity of a vector with the size of a vector. The size is the number of elements in a vector, whereas the capacity is the number of elements for which there is memory allocated. Typically the capacity is larger than the size, and the capacity is always greater than or equal to the size.

Whenever a vector runs out of capacity and needs room for an additional member, the capacity is automatically increased. The amount of increase is implementation dependent but always allows room for more capacity than is immediately needed. A common implementation scheme is for the capacity to double whenever it needs to increase.

If efficiency is a concern, you can use the member function ``reserve()`` to explicitly increase the capacity of a vector. For example,
```cpp
v.reserve(32);
```
sets the capacity to at least 32 elements.

``reserve()`` works well for increasing the capacity of a vector, but it does not necessarily decrease the capacity of a vector if the argument is smaller than the current capacity.

Change the size of a vector using ``resize()``. For example
```cpp
v.resize(24);
```
resizes the vector v to 24 elements. If the previous size was less than 24 then the new elements are initialized with the constructor with an integer argument. If the previous size was greater than 24, then all but the first 24 elements are lost.

## Character Manipulation Tools
Any form of string is ultimately composed of individual characters. Thus, when doing string processing it is often helpful to have tools at your disposal to test and manipulate individual values of type ``char``.

Before now, we have used ``cin`` with the extraction operator, ``>>``, in order to read a character of input (or any other input, for that matter). When you use the extraction operator ``>>``, some things are done for you automatically, such as skipping over whitespace. But sometimes you do not want to skip over whitespace. The member function ``cin.get`` reads the next input character no matter whether the character is whitespace or not.
```cpp
char nextSymbol;
cin.get(nextSymbol);
```
Your program can read any character in this way.

A useful thing you can do with ``get()`` is to have your program detect the end of a line. The example code here echoes a line of input exactly.
```cpp
cout << "Enter a line of input and I will echo it:\n";
char symbol;
do
{
    cin.get(symbol);
    cout << symbol;
} while (symbol != '\n');
cout << "That's all for this demonstration.\n";
```

'\n' is a value of type ``char``. "\n" is a value of type ``string`` and thus cannot be stored in a variable fo type ``char``.

The member function ``cout.put()`` allows your program to output one character and is analogous to ``get()``. ``put()`` does not allow you to do anything you could not do with the insertion operator ``<<``.

The function ``cin.putback`` takes one argument of type ``char`` and places the value of that argument back in the input stream so that it will be the next character to be read. The argument can be any expression that evaluates to a value of type ``char``.

The function ``cin.peek`` returns the next character to be read by ``cin``, but does not use up that character; the next read starts with that character.

If you want to skip over input up to some designated character you can use the ``cin.ignore`` member function. This is useful to ignore the unexpected '\n' that ends every input line.

### Character-Manipulating Functions
Some functions in ``<cctype>``
|Function               |Description                |
|---                    |---                        |
|``toupper(char_exp)``  |Returns uppercase version of ``char_exp`` (as a value of type ``int``)|
|``tolower(char_exp)``  |Returns lowercase version of ``char_exp`` (as a value of type ``int``)|
|``isupper(char_exp)``  |Returns ``true`` if ``char_exp`` is uppercase; ``false`` otherwise|
|``islower(char_exp)``  |Returns ``true`` if ``char_exp`` is lowercase; ``false`` otherwise|
|``isalpha(char_exp)``  |Returns ``true`` if ``char_exp`` is letter of the alphabet; ``false`` otherwise|
|``isdigit(char_exp)``  |Returns ``true`` if ``char_exp`` is a digit '0' through '9'; ``false`` otherwise|
|``isalnum(char_exp)``  |Returns ``true`` if ``char_exp`` is a letter or digit; ``false`` otherwise|
|``isspace(char_exp)``  |Returns ``true`` if ``char_exp`` is a whitespace character(blank or newline); ``false`` otherwise|
|``ispunct(char_exp)``  |Returns ``true`` if ``char_exp`` is a character other than whitespace, letter, or digit; ``false`` otherwise|
|``isprint(char_exp)``  |Returns ``true`` if ``char_exp`` is a printing character; ``false`` otherwise|
|``isgraph(char_exp)``  |Returns ``true`` if ``char_exp`` is a printing character other than whitespace; ``false`` otherwise|
|``isctrl(char_exp)``   |Returns ``true`` if ``char_exp`` is a control character; ``false`` otherwise|
