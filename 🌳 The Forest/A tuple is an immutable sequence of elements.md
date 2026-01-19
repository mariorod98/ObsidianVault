---
created: 2026-01-19
last updated: 2026-01-19
---

up:: [[🐍 Python]]
tags:: #state/bud #on/python/data_structures

# A tuple is a sequence of immutable elements
A tuple consist of a **heterogeneous**, **immutable** sequence of elements. Heterogeneous, because the elements can be of any type and you can mix types in the same tuple. Immutable, because once a tuple is defined, it cannot be modified.

```python
my_tuple = (32, 3.14, 'banana')
empty_tuple = ()
one_element_tuple = (3.14,)
```

Once a tuple is created, its shape is constant and cannot be modified. You cannot add or subtract any element or modify one element for another. However, elements in the list are mutable, so you can still change the inner state of the element.

```python
my_list = [3, 4]
my_tuple = (32, 3.14, 'banana', my_list)
my_tuple[0] = 12 # invalid, changing a tuple, it is immutable
my_tuple[3].append(2) #valid, changing an element of the typle, it is mutable
```

The elements in a tuple are accessed via [[Sequence unpacking is a way of decomposing a tuple into multiple variables|sequence unpacking]] or [[indexing]].

## References
[5. Data Structures — Python 3.14.2 documentation](https://docs.python.org/3/tutorial/datastructures.html#tuples-and-sequences)

## Related notes
[[A list is a mutable sequence of typically homogenous elements]]