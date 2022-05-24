# Flow of Control
**Short-circuit evluation** - C++ first evaluates the leftmost of the two expressions joined by an && or ||. If that gives it enough information to determine the final value of the expression (independent of the value of the second expression), then C++ does not bother to evaluate the second expression.

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
    cout << "Excellent. "
         << "You need not take the final.\n";
    break;
}
```

If no case label has a constant that matches the value of the controlling expression, then the statements following the default label are executed.

You can use a multiway if-else statement anywhere you can use a switch statement.
