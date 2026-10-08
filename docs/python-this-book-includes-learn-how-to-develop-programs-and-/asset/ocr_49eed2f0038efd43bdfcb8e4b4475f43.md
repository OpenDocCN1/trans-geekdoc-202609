+   1. There is a high correlation between height and weight.

+   2. There exists a weak positive correlation between successful field goals in terms of weight and height.

+   3. The mean points attained tend to have the highest correlation with success_field_goals, but they aren't highly correlated.

Now, let's look at the distribution of each of the independent variables with reference to the dependent variable:
Below is the output:

![](bbox=[0.118, 0.323, 0.636, 0.563])

In the following scatter plot, you can see that there is no obvious pattern between the average points attained and the height. The distribution appears quite random.
Let's examine the distribution between average points scored and the weight:

```
fig, ax = plt.subplots(1, 1)
ax.scatter(b_data.weight, b_data.avg_points_scored)
ax.set_xlabel('weight')
ax.set_ylabel('Average points scored per game')
plt.show()
```

Here's the output: