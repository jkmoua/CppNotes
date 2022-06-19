## Structures

Sometimes it is useful to have a collection of values of different types and to treat the collection as a single item. In C++, structures do exactly this.

A **structure** type is a user-defined composite type. Analogous to the primitive types we are already familiar with such as ``int``, ``double``, and ``char``, we create variables of this type and store values in the variables of specified type. In the case of structures, its values are variables, all of which can be their own type, even other structures! The structure's values are variables called **members** and they will also hold their own values.

Before we can create a variable of a structure type, we must first define what this structure will contain. 

It is a convention that structure type names, the **structure tag,** starts with an uppercase letter.

Creating a structure is as follows
```cpp
//We first define the structure type telling the compiler what is the name 
//of the structure type, and what are the types of each member and their names.
struct StructureName{
    member1type member1name;
    member2type member2name;
    member3type member3name;
    .
    .
    .
    memberNtype memberNname;
};
```

Once we have defined our structure type, we can create variables of that type. An example below:
```cpp
//Structs are usually defined globally (outside any function definitions).
//We define a struct type called Autombile whose values are the variable "year" and "doors"
//of type int, a variable "horsePower" of type double, and a variable "model" of type char
struct Automobile
{
    int year;
    int doors;
    double horsePower;
    char model;
};

//In the rest of our program, we can now create variables of type Automobile to use.
int main()
{
    //We define variables of type Autombile.
    Automobile myCar, yourCar;

    //We access the member variables of our Autombile variables using the dot operator.
    myCar.Year = 2022;
    myCar.doors = 4;
    myCar.horsepower = 200.0;
    myCar.model = 'H';
}
```

Member variables of a structure type can be initialized at the time the structure variable is declared. From our example above, we could've intialized the variable myCar of type Autombile like this:
```cpp
Autombile myCar = {2022, 4, 200.0, 'H'};
```

The initializing values must be given in the order that corresponds to the order of member variables in the structure-type definition.

## Classes
A **class** is a type that is similar to a structure type, but a class type normally has member functions as well as member variables. A class is a type just like a structure and the types int and double. You can have variables of a class type, you can have parameters of a class type, a function can return a value of a class type, and more generally, you can use a class type like any other type.

Classes are perhaps the single most significant feature that separates the C++ language from the C language.

The value of a variable of a class type is called an **object** (therefore, when speaking loosely, a variable of a class type is also often called an object). An object has both data members and function members.

A **member function** is defined similar to any other function except that the Class_Name and the **scope resolution operator**, ::, are given in the function heading.
```cpp
Returned_Type Class_Name::Function_Name(Parameter_List)
{
    Function_Body_Statements
}
```

We access and call class member variables and functions the same way as we do structs, using the dot operator:
```cpp
classObject.classMemberVariable;
classObject.classMemberFunction();
```

### Encapsulation
A **data type** consists of a collection of values together with a set of basic operations defined on these values. For example, when we think of the data type ``int`` we think of its specified values, such as 0, 1, -1, 2, and so forth, but the operations on these values (+, -, \*, /, %, etc.) are also just as important.

A data type is called an **abstract data type** (abbreviated **ADT**) if the programmers who use the type do not have access to the details of how the values and operations are implemented. The predefined types, such as int, are all ADT's since we do not know how the operations such as + and * are implemented for the type int.

Classes, which are programmer-defined types, should also be ADTs; that is, the details of how the “operations” are implemented should be hidden from, or at least irrelevant to, any programmer who uses the class.

Defining a class so that the implementation of the member functions and the implementation of the data in objects are not known, or are at least irrelevant, to the programmer who uses the class is known by a number of different terms such as **information hiding, data abstraction, or encapsulation.**

One of the ways to apply this principle of encapsulation to your class definitions is to make all member variables private.

All members of a struct are public by default. Conversely, all members of a class are private by default. We can specify the access level of members using the ``public:`` and ``private:`` **access specifiers.** Now, the syntax for a class type is given below:
```cpp
class ClassName{
public:
    publicMemberFunction1();
    publicMemberFunction2();
    publicMemberFunction3();
    .
    .
    .
    publicMemberFunctionN();
private:
    privateMember1Type privateMember1Name;
    privateMember2Type privateMember2Name;
    privateMember3Type privateMember3Name;
    .
    .
    .
    privateMemberNType privateMember3Name;
};
```

For both structs and classes, their declarations do not allocate memory, they just define what the respective type will look like.

For classes in general, it is best practice to make member variables private, and member functions public, unless you have a good reason not to.

Now that we’ve talked about access specifiers, we can talk about the actual differences between a class and a struct in C++. A class defaults its members to private. A struct defaults its members to public. That's it!

In C, structs only have data members, not member functions. In C++, after designing classes (using the class keyword), Bjarne Stroustrup spent some amount of time considering whether structs (which were inherited from C) should be granted the ability to have member functions. Upon consideration, he determined that they should, in part to have a unified ruleset for both.

A C++ structure can do anything a class can do. Knowing this, it is best practice to use the struct keyword for public data-only structures and use the class keyword for objects that have both data and functions.

For classes, we refer to member functions that allow us to read the data in an object as **accessor functions.** The member functions that allow us to change the data are referred to as **mutator functions.** It is convention to name accessor functions using "get" and mutator functions using "set."

## Interface and Implementation
We define the rules for how to use a class as the **interface** or **application programmer interface.** For a C++ class, the interface consists of two sorts of things: the comments, usually at the beginning of the class definition, that tell what the data of the object is supposed to represent, such as a date or bank account or state of a simulated car wash; and the public member functions of the class along with the comments that tell how to use these public member functions. In a well-designed class which achieves our goal of encapsulation, the interface of the class should be all you need to know in order to use the class in your program.

