
## 分类图
分类图用于可视化分类数据与数值数据之间的关系。

条形图 (`sns.barplot`)：用于显示不同类别下数值变量的均值。示例：按产品类别显示平均销售额。

计数图 (`sns.countplot`)：可视化每个类别的出现次数。示例：统计数据集中产品类型的频率。

箱线图 (`sns.boxplot`)：通过四分位数展示数值变量的分布，并突出显示异常值。示例：可视化不同职业部门间的收入分布。

小提琴图 (`sns.violinplot`)：结合箱线图和 KDE 图显示数据的分布和概率密度。示例：比较不同学校学生的考试成绩。

散点图和蜂群图 (`sns.stripplot`, `sns.swarmplot`)：散点图沿分类轴显示单个数据点，而蜂群图防止重叠以提高清晰度。示例：可视化不同行业中的个人薪资。

### 分布图
分布图用于可视化数值变量的分布。

直方图 (`sns.histplot`)：显示数据点在各区间内的频率。示例：分析人口中的年龄分布。

KDE 图 (`sns.kdeplot`)：核密度估计图平滑数据以显示其潜在概率密度。示例：可视化数据集中房价的密度。

Rug 图 (`sns.rugplot`)：沿轴显示单个数据点，常与直方图或 KDE 图一起使用。示例：在直方图上添加 rug 图以更清晰地查看数据点。

### 关系图
关系图用于显示两个数值变量之间的关系。

散点图 (`sns.scatterplot`)：用于可视化两个数值变量之间的关系。示例：绘制销售额与广告支出以识别趋势。

折线图 (`sns.lineplot`)：显示数值变量随时间或连续输入的变化趋势。示例：随时间绘制股票价格。

### 矩阵图
矩阵图有助于可视化表格数据中的关系。

热力图 (`sns.heatmap`)：以矩阵格式显示数据，颜色代表值的大小。示例：可视化数据集中不同特征之间的相关性。

聚类图 (`sns.clustermap`)：与热力图类似，但包含层次聚类以对相似数据点进行分组。示例：根据购买行为对客户进行聚类。

Seaborn 提供了一个直观且多功能的框架，用于创建高质量、可出版的视觉化图表。通过组合这些图表类型，你可以发现数据中有意义的模式、关系和洞察。

