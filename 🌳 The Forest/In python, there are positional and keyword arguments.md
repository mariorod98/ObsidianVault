---
created: 2025-11-07
last updated: 2025-11-07
---

up:: [[🐍 Python]]
tags:: #state/bud #on/python

# In python, there are positional and keyword arguments
When we call a function, we can specify the arguments in three ways:
- By specifying all its parameters sequentially as they are defined in the function header. In this case, we talk about **positional arguments**.
- By preceding each argument with the parameter name. In this case, we talk about **keyword arguments**. in this case, the order does not have to be respected.
- Using both types of arguments. However, ==you must specify first the positional arguments and then the keyword arguments==.

```python
from math import sqrt

def distance(x1, y1, x2, y2):
	return sqrt((x1 - x2)**2 + (y1 - y2)**2)

# positional arguments, order matters
distance(3.0, 4.5, 1.0, 5.6)

# keyword arguments, order doesn't matter
distance(x1=3.0, y1= 1.0, y2=5.6, x2=4.5)

# valid, x1 = 3.0, y1 = 4.5
distance(3.0, 4.5, x2 = 1.0, y2 = 5.6)

# invalid, once you use a keyword argument, all arguments after that must be keyword
distance(3.0, 4.5, x2 = 1.0, 5.6)

# invalid, parameter assigned value both with positional and keyword argument
distance(3.0, 1.0, 5.6 ,y1 = 1.0)
```

## References

## Related notes
[[In python, keyword parameters can have default values]]