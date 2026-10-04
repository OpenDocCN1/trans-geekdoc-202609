

# 预测纽约市 Airbnb 价格

## 3.1.2 代码介绍

现在我们已经介绍了纽约市 Airbnb 数据集，让我们来看看解决方案的实现实现。在本节中，我们不会深入探讨代码的所有细节，但了解各个部分是如何组合在一起的至关重要。

图 3.3 总结了构成两个解决方案的文件。

![](img/def89cc476fa39f4c54bd34e78d91674_87_0.png)

图 3.3 构成 Airbnb NYC 解决方案的文件

以下是关于构成解决方案的文件的更多详细信息：

- 输入 CSV (https://mg.bz/avJ7)。
- 数据清洗笔记本 (https://mg.bz/gawV)。请注意，虽然 XGBoost 和 Keras 版本的代码使用同一个数据清洗笔记本，但 XGBoost 具有内置功能（例如处理缺失值），这意味着仅限 XGBoost 版本的清洗过程可能比通用版本更简单。
- 清洗配置文件 (https://mg.bz/ey7Q)。
- XGBoost 训练配置文件 (https://mg.bz/pKOz)。
- Keras 训练配置文件 (https://mg.bz/vkPr)。
- XGBoost 训练笔记本 (https://mg.bz/YDGA)。在我们选择的梯度提升解决方案中，我们选择 XGBoost 是因为它非常流行，而且如果我们遇到任何问题，有很多关于 XGBoost 的指导。
- Keras 训练笔记本 (https://mg.bz/JVwP)。我们选择 Keras 作为代表性的深度学习方法，是因为与 PyTorch 或基于 PyTorch 的 fastai 等替代方案不同，Keras 与原生 TensorFlow 一样在业务应用中用得最广泛。在“比较梯度提升方法与深度学习的研究成功率”章节中，我们将 Keras 作为介绍的表格深度学习库之一，是因为 Keras 的使用范围比其中任何一个库都更广泛，且其 API 与 XGBoost API 的比较，比将专门为表格数据设计的深度学习库与 XGBoost 的通用功能进行比较更具“可比性”。

为了方便起见，XGBoost 和 Keras 解决方案被分层存储在两个独立的文件夹中，但两者的大部分代码是通用的：

- 你可以在 https://mng.bz/GeEO 找到 XGBoost 解决方案的代码。
- 你可以在 https://mng.bz/rZAQ 找到 Keras 解决方案的代码。

这两个仓库之间的区别仅限于训练笔记本和训练配置。

## 3.1.3 使用 Keras 的深度学习解决方案

在深入研究 Airbnb 数据集的细节和解决方案中使用的代码之前，让我们将 Keras 解决方案放在其软件栈的上下。图 3.4 显示了用于 Airbnb 价格预测问题的 Keras 解决方案栈。

| Airbnb NYC 解决方案 |
| :--- | :--- |
| 底层框架 | TensorFlow |
| 高级 API | Keras |
| 自定义代码 | get_model() 函数，用于定义模型中每个列类型的 Keras 层 |

> 图 3.4 图 3.4 所示的 Airbnb NYC 解决方案的栈。

在第 8 章中，我们将详细介绍所示所示的栈层。目前，我们可以观察到 Keras 是我们用来实现本章将检查的 Airbnb 问题深度学习解决方案的高级深度学习 API。有两个底层深度学习框架，而我们在本章将检查的学习解决方案取决于 TensorFlow 底层框架，因为 Keras 正是在其之上构建的。

## 3.1.4 特征训练

两个解决方案的目标都是预测给定的 Airbnb 房源价格高于或低于输入数据集中的平均价格。为了实现这一点，两个模型都在同一组特征上进行训练。用于训练模型的特征子集定义在训练文件中：https://mng.bz/OE。以下是指定训练模型的配置文件部分：

```
categorical: # 类别列
- 'neighbour_group'
- 'neighbourhood'
- 'room_type'
continuous: # 连续列
- 'minimum_nights'
- 'number_of_reviews'
- 'reviews_per_month'
```

配置文件还包含被排除的特征列表：

```
excluded: # 不使用的列
- 'price'
- 'id'
- 'latitude'
- 'longitude'
- 'host_id'
- 'last_review'
- 'name'
- 'host'
```

这些列不使用的原因如下：

- price 是我们要预测的目标变量。
- id 是唯一标识符，不是预测特征。
- latitude 和 longitude 通过特定方法处理或在模型中被排除。
- host_id 是唯一标识符。
- last_review 和 name 是需要更复杂处理的数据。
- host 在此模型中未使用。

## 3.1.5 比较梯度提升与深度学习

正如我们之前提到的，这两个解决方案在几个处有所不同。图 3.5 显示了突出显示差异的文件结构。

![](img/def89cc476fa39f4c54bd34e78d91674_90_0.png)

图 3.5 Airbnb 房源文件

如果解决方案仅区别于这些文件，我们如何利用这个示例来对比 XGBoost 和深度学习的简单性？表 3.1 比较了几个领域的代码复杂度。

| 复杂度维度 | XGBoost | Keras 深度学习 |
| :--- | :--- | :--- |
| 数据准备 | 需要代码将数组列表转换为列表的 numpy  | 无——数据准备是针对 Keras 解决方案设计的 |
| 模型定义 | 单条语句，符合 Scikit-learn 模式 | 需要代码块来定义层，且每种类型（连续、类别、文本）都有独特的层集 |
| 模型训练 | 单条语句，符合 Scikit-learn 模式 | 需要代码块来允许训练过程回调，以避免过拟合并确保过程输出性能最佳训练模型 |
| 模型保存 | 单条语句，符合 Scikit-learn 模式 | 包含在模型保存回调中 |
| 模型加载 | 代码块——需要安装最新版本的 XGBoost，否则加载将失败 | 单条语句 |

