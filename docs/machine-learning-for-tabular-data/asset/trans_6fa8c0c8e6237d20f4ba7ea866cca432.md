

# 表格数据深度学习技术栈 303

API。尽管如此，还有两个高层 API 抽象了 PyTorch 的某些方面。fastai 专为为那些来自其他领域的人士设计的，他们希望使用深度学习来解决自己所在领域的问题，其核心理念是仅需几行代码即可定义、训练和运行深度学习模型。相比之下，Lightning 抽象了 PyTorch 的单一方面——训练循环（Lightning）。构建在 Lightning 之上的 Lightning Flash，根据其文档描述，是“一个用于快速原型设计、基准测试、微调和解决深度学习问题的高层深度学习框架”。虽然 fastai 和 Lightning 都有忠实的用户社区，但它们中没有哪一个在 PyTorch 世界中吸引到过像 Keras 在 TensorFlow 世界中那样的流行程度。

- 表格数据库——低层框架和高层 API 为通用的深度学习提供了一个环境。深度学习库提供了专门处理表格数据的能力。正如我们在第 3 章中针对 Airbnb 纽约预测问题的深度学习解决方案所示的那样，你不需要使用表格数据库就可以对表格数据进行深度学习。

关于表格数据库，有两个细节需要注意：

- 表格数据库可能同时支持 TensorFlow 和 PyTorch。TabNet 是一个同时支持两种低层深度学习框架的库示例。
- fastai 既是一个通用的高层 API，也是一个表格数据库。fastai 兼容两者，因为它抽象了 PyTorch 的某些复杂性，使其更容易在各种数据类型（包括图像和文本）上构建和训练模型，而且它还具有专门针对表格数据的设施（例如，自动处理数据集中类别特征的基本操作）。

现在我们已经查看了表格数据深度学习技术栈，让我们来看看本章将要研究的技术栈，并应用它们来解决 Airbnb 纽约价格预测问题：

- PyTorch 配合 fastai——这是最“传统”的方法，因为 fastai 是一个成熟的框架，有数万开发者在使用。根据仓库统计，fastai 是最明确支持表格数据的最受欢迎的框架。fastai 在学习深度学习和业余爱好者的人群中特别受欢迎。
- PyTorch 配合 TabNet——根据仓库统计，TabNet 是仅次于 fastai 的流行的表格数据库。TabNet 是 Google 在其文档（https://mng.bz/av1m）中重点介绍的表格数据库。该技术栈展示了如何使用专门的表格数据库来创建一个在表格数据上训练的模型。

# 304 第 8 章 开始使用表格数据进行深度学习

- Lightning Flash——PyTorch 是一个流行的框架，它抽象了 PyTorch 的复杂性。Lightning Flash 构建在 PyTorch Lightning 之上，提供了一种易创建深度学习应用的方法。它还对表格数据提供了显式支持，因此与其他技术栈相比是一个有趣的比较。

本章接三个部分描述了使用每种技术栈解决 Airbnb 价格预测问题的解决方案。在每个节中，我们将回顾解决方案的代码，并比较该解决方案与我们的基准（第 3 章中的 Keras 解决方案）相比的优缺点。

## 8.2 PyTorch 配合 fastai

现在让我们来看看其中一个工具包：PyTorch/fastai。由于我们考虑的是相同的数据集和问题，我们不会重做一遍。不同工具包之间的解决方案大部分非常相似。在这里，我们将集中于 PyTorch 代码的独特特征。你可以在书籍的代码仓库中找到完整的解决方案：https://mng.bz/gaav。

### 8.2.1 回顾 fastai 的关键方面

现在让我们深入研究 fastai 对我们 Airbnb 价格预测问题的解决方案。首先，fastai 有有一套独特的导入语句，如 8.2 所示，这是在 Jupyter notebook 中使用 fastai 所需的库。

列表 8.2 fastai 的导入语句

