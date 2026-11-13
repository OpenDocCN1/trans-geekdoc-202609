

### (a) 使用 Excel

屈服强度 (MPa) 混凝土抗压强度 (MPa)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_63_0.png)

### (b) 使用 Python

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_63_1.png)

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3 [Examples].xlsx")
sns.set(rc = {'figure.figsize':(6,6)})
df
sns.boxplot( y=df['Compressive strength of concrete (MPa)'] ) ;
```

图 3.3 箱线图演示。

如上所述，散点图可以容纳多个特征 65（参见图 3.5）。观察图 3.5 可知，向散点图添加多个特征作为可视化工具可能效率低下。稍微格式化一下图表可以改善这一问题。另一种方法是减少涉及的特征数量。66 更实际的方法是使用不同的可视化工具。

为完整起见，还有其他可使用和应用的可视化工具，例如小提琴图、点图、漏斗图、时间序列图等。您将在本书的示例中反复看到这些工具。目前，我希望您记住，使用此类工具的目标是尝试深入了解您的数据集。

65 视特征而定——这些图表可能适用于两个特征。对于可视化高维数据集，可以使用主成分分析（PCA）算法（将在后续章节中讨论）。
66 例如，我们可以用抗压强度除以屈服强度。也可以对管厚和管径做同样的处理。第一个比率可被视为材料强度的度量，第二个比率可被视为管子截面特性的度量。

### (a) 使用 Excel

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_64_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_64_1.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_64_2.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_64_3.png)

### (b) 使用 Python

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_64_4.png)

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3 [Examples].xlsx")
sns.set(rc = {'figure.figsize': (6, 6)})
df
sns.scatterplot(x='Compressive strength of concrete (MPa)', y='Axial capacity (kN)', data=df)
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_65_0.png)

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3 [Examples].xlsx")
sns.set(rc = {'figure.figsize': (6, 6)})
df
sns.jointplot('Yield strength (MPa)', 'Axial capacity (kN)', data=df);
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_65_1.png)

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3 [Examples].xlsx")
sns.set(rc = {'figure.figsize': (6, 6)})
df
sns.pairplot (df)
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_66_0.png)

```r
library(tidyverse)
library(ggplot2)
data=read.csv('C:/Chapter 3.csv ')
data
str(data)
#scatter plot
p <- ggplot(data, aes(x=Compressive.strength.of.concrete..MPa., y=Axial.capacity..kN.)) +
geom_point() +
theme(legend.position="none")
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_66_1.png)

```r
library(tidyverse)
library(ggplot2)
data=read.csv('C:/Chapter 3.csv ')
data
str(data)
p2<-lines(density(data$Diameter..mm.))
p <- ggplot(data, aes(x=Diameter..mm., y=Yield.strength..Mpa.)) +
geom_point() +
theme(legend.position="none")
#marginal histplot
p3 <- ggMarginal(p, type="histogram")
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_67_0.png)

```r
library(tidyverse)
library(ggplot2)
data=read.csv('C:/Chapter 3.csv ')
data
str(data)
p2<-lines(density(data$Diameter..mm.))
p <- ggplot(data, aes(x=Diameter..mm., y=Yield.strength..MPa.)) +
geom_point() +
theme(legend.position="none")
#marginal histoplot
p5 <- ggMarginal(p, type="boxplot")
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_67_1.png)

```r
library(tidyverse)
library(ggplot2)
data=read.csv('C:/Chapter 3.csv ')
data
str(data)
pairs(data[,1:6],
col = "black",
pch = 16,
main = "A pair plot for dataset")
```

图 3.4（续）散点图演示（左：未格式化，右：已格式化，上：未格式化，下：已格式化）。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_68_0.png)

让我们现在探索一些适用于分类数据的可视化工具。

柱状图：与直方图类似，但用于显示分类特征的计数。这些图表也可以格式化以显示特征的比率（按其类别划分）。例如，图 3.6 显示了在屈曲和压溃中失效的柱子数量。该图还比较了柱子的类型（非常长 vs. 长 vs. 短⁶⁷）。如您所见，在压溃中失效的长柱子的百分比相对较小（约为短柱子的 20%）。

其他类型的可视化包括箱线图、⁶⁸ 列联表和马赛克图。列联表（显示分类变量组合的频数）和马赛克图（显示多个分类特征的整体与部分关系）的示例见图 3.7。

为完整起见，允许我展示软件 Exploratory。这是一种基于 R 的软件，可用于创建机器学习模型，并且我们将在接下来的几章中使用它。Exploratory 具有完整的数据可视化功能。我将展示一些数值数据和分类数据的示例。⁶⁹

### (a) 使用 Excel（上：传统，下：堆叠）。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_69_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_69_1.png)

### (b) 使用 Python

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_69_2.png)

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3 [Examples].xlsx")
sns.set(rc = {'figure.figsize': (6, 6)})
df
sns.countplot(df['Column type', ])
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_70_0.png)

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3 [Examples].xlsx")
sns.set(rc = {'figure.figsize':(6,6)})
df

Grouped_bar_chart = pd.pivot_table(df,
values="Diameter (mm)",index="Column type",columns="Failure Mode",
aggfunc=np.mean)
#Creating a grouped bar chart
ax = Grouped_bar_chart.plot(kind="bar",
alpha=0.5)
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_70_1.png)

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3 [Examples].xlsx")

sns.set(rc = {'figure.figsize':(6,6)})
df

sns.barplot(x = 'Yield strength (MPa)', y = 'Column type', hue = 'Failure Mode', data = df, palette = "Blues")
sns.set(rc = {'figure.figsize':(14,6)})
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_70_2.png)

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3 [Examples].xlsx")

sns.set(rc = {'figure.figsize':(6,6)})
df

sns.histplot(data = df, x = "Diameter (mm)", kde = False, hue = "Failure Mode")
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_71_0.png)

```
import matplotlib as plt
import seaborn as sns
df = pd.read_excel("Chapter 3 [Examples].xlsx")
sns.set(rc = {'figure.figsize':(6,6)})
df
sns.histplot(data = df, x = "Yield strength (MPa)", kde = True, hue = "Failure Mode")
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_71_1.png)

```r
library(tidyverse)
library(ggplot2)
data=read.csv('C:// Chapter 3 [Examples].xlsx')
data
str(data)
ggplot(data = data, aes(x=Column.type)) +
geom_bar()
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_71_2.png)

```r
library(tidyverse)
library(ggplot2)
data=read.csv('Chapter 3 [Examples].xlsx')
data
str(data)
# Barplot
ggplot (data, aes (y=Column.type, x=Yield strength..MPa.,
fill=Failure.Mode)) +
geom_bar(stat = "identity",position = "dodge")
```

图 3.6（续）柱状图演示。

| 模式 | 超长柱子 | 长柱子 | 短柱子 |
|---|---|---|---|
| 屈曲 | 347 | 254 | 57 |
| 压溃 | 491 | 70 | 26 |

超长柱子   长柱子   短柱子
超长柱子   长柱子   短柱子

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_72_0.png)

图 3.7 列联表（上）和马赛克（树）图（下）演示。

步骤 1：上传数据集。进入数据帧，然后选择文件数据。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_72_1.png)

