---
created: 2025-11-22
last updated: 2025-11-22
---

up:: [[pandas]]
tags:: #state/seedling #on/python/library/pandas

# pandas Series
A Series is a one-dimensional array-like object that contains a sequence of values **of the same type** (like [[numpy arrays]]). These values are associated to an *index*.

Whenever you slice a [[pandas Dataframe|Dataframe]] to one column, you create a Series.
## Operation
### Convert from and to a dict
```python
# key will be index, kalue will be value
data = {"Ohio": 35000, "Texas": 71000, "Oregon": 16000, "Utah": 5000}
my_series = pd.Series(data)
my_dict = my_series.to_dict()
```

### Access an element of the Series
```python
# You can access by the index
data = {"Ohio": 35000, "Texas": 71000, "Oregon": 16000, "Utah": 5000}
my_series = pd.Series(data)

my_value = my_series["Ohio"] # value = 35000
```
## References

## Related notes