# (a) Using Excel

![](bbox=[0.106, 0.105, 0.63, 0.345])

# (b) Using Python

![](bbox=[0.106, 0.385, 0.475, 0.665])

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3 [Examples] .xlsx")
sns.set(rc = {'figure.figsize':(6,6)})
df
sns.distplot(df['Compressive strength of concrete (MPa)'], bins=15, kde=False)
```

![](bbox=[0.106, 0.705, 0.485, 0.915])

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3 [Examples] .xlsx")
sns.set(rc = {'figure.figsize':(6,6)})
df
sns.histplot(data = df, x = "Yield strength (MPa)", kde = True)
```