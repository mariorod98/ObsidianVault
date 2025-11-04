---
created: 2025-11-04
last updated: 2025-11-04
---

up:: [[🐍 Python]]
tags:: #state/bud #on/python/builtin 

# Map Function
The map functions returns an iterator that applies a *function* to every item of an [[iterable]]. It can receive many iterables, but then the function received has to have as many parameters as iterables, it will apply the function to the values at the same index of each iterable. With multiple iterables, the iterator stops when the shortest iterable is exhausted.

```python
def square(x):
	return x*x

values = [1, 2, 3, 4, 5]
mapped = map(square, values)
print(mapped) # prints [1, 4, 9, 16, 25]

def exponent(x, y)
	return x**y
	
mapped = map(exponent, values, values)
print(mapped) # prints [1, 4, 27, 256, 3125]
```

## References
[Built-in Functions — Python 3.14.0 documentation](https://docs.python.org/3/library/functions.html#map)