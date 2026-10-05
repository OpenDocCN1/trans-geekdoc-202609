# 8 Estimation, Confidence Intervals, and Bootstrapping

**Step 3:** Put the almond back into the bag! In other words, replace it as seen in Figure 8.11.

![](bbox=[0.303, 0.126, 0.696, 0.401])

**FIGURE 8.11:** Step 3: Replacing almond.

**Step 4:** Repeat Steps 2 and 3 a total of 99 more times, resulting in 100 weights.

These steps describe *resampling with replacement*, and the resulting sample is called a *bootstrap sample*. This procedure results in some almonds chosen more than once and others not being chosen at all. Resampling with replacement induces *sampling variation*, every bootstrap sample can be different than any other.

This activity can be performed manually following the steps described above. We can also take advantage of the R code we have introduced in Chapter 7 and do this virtually. The data frame `almonds_sample_100` contains the random sample of almonds taken from the population. We show selected rows from this sample.

```
almonds_sample_100 <- almonds_sample_100 |>
ngroup() |>
select(-replicate)
almonds_sample_100
```

```
# A tibble: 100 x 2
ID weight
<int> <dbl>
1 166 4.2
2 1215 4.2
3 1899 3.9
4 1912 3.8
```