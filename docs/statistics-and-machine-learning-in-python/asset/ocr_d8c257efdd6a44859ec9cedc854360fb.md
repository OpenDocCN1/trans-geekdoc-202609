![](bbox=[0.12, 0.09, 0.73, 0.38])

# Detrending

```
df_dtrend = df[["diet", "gym"]] - df_avg
df_dtrend.plot()
plt.xlabel('Year')
```

```
Text(0.5,0,'Year')
```

![](bbox=[0.17, 0.55, 0.76, 0.84])