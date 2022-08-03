## Polymorphism

### Virtual Function
A virtual function is indicated by including the modifier virtual in the member function declaration (which is given in the definition of the class). If a function is virtual and a new definition of the function is given in a derived class, then for any object of the derived class, that object will always use the definition of the virtual function that was given in the derived class, even if the virtual function is used indirectly by being invoked in the definition of an inherited function. This method of deciding which definition of a virtual function to use is known as late binding.

### Polymorphism
Polymorphism refers to the ability to associate many meanings to one function name by means of the late-binding mechanism. Thus, polymorphism, late binding, and virtual functions are really all the same topic.

### Overriding
When a virtual function definition is changed in a derived class, programmers often say the function definition is overridden. In the C++ literature, a distinction is usually made between the terms redefined and overridden. Both terms refer to changing the definition of the function in a derived class. If the function is a virtual function, this act is called overriding. If the function is not a virtual function, it is called redefining. This may seem like a silly distinction to you the programmer, since you do the same thing in both cases, but the two cases are treated differently by the compiler.

