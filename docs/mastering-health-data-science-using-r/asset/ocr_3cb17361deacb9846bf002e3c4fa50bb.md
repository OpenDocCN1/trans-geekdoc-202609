# 3.2.4  Practice Question

Find the sum of each of the PROMIS measures across all patients using `apply()` and then using `colSums()`. Verify that these two methods return the same result, which is given in **Figure 3.2**.

![](bbox=[0.123, 0.191, 0.884, 0.211])

**Figure 3.2:** Summing Across Columns.

```
```r
# Insert your solution here:
```
```

# 3.2.5  Missing, Infinite, and NaN Values

As we have seen, this data contains some missing values, which are represented as `NA` in R. R treats these values as if they were unknown, which is why we have to add the `na.rm=TRUE` argument to functions like `sum()` and `max()`. In the following example, we can see that R figures out that 1 plus an unknown number is also unknown!

```
```r
NA+1
#> [1] NA
```
```

We can determine whether a value is missing using the function `is.na()`. This function returns `TRUE` if the value is NA, and `FALSE` otherwise. We can then sum up these values for a single column since each `TRUE` value corresponds to a value of 1, and each `FALSE` corresponds to a value of 0. We observe that there is a single NA value for the column `PATIENT_NUM`, which is the patient ID number.

```
```r
sum(is.na(pain$PATIENT_NUM))
#> [1] 1
```
```

If we want to calculate the sum of NA values for each column instead of just a single column, we can use the `apply()` function. Since we want to apply this computation over the columns, the second argument has value 2. Recall that the last argument is the function we want to call for each column. In this case, we want to apply the combination of the `sum()` and `is.na()` function. To do so, we have to specify this function ourselves. This is called an **anonymous function**, since it doesn’t have a name.