---
created: 2026-03-07
last updated: 2026-03-07
---

up::
tags:: #state/seedling  #on/r

# A factor stores categorical variables

A factor is a data type in [[R]] that defines a categorical variable with a limited number of categories. There are two types of factors:
- **unordered factors** used for [[nominal categorical variables]].
- **ordered factors** used for [[ordinal categorical variables]].

Factor are created with the function `factor()`. This function can receive an array of values that will be stored in the factor. To create an ordered factor, set the parameter `order=TRUE` and specify the order of the levels with parameter `levels`.

```r
sex <- c("Male", "Female", "Female", "Female", "Male", "Non-binary")
sex_factor <- factor(sex)
```

==To know how many categories are there and their frequency, use the function `summary`.==

## Levels
The levels of a factor are all the unique values contained in a factor.
```r
levels(sex_factor) # "Male", "Female" and "Non-binary"
```

You can change the levels of a factor by assigning a new array of values. It has to be the exact same length. The order in which the elements appear in levels is the order in which they modification will take place.
```r
levels(sex_factor) <- c("M", "F", "NB")
```

If you want to change a specific level, you can use the function `recode_factor` from the library `dplyr` ([[recode_factor_link]]).

```r
# in this example, we imported sex data registered in many different ways, we recode the factor to have only Male/Female
sex_factor <- recode_factor(sex_factor, "F" = "Female", "Fem" = "Female", "female" = "Female", "M" = "Male", "male" = "Male")
```
## References

## Related notes