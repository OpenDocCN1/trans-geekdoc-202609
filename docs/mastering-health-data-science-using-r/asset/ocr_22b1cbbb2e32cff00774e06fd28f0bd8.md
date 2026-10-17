```
```r
TRUE + FALSE + TRUE
#> [1] 2
```
```

To create all of these objects, we used the assignment operator <-, which we discussed in Chapter 1. You may see code elsewhere that uses an = instead. While = can also be used for assignment, it is more standard practice to use <-.

# ## 2.2 Vectors

In the previous examples, we created objects with a single value. R actually uses a vector of length 1 to store this information. **Vectors** are one-dimensional data structures that can store multiple data values of the same type (e.g., character, Boolean, or numeric). See Figure 2.2.

![](bbox=[0.27, 0.44, 0.728, 0.57])

**Figure 2.2:** Vector Examples.

We can confirm this by using the `is.vector()` function, which returns whether or not the inputted argument is a vector.

```
```r
is.vector(ex_bool)
#> [1] TRUE
```
```

One way to create a vector with multiple values is to use the combine function `c()`. In the following code, we create two vectors: one with the days of the week and one with the amount of rain on each day. The first vector has all character values, and the second one has all numeric values.

```
```r
days <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday")
rain <- c(5, 0.1, 0, 0, 0.4)
```
```