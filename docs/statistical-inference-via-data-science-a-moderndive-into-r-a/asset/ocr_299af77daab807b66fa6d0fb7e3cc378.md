# 288 Estimation, Confidence Intervals, and Bootstrapping

The variables are:

+   * subj: The participant ID with values 1 through 50.
* group: A binary treatment variable indicating whether the participant was exposed to yawning. "seed" indicates the participant was exposed to yawning while "control" indicates the participant was not.
* yawn: A binary response variable indicating whether the participant ultimately yawned.

Recall that you learned about treatment and response variables in Subsection 5.3.1 in our discussion on confounding variables.

Let’s use some wrangling to calculate counts of the four possible outcomes:

```
mythbusters_yawn |>
group_by(group, yawn) |
summarize(count = n), .groups = "keep")

# tibble: 4 x 3
# Groups: group, yawn [4]
group yawn count
<chr> <chr> <int>
1 control no 12
2 control yes 4
3 seed no 24
4 seed yes 10
```

Let’s first focus on the "control" group participants who were not exposed to yawning. 12 such participants did not yawn, while 4 such participants did. So out of the 16 people who were not exposed to yawning, 4/16 = 0.25 = 25% did yawn.

Let’s now focus on the "seed" group participants who were exposed to yawning where 24 such participants did not yawn, while 10 such participants did yawn. So out of the 34 people who were exposed to yawning, 10/34 = 0.294 = 29.4% did yawn. Comparing these two percentages, the participants who were exposed to yawning yawned 29.4% - 25% more than those who were not.

# 8.4.2 Sampling scenario

Let’s review the terminology and notation related to sampling we studied in Subsection 7.2.1. In Chapter 7, our study population was the bowl of N = 2400 balls. Our population parameter of interest was the population proportion of balls that were red, denoted mathematically by p. In order to estimate p, we extracted a