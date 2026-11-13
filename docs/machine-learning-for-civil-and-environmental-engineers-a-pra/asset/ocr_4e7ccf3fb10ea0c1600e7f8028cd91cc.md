![](bbox=[0.12, 0.09, 0.53, 0.33])

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3 [Examples].xlsx")
sns.set(rc = {'figure.figsize':(6,6)})
df
sns.histplot(data = df, x = "Yield strength (MPa)", kde = True, hue = "Failure Mode")
```

![](bbox=[0.12, 0.36, 0.5, 0.55])

```
library(tidyverse)
library(ggplot2)
data=read.csv('C:// Chapter 3 [Examples].xlsx')
data
str(data)
ggplot(data = data, aes(x=Column.type)) +
geom_bar()
```

![](bbox=[0.12, 0.58, 0.51, 0.72])

```
library(tidyverse)
library(ggplot2)
data=read.csv(Chapter 3 [Examples].xlsx')
data
str(data)
# Barplot
ggplot (data, aes (y=Column.type, x=Yield strength..MPa.,
fill=Failure.Mode)) +
geom_bar(stat = "identity",position = "dodge")
```

Figure 3.6 (Cont’d) Demonstration of bar charts.