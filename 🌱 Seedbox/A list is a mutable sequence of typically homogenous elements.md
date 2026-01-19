---
created: 2026-01-19
last updated: 2026-01-19
---

up:: [[🐍 Python]]
tags:: #state/seedling #on/python/data_structures 

# A list is a mutable sequence of typically homogenous elements
Lists are a mutable sequence, typically used to store collections of homogenous items. List items are **ordered**, **changeable** and **allow duplicate values**. Ordered, because they have a defined order that will not change (except if you use the `insert` method). Changeable, because you can add and remove elements as well as modify them, in contrast with the [[A tuple is an immutable sequence of elements|tuple]]. Allow duplicates, because the lists are indexed, and you access the elements through these unique indices.

```python

my_list = [3, 14, 53]
my_list.append(21) # [3, 14, 53, 21]
my_value = my_list[2] # 14
my_value_2 = my_list [1:2] # [14, 53]
```

You can create list using [[list comprehension]], a way of creating complex list with a compact syntax.


## References
[Built-in Types — Python 3.14.2 documentation](https://docs.python.org/3/library/stdtypes.html#typesseq-list)
[Python Lists](https://www.w3schools.com/python/python_lists.asp)

## Related notes
[[A tuple is an immutable sequence of elements]]