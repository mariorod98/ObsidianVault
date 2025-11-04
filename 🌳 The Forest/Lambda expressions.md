---
created: 2025-11-04
last updated: 2025-11-04
---

up:: [[🐍 Python]]
tags:: #state/bud #on/python

# Lambda functions
Lambda expressions are small anonymous functions created by using the `lambda` keyword. They can be used wherever function objects are required and ==they are restricted to a single expression==. Lambda expressions can reference variables from the containing scope.

```python
my_var = 13
my_other_var = 15
my_list = [1, 2, 3, 4, 5, 6]

filtered_list = filter(lambda x: x + my_var > my_other_var, my_list)

# it can also have multiple parameters
from functools import reduce
reduced_val = reduce(lambda x, y: x * y, my_list)
```

## References
[4. More Control Flow Tools — Python 3.14.0 documentation](https://docs.python.org/3/tutorial/controlflow.html#lambda-expressions)