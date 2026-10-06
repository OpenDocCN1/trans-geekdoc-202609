

## 7.3 练习题

Q1. R 和 Python 语言用于 Web 服务的集成。请解释集成的优势。

Q2. R 和 Python 语言用于 Web 服务的集成。请解释集成过程。

## 第 8 章
## 使用 Microsoft Azure Machine Learning Studio 集成创建预测模型

### 8.1 R 脚本集成

如果你正在使用 Azure Machine Learning Studio 并希望应用给定算法块以外的算法，可以创建并使用 R 脚本块。

### 8.1.1 使用 R 脚本查看数据

在调板中，从调板检索“成人人口收入二分类”（Adult Census Income Binary Classification）数据集并将其放在画布上，如图 8-1 所示。同时放置“执行 R 脚本”（Execute R Script）块。

将数据集连接到“执行 R 脚本”块，如图 8-2 所示，点击右上角的按钮。

124 机器学习：概念、工具与数据可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_140_0.png)

图 8-1 使用 R 脚本的布局

![](img/3c3c87d78136583581b0cf0620f5ae66_140_1.png)

图 8-2 R 脚本修改

Azure Machine Learning Studio 中的 R 脚本有两个映射的输入端口。如图 8-3 所示，仅连接了一个数据集以便检查数据。数据集 1 包含连接到第一个端口的数据。

使用 Microsoft Azure Machine Learning 脚本集成创建预测模型

![](img/3c3c87d78136583581b0cf0620f5ae66_141_0.png)

图 8-3 R 脚本编辑

# Source (8-3)

```
dataset1 <- maml.mapInputPort(1)
mydata <- dataset1[sample(1:nrow(dataset1), 50, replace=FALSE),]

data.set = mydata
print(mydata)
maml.mapOputPort("data.set");
```

之后，取 50 个 dataset1 值并将其放入“my data”中。你可以通过 `print` 函数检查整个样本数据。源可以在下方找到。
点击底部的“运行”（Run）按钮训练预测模型。之后，你可以通过点击“结果数据集”（Result Dataset）菜单中的“可视化”（Visualize）来检查提取的值，如图 8-4 所示。
图 8-5 显示 50 个 dataset1 值已正确输入。

## 图 8-4 使用 R 脚本的数据可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_142_0.png)

## 图 8-5 数据可视化结果

![](img/3c3c87d78136583581b0cf0620f5ae66_142_1.png)

图 8-6 显示了通过 R 设备可视化由 R 脚本的 `head()` 函数提取的数据集部分。

使用 Microsoft Azure Machine Learning 脚本集成创建预测模型

![](img/3c3c87d78136583581b0cf0620f5ae66_143_0.png)

图 8-6 R 脚本输出结果

### 8.1.2 使用 R 脚本实现决策树

在用 R 脚本应用决策树之前，让我们看看 iris 数据集。iris 数据由统计学家 Fisher 提供了三种鸢尾花（Setosa）、变色花（Versicolor）和毛尾花（Virginica）的花萼和花瓣长度，如图 8-7 所示。由于数据量小，iris 数据易于用于机器学习。

表 8-1 显示了 iris 数据集的描述。关于 iris 数据集的更多信息可以在 https://archive.ics.edu/datasets/iris 找到。
在创建模型之前，导入 iris 数据，如图 8-8 所示。iris 数据也作为样本数据在 Azure Machine Learning 中提供。

128 机器学习：概念、工具与数据可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_144_0.png)

Versicolor（变色花）

Setosa（鸢尾花）

Virginica（毛尾花）

图 8-7 iris 数据

## 表 8-1 iris 数据解释

| 列名 | 含义 | 数据类型 |
| --- | --- | --- |
| Species | 三种鸢尾花（Setosa, Versicolor, Virginica）之一 | String |
| Sepal.Width | 花萼宽度 | Number |
| Sepal.Length | 花萼长度 | Number |
| Petal.Width | 花瓣宽度 | Number |
| Petal.Length | 花瓣长度 | Number |