The program we write to use the classes we define is referred to as the **client.**

The **implementation** of a class tells how the class interface is realized as C++ code. The implementation consists of the private members of the class and the definitions of both the public and private member functions. Although you need the implementation in order to run a program that uses the class, you should not need to know anything about the implementation in order to write the rest of a program that uses the class; that is, you should not need to know anything about the implementation in order to write the main function of the program and to write any nonmember functions or other classes used by the main function

To test a class for encapsulation (that is, if it properly separates the interface and the implementation) you can try changing the implementation of the class (that is, change the data representation and/or change the implementation of some member functions) without needing to change any (other) code for any program that uses the class definition.

## Constructors
When you define a class you can define a special kind of member function known as a **constructor.** A constructor is a member function that is automatically called when an object of that class is declared. A constructor is used to initialize the values of some or all member variables and to do any other sort of initialization that may be needed.

You define a constructor the same way that you define any other member function, except for two points:
1. A constructor must have the same name as the class. For example, if the class is named BankAccount, then any constructor for this class must be named BankAccount
2. A constructor definition cannot return a value. Moreover, no type, not even void, can be given at the start of the function declaration or in the function header.

Normally, you should make your constructors public member functions. The syntax for constructors is given below
```cpp
class MyClass{
    public:
        MyClass(int Parameter1Name, double Parameter2Name);
    private:
        int Variable1Name;
        double Variable2Name;
};

//The definition of our constructor initializes an object's member variables to the given arguments
MyClass::MyClass(int Parameter1Name, double Parameter2Name)
{
    Variable1Name = Parameter1Name;
    Variable2Name = Parameter2Name;
}
```

We can overload a constructor name just like we can overload any other member function name and define multiple constructors so that it can have no arguments, one argument, two arguments, etc.

The constructor that takes no arguments is called the **default constructor.**

Another syntax to define constructors is
```cpp
MyClass::MyClass(int Parameter1Name, double Parameter2Name)
                            : Variable1Name(Parameter1Name), Variable1Name(Parameter2Name)
{
    //constructor statements
}
```

The syntax for object declaration when you have constructors is
```cpp
MyClass ObjectOfClassName(Arguments_for_Constructor);
```

A constructor is called automatically whenever you declare an object of the class type, but it can also be called again after the object has been declared which allows us to conveniently set all the members of an object.

The syntax for **explicit constructor calls** is
```cpp
ObjectOfClassName = ConstructorName(Arguments_For_Constructor);
```

When we want to declare a variable of our class type and invoke the constructor with no arguments we cannot use the empty parentheses i.e ``MyClass ObjectOfClassName(); //This is WRONG!``
We may see this as a constructor invocation, but the compiler sees this as a declaration of a function name ``ObjectOfClassName`` that has no parameters and returns a value of type ``MyClass``. The proper way to declare a class variable and invoke the default constructor is ``MyClass ObjectOfClassName;``

Note that when we explicitly invoke a constructor with no arguments, we do include parentheses.

If you define a class and include absolutely no constructors of any kind, then a default constructor will be automatically created. If you include one or more constructors that each takes one or more arguments, but you do not include a default constructor in your class definition, then there is no default constructor and any declaration of a class variable that is invoked with no arguments is illegal.

Best practice is to always include a default constructor.

**Constructor delegation** allows one constructor to call another constructor. For example, we could modify the implementation of the default constructor so that it invokes the constructor with two parameters:
```cpp
MyClass::MyClass() : MyClass(Argument1, Argument2)
{}
```

## const Parameter Modifier

If you are using a call-by-reference parameter and your function does not change the value of the parameter, you can mark the parameter by placing the modifier ``const`` before the parameter type so that the compiler knows that the parameter should not be changed. This is called a **constant parameter** or **constant call-by-reference parameter.**

If you have a member function that should not change the value of a calling object, you can mark the function with the ``const`` modifier

The syntax for ``const`` is given below
```cpp
class Sample
{
public:
    Sample( );
    void input( );
    void output( ) const;
private:
    int stuff;
    double moreStuff;
};

int compare(const Sample& s1, const Sample& s2);
```

You should use the constmodifier whenever it is appropriate for a class parameter and whenever it is appropriate for a member function of the class. If you do not use const every time that it is appropriate for a class, then you should never use it for that class.

**Inline function definitions** give the complete definition of a member function within the definition of its class and are typically used for very short function definitions.

The code for an inline function declaration is inserted at each location where the function is invoked in order to save the overhead of a function invocation.

Inline functions have the disadvantage of mixing the interface and implementation of a class and so go against the principle of encapsulation. 

To define a nonmember function to be ``inline``, just place the keyword inline before the function declaration and function definition. Example:
```cpp
double getRate( ) const { return rate; }
int getCents( ) const { return accountCents; }
```

**Static variables** are variables that are shared by all objects of a class and they can be used for objects of a class to communicate with each other or coordinate their actions. Static variables are indicated by the qualifying keyword ``static`` at the start of their declaration.
```cpp
static int variable1;
static bool variable2;
```

If a function does not access the data of any object and yet you want the function to be a member of the class, you can make it a **static function.** Static functions can be invoked in the normal way, using a calling object of the class, but it is more common and clear to use the form:
```cpp
ObjectOfClassName::staticFunctionCall( ) // notice that keyword 'static' is not needed for function definition
```

Because a static function does not need a calling object, the definition of a static function cannot use anything that depends on a calling object.


