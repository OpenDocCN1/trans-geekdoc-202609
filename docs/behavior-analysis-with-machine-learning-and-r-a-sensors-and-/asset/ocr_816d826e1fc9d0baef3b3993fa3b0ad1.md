# CHAPTER 7. ENCODING BEHAVIORAL DATA

It is also possible to get the adjacency matrix with the method as_adjacency_matrix().

as_adjacency_matrix(g)

```
#> 6 x 6 sparse Matrix of class "dgCMatrix"
#>   1 11 12 3 4 8
#>   1  1    1   . .
#>  11     1 1 1 1 .
#>  12      1     .
#>   3  1  1   . 1
#>   4              . 1 .
#>   8              . . 1 1
```

In this matrix, there is a 1 if the edge is present and a . if there is no edge. this adjacency matrix does not contain information about the weights. We can print the adjacency matrix with weights by specifying attr = "weight".

```
as_adjacency_matrix(g, attr = "weight")

#> 6 x 6 sparse Matrix of class "dgCMatrix"
#>               1        11        12        3        4        8
#>   1  0.06066946 0.001046025      0.023012552      .
#>  11             0.030692431 0.002092050 0.017782427 0.001046025
#>  12             0.002092050               0.532426778      0.002092050
#>   3  0.02405858 0.017782427               0.002092050 0.002092050
#>   4                               0.002092050 0.002092050 0.001046025
#>   8                             0.001046025 0.001046025
```

The adjacency matrices can then be used to train a classifier. Since many classifiers expect one-dimensional vectors and not matrices, we can flatten the matrix. This is left as an exercise for the reader to try. Which representation produces better classification results (adjacency matrix or BoW)?

> The book “Practical graph mining with R” (Samatova et al., 2013) is a good source to learn more about graph analytics with R.