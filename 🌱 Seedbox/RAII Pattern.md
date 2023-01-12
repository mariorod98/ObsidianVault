up::
tags:: #state/seedling #on/cpp 

# RAII Pattern

*Resource Acquisition Is Initialization* (RAII) is a C++ technique that limits the creation and initialization of an object to be done in the same instant.

RAII can be summarized as follows:
- Encapsulate each resource into a class, where
	- The constructor acquires the resource (or throws an exception if that cannot be done).
	- The destructor releases the resource and never throws exception.
- Always use the resource via an instance of a RAII-class that either
	- Has automatic storage duration or temporary lifetime itself, or
	- Has lifetime that is bounded by the lifetime of an automatic or temporary object.

RAII guarantees that a resource is available to any function that may access the object
## References
[RAII - cppreference.com](https://en.cppreference.com/w/cpp/language/raii)

---
Planted: 2023-01-10
Last tended: 2023-01-10