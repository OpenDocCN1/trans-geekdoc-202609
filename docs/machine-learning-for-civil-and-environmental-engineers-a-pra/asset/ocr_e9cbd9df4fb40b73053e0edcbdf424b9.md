![](bbox=[0.113, 0.09, 0.491, 0.373])

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3 [Examples].xlsx")
sns.set(rc = {'figure.figsize': (6, 6)})
df
sns.jointplot('Yield strength (MPa)',
'Axial capacity (kN)', data=df);
```

![](bbox=[0.111, 0.442, 0.592, 0.821])

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3
[Examples].xlsx")
sns.set(rc = {'figure.fig-
size': (6, 6)})
df
sns.pairplot (df)
```