![](img/3c3c87d78136583581b0cf0620f5ae66_144_1.png)

图 8-8 导入数据

使用 Microsoft Azure Machine Learning 脚本创建模型

插入数据集后，将来自调板的数据放在画布上，如图 8-9 所示。放置“在数据集选择列”（Select Columns in Dataset）块来定义算法。如图 8-10 所示放置后，点击“列选择器”（Column Selector）。

![](img/3c3c87d78136583581b0cf0620f5ae66_145_0.png)

![](img/3c3c87d78136583581b0cf0620f5ae66_145_1.png)

130 机器学习：概念、工具与数据可视化

选择所有列以应用算法，如图 8-11 所示。
放置“执行 R 脚本”（Execute R Script）块，如图 8-12 所示，点击 R 脚本属性上方的小方块来修改 R 脚本。在 R 脚本窗口底部输入代码，如图 8-13 所示。

![](img/3c3c87d78136583581b0cf0620f5ae66_146_0.png)

图 8-11 用于算法的列选择

![](img/3c3c87d78136583581b0cf0620f5ae66_146_1.png)

图 8-12 R 脚本修改

131 使用 Microsoft Azure Machine Learning 脚本集成创建预测模型

![](img/3c3c87d78136583581b0cf0620f5ae66_147_0.png)

图 8-13 R 脚本编辑

# Source (rpart)

```
library(rpart)
Dataset1 <- maml.mapInputPort(1)
irisData <- rpart(Species~Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, method="class",
data=Dataset1)

print(irisData)
plot(irisData)
summary(irisData)

plot(irisData, uniform=TRUE, margin=0.1, compress=TRUE, main="Classification Tree")
text(irisData, use.n=TRUE, all=TRUE, cex=0.8, pretty=1)
data.set = Dataset1

maml.mapOutputPort("data.set")
```

使用图 8-14 中的可视化验证应用到 R 脚本的结果是完好的的。
你可以如图 8-15 所示看到结果没有问题。R Studio 和 Azure Machine Studio 的结果相同吗？

132 机器学习：概念、工具与数据可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_148_0.png)

图 8-14 决策树结果可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_148_1.png)

图 8-15 使用 R 脚本的决策树结果（Azure Machine Studio）

如图 8-16 所示，相同的结果已应用到 R Studio。图 8-17 显示了应用到 iris 数据的决策树可视化。可以看到三种鸢尾花根据标准进行了分类。

133 使用 Microsoft Azure Machine Learning 脚本集成创建预测模型

分类树：
rpart(formula = Species ~ Sepal.Length + Sepal.Width + Petal.Length + 
Petal.Width, data = irisData, method = "class")

树中实际使用的变量：
[1] Petal.Length.Petal.Width

根节点误差：100/150 = 0.6667

| CP | nsplit | rel | xerror | xstd |
|---|---|---|---|---|
| 1 | 50 | 0 | 1.00 | 1.24 | 0.046361 |
| 2 | 44 | 1 | 0.50 | 0.80 | 0.061101 |
| 3 | 01 | 2 | 0.06 | 0.09 | 0.029086 |

n= 150

图 8-16 使用 R 脚本的决策树结果（R Studio）

![](img/3c3c87d78136583581b0cf0620f5ae66_149_0.png)

图 8-17 使用 R 的决策树可视化

134 机器学习：概念、工具与数据可视化

### 8.2 Python 脚本集成

Python 和 R 脚本一样，也可以与 Azure Machine Studio 集成。

放置并连接 iris 数据并点击“在数据集选择列”以集成 R 语言。要集成 Python 语言，选择要包含的所有列，如图 8-18 所示。

然后，从调板中导入并放置“执行 Python 脚本”（Execute Python Script）块，如图 8-19 所示。

![](img/3c3c87d78136583581b0cf0620f5ae66_150_0.png)

图 8-18 用于算法的列选择

![](img/3c3c87d78136583581b0cf0620f5ae66_150_1.png)

图 8-19 Python 集成的布局

