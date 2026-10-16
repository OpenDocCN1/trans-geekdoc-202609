```
In [48]:

fig, axes = plt.subplots(1,2,figsize=(8,3))
for ax, variable in zip(axes, ['d1', 'd2']):
    predicted = (smf.ols("{}".format(variable), data=comparison)
        .fit()
        .predict())
    actual = comparison[variable]
    sns.distplot(predicted - actual, norm_hist=True, rug=True, ax=ax)
    ax.set_xlabel(variable)
    ax.set_ylabel('residual')
fig.tight_layout();
```

![](bbox=[0.15, 0.38, 0.8, 0.6])

Before we panic, let's see what happens when we try to relate a slighty different version of x, x², to d2. We'll look at the residuals, as well.

```
In [49]:

magic = pd.DataFrame({'d2' : 2*x**2+5+n1,
                      'x_sq' : x**2})
melted = pd.melt(magic, id_vars=['x_sq'])

fig, (ax1, ax2) = plt.subplots(1,2,figsize=(8,3))
sns.regplot(x='x_sq', y='value',
            data=melted, ci=None, ax=ax1)

predicted = (smf.ols("d2 ~ x_sq", data=magic)
    .fit()
    .predict())
actual = comparison['d2']
sns.distplot(predicted - actual, rug=True,
            norm_hist = True, ax=ax2)
```