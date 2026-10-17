# # 18

## Functions

Functions are an important part of creating reproducible research and clean code. So far we have been using many useful functions from base R and available packages by learning how to specify the inputs and use the output. We now shift to writing our own functions. To start, we need to understand the arguments and return values of functions as well as the scope of objects used or created within functions. We also talk about how to document, test, and debug your functions so that we can ensure they are correct and easy to use. We use the **testthat** package to create simple tests for our functions.

```
```r
library(testthat)
library(tidyverse)
```
```

One type of function we have already written is an *anonymous function*. These are functions that are not saved or given a name. These functions typically exist if we want to input a function argument to another function but we don’t want to save that function for future use. For example, in the following code, we use the `apply()` function on a data frame to find the proportion of observations that are NA for each column. Note that since the function is so short, it is easy enough to define within the `apply()` function call by just including the code for what is returned. For functions with more than one line, you would not want to use an anonymous function and would need to define the function.

```
```r
df <- data.frame(x1 = c(NA, 1, 1, 0),
                 x2 = c(0, 1, 0, 0),
                 x3 = c(0, 0, NA, NA))
apply(df, 2, function(x) sum(is.na(x)) / length(x))
#>    x1   x2   x3
#> 0.25 0.00 0.50
```
```