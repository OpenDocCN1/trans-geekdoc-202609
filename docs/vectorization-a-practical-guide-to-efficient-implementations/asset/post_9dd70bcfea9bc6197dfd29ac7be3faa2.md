
github.com/tensorflow/transform/blob/a6cca798e550c4eb7ffca90ad76288-e28fbae88/tensorflow_transform/mappers.py#L213-L239, 2023.

Jim Pivarski, Ianna Osborne, Ioana Ifrim, Henry Schreiner, Angus Hollands, Anish Biswas, Pratyush Das, Roy Choudhury Santam, Nicholas Smith, and Manasvi Goyal. Awkward Array, October 2018.

## Groupby, Apply, and Aggregate

Consider the following tabular dataset (Table 9.1):

Table 9.1 Example user-movie viewing hours dataset.

| User | Movie | Viewing Hours |
|---|---|---|
| 1 | 3 | 0.6 |
| 3 | 2 | 1.3 |
| 2 | 3 | 0.6 |
| 1 | 2 | 0.7 |
| 2 | 1 | 0.1 |
| 3 | 3 | 0.5 |
| 1 | 1 | 0.9 |

We can ask several questions about the behaviors of the users and the items from this dataset:

- 1. How many viewing hours each user has on an average?
- 2. How many movies does each user watch on an average?
- 3. How many hours does each user spend on each movie?

To answer these questions, we first need to group the feature values from the same users or items together and then compute summary statistics on the features within the groups. For instance, for the question of how many viewing hours each user has on average, we need to first identify how many total viewing hours user 1 has, then user 2 has, then user 3 has, ... etc. In Pandas, this is often done by using the `.groupby(...) .agg()` pattern applied on a `pandas.DataFrame`. We then can take the average across all the users to obtain our answer. The feature we use to identify the group is called the group(by) key. The feature we used to compute summary statistics is called the group value. In this particular example, the groupby key is user, and the group value feature is the viewing hours feature, where we need to add all the values together within the same user.

### 9.1 Pandas Groupwise Operations

Let us attempt to answer those three questions we posted above using Pandas

```
import pandas as pd

df = pd.DataFrame(
    {
        "user": [1, 3, 2, 1, 2, 3, 1],
        "movie": [3, 2, 3, 2, 1, 3, 1],
        "viewing hours": [0.6, 1.3, 0.6, 0.7, 0.1, 0.5, 0.9],
    }
)

# Question 1: How many viewing hours each user has on average?
# Compute total viewing hours of each user
df_total = df.groupby(by="user", as_index=False).sum()
# user movie viewing hours
# 0 1 6 2.2
# 1 2 4 0.7
# 2 3 5 1.8

# Compute average
df_total["viewing hours"].mean()
# 1.567

# Question 2: How many items does each user watch on average?
# Compute total number of contents each user watch
df_watch = df.groupby(by="user", as_index=False)["movie"].nunique()
# user movie
# 0 1 3
# 1 2 2
# 2 3 2

# Compute average
df_watch["movie"].mean()
# 2.333

# Question 3: How many hours does each user spend on each content?
# Compute total viewing hours for each item
df_user_hrs = df.groupby(by="movie", as_index=False).agg(
    {
        "viewing hours": "sum", # compute total hours
        "user": "nunique", # count unique users
    }
)
# movie viewing hours user
# 0         1.0    2
# 1         2.0    2
# 2         3.0    3
## Compute average hours for each content
df_user_hrs["viewing hours"] / df_user_hrs["user"]
# 0    0.500000
# 1    1.000000
# 2    0.566667
# dtype: float64
```

- For question 1, we apply the generic groupby (by="key") .<agg_func> pattern, where <agg_func> can be, for instance, sum, mean, min, max, etc. Notice that we ended up with an extraneous column movie after the groupby operation, which we ignored in our subsequent calculation.

- For question 2, we apply the aggregation on a specific group value, rather than on all the features except user. After the groupby operation, we only end up with the key user and the grouped value feature movie, which we apply the aggregation nunique to count the size of the unique set of movie ids.

- For question 3, to compute average viewing per user, we need to apply two different aggregation functions on two group values. For the viewing hours feature, we need to sum together all the numbers within the same movie id and for the user feature, we need to count the distinct number of user ids. This is, therefore, expressed using a dict to map the feature name to the aggregation function. We subsequently use the two summarized features to compute the per-user average hours of each content.

