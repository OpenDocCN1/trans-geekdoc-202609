Now, divide each Euclidean distance by this simulated maximum to get our distances inside a [0,1] range. We'll call these normalized Euclidean distances.

```
toy_max_euc <- get_maxeuc(toy_dtm)
(dist(toy_dtm, method = "euclidean") / toy_max_euc) |> as.matrix()
```

1 2 3
0.0000000 0.3464102 0.4242641
0.3464102 0.0000000 0.4242641
0.4242641 0.4242641 0.0000000

That makes Euclidean distances more interpretable! As we'll see, this normalization does not overcome the effect of word count differences. Let's repeat our previous test. This time we'll subtract each normalized Euclidean distance from 1 so we have normalized Euclidean similarities. The two metrics now run the same direction (larger scores indicate more similarity for both).

```
# Normalized Euclidean similarity for the original DTM
max1 <- get_maxeuc(toy_dtm)
1 - as.matrix(dist(toy_dtm, method = "euclidean") / max1)
# Normalized Euclidean similarity for the new DTM
max2 <- get_maxeuc(toy_dtm_2)
1 - as.matrix(dist(toy_dtm_2, method = "euclidean") / max2)
```

# Original DTM

1 2 3
1.0000000 0.6535898 0.5757359
0.6535898 1.0000000 0.5757359
0.5757359 0.5757359 1.0000000

# New DTM

1 2 3
1.0000000 0.6464466 0.5949537
0.6464466 1.0000000 0.7348350
0.5949537 0.7348350 1.0000000

The cosine and Euclidean similarities are more comparable now. While the Euclidean similarities don't seem to move that much, recall the cosines didn't change at all.

Let's return to our Annual Review of Sociology example. Using cosine, which article abstracts are the most similar to the one for Rivera's article?

```
dtm_cos <- sim2(dtm_sim, method = "cosine")
dtm_cos[, "Employer Decision Making"] |>
sort(decreasing = TRUE) |>
head(5) |>
names()
```

+   [1] "Employer Decision Making"
+   [2] "Relational Work in the Economy"
+   [3] "Violence in Latin America..."
+   [4] "Multiracial Categorization, Identity..."
+   [5] "The Social Consequences of Disasters..."