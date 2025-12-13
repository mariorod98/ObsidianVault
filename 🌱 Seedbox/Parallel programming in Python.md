---
created: 2025-12-13
last updated: 2025-12-13
---

up:: [[🐍 Python]]
tags:: #state/seedling #on/python 

# Parallel programming in Python
To use multiple processes in Python, we use the module `multiprocessing`. The most important feature of this module is the `Process` class. Parallel programming in python consists on spawning multiple `Process` objects that will execute in parallel.

## The Process class
This class represents the flow of execution of an individual process. The main program can create different `Process` objects and specify to each one what function and which parameters to use.

The process class has equivalents of all the methods of the [[Multithreading in python#The Thread class|Thread]] class.
### Creating a Process
To create a process we specify the function to execute with the parameter `target` and the arguments of the function with the parameter `args`.
```python
def my_func(n, m)
	return n + m

a = 3
b = 12
p = Process(target=my_func, args=(a, b,))
```
## References
[multiprocessing — Process-based parallelism — Python 3.14.2 documentation](https://docs.python.org/3/library/multiprocessing.html)

## Related notes
[[Multithreading in python]]