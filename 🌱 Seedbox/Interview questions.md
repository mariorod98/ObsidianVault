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

## References

---
Planted: 2023-03-15
Last tended: 2023-03-15