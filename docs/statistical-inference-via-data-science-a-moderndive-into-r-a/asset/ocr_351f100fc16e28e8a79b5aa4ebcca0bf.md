# 7.5 The sampling distribution in other scenarios

and summarize functions to produce the random samples and the necessary portions, respectively. A total of 1000 random samples and sample proportions are acquired from each bowl with the appropriate sample sizes, 50 and 60, respectively. Moreover, the inner join function introduced in Section 3.7 is used to merge the sample proportions into a single data frame and the difference in these sample proportions is calculated for each replication.

```
virtual_prop_red <- bowl |
rep_slice_sample(n = 50
```

The results are stored in the data frame prop_joined. The variable prop_diff represents the difference in sample proportions. We present here the first 10 values of this data frame:

```
prop_joined
```

```
# A tibble: 1,000 x 4
replicate prop_red prop_almond prop_diff
<int> <dbl> <dbl> <dbl>
1 1 0.24 0.45 -0.21
2 2 0.46 0.5 -0.0400
3 3 0.38 0.35 0.0300
4 4 0.36 0.433 -0.0733
5 5 0.38 0.367 0.0133
6 6 0.3 0.317 -0.0167
7 7 0.42 0.383 0.0367
8 8 0.42 0.483 -0.0633
9 9 0.32 0.5 -0.18
10 10 0.48 0.433 0.0467
# i 990 more rows
```

As we did before, we build a histogram for these 1000 differences in Figure 7.27.

```
ggplot(prop_joined, aes(x = prop_diff)) +
geom_histogram(binwidth = 0.04, boundary = 0, color = "white") +
```