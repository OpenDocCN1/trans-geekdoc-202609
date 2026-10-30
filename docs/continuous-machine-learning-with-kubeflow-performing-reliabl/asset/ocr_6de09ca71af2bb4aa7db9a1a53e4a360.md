# 7.5.2.4 Correlation & Scatter Plots

Here, we will plot the correlation to check the relation between the variables and scatter the plots to check the outlier analysis with respect to the dependent feature House price.

```
corr = raw_data.corr()
top_correlation = corr['SalePrice'].sort_values(ascending=False)[:25]
threshold = 0.51
top_corr = corr.index[np.abs(corr["SalePrice"]) > threshold]
```

```
plt.figure(figsize=(10,8))
sns.heatmap(raw_data[top_corr].corr(),annot=True,cmap="RdBu_r")
```

So, the correlation plot will look like the following: