## Inheritance

### Inherited Members
A **derived class** automatically has all the member variables and all the ordinary member functions of the **base class.** (there are some specialized member functions, such as constructors, that are not automatically inherited.) These members from the base class are said to be inherited. These inherited member functions and inherited member variables are, with one exception, not mentioned in the definition of the derived class but are automatically members of the derived class. As explained in the text, you do mention an inherited member function in the definition of the derived class if you want to change the definition of the inherited member function

### Parent and Child Classes
When discussing derived classes, it is common to use terminology derived from family relationships. A base class is often called a parent class. A derived class is then called a child class. This makes the language of inheritance very smooth. For example, we can say that a child class inherits member variables and member functions from its parent class. This analogy is often carried one step further. A class that is a parent of a parent of a parent of another class (or some other number of “parent of” iterations) is often called an ancestor class. If class A is an ancestor of class B, then class B is often called a descendant of class A.

### Proper Use of Derived Classes
A derived class must possess an is a relationship with its base class. An Employee is a Person. A Truck is an Automobile. A PhoneWX is a Phone. However, a UserInterfaceForEmployee is NOT an Employee, and an EnginePart is NOT an Automobile. Making one class a sub-class of another just because, in your own mind, you can program something more easily is wrong headed.

### Fundamental Law of Base/Derived Pointers
A base class pointer can point to a derived class object without being cast (coerced).  A derived class pointer can only point to a base class object if a type cast is used.
```cpp
Phone *phPtr, myPhone;
PhoneWX *pwxPtr, myPwx;

phPtr = &myPwx;  // ok
phPtr = pwxPtr;  // ok
pwxPtr = &myPhone;  // compiler error
pwxPtr = phPtr;  // compiler error
pwxPtr = (PhoneWX *)phPtr;  // ok
```

### An Object of a Derived Class Has More Than One Type
In everyday experience, an hourly employee is an employee. In C++ the same sort of thing holds. Since HourlyEmployee is a derived class of the class Employee, every object of the class HourlyEmployee can be used anyplace an object of the class Employee can be used. In particular, you can use an argument of type HourlyEmployee when a function requires an argument of type Employee. You can assign an object of the class HourlyEmployee to a variable of type Employee. (But be warned: you cannot assign a plain old Employee object to a variable of type HourlyEmployee. After all, an Employeeis not necessarily an HourlyEmployee.) Of course, the same remarks apply to any base class and its derived class. You can use an object of a derived class anyplace that an object of its base class is allowed. More generally, an object of a class type can be used any place that an object of any of its ancestor classes can be used. If class Child is derived from class Ancestor and class Grandchild is derived from class Child, then an object of class Grandchild can be used any place an object of class Child can be used, and the object of class Grandchild can also be used anyplace that an object of class Ancestor can be used.

### Constructors in Derived Classes
A derived class does not inherit the constructors of its base class. However, when defining a constructor for the derived class, you can and should include a call to a constructor of the base class (within the initialization section of the constructor definition). If you do not include a call to a constructor of the base class, then the default (zero-argument) constructor of the base class will automatically be called when the derived class constructor is called.

### Protected Members
If you use the qualifier **protected** (rather than private or public) before a member variable of a class, then for any class or function other than a derived class the effect is the same as if the member variable were labeled private. However, in the definition of a member function of a derived class, the variable can be accessed by name. Similarly, if you use the qualifier protected before a member function of a class, then for any class or function other than a derived class, the effect is the same as if the member variable were labeled private. However, in the definition of a member function of a derived class, the protected function can be used. Protected members are inherited in the derived class as if they were marked protected in the derived class. In other words, if a member is marked as protected in a base class, then it can be accessed by name in the definitions of all descendant classes, not just in those classes directly derived from the base class.

### Redefining an Inherited Function
A derived class inherits all the member functions (and member variables) that belong to the base class. However, if a derived class requires a different implementation for an inherited member function, the function may be redefined in the derived class. When a member function is redefined, you must list its declaration in the definition of the derived class, even though the declaration is the same as in the base class. If you do not wish to redefine a member function that is inherited from the base class, do not list it in the definition of the derived class.

### Signature
A function’s **signature** is the function’s name with the sequence of types in the parameter list, not including the const keyword and the ampersand, &;. When you overload a function name, the two definitions of the function name must have different signatures using this definition of signature. (Some authorities include the const and/or ampersand as part of the signature, but we wanted a definition that works for explaining overloading.) A function that has the same name in a derived class as in the base class but has a different signature is overloaded, not redefined.

