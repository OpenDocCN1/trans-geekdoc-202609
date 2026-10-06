
- `fastai` 既是一个通用的高层 API，也是一个表格数据库。`fastai` 兼容两者，因为它抽象了 PyTorch 的某些复杂性，使其更容易在各种数据类型（包括图像和文本）上构建和训练模型，而且它还具有专门针对表格数据的设施（例如，自动处理数据集中类别特征的基本操作）。

现在我们已经查看了表格数据深度学习技术栈，让我们来看看本章将要研究的技术栈，并应用它们来解决 Airbnb 纽约价格预测问题：

- PyTorch 配合 `fastai`——这是最“传统”的方法，因为 `fastai` 是一个成熟的框架，有数万开发者在使用。根据仓库统计，`fastai` 是最明确支持表格数据的最受欢迎的框架。`fastai` 在学习深度学习和业余爱好者的人群中特别受欢迎。

- PyTorch 配合 TabNet——根据仓库统计，TabNet 是仅次于 `fastai` 的流行的表格数据库。TabNet 是 Google 在其文档（https://mng.bz/av1m）中重点介绍的表格数据库。该技术栈展示了如何使用专门的表格数据库来创建一个在表格数据上训练的模型。

# 304 第 8 章 开始使用表格数据进行深度学习

- Lightning Flash——PyTorch 是一个流行的框架，它抽象了 PyTorch 的复杂性。Lightning Flash 构建在 PyTorch Lightning 之上，提供了一种易创建深度学习应用的方法。它还对表格数据提供了显式支持，因此与其他技术栈相比是一个有趣的比较。

本章接三个部分描述了使用每种技术栈解决 Airbnb 价格预测问题的解决方案。在每个节中，我们将回顾解决方案的代码，并比较该解决方案与我们的基准（第 3 章中的 Keras 解决方案）相比的优缺点。

## 8.2 PyTorch 配合 fastai

现在让我们来看看其中一个工具包：PyTorch/fastai。由于我们考虑的是相同的数据集和问题，我们不会重做一遍。不同工具包之间的解决方案大部分非常相似。在这里，我们将集中于 PyTorch 代码的独特特征。你可以在书籍的代码仓库中找到完整的解决方案：https://mng.bz/gaav。

### 8.2.1 回顾 fastai 的关键方面

现在让我们深入研究 `fastai` 对我们 Airbnb 价格预测问题的解决方案。首先，`fastai` 有有一套独特的导入语句，如 8.2 所示，这是在 Jupyter notebook 中使用 `fastai` 所需的库。

列表 8.2 fastai 的导入语句

| 命令 | 说明 |
| :--- | :--- |
| `pip install -U fastbook` | 安装在 Jupyter notebook 中使用 `fastai` 需要的库 |
| `import fastbook` |  |
| `from fastbook import *` | 导入使用 `fastai` 需要的库 |
| `from fastai.tabular import *` | 导入处理表格数据集所需的库 |

在如 8.2 所示导入了这些库后，你就拥有了在 Jupyter notebook 中运行 `fastai` 应用所需的全部库。接下来，`fastai` 需要定义表格数据集的特征，包括包含模型目标的列（在 `fastai` 中称为因变量）以及类别列和连续列的列表，如下所示。

列表 8.3 fastai 的数据集定义

| 代码 | 说明 |
| :--- | :--- |
| `dep_var = 'target'` | 指定数据集中包含目标的列，即模型正在预测的值 |
| `cat = ['neighbour_group', 'neighbour', 'room_type']` | 指定数据集中属于类型的列 |

# PyTorch 配合 fastai 305

```python
cont = ['minimum_nights', 'number_of_reviews', 'reviews_per_month', 'calculated_listings_count']
```

> 指定数据集中连续的列

当我们为该模型定义 `TabularDoaders`（https://mng.bz/5gw0）对象时，将使用 8.3 中定义的值。`TabularDoaders` 对象封装了数据集中的样本（包括标签），以便于处理数据集。接下来，我们需要确保目标列包含字符串：

```python
merged_data['target'] = merged_data.target.astype(str)
```

如果不这样做，将会遇到问题。为了尝试一下，请注释掉该语句并运行 `fastai`。如图 8.4 所示，训练会产生奇怪的结果。

| 迭代 (epoch) | 训练损失 (train_loss) | 验证损失 (valid_loss) | 准确率 (accuracy) |
| :--- | :--- | :--- | :--- |
| 0 | 0.140194 | 0.13597 | 0.6450 |
| 1 | 0.137211 | 0.14075 | 0.6450 |
| 2 | 0.127553 | 0.13714 | 0.6450 |

![](img/89cc476fa39fc54bd34e78d9164_327_0)

