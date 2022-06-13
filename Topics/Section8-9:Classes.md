## Structures

Sometimes it is useful to have a collection of values of different types and to treat the collection as a single item. In C++, structures do exactly this.

A **structure** type is a user-defined composite type. Analogous to predefined types we are already familiar with such as ``int``, ``double``, and ``char``, we create variables of this type and store values in the variables of specified type. In the case of structures, its values are variables, all of which can be their own type, even other structures! The structure's values are variables called **members** and they will also hold their own values.

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
A **class** is a type that is similar to a structure type, but a class type normally has member functions as well as member variables. A class is a type just like the types int and double. You can have variables of a class type, you can have parameters of a class type, a function can return a value of a class type, and more generally, you can use a class type like any other type.

Classes are perhaps the single most significant feature that separates the C++ language from the C language.

The value of a variable of a class type is called an **object** (therefore, when speaking loosely, a variable of a class type is also often called an object). An object has both data members and function members.

A **member function** is defined similar to any other function except that the Class_Name and the **scope resolution operator**, ::, are given in the function heading.
```cpp
Returned_Type Class_Name::Function_Name(Parameter_List)
{
    Function_Body_Statements
}
```

### Encapsulation
A **data type** consists of a collection of values together with a set of basic operations defined on these values. For example, the data type ``int`` has certain specified values, such as 0, 1, -1, 2, and so forth, but the operations on these values (+, -, \*, /, %, etc.)are also just as important.

A data type is called an **abstract data type** (abbreviated **ADT**) if the programmers who use the type do not have access to the details of how the values and operations are implemented. 
