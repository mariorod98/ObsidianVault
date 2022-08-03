up:: [[🖥️ C_C++]]
tags:: #state/seedling #on/cpp


# C++ virtual

==The **virtual** keyword is used to define class methods that are expected to be redefined in derived classes==. When you refer to a derived class object using a pointer or a reference to the base class, you can call a virtual function for that object and execute the derived class's version of the function.

Virtual functions ensure that the correct function is called for an object, regardless of the type of reference (or pointer) used for the call. When a virtual function is called, the resolving of which function to execute is done at runtime ([[Polymorphism|Runtime polymorphism]]). 

```c++
class Base {
	virtual int my_func() {
		return 3;
	}
}

class Derived : public Base {
	int my_func() {
		return 4;
	}
}

...

int result;
Base b1 = new Base();
Derived d1 = new Derived();

Base* b_pointer = &b1;          // the pointer points to the base class
result = b_pointer->my_func();  // result = 3

b_pointer = &d1;                // the pointer points to the derived class
result = b_pointer->my_func();  // result = 4

```

## Rules for virtual functions

1. Virtual functions cannot be static.
2. A virtual function can be a [[friend function]] of another class.
3. Virtual functions should be accessed using pointer or reference of base class type to achieve [[runtime polymorphism]].
4. The prototype of virtual functions should be the same in the base as well as derived class.
5. It is not mandatory for the derived class to override a virtual function. In that case, the base class version of the function is used.
6. A class may have virtual destructor, but it cannot have virtual constructor.

## Limitations
-  ==The call of a virtual function is slightly slower== due to the runtime mechanism and it makes it more difficult for the compiler to optimize because it doesn't know exactly which function is going to be called at compile time.
- In a complex system, virtual functions can make it a little more difficult to figure out where a function is being called from, making it more difficult to debug.

## References
[Virtual Function in C++ - GeeksforGeeks](https://www.geeksforgeeks.org/virtual-function-cpp/)
[Virtual Functions | Microsoft Docs](https://docs.microsoft.com/en-us/cpp/cpp/virtual-functions?view=msvc-170)


---
Planted: 2022-03-24
Last tended: 2022-08-03