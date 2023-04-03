up::
tags:: #state/seedling

# C++ static
The **static** keyword can be used along with function and variable declarations. The meaning of the keyword varies between variables and functions and whether it is declared inside or outside a class.

When a variable is declared as **static**, ==space for the variable is allocated for the lifetime of the program==.

## Use of the static keyword inside a class

### Static variables
As a static variable is only allocated once in memory, a static variable in a class is shared by all the objects of that class.

**The static variable must be initialized outside of the class scope.** Usually, it is done in the cpp file that contains the class definitions. However, if the variable is [[C++ const|const]], it can be defined in the class definition.

### Static function

When a function is declared as static, that function ==can be called without an instance of a class==. This function **cannot access non-static members/functions of the class**.

Static member functions cannot be [[C++ Virtual|virtual]], [[C++ const|const]] or [[C++ volatile|volatile]].

## Use of the static keyword outside a class
The **static** keyword outside a class refers to the [[Storage duration in C++|storage duration]] . A **static** storage duration means that the memory for the object is allocated when the program begins and deallocated when the program ends. **Only one instance of the object exists.**

Variables and functions declared **static** can only be linked in their [[C++ Translation Unit|translation unit]].

### Static variable in a function
If a static variable is declared in a function, ==only that function can access the variable==. However, **the memory (and value) of the variable is preserved between function calls**.

Static variables declared in functions are initialized during the first call of the function.

### Static variables in classes


### Static class object
As with other types, objects can also be declared as static. A static object has the scope of the entire execution of the program. The constructor is called at the beginning of the main function and the destructor is called at the end.

## Static functions

### Inside a class


### Outside of a class

When a function that is not in a class is declared as static, this means that that function will not be referred by any other [[translation unit]]

Cualquier funcio pública (no static) será tratada por el compilador mediante el prolog y el epilog, para garantizar que cualquier archivo puede llavmar a la funcion

## Static in a .c
Static in C means that the variable or method is private to the file. There can exist two global variables, structs, functions, etc with the same signature that are static.

## Static in a .h
Each .c that includes that header will have a private variable with that signature.

## References
[What is Static Member Function in C++? | Edureka](https://www.edureka.co/blog/what-is-static-member-function-in-cpp#:~:text=Static%20is%20a%20keyword%20in,or%20outside%20of%20a%20class.)
[static members - cppreference.com](https://en.cppreference.com/w/cpp/language/static)
[Storage class specifiers - cppreference.com](https://en.cppreference.com/w/cpp/language/storage_duration)

---
Planted: 2023-01-16
Last tended: 2023-04-04