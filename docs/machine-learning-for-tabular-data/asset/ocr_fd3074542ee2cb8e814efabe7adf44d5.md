# CHAPTER 7 An end-to-end example using XGBoost

```
perc = [1, 5, 10, 25, 50, 75, 90, 95, 99]
for p in perc:
    print(f"percentile {p}: {np.percentile(y, p).round(2)}")
```

We are the output percentiles, and have confirmation of the presence of
extreme values at the right of the distribution even the 99th percentile is quite far
from the maximum we had previously reported:

+   percentile 1: 3000.0
percentile 5: 5198.2
percentile 10: 7325.67
percentile 25: 11870.0
percentile 50: 19830.78
percentile 75: 37741.64
percentile 90: 83936.03
percentile 95: 84857.11
percentile 99: 304531.4

Not only is the maximum value quite far from the 99th percentile, but also
appears to be a significant gap between the 95th and 99th percentiles. Our decision
is to focus on the core of the distribution by dropping 10% of the distribution: 5%
on the lower and 5% on the upper part. We manage this by using a Boolean
selection variable:

```
valid_samples = (y >= 5200) & (y <= 84857)
```

Before definitely defining the selection, we plot the distribution.

# Listing 7.10 Plotting the target distribution

```
import matplotlib.pyplot as plt
import seaborn as sns

valid_y = y[valid_samples]
sns.kdeplot(valid_y, fill=True)

median = np.median(valid_y)
plt.axvline(median, color='r', linestyle='--', linewidth=2, label='Median')

plt.xlabel('Value')
plt.ylabel('Density')
plt.title('Distribution Curve with Median')
plt.legend()
plt.show()
```

![](bbox=[0.548, 0.627, 0.843, 0.706])

The previous code snippet will output a density plot, revealing the distribution and the
median value for the selection of the target based by the selection variable we have just
defined. Figure 7.10 shows the resulting plot.