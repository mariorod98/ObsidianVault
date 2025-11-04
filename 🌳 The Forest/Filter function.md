---
created: 2025-11-04
last updated: 2025-11-04
---
up:: [[🐍 Python]]
tags:: #state/bud #on/python/builtin

# Filter function
The filter function is used to extract elements from an iterable object (like a list, a tuple or a set) that satisfy a given condition. It applies the given function to all the elements, one by one. If the function returns true, it add the element to a list that is then returned with all the filtered elements.

```python
list = [3.54, 12, 5.9, 7.3, 198.3]
filtered = filter(x => x > 10, list)
print(filtered) #prints 12, 198.
```

Notice that this function is the equivalent to the expression
```python
[item for item in iterable if function(item)]
```

## References
[Built-in Functions — Python 3.14.0 documentation](https://docs.python.org/3/library/functions.html#filter)

---
Planted: 2025-11-04
Last tended: 2025-11-04