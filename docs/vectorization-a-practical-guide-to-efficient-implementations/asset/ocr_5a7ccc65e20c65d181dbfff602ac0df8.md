```
```python
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
```

+   For question 1, we apply the generic groupby (by="key") .<agg_func> pattern, where <agg_func> can be, for instance, sum, mean, min, max, etc. Notice that we ended up with an extraneous column movie after the groupby operation, which we ignored in our subsequent calculation.

+   For question 2, we apply the aggregation on a specific group value, rather than on all the features except user. After the groupby operation, we only end up with the key user and the grouped value feature movie, which we apply the aggregation nunique to count the size of the unique set of movie ids.

+   For question 3, to compute average viewing per user, we need to apply two different aggregation functions on two group values. For the viewing hours feature, we need to sum together all the numbers within the same movie id and for the user feature, we need to count the distinct number of user ids. This is, therefore, expressed using a dict to map the feature name to the aggregation function. We subsequently use the two summarized features to compute the per-user average hours of each content.

The above three examples illustrated Pandas' "groupby-aggregate" pattern. Another pattern that leverages groupby is the "groupby-apply" pattern: instead of reducing the grouped values into a single summary statistics, it performs a transformation on the existing value, retaining the size of the input. Let us illustrate this pattern by answering the following question: What percentage of time does each user spend on each movie? We assume that in the above data, each user only watches each item only once. Otherwise, we need to use the groupby-aggregate pattern first to sum together the watch hours by each user by each item first.

```
```python
# Question 4: what percentage of time does each user spend on each movie
percentage = df.groupby(by="user")["viewing hours"].apply(
lambda x: x / x.sum() * 100,
).droplevel(0)
percentage = percentage.rename("percentage")
df_perc = df.join(percentage, how="left").reset_index(drop=True)
df_perc = df_perc.sort_values(by=["user"]).reset_index(drop=True)
```
```