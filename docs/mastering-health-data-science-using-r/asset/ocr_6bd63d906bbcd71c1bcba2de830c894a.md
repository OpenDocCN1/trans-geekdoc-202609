```
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
```

This worked. Next we need to find the strong correlations. Now, we can use the correlation function to find the correlations. We then want to iterate through all pairs to check if the absolute value of the correlation is above our threshold. We use a loop for this. In our first attempt, we create a nested for loop where i is the index of one column and j is the index of the second column in the pair. We can see we must have some mistakes because we are getting pairs where i and j are equal to each other, and we are also getting zeros. Note how we are using print statements. This helps us to identify that we need to add parentheses for the first for loop, and we need to update j to start at i+1.

```
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
```

Let's try again. This time we create a variable n which is the number of columns.