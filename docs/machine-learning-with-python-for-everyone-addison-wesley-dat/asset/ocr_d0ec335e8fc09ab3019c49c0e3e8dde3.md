```
sns.stripplot(data=df)
display(df.describe().loc[['mean', 'std']])
```

|  | x | std-ized |
|---|---|---|
| mean | 2.5000 | 0.0000 |
| std | 4.6706 | 1.0000 |

![](bbox=[0.33, 0.29, 0.67, 0.53])

That's all well and good, but things get far more interesting in two dimensions:

```
In [21]:
# 2 1D standardizations
xs = np.linspace(-5, 10, 20)
ys = 3*xs + 2 + np.random.uniform(20, 40, 20)

df = pd.DataFrame({'x':xs, 'y':ys})
df_std_ized = (df - df.mean()) / df.std()

display(df_std_ized.describe().loc[['mean', 'std']])
```

|  | x | y |
|---|---|---|
| mean | 0.0000 | -0.0000 |
| std | 1.0000 | 1.0000 |

We can look at the original data and the standardized data on two different scales: the natural scale that matplotlib wants to use for the data and a simple, fixed, zoomed-out scale: