up::
tags:: #state/seedling

# Interview questions

### What is the size of an empty class
An empty class has a size of 1 byte to guarantee that it has a specific address in memory.

### How to calculate the size of a class
1. First calculate the size of all the non-static attributes. Remember to consider the padding between attributes to reach 4 bytes.
2. The size of a class also includes the size of its immediate base class.
3.  Each virtual function adds 4 bytes to the vtable of the class. If the base class has this function, then it is not added again.
4. If there is virtual inheritance, then it adds 4 bytes for a pointer to the base class.

### How do we declare a constant variable in a header file? 

### What is the diamond problem in inheritance?

### How is the memory of the program arranged?

### What is the vtable?

### What is a friend class?

### What is forward declaration?

### How does a virtual function work inside a compiler?

### What is a static variable? and function?

### What are smart pointers? Advantages and disadvantages?

### What differences does vectors and lists have? Which is better at what?

### What are the differences between a struct and a class?

### What is the difference between a pointer and a reference?

### What is a parameter pack?

### What does rvalue and lvalue mean?

### What are the benefits of templatization?
## References

---
Planted: 2023-03-15
Last tended: 2023-03-15