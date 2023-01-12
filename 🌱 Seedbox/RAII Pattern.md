up::
tags:: #state/seedling #on/programming/patterns 

# RAII Pattern

*Resource Acquisition Is Initialization* (RAII) is a programming pattern that binds the life cycle of a resource that must be acquired before use to the lifetime of an object. When that object is created, the resource is initialized, when the object is destroyed, the resource is freed.

This pattern is used to ensure that resources are used only in a limited scope and that they are always initialized and freed in that scope.

Some resources that can fit to the RAII pattern are:
- Thread execution.
- Open socket.
- Open file.
- Locked mutex.
- Database connection.

## Formal definition
RAII can be summarized as follows:
- Encapsulate each resource into a class, where
	- The constructor acquires the resource (or throws an exception if that cannot be done).
	- The destructor releases the resource and never throws exception.
- Always use the resource via an instance of a RAII-class that either
	- Has automatic storage duration or temporary lifetime itself, or
	- Has lifetime that is bounded by the lifetime of an automatic or temporary object.

RAII guarantees that a resource is available to any function that may access the object

## Benefits


## Examples

## References
[RAII - cppreference.com](https://en.cppreference.com/w/cpp/language/raii)
[c++ - What is meant by Resource Acquisition is Initialization (RAII)? - Stack Overflow](https://stackoverflow.com/questions/2321511/what-is-meant-by-resource-acquisition-is-initialization-raii)

---
Planted: 2023-01-10
Last tended: 2023-01-12