The above three examples illustrated Pandas' "groupby-aggregate" pattern. Another pattern that leverages groupby is the "groupby-apply" pattern: instead of reducing the grouped values into a single summary statistics, it performs a transformation on the existing value, retaining the size of the input. Let us illustrate this pattern by answering the following question: What percentage of time does each user spend on each movie? We assume that in the above data, each user only watches each item only once. Otherwise, we need to use the groupby-aggregate pattern first to sum together the watch hours by each user by each item first.

```
# Question 4: what percentage of time does each user spend on each movie
percentage = df.groupby(by="user")["viewing hours"].apply(
lambda x: x / x.sum() * 100,
).droplevel(0)
percentage = percentage.rename("percentage")
df_perc = df.join(percentage, how="left").reset_index(drop=True)
df_perc = df_perc.sort_values(by=["user"]).reset_index(drop=True)
```

| # | user | movie | viewing hours | percentage |
|---|---|---|---|---|
| 0 | 1 | 3 | 0.6 | 27.272727 |
| 1 | 1 | 2 | 0.7 | 31.818182 |
| 2 | 1 | 1 | 0.9 | 40.909091 |
| 3 | 2 | 3 | 0.6 | 85.714286 |
| 4 | 2 | 1 | 0.1 | 14.285714 |
| 5 | 3 | 2 | 1.3 | 72.222222 |
| 6 | 3 | 3 | 0.5 | 27.777778 |

The groupby-apply pattern in the current example produces a Pandas Series that is sorted according to the user id after grouping, which is not the same as the original order in the input DataFrame. We use DataFrame.join to combine the new percentage feature back to the input DataFrame.

Note that when we were introducing vectorization and parallel computing in Chapter 1, we also illustrated an example of using the groupby-apply pattern with a custom apply function which can use even more complicated logic than the simple lambda function we illustrated in this example. Both groupby-aggregate and groupby-apply patterns are useful in either exploratory data analysis to understand data properties or data preprocessing for machine learning feature engineering.

### 9.2 Reshaping and Windowing of Dense Tensors

In Chapter 2, we introduced reduction operation, in which we apply an arithmetic operation along one or more dimension(s) or axis (axes) of a tensor. When combined with a reshaping operation, a reduction operation can be seen as applying the groupby-aggregate pattern. For instance, suppose we would like to downsample a time series by taking the average over chunks of 10 elements.

```
import numpy as np
import matplotlib.pyplot as plt
# Simulate time series
x = np.linspace(0, 10, 500)
y = np.sin(x) + np.random.rand(len(x))
# Downsample by averaging groups of 10 elements
x_downsample = x[::10]
y_reshaped = y.reshape(-1, 10)
y_downsample = y_reshaped.mean(axis=1)
# Plot out the results
fig, ax = plt.subplots(1, 1, figsize=(8, 4))
ax.plot(x, y, label="original", zorder=0)
ax.plot(x_downsample, y_downsample, label="downsampled", c="r", zorder=1)
17 ax.scatter(x_downsample, y_downsample, c="r", zorder=2)
18 ax.set_xlabel("Time")
19 ax.set_ylabel("Value")
20 ax.legend()
```

Here, in Line 10, we reshaped y from a shape of (500, ) array to a 2D (50, 10) matrix. The reshaping operation collects every 10 elements in the second dimension (axis=1) and stacks each of the collections along the first dimension (axis=0). Therefore, this is as if using the groupby pattern. Then, we apply the mean reduction operation along axis=1 in Line 11, which takes the average within the grouped values. Together, this reshape-reduce operation combination completes the implementation of a groupby-aggregate pattern. See Figure 9.1 for the results of the plot. See also Figure 9.2 for a schematic illustration of the concept of combining reshaping and reduction operations to implement the groupby-aggregate pattern. Note that to use the reshape-reduce operation, we need to assume that the length of the sequence is divisible by the number of groups we would like to create via reshape. Otherwise, we should pad the sequence so that it can be grouped/reshaped properly.

Similarly, in Chapter 2, we also introduced the concept of broadcasting, where we apply a lower-dimensional tensor to a higher-dimensional tensor to perform arithmetic operations. Another way to look at broadcasting is from the perspective of groupby-apply. Again, using the above time series example, let us now suppose we would like to remove the mean of the time series for every chunk of 10 data points.

![](img/e891acaacd4fb5b80dab2ed824618203_320_0.png)

Figure 9.1 Downsampled time series from the code example.
