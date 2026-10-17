```
#> # X131 <dbl>, X132 <dbl>, X133 <dbl>, X134 <dbl>, X135 <dbl>,
#> # X136 <dbl>, X201 <dbl>, X202 <dbl>, X203 <dbl>, X204 <dbl>,
#> # X205 <dbl>, X206 <dbl>, X207 <dbl>, X208 <dbl>, X209 <dbl>, ...
```

I now compute the row sums and column sums on this subset of data. The row sum for each patient is the total number of body parts in which they experience pain, whereas the column sum for each pain region is the total number of patients who experience pain in that area. The following histogram shows that most people select a low number of total regions.

```
hist(rowSums(pain_body_map))
```

![](bbox=[0.105, 0.382, 0.885, 0.642])

We can also see that some body parts are more often selected than others. We create a vector called perc_patients by finding the number of patients who selected each region divided by the total number of patients. The histogram shows that some body regions are selected by over 50% of patients!

```
perc_patients <- colSums(pain_body_map, na.rm=TRUE) /
nrow(pain_body_map)
hist(perc_patients)
```