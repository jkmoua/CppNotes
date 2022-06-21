# Flow of Control
**Short-circuit evluation** - C++ first evaluates the leftmost of the two expressions joined by an && or ||. If that gives it enough information to determine the final value of the expression (independent of the value of the second expression), then C++ does not bother to evaluate the second expression. ``false && `` and ``true || `` will always be false and true respectively regardless of the second expression.

Short-circuit evaluation can be useful in the even that the second subexpression is undefined i.e. dividing by a variable that may be zero which will cause a run-time error.

In **complete evaluation,** when two expressions are joined by an && or ||, both subexpressions are always evaluated and then the truth tables are used to obtain the value of the final expression.

## Switch Statement
When a **switch statement** is executed, one of a number of different branches is executed. The choice of which branch to execute is determined by a **controlling expression** given in parentheses after the keyword switch. The controlling expression for a switch statement must always return either a bool value, an enum constant (discussed later in this chapter), one of the integer types, or a character. When the switch statement is executed, this controlling expression is evaluated and the computer looks at the constant values given after the various occurrences of the case identifiers. If it finds a constant that equals the value of the controlling expression, it executes the code for that case.

```cpp
//switch statement syntax
switch (Controlling_Expression)
{
    case Constant_1:
        Statement_Sequence_1
        break;
    case Constant_2:
        Statement_Sequence_2
        break;
        .
        .
        .
    case Constant_n:
        Statement_Sequence_n
        break;
    default:
        Default_Statement_Sequence
}
```

You can have two case labels for the same section of code in a switch statement.
```cpp
switch (Controlling_Expression)
{
    case 'A':
    case 'a':
        cout << "Excellent. You need not take the final.\n";
        break;
}
```

If no case label has a constant that matches the value of the controlling expression, then the statements following the default label are executed.

You can use a multiway if-else statement anywhere you can use a switch statement. The switch statement is a particularly better choice for implementing menus.

## Enumeration Types

An **enumeration type** is a type whose values are defined by a list of constants of type int and it is very much like a list of declared constants. If no numeric values are assign to the idenrifiers in an enumeration, the default for the first enumaration constant is 0 and the rest increase by 1 unless you set onbe or more of the constants.
```cpp
enum MyEnum { ONE = 17, TWO, THREE, FOUR = −3, FIVE };

//is equivalent to

enum MyEnum { ONE = 17, TWO = 18, THREE = 19, FOUR = −3, FIVE = -2 };
```

C++11 introduced a new version of enumerations called **stron enums** or **enum classes** which allows us to define an enumeration type whose values need not be integers. For example,
```cpp
enum class Days { Sun, Mon, Tue, Wed, Thu, Fri, Sat };
enum class Weather { Rain, Sun };
Days d = Days::Tue;
Weather w = Weather::Sun;
```

## The Conditional Operator
The **conditional operator** is an operator that allows us to embed a condition inside of an expression. It is reminiscent of an older programming style, and its use is not advised!

Consider the statement
```cpp
if (n1 > n2)
    max = n1;
else
    max = n2;
```
This can be expressed using the conditional operator as follows:
```cpp
max = (n1 > n2) ? n1 : n2;
```

## Loops
The important difference between the **while** and **do-while** loops involves when the controlling Boolean expression is checked. With a while statement, the Boolean expression is checked before the loop body is executed. If the Boolean expression evaluates to false, the body is not executed at all. With a do-while statement, the body of the loop is executed first and the Boolean expression is checked after the loop body is executed. Thus, the do-while statement always executes the loop body at least once.

### Loop Patterns
The loop patterns discussed here are not actual C++ constructs. They are just helpful ways to categorize loops while learning. 

**Question Type Loop** - The decision about whether to continue executing the loop is made by asking the user a question.
```cpp
    cout << "Is there a ....? ";
    cin >> response;
    while (response == 'Y'){
        <body of loop>
  
        cout << "Is there another ....? ";    
        cin >> response;
    }
```

**Special-Value Type Loop** - The decision about whether to continue executing the loop is made by telling the user to enter aspecial value when they are done.
```cpp
    cout << "Enter... (negative number to quit) ";
    cin >> response;
    while (response >= 0){
        <body of loop>

        cout << "Enter... (negative number to quit) ";    
        cin >> response;
    }
```

A **counter controlled loop** is used when we know before entering the loop how many times it will be executed.
```cpp
    count = 0;
    while (count < howManyTimes){    
        <body of loop>

        count = count + 1;
    }
```

**A do-while statement** - The only difference between a while loop and a do-while loop is that in a while loop the condition is checked at the top of the loop, whereas in a do-while loop the condition is checked at the bottom of the loop.
```cpp
do
{
    Statement_1
    Statement_2
    .
    .
    .
    Statement_Last
} while (Boolean_Expression);
```

Use a do-while loop if you know that the user will want to execute the loop at least once. Use a while loop if you aren't sure.

### For loops

The **for statement** is most commonly used to step through some integer variable in equal increments.
```cpp
    for (Initialization_Action; Boolean_Expression; Update_Action) {
        <body>
    }

    for (count = 0; count < N; count++){    
        <body>    
    }
```

The first expression tells how the variable, variables, or other things are initialized, and is executed exactly once before execution of the loop begins.
The second gives a Boolean expression that is checked before each iteration to check if the loop should end.
The last expression tells how the loop control variable is updated after each iteration of the loop body.

If you place a semicolon after nothing, you still create a statement. Thus, the semicolon by itself is a statement, which is called the **empty statement** or the **null statement.** The empty statement performs no action, but it still is a statement.

The two ways of altering the flow of control are to insert a **break** or **continue** statement. The break statement ends the loop. The continue statement ends the current iteration of the loop body.

When executed, the break statement ends the nearest enclosing switch or loop statement. When executed, the continue statement ends the current loop body iteration of the nearest enclosing loop statement.

When using the continue statement in a for loop is that the continue statement transfers control to the update expression. So, any loop control variable will be updated immediately after the continue statement is executed.

## The Comma Operator
The **comma operator** is a way of evaluating a list of expressions and returning the value of the last expression.

The comma operator is illustrated below
```cpp
result = (first = 2, second = first + 1);
//result is set equal to 2
```

For longer lists of expressions connected with commas, you should use parentheses if the order of evaluation is important.
For example,
```cpp
result = ((first = 2, second = first + 1), third = second + 1);
//result is set equal to 4
```

## File Input
Steps to read from or write to a file in your program
1. Add ``#include <fstream>`` to the top of your file
2. Declare an input stream variable which represents a file ``ifstream fileIdentifier;``
3. Open the file using ``fileIdentifier.open("fileName.txt");``
4. Check to make sure the file opened successfully
```cpp
    if (!fileIdentifier){
        cout << "couldn't open file." << endl;
    } else {
```
5. Use a special-value type loop to read through the file

Reading one character at a time
```cpp
    fileIdentifier.get(ch);
    while (fileIdentifier){
        cout << ch;
        fileIdentifier.get(ch);
    }
```

Reading one string at a time
```cpp
    fileIdentifier >> astring;        
    while (fileIdentifier){                    
        <process astring>
        fileIdentifier >> astring;
    }
```

Stream variables can be used in place of a logical expression which is why it appears where it does in our loops. When everything is fine, they equate to "true." They equate to "false" when the stream variable has gone into error. Stream variables can go into error for reasons such as the file not being found or when an attempt is made to read past the end of the file. This can be useful since this is likely when we want our loop to stop.

6. Close the file ``fileIdentifier.close();``

Use ``fileIdentifier.clear()`` to clear the error flags of the respective stream.

