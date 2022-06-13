## Structures

Sometimes it is useful to have a collection of values of different types and to treat the collection as a single item. In C++, structures do exactly this. The ``struct`` keyword defines a structure type and/or a variable of a structure type. 

A **structure** type is a user-defined composite type. It is composed of fields or **members** that can have different types.

It is a convention that structure type names, the **structure tag,** starts with an uppercase letter.

Creating a structure is as follows
```cpp
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
//We define a struct type called Autombile. 
//Structs are usually defined globally (outside any function definitions).
struct Automobile
{
    int year;
    int doors;
    double horsePower;
    char model;
};

//In our functions, we can create variables of type Automobile to use.
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

