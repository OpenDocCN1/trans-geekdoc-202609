# Listing 7.8 Plotting boxplots for numeric features

```
import matplotlib.pyplot as plt
```

```
numeric = ['minimum_nights', 'number_of_reviews', 
    'days_since_last_review', 'reviews_per_month', 
    'calculated_host_listings_count', 
    'availability_365', 'score',
    'number_of_reviews_ltm',\n    'number_of_reviews_ltm_ratio',
    'number_of_bedrooms', 'number_of_beds',
    'number_of_baths', 'imperial_palace_distance',
    'nearest_conven_store',
    'nearest_train_station', 'nearest_airport',
    'nearest_bus_station']
```

```
num_plots = len(numeric)
num_rows = (num_plots + 2) // 3
num_cols = min(num_plots, 3)
```

```
fig, axes = plt.subplots(
    num_rows,
    num_cols,
    figsize=(8, 12)
)
axes = axes.flatten()
```

```
for i, feat in enumerate(numeric):
    X[feat].boxplot(ax=axes[i])
```

```
plt.tight_layout()
plt.show()
```

Figure 7.7 shows the charted results. By inspecting the values outside the whiskers of the plots, represented as empty points, we immediately notice that almost all the distributions have heavy tails on the right, with values decisively much larger than the mean value. For distance-based features, such extreme values may sound reasonable because of the extension of Tokyo’s metropolitan area, as features such as minimum night and number_of_reviews, extreme values may represent outliers far from the core of the distribution. We could use winsorizing to solve such problem, using a solution we proposed in chapter 2. This data transformation replaces extreme values in a dataset with less extreme values to reduce the influence of outliers on statistical analysis and modeling.

In Listing 7.9, using the winsorize function from the Scipy package, we winsorize the 0.1% of the upper part of the distribution of the minimum_nights feature. All values above the 0.999 percentile will be changed to the value of the 0.999 percentile, thus removing extreme values.