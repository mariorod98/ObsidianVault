---
created: 2025-11-22
last updated: 2025-11-22
---

up:: [[🐍 Python]]
tags:: #state/seedling #on/python/library/pandas

# pandas DataFrame
A DataFrame is a rectangular table of data and contains an ordered, named collection of columns, each of which can be a different value type. It can be thought as a dictionary of [[pandas Series|Series]].

![[Pasted image 20251122121003.png]]

## Obtaining DataFrame infos
To see a summary of the DataFrame, use the method `infos`. This prints the name and type of de index and each column.
```python
print(df.info())

<class 'pandas.core.frame.DataFrame'>
RangeIndex: 7 entries, 0 to 6
Data columns (total 6 columns):
# Column Non-Null Count Dtype
-- ------ -------------- -----
0 name 7 non-null object
1 breed 7 non-null object
2 color 7 non-null object
3 height_cm 7 non-null int64
4 weight_kg 7 non-null int64
5 date_of_birth 7 non-null object
dtypes: int64(2), object(4)
memory usage: 464.0+ bytes
```

To know the size of the DataFrame, use `shape`.
```python
print(df.shape)

(7, 6)
```

To generate descriptive statistics for each column, use `describe`.
```python
print(df.describe())

height_cm weight_kg
count 7.000000 7.000000
mean 49.714286 27.428571
std 17.960274 22.292429
min 18.000000 2.000000
25% 44.500000 19.500000
50% 49.000000 23.000000
75% 57.500000 27.000000
max 77.000000 74.000000
```

To obtain the columns and values of the table as lists, use `values` and `columns`
```python
print(df.values)

array([['Bella', 'Labrador', 'Brown', 56, 24, '2013-07-01'],
['Charlie', 'Poodle', 'Black', 43, 24, '2016-09-16'],
['Lucy', 'Chow Chow', 'Brown', 46, 24, '2014-08-25'],
['Cooper', 'Schnauzer', 'Gray', 49, 17, '2011-12-11'],
['Max', 'Labrador', 'Black', 59, 29, '2017-01-20'],
['Stella', 'Chihuahua', 'Tan', 18, 2, '2015-04-20'],
['Bernie', 'St. Bernard', 'White', 77, 74, '2018-02-27']],
dtype=object)
```

```python
print(df.columns)

Index(['name', 'breed', 'color', 'height_cm', 'weight_kg', 'date_of_birth'],
dtype='object')
```

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