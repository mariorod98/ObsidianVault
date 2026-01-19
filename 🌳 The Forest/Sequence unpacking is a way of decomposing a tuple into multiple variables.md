---
created: 2026-01-19
last updated: 2026-01-19
---

up:: [[A tuple is an immutable sequence of elements]]
tags:: #state/forest 

# Sequence unpacking
Sequence unpacking is a way of decomposing a [[A tuple is an immutable sequence of elements|tuple]] into multiple variables. 

```python
my_tuple = (32, 'banana', 7.65)
x, y, z = my_tuple
```

Sequence unpacking works for any sequence on the right-hand side. It requires that there are as many variables on the left side of the equals sign as there are elements in the sequence.

When there are elements that we don't care to unpack, it is common practice to unpack them into a variable named `_`.

```python
my_tuple = (32, 'banana', 7.65)
x, _, z = my_tuple
```

Sequence unpacking is used when unpacking the return of a function with multiple elements into different variables
```python
def return_neighbours(n : int):
	return n -1, n + 1
	
prev, post = return_neighbours(33)
```

## References
[5. Data Structures — Python 3.14.2 documentation](https://docs.python.org/3/tutorial/datastructures.html#tuples-and-sequences)

## Related notes