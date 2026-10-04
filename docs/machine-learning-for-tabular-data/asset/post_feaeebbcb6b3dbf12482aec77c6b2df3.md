
# Preparing and exploring your data

263

![](img/def89cc476fa39f4c54bd34e78d91674_285_0.png)

**Figure 7.7** Panel of boxplots illustrating the skewed distributions of most numeric features

# CHAPTER 7 An end-to-end example using XGBoost

# Listing 7.9 Winsorizing extreme values

```python
from scipy.stats.m import winsorize

lower_cut_percentile = 0.00
upper_cut_percentile = 0.001

X['minimum_nights'] = winsorize(X['minimum_nights'].values,
limits=(lower_cut_percentile,upper_cut_percentile))

X['minimum_nights'].boxplot()
```

Indicates the lower percentile below which values will not be changed during winsorization

Indicates the upper percentile above which values will not be changed during winsorization

Figure 7.8 shows the highest value is 120, not over 1,000, as before.

![](img/def89cc476fa39f4c54bd34e78d91674_286_0.png)

**Figure 7.8** Boxplot of winsorized minimum_nights feature

We replicate the same also for the number_of_reviews feature:

```python
X['number_of_reviews'] = winsorize(X['number_of_reviews'].values,
limits=(lower_cut_percentile,
upper_cut_percentile))

X['number_of_reviews'].boxplot()
```

Figure 7.9 shows that the feature still has a heavy right tail. However, the extreme values have been compressed to below the 500 value.

![](img/def89cc476fa39f4c54bd34e78d91674_287_0.png)

**Figure 7.9** Boxplot of winsorized number_of_reviews

Having completed checking and remediating for missing values and extreme values in our dataset of predictors, we can proceed in the next subsection to look at the target itself.

## 7.1.6 Exploring your target

When dealing with exploratory data analysis (EDA), it is critical to examine the predictors and the target, and sometimes both predictors and target together and how they relate to each other. For our example, by a regression problem, we simply start by figuring out the mean and the range of the target:

```python
print(f'minimum: {y.min()}')
print(f'average: {y.mean().round(2)}')
print(f'maximum: {y.max()()}')
```

These commands will print the minimum, the average, and the maximum values in the target variable $y$:

- minimum: 1450.0
- average: 36573.1
- maximum: 1306500.0

We immediately notice that the maximum is on a quite different scale than the average and the minimum. Estimating percentiles can be helpful to understand better if there is a problem with extreme values or skewed distribution in the target. The presence of extreme values can be better understood by requiring a range of percentiles focusing on the extremities of the distribution:

```python
perc = [1, 5, 10, 25, 50, 75, 90, 95, 99]
for p in perc:
    print(f"percentile {p}: {np.percentile(y, p).round(2)}")
```

We are the output percentiles, and have confirmation of the presence of extreme values at the right of the distribution even the 99th percentile is quite far from the maximum we had previously reported:

- percentile 1: 3000.0
- percentile 5: 5198.2
- percentile 10: 7325.67
- percentile 25: 11870.0
- percentile 50: 19830.78
- percentile 75: 37741.64
- percentile 90: 83936.03
- percentile 95: 84857.11
- percentile 99: 304531.4

Not only is the maximum value quite far from the 99th percentile, but also appears to be a significant gap between the 95th and 99th percentiles. Our decision is to focus on the core of the distribution by dropping 10% of the distribution: 5% on the lower and 5% on the upper part. We manage this by using a Boolean selection variable:

```python
valid_samples = (y >= 5200) & (y <= 84857)
```

Before definitely defining the selection, we plot the distribution.

# Listing 7.10 Plotting the target distribution

```python
import matplotlib.pyplot as plt
import seaborn as sns

valid_y = y[valid_samples]
sns.kdeplot(valid_y, fill=True)

median = np.median(valid_y)
plt.axvline(median, color='r', linestyle='--', linewidth=2, label='Median')

plt.xlabel('Value')
plt.ylabel('Density')
plt.title('Distribution with Median')
plt.legend()
plt.show()
```

![](img/def89cc476fa39f4c54bd34e78d91674_288_0.png)

The resulting distribution shown in 7.10 shows the.

![](img/def89cc476fa39f4c54bd34e78d91674_289_0.png)

The resulting distribution shown in 7.10 shows the.

![](img/def89cc476fa39f4c54bd34e78d91674_290_0.png)