8.4 显示了每个迭代的训练损失、验证损失。如图 8.4 所示，验证损失比第 3 章中看到的 Keras 解决方案显著降低。由于目标列是浮点数，`fastai` 会出现问题。`fastai` 试图解决一个分类问题（预测一个连续值），而不是我们预想的分类问题。

```python
learn.loss_func
FlattenLoss()
```

> 用于 `fastai` 训练的损失函数

```python
learn.loss_func
MSELoss()
```

> 用于 `fastai` 训练的损失函数

我们希望 8.4 中的目标列是 "0" 或 "1" 来指示房源价格高于或低于中位数。

如图 8.5 所示，`dls.valid.show_batch()` 的输出显示目标列是浮点数而不是 "0" 或 "1"。

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

# 使用 fastai 的 PyTorch

| 计算的房东列表 | 365天可用性（纬度，经度） | 目标 |
|---|---|---|
| 6 | 365 (40.64749, -73.97237) | 0 |
| 2 | 355 (40.75362, -73.98377) | 1 |
| 1 | 365 (40.80902, -73.94199) | 0 |
| 1 | 194 (40.68514, -73.95976) | 0 |
| 1 | 0 (40.79851, -73.94399) | 0 |

图 8.6 当目标列显式转换为字符串值时的样本批值

现在我们已经知道了为什么将目标列中的值转换为字符串至关重要，让我们查看剩余代码以创建一个训练好的 `fastai` 模型。列表 8.5 显示了定义 `TabularDataLoaders` 对象的代码块。该对象是对 PyTorch `DataLoader`（https://mng.bz/6eDe）对象的表格数据封装器，后者是数据集中样本和标签的可迭代封装。

# 列表 8.5 定义 TabularDataLoaders 对象

| | 定义了在实现的流水线中应用于数据集的转换程序 | 指定 TabularDataLoaders 对象基于合并后的 merged_data dataframe |
|---|---|---|
| | 为 path 对象设置了占位符值 | 指定了配合 TabularDataLoaders 应用的转换列表 |

```
path = '.'
procs = [FillMissing, Categorify, Normalize]
dls = TabularDataLoaders.from_df(dtrain,
path,
procs=procs,
cat_names=cat_names, # 指定分类特征
cont_names=cont_names, # 指定连续特征
y_names=dep_var, # 指定目标特征
valid_idx=list(range((merged_data.shape[0]-100000), merged_data.shape[0])), # 指定训练过程中用于验证的数据集子集
bs=32 # 指定批大小
```

# 第 8 章 使用表格数据开始深度学习之旅

我们将使用在 8.5 中定义的 `TabularDataLoaders` 对象来定义 8.7 所示的 `fastai` 模型。

`fastai` 的特征之一提供了一系列便利功能，使其易于通过训练各个阶段检查数据集。后续列表中所示 `show_batch()` 语句就是这种便利函数的示例。

# 列表 8.6 显示一组训练数据的语句

```
dls.valid.show_batch()
```

在 8.6 所示的语句让我们能够很容易地看到在经过 `TabularDataLoaders` 定义中 `procs` 参数指定的转换后，用于训练模型的数据是什么样子的。图 8.7 显示了该语句的输出。

| 社区分组 | 社区 | 房型 |
|---|---|---|
| Manhattan | Hell's Kitchen | 私人房间 |
| Manhattan | Hell's Kitchen | 私人房间 |
| Manhattan | Hell's Kitchen | 私人房间 |
| Brooklyn | Bushwick | 私人房间 |
| Brooklyn | Williamsburg | 私人房间 |

| 最少晚数 | 评论数 | 每月评论数 | 计算的房东列表数 | 目标 |
|---|---|---|---|---|
| 1.000000 | 18.000000 | 2.490000e+00 | 0.300001 | 1 |
| 1.000000 | 16.000000 | 2.222000e+00 | 0.300001 | 1 |
| 1.000000 | 13.000000 | 1.820000e+00 | 0.300001 | 1 |
| 15.000000 | 0.00001 | 1.455204e-08 | 2.000000 | 0 |
| 19.999999 | 1.999999 | 4.200000e-01 | 1.000000 | 0 |

图 8.7 show_batch() 语句的输出

现在我们已经指定了用于训练模型的数据，是时候定义并训练模型了。

# 8.7 定义并拟合 fastai 模型

> 使用 tabularDataLoaders 对象 dls 将模型定义为表格学习器对象，并使用 accuracy 作为训练的性能衡量标准

```
learn = tabular(dls, metrics=accuracy)
learn.fit_one_cycle(3)
```

注意，列表 8.7 中的定义和拟合模型语句比我们在第 3 章中看到的 Keras 模型定义和拟合语句要简单得多。从这个意义上说，`fastai` 解决方案解决了我们在第 3 章中看到的 XGBoost 解决方案。

