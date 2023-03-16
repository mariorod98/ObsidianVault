up::
tags:: #state/seedling

# Interview questions

## Design, structures, algorithms
### What is the diamond problem in inheritance?

### What are smart pointers? Advantages and disadvantages?

### What differences does vectors and lists have? Which is better at what?

## C++

### What is the size of an empty class
An empty class has a size of 1 byte to guarantee that it has a specific address in memory.

### How to calculate the size of a class
1. First calculate the size of all the non-static attributes. Remember to consider the padding between attributes to reach 4 bytes.
2. The size of a class also includes the size of its immediate base class.
3.  Each virtual function adds 4 bytes to the vtable of the class. If the base class has this function, then it is not added again.
4. If there is virtual inheritance, then it adds 4 bytes for a pointer to the base class.

### How do we declare a constant variable in a header file? 
Before C++17, we had to declare the variable `static` in the header file and then initialize it in a cpp file.

Since C++17, we can declare and initialize a constant in a header file with the keyword `inline` to ensure that the constant is created only once in one file. Then, the linker is the responsible to link that constant in the rest of the files that use it.

### How is the memory of the program arranged?

### What is the vtable?

### What is a friend class?

### What is forward declaration?

### How does a virtual function work inside a compiler?

### What is a static variable? and function?

### What are the differences between a struct and a class?

### What is the difference between a pointer and a reference?

### What is a parameter pack?

### What does rvalue and lvalue mean?

### What are the benefits of templatization?

## Unreal
### What is the EQS and what is it used for?

## References

---
Planted: 2023-03-15
Last tended: 2023-03-15