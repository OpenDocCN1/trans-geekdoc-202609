
```r
add_x_seq <- function(x){
  # Adds x to 1:10 and returns
  add_x <- function(y){
    return(y + x)
  }

  return(add_x(1:10))
}

add_x_seq(3)
#>  [1]  4  5  6  7  8  9 10 11 12 13
#add_x(3) # would return an error
```

If we want to use the created function, we can return it. In the updated example, we return an anonymous function. By doing so, we create a unique function for each x value.

```r
add_x <- function(x){
  # Returns a function to add x to any value
  return(function(y) y + x)
}

add2 <- add_x(2)
add2(1:10)
#>  [1]  3  4  5  6  7  8  9 10 11 12

add10 <- add_x(10)
add10(1:10)
#>  [1] 11 12 13 14 15 16 17 18 19 20
```

## 18.2 Documenting Functions

The functions we wrote had minimal comments or documentation. When creating functions, we should document them including any information about the format of the input and output. We do so using comments that precede the function and start with '#'. This style of function documentation is called roxygen. The following code chunk shows an example for our Euclidean distance function. You can see we provided information about the two arguments and the return value. The roxygen style is the style used for published R packages.

```r
#' Euclidean distance
#'
#' @description Calculates the Euclidean distance between two points
#'
#' @param pt1 numeric vector
#' @param pt2 numeric vector
#' @return the Euclidean distance from pt1 to pt2
euclidean_dist <- function(pt1, pt2){
  return((sum((pt1 - pt2)^2))^0.5)
}
```

Each comment should start with a pound sign and apostrophe. The first block of lines is the introduction, and the first line of the comment block is reserved for the title. This is the first information we want the user to know about the function and should be a single line. For all other information besides the title, we use certain tags.

- `@description` This tag should be placed first and is a place where you can briefly put more information about the function beyond the title. You can also add more details with the `@details` tag.
- `@param` This tag comes before each input argument’s description. For each argument, we want to include the name and type, but we might also include information on how that argument is used.
- `@return` This tag documents the returned object and specifies the type. If we are returning a list, then we might include information about each object in the list.

### 18.2.1 Practice Question

Write the documentation for the following coin flip function.

```r
#' Insert your solution here:
coin_flips <- function(prob, n = 10){
  results <- rbinom(n = n, size = 1, prob = prob)
  return(list(percent_heads = sum(results)/n, results = results))
}
```

## 18.3 Debugging and Testing

As we write more complex code and functions, we want to learn how to test our code. When it comes to testing code, a good mantra is “test early and test often”. So avoid writing too much code before running and checking that the results match what you expect. Here are some simple principles that are applicable to debugging in any setting.

- Start simple and build up in steps.
- Check your syntax by checking that all parentheses (), brackets [], and curly braces {} match where you expect.
- Check that object names are correct and you don’t have any accidental typos or that you are accidentally using the same name for different objects.
- Restart your R session and re-run all code.
- Check if you use the same object name for different objects.
- Localize your error by printing out the values of objects at each stage or use break points in R.
- Modify your code one piece at a time and check all test values again to avoid introducing new errors.

For example, suppose we want to write a function that finds any pairs of numeric columns with a Pearson correlation with absolute value above a certain threshold. We want our code to be structured so that it makes sense, is flexible to our needs, and avoids unnecessary work. To start building up this function, we need to first think about the inputs and outputs we want. This is called a _top-down approach_. Sketching out the overall steps your code needs to complete before writing any of them can help to improve your structure and avoid having to rewrite large pieces.

In this case, our input to this function is a data frame which could contain a mixture of numeric and categorical columns and a threshold correlation value with a default value of 0.6. We want to return a data frame with the pairs and their correlation. This gives us a template for our documentation.

```r
#' Find pairs of columns with strong correlation
#'
#' @description Finds all pairs of numeric columns with strong Pearson
#' correlation and returns the pairs in a data frame
#'
#' @param df data frame
#' @param threshold positive numeric threshold value to define a
#' strong correlation as one with absolute value above the threshold
#' @return data frame with one row for each pair of columns
#' with high correlation containing the names of the columns
#' and the corresponding correlation
high_cor <- function(df, threshold = 0.6){
  return()
}
```

Next, to start simple, we want to create some artificial data we can use to test our function. We use the `mvrnorm()` function from the **MASS** package (Venables and Ripley 2002) to control the correlation between our columns and add in a categorical column that should be ignored by our function.

```r
set.seed(4)
cor_mat <- matrix(c(1, 0.9, 0.4, 0,
                    0.9, 1, 0.3, 0,
                    0.4, 0.3, 1, 0,
                    0, 0, 0, 1.0), nrow = 4)
m <- round(MASS::mvrnorm(100, c(0,0,0,0), Sigma = cor_mat), 3)
test_df <- as.data.frame(m)
test_df$V5 <- sample(c("A", "B", "C"), 100, replace = TRUE)
high_cor(test_df)
#> NULL
```

We can use the `cor()` function to find the Pearson correlation.

```r
cor(test_df[,-5])
#>         V1      V2      V3      V4
#> V1  1.0000  0.9006  0.324  -0.0797
#> V2  0.9006  1.0000  0.291  -0.0702
#> V3  0.3241  0.2912  1.000  -0.2306
#> V4 -0.0797 -0.0702 -0.231  1.0000
```

Great, now let’s roughly sketch out the steps we need to complete.

- 1. Subset the data to only numeric columns.
- 2. Find the correlation of all pairs of columns.
- 3. Check if a pair has a strong correlation.
- 4. If so, add it to our results.

Let’s start with step 1. Before putting code into our function, we are going to test our steps on our example data. To do so, we use the `select_if()` function from the **dplyr** package.

```r
df_numeric <- select_if(test_df, is.numeric)
head(df_numeric)
#>
#>   V1    V2    V3    V4
#> 1 -0.656 0.417 1.188 0.685
#> 2  0.117 -0.336 -1.611 -0.115
#> 3  1.229  0.617  0.241 -0.356
#> 4  0.478  0.121  1.176 -0.106
#> 5  1.546  1.914  0.366  0.045
#> 6  0.416  0.110  1.630 -1.726
```

This worked. Next we need to find the strong correlations. Now, we can use the correlation function to find the correlations. We then want to iterate through all pairs to check if the absolute value of the correlation is above our threshold. We use a loop for this. In our first attempt, we create a nested for loop where i is the index of one column and j is the index of the second column in the pair. We can see we must have some mistakes because we are getting pairs where i and j are equal to each other, and we are also getting zeros. Note how we are using print statements. This helps us to identify that we need to add parentheses for the first for loop, and we need to update j to start at i+1.

```r
cor_mat <- cor(df_numeric)
for (i in 1:nrow(cor_mat) - 1){
for (j in (i:nrow(cor_mat))){
print(paste(i, j)))
}
}
#> [1] "0 0"
#> [1] "0 1"
#> [1] "0 2"
#> [1] "0 3"
#> [1] "0 4"
#> [1] "1 1"
#> [1] "1 2"
#> [1] "1 3"
#> [1] "1 4"
#> [1] "2 2"
#> [1] "2 3"
#> [1] "2 4"
#> [1] "3 3"
#> [1] "3 4"
```

Let's try again. This time we create a variable n which is the number of columns.
