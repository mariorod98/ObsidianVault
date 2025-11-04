---
created: 2025-11-04
last updated: 2025-11-04
---

up:: [[🐍 Python]]
tags:: #state/bud #on/python/functools

# Reduce function
The **reduce function** (contained in [[functools]]) applies a function of two arguments cumulatively to the items of an [[iterable]], from left to right, to *reduce* the iterable to a single value.

The function has a third optional parameter to specify the initial value to use.

For example, if we apply a sum function to an iterable, it will add the first element with the second, then add the result with the third, and continue until the last one.

```python
from functools import reduce

def sum(x, y):
	return x + y
	
values = [1, 2, 3, 4, 5]
reduce(sum, values)

# is equivalent to
total = 0
for v in values:
	total = sum(total, v)
```

## References
[functools — Higher-order functions and operations on callable objects — Python 3.14.0 documentation](https://docs.python.org/3/library/functools.html)