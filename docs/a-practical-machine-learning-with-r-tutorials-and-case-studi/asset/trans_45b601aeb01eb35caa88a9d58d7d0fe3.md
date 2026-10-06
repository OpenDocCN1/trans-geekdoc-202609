

# 4.9 项目：通过多种化学属性预测葡萄酒颜色 91

并对划分后的测试数据进行测试，将它们分配给数据框 DataTrain 和 DataTest。

```r
library(tidymodels); library(rio); library(janitor)
DataWine=import("https://ai.large-analytics.com/data/WineData.rds") |>
clean_names("upper_camel") |>
select(Quality) |>
rename(Sulfur=TotalSulfurioxide) |>
mutate(WineColor=as.factor(WineColor))
```

```r
set.seed(876)
Split7030=initial_split(DataWine, prop=0.7, strata=WineColor)
```

```r
DataTrain=.... 
DataTest=....
```

```r
head(DataTrain)
```

接下来，通过执行下方的代码块，你将创建一个配方（recipe）。命令与之前相同，结果将保存到 R 对象 RecipeWine 中：

```r
RecipeWine=recipe(WineColor~, data=DataTrain) |>
step_naomit() |>
step_normalize(all_predictors())
```

```r
print(RecipeWine)

## -- Recipe --------------------
## -- Inputs
## 变量按角色分类
## outcome: 1
## predictor: 11
##
## -- Operations
## * 移除包含 NA 值的行: <none>
## * 对以下进行中心化和标准化:
## all_predictors()
```

# 92 k-近邻算法 — 入门

创建模型设计的命令与之前相同。当你执行下方的代码块时，模型设计将被创建并保存存在 R 对象 ModelDesignKNN 中：

```r
ModelDesignKNN=nearest_neighbor(neighbors=4,
  weight_func="rectangular") |>
  set_engine("kknn") |>
  set_mode("classification")

print(ModelDesignKNN)
```

## 近邻模型规范 (分类)
## 主要参数：
- neighbors = 4
- weight_func = rectangular
- 计算引擎: knn

你的任务是将配方和模型设计添加到一个工作流（workflow）中，然后将工作流拟合到训练数据。请注意，recipe recipeWine、模型设计 ModelDesignKNN 以及数据框 DataTrain 已经在后台加载完毕。请完成下方的代码块并执行它。

```r
WFModelWine=workflow() |>
  add_recipe(...) |>
  add_model(...) |>
  fit(...)

print(WFModelWine)
```

由于模型已经拟合到训练数据，我们可以使用它进行预测。这里我们使用 `predict()` 命令，该命令根据测试数据中的预测变量预测 WineColor，并将预测结果作为名为 `pred_class` 的新变量添加到 DataTest 中。完整结果保存在 R 对象 DataTestWithPred 中。

由于 R 对象 DataTestWithPred 包含了葡萄酒颜色的预测值（估计值）以及真实值（存储在变量 WineColor 中），我们可以将其作为指标命令的 `data` 参数。例如用于生成混淆矩阵的 `conf_mat()` 命令。相关的代码已经准备就，你只需要执行即可。

# 4.9 项目：通过多种化学属性预测葡萄酒颜色 93

```r
DataTestWithPred=augment(WFModelWine, DataTest)
conf_mat(DataTestWithPred, truth=WineColor, estimate=.pred_class)
```

| 真值 (Truth) | 预测红 | 预测白 |
| :--- | :--- | :--- |
| 红 | 474 | 2 |
| 白 | 6 | 478 |

一眼观察混淆矩阵的对角线元素，就已经表明比只有两个预测变量的模型有所改进。

tidymodels 包可以帮助你计算准确率（accuracy）、灵敏度（sensitivity）和特异性（specificity）等指标。与其分别计算这些指标，不如通过创建一个指标集（metric set）来简化流程。

在下方的代码块中，`metric_set()` 命令创建了一个用于计算准确率、灵敏度和特异性的新命令。我们将新命令命名为 MetricWine。

新创建的 MetricWine() 的用法与 `conf_mat()` 命令类似，但它不是创建混淆矩阵，而是同时创建之前通过 `metric_set()` 指定的所有指标。这节省了你的打字工作。

请尝试运行下方的代码块（注意，数据框 DataTest 和拟合后的工作流模型 WFModelWine 已经在后台加载）：

```r
DataTestWithPred=augment(WFModelWine, DataTest)

MetricsWine=metric_set(accuracy, sensitivity, specificity)
MetricsWine(DataTestWithPred, truth=WineColor, estimate=.pred_class)
```

```
## A tibble: 3 x 3
## .metric .estimator .estimate
## <chr> <chr> <dbl>
## 1 accuracy binary 0.992
## 2 sensitivity binary 0.988
## 3 specificity binary 0.996
```

混淆矩阵和上述三个指标确认了，我们达到了近乎完美的预测质量。

尝试将 `metric_set()` 命令中的参数改为不同的指标，看看会发生什么。

从葡萄酒数据集中预测葡萄酒颜色是一项众所周知的简单的任务。因此，下一节将处理一个更现实的问题。我们将：

# 94 k-近邻算法 — 入门

尝试从手写体中识别十个数字（0-9）。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 ◎ 项目：识别手写数字

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10 项目：识别手写数字 95

在本节中，你将开发一个机器学习模型，从手写体中识别数字。这也被称为 OCR（光学字符识别）。

# 4.10.1 图像是如何存储的

在处理近邻模型之前，我们首先需要理解要解决的问题。这就是领域知识（domain knowledge）发挥重要作用的地方。在图像识别的情况下，领域知识涉及对图像的理解。

通常，灰度图像可以以光栅（raster）格式存储。光栅是一个具有两个维度的网格。MNIST 图像存储在 28 行 28 列的网格中。网格中的每个条目（称为像素）识别颜色的亮度。

图 10 展示了手写数字“9”如何存储在图像文件中。图中单元格的背景颜色仅供演示。图像文件仅包含 0 到 255 之间的数字。

在机器学习模型中使用图像存在一个问题。机器学习模型通常要求每个观测都是数据框中的行，而列表示预测变量。如上述，图像存储在二维网格中。

解决方案是将图像的所有行合并成一个长行。在我们的情况下，我们从第一行开始，追加光栅的第二行，追加第三行，依此类推，直到追加第 28 行。由于图像最初有 28 行 28 列，每个图像将转换为一个由 784（28x28）列组成的长。这是通过 MNIST 数据集完成的。每个图像存储在行中。图像 784 个像素中的每一个都存储在 784 列中的。这些列将是 784 个预测变量。结果变量（称为 Label）存储在数据框的第一列中。它包含了图像的数字。

查看表 4.1，它显示了 MNIST 数据框前六张图像的摘录。注意表格没有显示所有 784 个预测变量（像素）。相反，它只显示了六张图像前三个像素和最后两个像素的值。这些像素代表每张图像的左上角和右下角。它们都是 0（黑色），因为数字是用白色笔书写的，相应的像素更接近图像的中心。