# 7.5 自定义 Seaborn 可视化
## 调整图表美观性
Seaborn 使调整可视化的美观性以匹配不同的上下文和风格变得容易，从而提高清晰度和吸引力：
设置上下文：`sns.set_context()` 函数可为各种上下文自定义图表的比例和样式：
• paper：用于研究论文或文档中的小型图表。
• notebook：在 Jupyter notebook 中工作的默认设置。
• talk：用于演示放大的图表。
• poster：用于海报或幻灯片的更大图表。
示例：
```
sns.set_context("talk")
sns.scatterplot(x="sepal_length", y="sepal_width", data=df)
```
颜色调色板和主题：Seaborn 提供内置颜色调色板（例如，deep、pastel、dark）和主题（darkgrid、whitegrid、ticks）：
• 使用 `sns.set_palette()` 为图表定义配色方案。
• 应用 `sns.set_theme()` 调整整体图表样式。
示例：
```
sns.set_theme(style="whitegrid", palette="pastel")
sns.barplot(x="day", y="total_bill", data=tips)
```
![一个图表的图表，AI 生成的内容可能不正确。](image_rsrcF0X.jpg)
## 添加注释
注释通过突出显示关键数据点或统计信息提供额外上下文：使用 `plt.text()` 在图表上的特定点添加文本标签。直接在可视化上标注汇总统计信息或最大值。
示例：
```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
# Define raw data
raw_data = {'year': [2018, 2019, 2020, 2021, 2022],
'value': [50, 80, 100, 90, 60]}
# Convert to a pandas DataFrame
data = pd.DataFrame(raw_data)
# Plot using seaborn
sns.lineplot(x="year", y="value", data=data)
# Annotate the peak value
plt.text(2020, 100, "Peak Value", fontsize=12, color="red")
plt.show()
```
![包含折线图的图表，AI 生成的内容可能不正确。](image_rsrcF0Y.jpg)
## 使用 FacetGrid 和 PairGrid 工作于多图表
Seaborn 支持涉及网格布局中多个图表的高级可视化：
`FacetGrid`：用于在多个分面中可视化数据的子集。示例：
```
g = sns.FacetGrid(tips, col="time", row="sex")
g.map(sns.scatterplot, "total_bill", "tip")
```
`PairGrid`：用于数据集中变量之间的成对关系。示例：
```
import seaborn as sns
import matplotlib.pyplot as plt
# Load the Iris dataset
iris = sns.load_dataset("iris")
# Create a PairGrid
g = sns.PairGrid(iris)
g.map_diag(sns.histplot)
g.map_offdiag(sns.scatterplot)
plt.show()
```
## 自定义坐标轴和图例
Seaborn 提供灵活的工具来自定义坐标轴和图例：
坐标轴：使用 `set_xlabel()` 和 `set_ylabel()` 为坐标轴添加标签。使用 `set_xlim()` 和 `set_ylim()` 调整坐标轴限制。使用 Matplotlib 的 `plt.xticks()` 或 `plt.yticks()` 旋转刻度标签。
图例：使用 Seaborn 的 `legend()` 参数自定义图例。使用 `remove_legend()` 在不必要时排除图例。
示例：
```
sns.scatterplot(x="total_bill", y="tip", hue="sex", data=tips)
plt.legend(title="Gender", loc="upper left")
```
![包含蓝色和橙色点的图表，AI 生成的内容可能不正确。](image_rsrcF0Z.jpg)
自定义 Seaborn 可视化有助于将图表定制给特定受众，确保它们在视觉上具有吸引力并有效传达预期洞察。这些功能使 Seaborn 成为数据可视化的极其多功能工具。

# 7.6 结合 Matplotlib 和 Seaborn
## 何时结合 Matplotlib 和 Seaborn
Matplotlib 和 Seaborn 是互补的库，可以结合起来创建自定义、高质量的可视化。Seaborn 提供易于使用的接口，用最少的代码创建美观的图表，而 Matplotlib 提供对图表自定义的精细控制。结合两者在以下情况很有用：
你想要 Seaborn 的高级美观性和统计功能，但需要 Seaborn 单独无法提供的精细定制。
你需要通过注释、多个子图或高级图例等附加元素增强 Seaborn 图表。
## 使用 Matplotlib 自定义 Seaborn 图表
虽然 Seaborn 会自动配置图表，但你可以使用 Matplotlib 函数来调整 Seaborn 生成的图表：
调整标题、坐标轴和图例：使用 Matplotlib 的 `plt.title()`、`plt.xlabel()` 和 `plt.legend()` 函数修改 Seaborn 图表。
```
import seaborn as sns
import matplotlib.pyplot as plt
tips = sns.load_dataset("tips")
sns.boxplot(x="day", y="total_bill", data=tips)
plt.title("Box Plot of Total Bill by Day")
plt.xlabel("Day of the Week")
plt.ylabel("Total Bill (USD)")
plt.show()
```
![包含蓝色方块和黑色文字的图表，AI 生成的内容可能不正确。](image_rsrcF10.jpg)
更改图形大小和布局：在使用 Seaborn 绘图之前，使用 Matplotlib 的 `plt.figure()` 或 `plt.subplots()` 配置图形大小和子图布局。
```
plt.figure(figsize=(10, 6))
sns.histplot(tips['total_bill'], kde=True)
plt.title("Distribution of Total Bill")
plt.show()
```
## 使用 Matplotlib 添加高级功能
Seaborn 图表可以通过 Matplotlib 的高级功能增强，例如：
