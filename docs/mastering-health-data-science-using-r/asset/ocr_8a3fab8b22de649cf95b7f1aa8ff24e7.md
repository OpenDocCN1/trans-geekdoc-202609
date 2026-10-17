```
# change threshold - lower, should have three pairs
expect_equal(high_cor(test_df, 0.2)$cor,
           c(0.9011631, 0.31765407, 0.30748633),
           tolerance = 0.001)

# change threshold - higher, should be empty
expect_equal(high_cor(test_df, 0.95)$cor, vector("numeric"),
           tolerance = 0.001)

# single numeric column - should return an empty data frame
expect_equal(high_cor(test_df[,4:5])$cor, vector("numeric"))

# single row - should return an empty data frame
expect_equal(high_cor(test_df[1,])$cor, numeric())
```

# 18.4 Exercises

For each question, be sure to document your function(s) using roxygen style documentation.

+   1. Standardizing a variable means subtracting the mean and then dividing through by the standard deviation. Create a function called `standardize_me()` that takes a numeric vector as an argument, and returns the standardized version of the vector. Write at least three unit tests to check that the result is correct.

+   2. Suppose we have two binary vectors x and y each of length n. Let m1 be the number of indices where x or y has a 1 and m2 be the number of indices where both x and y equal 1. For example, if x <- c(1,1,0) and y <- c(0,1,0) then m1 = 2 and m2 = 1. The Jaccard distance is defined as 1-m2/m1 and measures the dissimilarity between two binary vectors. Write a function `jaccard_dist()` that takes in two binary vectors and returns the Jaccard distance between the two.

+   3. For this question we use a subset of the pain data from the HDSinRdata package. Recall, that this data contains binary variables representing where people experienced pain. Write a function that takes in a data frame with all binary columns and returns a matrix with the Jaccard distance between all observations. That is, if d is the returned matrix, then d[i,j] is the Jaccard distance between