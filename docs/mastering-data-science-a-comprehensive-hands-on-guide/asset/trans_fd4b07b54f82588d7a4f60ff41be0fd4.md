
```
avg_tips = data.groupby('day')['tip'].mean()

print(avg_tips)
```

## 处理缺失值

检查缺失值：

```
print(data.isnull().sum())
```

填充缺失值：

```
data.fillna(0, inplace=True)
```

如果出现错误：“TypeError: Cannot setitem on a Categorical with a new category (0), set the categories first,” 请使用以下 `replace()` 来处理缺失值，将其替换为 0。

```
data.replace(np.nan, 0)
```

删除包含缺失值的行：

```
data.dropna(inplace=True)
```

## 使用 Matplotlib 进行数据可视化

### 折线图

可视化连续数据中的趋势。

```
plt.plot(data['total_bill'], data['tip'], 'o')
plt.xlabel('Total Bill')
plt.ylabel('Tip')
plt.title('Total Bill vs. Tip')
plt.show()
```

![一张蓝色点的图表 AI 生成的内容可能不正确。](image_rsrcF07.jpg)

来自 Jupyter Notebook 的截图

### 柱状图

比较分类数据。

```
data.groupby('day')['total_bill'].mean().plot(kind='bar')
plt.ylabel('Average Total Bill')
plt.show()
```

![一张蓝色条形的图表 AI 生成的内容可能不正确。](image_rsrcF08.jpg)

来自 Jupyter Notebook 的截图

### 直方图

显示单个变量的分布。

```
data['total_bill'].plot(kind='hist', bins=10, edgecolor='black')
plt.xlabel('Total Bill')
plt.title('Distribution of Total Bill')
plt.show()
```

![一张账单分布的图表 AI 生成的内容可能不正确。](image_rsrcF09.jpg)

来自 Jupyter Notebook 的截图

## 使用 seaborn 进行数据可视化

### 散点图

可视化两个变量之间的关系。

```
sns.scatterplot(x='total_bill', y='tip', data=data, hue='day', style='time')
plt.title('Total Bill vs. Tip by Day and Time')
plt.show()
```

![一张彩色点的图表 AI 生成的内容可能不正确。](image_rsrcF0A.jpg)

来自 Jupyter Notebook 的截图

### 箱线图

显示数据的分布并识别异常值。

```
sns.boxplot(x='day', y='total_bill', data=data)
plt.title('Total Bill by Day')
plt.show()
```

![一张图表的图形 AI 生成的内容可能不正确。](image_rsrcF0B.jpg)

来自 Jupyter Notebook 的截图

### 热力图

可视化变量之间的相关性。

```
data = sns.load_dataset('tips')
data = data.drop(['sex', 'smoker', 'day','time'], axis=1) # drop categorical values first
correlation = data.corr()
sns.heatmap(correlation, annot=True, cmap='coolwarm')
plt.title('Correlation Matrix')
plt.show()
```

![一张电脑的截图 AI 生成的内容可能不正确。](image_rsrcF0C.jpg)

来自 Jupyter Notebook 的截图

## 保存可视化图表

将图表保存为图像用于报告：

```
plt.savefig('plot.png')
```

## 最佳实践

- 首先探索数据：使用 `head()`、`info()` 和 `describe()` 来了解数据集。
- 处理缺失值：根据上下文决定是填充还是删除缺失数据。
- 选择合适的可视化方式：使用散点图表示关系，直方图表示分布，热力图表示相关性。
- 保持视觉简洁：避免用不必要的细节使图表杂乱。

总之，通过结合 pandas 进行数据处理以及 Matplotlib/seaborn 进行可视化，您可以深入洞察数据集。这些工具能够实现顺畅的工作流程，有效地分析和呈现数据。

# 4.5 章节复习题

问题 1：

以下哪个库主要用于 Python 中的数值运算？

A. pandas

B. NumPy

C. seaborn

D. scikit-learn