图 8.8 显示了拟合语句的输出。对于每个轮次（epoch），都列出了训练损失、验证损失和准确率。如果我们将图 8.4 所示的训练结果（目标列未转换为字符串时）与图 8.8 所示的训练结果（目标列已转换为字符串时）进行比较，很明显看出，当 `fastai` 将问题视为分类问题而非回归问题时，我们得到了更好的结果。

| epoch | train_loss | valid_loss | accuracy | time |
|---|---|---|---|---|
| 0 | 0.434672 | 0.407458 | 0.81790 | 00:17 |
| 1 | 0.424458 | 0.406396 | 0.81490 | 00:11 |
| 2 | 0.385092 | 0.405317 | 0.81710 | 00:10 |

![img/def89cc47fa39f4c54bd34e78d91674_331_0.png](使用 tabularDataLoaders 对象 dls 将模型定义为表格学习器对象，并使用 accuracy 作为训练的性能衡量标准)

在继续之前，我们花时间讨论一下训练损失、验证损失和准确率。如果我们将图 8.4 所示的训练结果（目标列未转换为字符串时）与图 8.8 所示的训练结果（目标列已转换为字符串时）进行比较，很明显看出，当 `fastai` 将问题视为分类问题而非回归问题时，我们得到了更好的结果。

# 第 8 章 使用表格数据开始深度学习

表 8.1 Keras 和 fastai 解决方案的优缺点总结

| Keras | fastai |
|---|---|
| 模型细节透明。使用该框架的社区很大，意味着很容易找到常见问题的解决方案 | 框架对表格模型有显式支持，这意味着代码更紧凑。框架自动定义流水线（pipeline）。框架包含了方便函数，可以轻松执行数据集。框架所做的假设可能会导致难以调试的棘手问题。用户社区比 Keras 社区小，在部署生产应用方面的参与度也较低，这意味着可能更难找到问题的解决方案。 |
| 内置不支持表格数据，这意味着我们需要定义自定义代码来定义模型的流水线和层。 |  |

让我们来看一下 Keras 解决方案和 `fastai` 解决方案之间的最后一点比较：底层的低级深度学习框架。对于 Keras，底层框架是 TensorFlow，而 `fastai` 是构建在 PyTorch 之上的。这这意味着我们现在已经通过两个主要的深度学习框架审查了针对表格数据问题的深度学习解决方案。

Keras 和 `fastai` 的相似点之一是它们都是通用的高层深度学习 API。我们已经看到它们都可以用于表格数据问题，但它们也被设计用于处理各种数据类型，而不仅仅是表格数据。在下一节中，我们将查看一个专门为表格数据设计的深度学习库：TabNet。我们将检查一个使用 TabNet 解决 Airbnb 纽约问题的解决方案，并将其与 Keras 解决方案进行对比。

## 8.3 结合 TabNet 的 PyTorch

我们到为止考虑的工具都是设计为通用深度学习库的。现在我们将使用一个专门的表格数据库：TabNet。同样，我们将跳过对问题的介绍，将讨论集中在解决方案与之前示例不同的部分。你可以在 https://mng.bz/ok1Lz 找到该解决方案的代码。

## 8.3.1 TabNet 解决方案的关键方面

在本节中，我们将介绍构成 Airbnb 纽约房源列表价格预测问题的 TabNet 解决方案的代码关键部分。

TabNet 解决方案需要一组导入语句，如下列表所示。

# 列表 8.10 TabNet 的导入语句

![](img/def89cc476fa39f4c54bd34e78d91674_335_0.png)

```
# pip install pytorch-tabnet
import torch
from pytorch_tabnet.tab_model import TabNetClassifier
```

> 导入 TabNetClassifier 库。我们将使用此库来定义模型。

注意，与 `fastai` 的导入语句不同，列表 8.10 中的 TabNet 语句包含了显式导入 PyTorch 库的语句。

与 `fastai` 解决方案不同（它没有定义流水线的任何显式代码，并且有独特的代码来定义数据集），TabNet 解决方案与 Keras 和 XGBoost 解决方案使用了相同的代码，包括流水线的定义。在流水线定义之后，TabNet 解决方案使用与 XGBoost 类似的代码，将来自流水线的 NumPy 数组列表转换为 NumPy 列表数组，如下列表所示。

# 列表 8.11 生成 NumPy 列表数组的语句

```
list_of_train = []
list_of_test = []
list_of_valid = []
for i in range(0,7):
    list_of_train.append(X_train[i].tolist())
    list_of_valid.append(X_valid[i].tolist())
    list_of_test.append(X_test[i].tolist())
X_train = np.array(list_of_train, T)
X_valid = np.array(list_of_valid, T)
X_test = np.array(list_of_test, T)
y_train = dtrain.target
y_valid = dval.target
y_test = test.target
```
