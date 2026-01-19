---
created: 2025-11-07
last updated: 2026-01-19
---

up:: [[🐍 Python]]
tags:: #state/bud #on/python 

# You can specify an arbitrary number of arguments for functions
In python functions, you can specify an arbitrary number of arguments in two ways:
- By using `*`, you specify a variable number of [[There are positional and keyword arguments|positional arguments]]. This will be a tuple with all the arguments in order.
- By using `**`, you specify a variable number of [[There are positional and keyword arguments|keyword arguments]]. This will be a dictionary with the pairs name:value of the arguments.

```python
def sum_values(*values):
	result = 0
	for v in values:
		result += v
	return result
	
def 
```

## References

## Related notes