问题 2：

pandas 库的主要用途是什么？

A. 执行统计分析

B. 处理和操作结构化数据

C. 可视化数据

D. 训练机器学习模型

问题 3：

哪个库通常用于在 Python 中创建静态、交互式和动画可视化？

A. Matplotlib

B. seaborn

C. NumPy

D. scikit-learn

问题 4：

Matplotlib 和 seaborn 之间有哪些关键区别？

A. Matplotlib 用于数据操作，而 seaborn 用于机器学习

B. seaborn 在 Matplotlib 之上提供高级接口，便于创建统计可视化

C. Matplotlib 专门用于机器学习任务

D. seaborn 用于数值运算

问题 5：

哪个库广泛用于在 Python 中构建和训练机器学习模型？

A. NumPy

B. Matplotlib

C. scikit-learn

D. pandas

问题 6：

使用 pip 安装 Python 库的推荐命令是什么？

A. `python install <library_name>`

B. `install <library_name>`

C. `pip install <library_name>`

D. `python setup.py install`

问题 7：

导入 Python 库时常见的以下问题是什么？

A. 库版本过旧

B. 导入语句中库名称错误

C. 缺少库安装

D. 以上全部

问题 8：

Python 中虚拟环境的用途是什么？

A. 使 Python 代码运行更快

B. 隔离项目依赖

C. 将 Python 连接到外部数据库

D. 管理多个 Python 安装

问题 9：

如何激活 Python 中的虚拟环境？

A. `activate env`

B. `python venv`

C. `source <env_name>/bin/activate`

D. `pip install venv`

问题 10：

如果需要高效处理大型数据集并执行数据清洗任务，您会选择哪个库？

A. scikit-learn

B. Matplotlib

C. pandas

D. seaborn

# 4.6 章节复习题答案

1. B. NumPy

解释：NumPy 主要用于 Python 中的数值运算，提供对数组、矩阵和数学函数的支持。

2. B. Handling and manipulating structured data

解释：pandas 专为处理结构化数据而设计，例如表格中的数据（DataFrames），并提供数据操作、清洗和分析的功能。

3. A. Matplotlib

解释：Matplotlib 是用于在 Python 中创建静态、交互式和动画可视化的通用库。

4. B. seaborn provides a high-level interface built on top of Matplotlib for easier statistical visualizations

解释：seaborn 通过在 Matplotlib 之上构建，简化了创建美观且信息丰富的统计可视化的过程。

5. C. scikit-learn

解释：scikit-learn 广泛用于在 Python 中构建和训练机器学习模型，提供分类、回归、聚类等工具。

6. C. `pip install <library_name>`

解释：`pip install <library_name>` 命令是安装 Python 库的标准方式。

7. D. All of the above

解释：导入时的常见问题包括库版本过旧、导入语句错误以及缺少安装。

8. B. To isolate project dependencies

解释：虚拟环境用于隔离项目特定的依赖，防止不同项目中使用的库发生冲突。

9. C. `source <env_name>/bin/activate`

解释：在大多数系统（例如 Linux 或 macOS）中，使用 `source <env_name>/bin/activate` 命令激活虚拟环境。

10. C. pandas

解释：由于其强大的 DataFrame 和 Series 结构，pandas 是处理大型数据集和高效执行数据清洗任务的最佳选择。

# 第 5 章 NumPy 在数据科学中的应用

NumPy 是 Python 中用于数值计算的基础库，在数据科学中被广泛用于高效处理大型数据集。本章探讨 NumPy 是什么、如何安装和导入它，以及它的核心功能，包括 NumPy 数组、其属性以及诸如重塑、索引和切片等操作。它深入介绍高级主题，如数组操作、随机数处理、输入/输出操作和线性代数应用。此外，本章还强调了 NumPy 在数据科学中的作用、优化技术和性能改进，并以实际应用和高效数据处理的最佳实践作结。

## 5.1 什么是 NumPy？