| 命令 | 说明 |
| :--- | :--- |
| pip install -U fastbook | 安装在 Jupyter notebook 中使用 fastai 需要的库 |
| import fastbook | |
| from fastbook import * | 导入使用 fastai 需要的库 |
| from fastai.tabular import * | 导入处理表格数据集所需的库 |

在如 8.2 所示导入了这些库后，你就拥有了在 Jupyter notebook 中运行 fastai 应用所需的全部库。接下来，fastai 需要定义表格数据集的特征，包括包含模型目标的列（在 fastai 中称为因变量）以及类别列和连续列的列表，如下所示。

列表 8.3 fastai 的数据集定义

| 代码 | 说明 |
| :--- | :--- |
| dep_var = 'target' | 指定数据集中包含目标的列，即模型正在预测的值 |
| cat = ['neighbour_group', 'neighbour', 'room_type'] | 指定数据集中属于类型的列 |

# PyTorch 配合 fastai 305

```python
cont = ['minimum_nights', 'number_of_reviews', 'reviews_per_month', 'calculated_listings_count']
```
> 指定数据集中连续的列

当我们为该模型定义 TabularDoaders（https://mng.bz/5gw0）对象时，将使用 8.3 中定义的值。TabularDoaders 对象封装了数据集中的样本（包括标签），以便于处理数据集。接下来，我们需要确保目标列包含字符串：

```python
merged_data['target'] = merged_data.target.astype(str)
```

如果不这样做，将会遇到问题。为了尝试一下，请注释掉该语句并运行 fastai。如图 8.4 所示，训练会产生奇怪的结果。

| 迭代 (epoch) | 训练损失 (train_loss) | 验证损失 (valid_loss) | 准确率 (accuracy) |
| :--- | :--- | :--- | :--- |
| 0 | 0.140194 | 0.13597 | 0.6450 |
| 1 | 0.137211 | 0.14075 | 0.6450 |
| 2 | 0.127553 | 0.13714 | 0.6450 |

![](img/89cc476fa39fc54bd34e78d9164_327_0)

8.4 显示了每个迭代的训练损失、验证损失。如图 8.4 所示，验证损失比第 3 章中看到的 Keras 解决方案显著降低。由于目标列是浮点数，fastai 会出现问题。fastai 试图解决一个分类问题（预测一个连续值），而不是我们预想的分类问题。

```python
learn.loss_func
FlattenLoss()
```
> 用于 fastai 训练的损失函数

```python
learn.loss_func
MSELoss()
```
> 用于 fastai 训练的损失函数

我们希望 8.4 中的目标列是 "0" 或 "1" 来指示房源价格高于或低于中位数。

如图 8.5 所示，dls.valid.show_batch() 的输出显示目标列是浮点数而不是 "0" 或 "1"。

| 社区组 (neighbour_group) | 社区 (neighbour) |
| :--- | :--- |
| 0 | Manhattan | Hell's Kitchen |
| 1 | Manhattan | Hell's Kitchen |
| 2 | Manhattan | Bushwick |
| 3 | Brooklyn | Bushwick |
| 4 | Brooklyn | Williamsburg |

类别特征

| 最小晚数 (minimum_nights) | 评论数 (number_of_reviews) | 每月评论数 (reviews_per_month) | 计算房源数量 (calculated_listings_count) | 目标 (target) |
| :--- | :--- | :--- | :--- | :--- |
| 1.000000 | 18.00000 | 2.490000e+00 | 30.000001 | 1.0 |
| 1.000000 | 16.00000 | 2.222000e+00 | 30.000001 | 1.0 |
| 1.000000 | 13.00000 | 1.822000e+00 | 30.000001 | 1.0 |
| 15.000000 | 0.000001 | 1.455204e-08 | 2.000000 | 0.0 |
| 19.999999 | 1.999999 | 4.200000e-01 | 1.000000 | 0.0 |

图 8.5 目标值未显式转换为字符串时的样本批值

