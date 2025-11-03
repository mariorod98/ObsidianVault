up:: [[🐍 Python]]
tags:: #state/seedling #on/python/library

# Pandas Dataframe

## Subsetting
You can create a subset of a dataset using the `[]` operators. These are very versatile and include multitude of ways to access the data. The subset returns a [[Pandas Series]] if it is only a column.

**Subsetting a single column**
``` python
dataframe["my_column"] #returns series object
```

**Subsetting multiple columns**
``` python
dataframe[["my_column1", "my_column2"]]
dataframe[["my_column"]] # returns a dataframe of 1 column

my_columns = ["my_column1", "my_column2"]
dataframe[my_columns]
```

**Conditional subsetting**
Returns only the rows that satisfies the condition. This will return all the columns, that you can then subset again.
``` python
age_values = dataframe["age"]
minors = dataframe[age_values < 18]

dataframe[dataframe["Department"] == "IT"] # returns all columns of dataframe
dataframe[dataframe["Department"] == "IT"]["Salary"] # returns the salary of people in IT

# if we want multiple conditions, we need to put them in parenthesis!
dataframe[(dataframe["age"] < 18) & (dataframe["Department"] == "IT")]
#or do them separately
is_minor = dataframe["age"] < 18
works_in_it = dataframe["Department"] == "IT"
dataframe[is_minor & works_in_it]
```

**Subsetting with method isin**
``` python
departments = ["IT", "Marketing", "Finance"]
dataframe[dataframe["Department"].isin(departments)]
```

## Sorting
The method `sort_values` sorts the dataframe by the columns indicated.

**Basic sorting (uses ascending)**
``` python
dataframe.sort_values("my_column")
```

**Sorting descending**
``` python
dataframe.sort_values("my_column", ascending=False)
```

**Sorting multiple columns (priority order left to right)**
``` python
dataframe.sort_values(["my_column1", "my_column2"])
dataframe.sort_values(["my_column1", "my_column2"], ascending=[False, True])
```

## Adding columns
```python
dataframe["height_m"] = dataframe.["height_cm"] / 100.0
```

## Summary statistics
You can have the `median()`, `mean()`, `mode()`, `min()`, `max()`, `var()`, `std()`, `sum()` and  `quantile()` of any numeric or `datatime` column.
```python
height_mean = dataframe["height"].mean()
```

You can also have your own specific function using `agg()`

```python
# A custom IQR function
def iqr(column):
    return column.quantile(0.75) - column.quantile(0.25)
    
dataframe["temperature"].agg(iqr)

# you can use multiple columns
dataframe[["temperature", "unemployment"]].agg(iqr)

# and add multiple functions to the aggregate
dataframe[["temperature", "unemployment"]].agg([iqr, "mean"])
```
## References

---
Planted: 2025-10-07
Last tended: 2025-11-03