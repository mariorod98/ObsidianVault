up:: [[🖥️ C_C++]]
tags:: #state/seedling #on/cpp


# C++ virtual

The **virtual** keyword is used to define class methods that are expected to be redefined in derived classes. When you refer to a derived class object using a pointer or a reference to the base class, you can call a virtual function for that object and execute the derived class's version of the function.

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

b_pointer = &d1;                // the pointer points to the derived class (polymorphism)
result = b_pointer->my_func();

```

---
Planted: 2022-03-24
Last tended: 2022-03-24