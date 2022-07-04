# Recursion
## Recursive _void_ Functions

In C++ a function definition may contain a call to the function being defined. In such cases the function is said to be **recursive.**

When a function is called, the computer plugs in the arguments for the parameter(s) and begins to execute the code. If it should encounter a recursive call, it temporarily stops its computation because it must know the result of the recursive call before it can proceed. It saves all the information it needs to continue the computation later on, and proceeds to evaluate the recursive call. When the recursive call is completed, the computer returns to finish the outer computation.

In order for a recursive function definition to be useful, it must be designed so that any call of the function must ultimately terminate with some piece of code that does not depend on recursion.

The general outline of a successful recursive function definition is as follows:
- One or more cases in which the function accomplishes its task by using one or more recursive calls to accomplish one or more smaller versions of the task.
- One or more cases in which the function accomplishes its task without the use of any recursive calls. These cases without any recursive calls are called base cases or stopping cases.

Every call of the function must eventually lead to a stopping case or else the function call will never end because of an infinite chain of recursive calls.

The most common way to ensure that a stopping case is eventually reached is to write the function so that some (positive) numeric quantity is decreased on each recursive call and to provide a stopping case for some “small” value. 

If every recursive call produces another recursive call, then a call to the function will, in theory, run forever. This is called **infinite recursion.**

## Stacks for Recursion
To keep track of recursion (and a number of other things), most computer systems make use of a structure called a stack. A **stack** is a very specialized kind of memory structure that is analogous to a stack of paper.

Since the last sheet that is put on the stack is the first sheet taken off the stack, a stack is often called a **last-in/first-out** memory structure.

The computer uses portions of memory rather than pieces of paper. The content of one of these portions of memory (“sheets of paper”) is called an **activation frame.**

If there is a long chain in which a function makes a recursive call to itself, and that call results in another recursive call, and that call produces yet another recursive call, and so forth, then each recursive call in this chain will cause another activation frame to be placed on the stack. If this chain is too long, the stack will attempt to grow beyond its limit. This is an error condition known as a **stack overflow.**

A function that uses **tail recursion** has the property that no further computation occurs after the recursive call; the function immediately returns.

## Recursive Functions That Return a Value
