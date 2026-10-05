# 8.4 Case study: Is yawning contagious?

first time, so we need to set the success argument to "yes" as follows to improve the transparency of the code:

```
mythbusters_yawn |>
specific(formula = yawn ~ group, success = "yes")
```

Response: yawn (factor)
Explanatory: group (factor)
# A tibble: 50 x 2
yawn group
<fct> <fct>
1 seed
2 control
3 seed
4 seed
5 seed
6 control
7 seed
8 control
9 control
10 seed
# i 40 more rows

# 2. generate replicates

Our next step is to perform bootstrap resampling with replacement like we did with the almonds in the activity in Section 8.2.1. We saw how it works with both a single variable in computing bootstrap means in Section 8.2.2, but we haven't yet worked with bootstrapping involving multiple variables.

In the infer package, bootstrapping with multiple variables means that each row is potentially resampled. Let's investigate this by focusing only on the first six rows of mythbusters_yawn:

```
first_six_rows <- head(mythbusters_yawn)
first_six_rows
```

```
# A tibble: 6 x 3
subj group yawn
<int> <chr>
1 1 seed yes
2 control yes
3 seed no
```