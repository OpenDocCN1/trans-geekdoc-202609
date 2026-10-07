

## 地面真（Ground-truth）将让你自由

在我们开始构建一个完整的物体检测器之前，让我们从一个更简单的任务开始。你首先将扩展上一章中基于 MobileNet 的分类模型，因此除了常规的类别预测外，它还会输出单个边界框（bounding box），尝试定位图像中最重要的物体所在的位置。

只需预测一个边界框，有多难呢？（答案：实际上比你想象的要容易。）

首先，我们应该重新回顾一下数据集。

尽管这个新的神经网络现在会进行不同类型的预测，但训练过程仍然是相同的：你提供一个包含图像和目标的数据集。你还提供一个合适的损失函数，通过将模型预测与目标进行比较来计算预测的误差有多大。然后，你使用像 Adam 这样的随机梯度下降优化器来寻找模型可学习参数的值，使损失最小化。这些我们都做过了。

无论你的神经网络执行什么任务，无论是预测类别还是边界框——或者是天气、股票价格或任何其他东西——训练过程始终是相同的。然而，每个任务都需要特定种类的训练数据。对于物体检测任务，训练数据必须包含边界框信息。

之前，目标只是图像的类别名称，但现在它们还必须包含所谓的“地面真”边界框，这些边界框会告诉你物体在图像中的位置。没有这些边界标注，损失函数将无法计算模型的误差有多大，训练模型预测边界框是不可能的。

我们已经以一组 CSV 形式为零食数据集（snacks dataset）提供了边界框标注。为了感受它们是如何工作的，现在将仔细查看这些标注。创建一个新的 Jupyter notebook，或者直接跟随本章资源中的 **final/Localization.ipynb**。

## 机器学习

## 第 9 章：超越分类

> 注意：与之前一样，你将使用 kerasenv Python 环境。使用 Anaconda Navigator 或使用 `conda create` 必要的命令来设置此环境。如果你在之前的章节中还没有它，请双击 starter/snacks-download-link.webloc 下载零食数据集并解压文件。它包含了你将用于训练模型的图像，包括地面真标注。

在 Python 中处理 CSV 文件最简单的方法是使用 Pandas 库。按照惯例，首先导入包——NumPy、Matplotlib 和 Pandas——并定义下载的数据集的路径：

```python
import os, sys
import numpy as np
import pandas as pd

%matplotlib inline
import matplotlib.pyplot as plt

data_dir = "snacks"
train_dir = os.path.join(data_dir, "train")
val_dir = os.path.join(data_dir, "val")
test_dir = os.path.join(data_dir, "test")
```

然后将 annotations-train.csv 文件加载到新的 Pandas DataFrame 对象：

```python
path = os.path.join(data_dir, "annotations-train.csv")
train_annotations = pd.read_csv(path)
train_annotations.head()
```

新的 dataframe `train_annotations` 包含的是与 CSV 文件完全相同的数据。Pandas 提供了许多函数来操作这些数据。这就像在 Python 内部使用 SQL 和 Excel 的功能，如果你喜欢这类操作，那就太棒了。

## 第 9 章：超越分类

`train_annotations.head()` 命令 own输出该 dataframe 的“头部”，即前五行：

| image_id | x_min | x_max | y_min | y_max | class_name | folder |
|---|---|---|---|---|---|---|
| 0 | 009218ad3ab2010 | 0.19260 | 0.72981 | 0.12760 | 0.662219 | cake | cake |
| 1 | 009218ad3ab2010 | 0.80237 | 1.00000 | 0.102585 | 0.40538 | ice cream | cake |
| 2 | 009218ad3ab2010 | 0.81484 | 0.97067 | 0.12168 | 0.35738 | ice cream | cake |
| 3 | 009218ad3ab2010 | 0.81484 | 0.97067 | 0.12168 | 0.35738 | muffin | muffin |
| 4 | 009218ad3ab2010 | 0.81484 | 0.97067 | 0.12168 | 0.35738 | muffin | muffin |

新的 dataframe `train_annotations` 包含的是与 CSV 文件完全相同的数据。Pandas 提供了许多函数来操作这些数据。这就像在 Python 内部使用 SQL 和 Excel 的功能，如果你喜欢这类操作，那就太棒了。

`train_annotations.head()` 命令输出该 dataframe 的“头部”，即前五行：

| image_id | x_min | x_max | y_min | y_max | class_name | folder |
|---|---|---|---|---|---|---|
| 0 | 009218ad3ab2010 | 0.19260 | 0.72981 | 0.12760 | 0.662219 | cake | cake |
| 1 | 009218ad3ab2010 | 0.80237 | 1.00000 | 0.102585 | 0.40538 | ice cream | cake |
| 2 | 009218ad3ab2010 | 0.81484 | 0.97067 | 0.12168 | 0.35738 | ice cream | cake |
| 3 | 009218ad3ab2010 | 0.81484 | 0.97067 | 0.12168 | 0.35738 | muffin | muffin |
| 4 | 009218ad3ab2010 | 0.81484 | 0.97067 | 0.12168 | 0.35738 | muffin | muffin |

新的 dataframe `train_annotations` 包含的是与 CSV 文件完全相同的数据。Pandas 提供了许多函数来操作这些数据。这就像在 Python 内部使用 SQL 和 Excel 的功能，如果你喜欢这类操作，那就太棒了。

`train_annotations.head()` 命令输出该 dataframe 的“头部”，即前五行：

| image_id | x_min | x_max | y_min | y_max | class_name | folder |
|---|---|---|---|---|---|---|
| 0 | 009218ad3ab2010 | 0.19260 | 0.72981 | 0.12760 | 0.662219 | cake | cake |
| 1 | 009218ad3ab2010 | 0.80237 | 1.00000 | 0.102585 | 0.40538 | ice cream | cake |
| 2 | 009218ad3ab2010 | 0.81484 | 0.97067 | 0.12168 | 0.35738 | ice cream | cake |
| 3 | 009218ad3ab2010 | 0.81484 | 0.97067 | 0.12168 | 0.35738 | muffin | muffin |
| 4 | 009218ad3ab2010 | 0.81484 | 0.97067 | 0.12168 | 0.35738 | muffin | muffin |

新的 dataframe `train_annotations` 包含的是与 CSV 文件完全相同的数据。Pandas 提供了许多函数来操作这些数据。这就像在 Python 内部使用 SQL 和 Excel 的功能，如果你喜欢这类操作，那就太棒了。

`train_annotations.head()` 命令输出该 dataframe 的“头部”，即前五行：

| image_id | x_min | x_max | y_min | y_max | class_name | folder |
|---|---|---|---|---|---|---|
| 0 | 009218ad3ab2010 | 0.19260 | 0.72981 | 0.12760 | 0.662219 | cake | cake |
| 1 | 009218ad3ab2010 | 0.80237 | 1.00000 | 0.102585 | 0.40538 | ice cream | cake |
| 2 | 009218ad3ab2010 | 0.81484 | 0.97067 | 0.12168 | 0.35738 | ice cream | cake |
| 3 | 009218ad3ab2010 | 0.81484 | 0.97067 | 0.12168 | 0.35738 | muffin | muffin |
| 4 | 009218ad3ab2010 | 0.81484 | 0.97067 | 0.12168 | 0.35738 | muffin | muffin |

