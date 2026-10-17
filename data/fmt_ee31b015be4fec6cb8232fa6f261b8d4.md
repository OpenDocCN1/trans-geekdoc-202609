
| `versionName` || `string` || 用于预测的模型版本 |
| `uri` || `string` || 模型的云存储位置 |

要执行预测作业，你需要提供一个 `SavedModel` 和包含输入数据的文件。你可以通过设置前两个字段 `dataFormat` 和 `inputPaths` 来标识输入数据的格式和位置。要指定数据的格式，你需要将 `dataFormat` 设置为 `TEXT`、`JSON`、`TF_RECORD`、`TF_RECORD_GZIP` 或 `DATA_FORMAT_UNSPECIFIED`。

最后三个条目构成一个联合，称为 `model_version`，因此在 `PredictionInput` 中只能设置其中一个。你可以通过将 `modelName` 设置为以下格式的字符串来标识你的模型：

```
projects/<var>[YOUR_PROJECT]</var>/models/<var>[YOUR_MODEL]</var>
```

如果使用 `versionName` 标识你的模型，你需要提供一个略有不同的字符串：

```
projects/<var>[YOUR_PROJECT]</var>/models/<var>YOUR_MODEL/versions/<var>[YOUR_VERSION]</var>
```

如果云存储桶中只包含一个模型，你只需将 `uri` 字段设置为桶的位置即可。

### Obtaining the prediction output

你可以通过将文件的 `predictionOutput` 字段设置为 `PredictionOutput` 来配置预测作业的输出。表 13-16 列出了可设置的字段。

TABLE 13-16 PredictionOutput Fields

| **Field** || **Type** || **Description** |
| --- | --- | --- |
| `outputPath` || `string` || 用于存储预测输出的云存储位置 |
| --- | --- | --- |
| `predictionCount` || `string` || 生成的预测数量 |
| `errorCount` || `string` || 产生错误的实例数量 |
| `nodeHours` || `number` || 预测作业消耗的节点小时数 |

这些字段易于理解和使用。`nodeHours` 字段提供了作业使用的节点数与完成作业所需小时数的乘积。

## Part 4

### The Part of Tens

IN THIS PART …

探索 TensorFlow 框架提供的十个最重要的 Python 类。

揭示在机器学习应用中训练神经网络时应遵循的有用指南。

#### Chapter 14

#### The Ten Most Important Classes

IN THIS CHAPTER

![check](img/check.png)**Exploring fundamental classes of the TensorFlow API**

![check](img/check.png)**Storing tensors and operations in graphs**

![check](img/check.png)**Using estimators and iterators**

TensorFlow API 庞大，包含数百个包和数千个模块。鉴于其规模，新手可能很难知道应重点研究哪些类。为了解决这种困惑，我挑选了 TensorFlow 的十个最重要的类，并解释该类实现的功能以及它为何如此重要。

##### Tensor

张量在 TensorFlow 开发中发挥着核心作用，是存储和操作数据的首要对象。优化器只接受包含在张量中的数据，图像处理函数要求图像以张量的形式提供。所有神经网络层，从密集层到 dropout 层，都接受张量作为输入并返回张量作为输出。

张量充当 N 维数组，其中 N 可以为零或更多。张量的维度数称为张量的 *rank*，每个维度的大小称为张量的 *shape*。例如，3-x-5 矩阵的形状为 `[3, 5]`，而大小为 200 x 200 的 RGB 图像将由形状为 `[200, 200, 3]` 的张量表示。

TensorFlow 提供了数百个用于创建、转换和处理张量的函数（参见 Chapter 3）。你可以通过调用 `tf.constant` 创建具有常量值的张量，也可以通过调用 `tf.random_normal` 或 `tf.random_uniform` 创建具有随机值的张量。你可以用 `tf.reshape` 重塑张量，并用 `tf.slice` 提取张量的部分。

##### Operation

当 Python 解释器到达对张量进行操作的函数时，它不会立即执行该操作。相反，它会创建 `Operation` 类的实例来表示该操作。每个 `Operation` 都有一个名为 `inputs` 的属性，包含其输入张量，以及一个名为 `outputs` 的属性，包含其输出张量。

每个 `Operation` 都有一个名为 `type` 的属性，通常设置为创建它的函数。例如，如果你调用 `tf.add`，相应的操作将把其 `type` 设置为 `add`。

其他数学运算包括 `tf.divide`、`tf.round` 和 `tf.sqrt`。TensorFlow 还支持传统的矩阵运算，包括 `tf.matmul`、`tf.diag` 和 `tf.matrix_solve`。

##### Graph

TensorFlow 为应用程序中的每个张量创建一个 `Tensor` 实例，为涉及张量的每个操作创建一个 `Operation`。它将这些 `Tensor` 和 `Operation` 存储在称为 `Graph` 的数据结构中。一次只能有一个 `Graph` 处于活动状态，你可以通过调用 `as_default` 使新的 `Graph` 处于活动状态。

`Graph` 类提供了一系列用于访问图中包含的数据的方法。你可以使用 `get_tensor_by_name` 访问特定的张量，或通过调用 `get_operations` 访问图中的所有操作。

每个 `Graph` 将数据存储在一系列称为 `collections` 的容器中。每个集合都可以通过特定的键访问，而 `get_all_collection_keys` 提供了所有键的完整列表。例如，图将其全局变量存储在键为 `tf.GraphKeys.GLOBAL_VARIABLES` 的集合中。

##### Session

在你向图添加张量和操作后，可以通过创建并运行会话来执行图的操作。你可以通过调用 `tf.Session` 创建一个会话，然后通过调用其 `run` 方法启动会话。

`run` 方法的第一个参数告诉会话要执行何种处理。如果该参数包含张量，会话将计算每个张量的元素并以 NumPy 数组的形式返回元素。如果该参数包含 `Operation`，会话将执行每个操作并返回适当的结果。

如果 StackOverflow 上的问题可以说明什么，那么 `run` 的 `feed_dict` 会让许多开发者感到困惑。该参数接受一个字典，将值与图中的张量（通常是 `placeholders`）关联起来。但该字典的值不能是张量。因此，在执行会话之前，使用 NumPy 数组存储和处理输入数据通常是一个好主意。

##### Variable

变量在许多方面类似于张量。它们将值存储在 N 维数组中，并且可以使用常规 TensorFlow 操作进行操作。但在训练操作期间，应用程序依赖变量来存储模型的状态。例如，如果一个应用程序由神经网络组成，网络的权重和偏置将作为变量存储。

另一个区别是变量需要与张量不同的方法集。例如，在创建 `Variable` 后，你需要通过在会话中运行特殊操作来初始化其值。如果你的应用程序有许多变量，你可以通过调用 `tf.global_variables_initializer` 获得一个合并的初始化操作。

在低层面上，训练的目标是将应用程序的变量设置为使模型与观测数据一致的值。这些变量至关重要，因此最好使用 `Saver` 将它们存储到检查点文件中。第 5 章 解释了如何在 TensorFlow 应用程序中创建、初始化和保存变量。

##### Optimizer

应用程序的模型与观测数据之间的差异称为 `loss`。TensorFlow 应用程序使用优化器来降低损失。在代码中，你可以通过实例化 `Optimizer` 类的子类来创建优化器。每个优化器都有一个 `minimize` 方法，该方法返回可在会话中执行的操作。

TensorFlow 支持多种不同的优化算法，每种算法都由 `Optimizer` 的不同子类表示。例如，最简单的优化算法梯度下降法由 `GradientDescentOptimizer` 表示。但最简单的算法很少是最有效的，我建议使用 `AdamOptimizer` 或 `AdagradOptimizer` 来优化你的应用程序。

##### Estimator

如 第 12 章 中所述，估计器极大地简化了开发和部署机器学习算法的过程。当你使用估计器时，你不必担心会话和图。你只需要了解 `Estimator` 类的三个方法：`train`、`evaluate` 和 `predict`。

使用估计器的另一个优点是 TensorFlow 提供了许多 `Estimator` 的子类。这些现成的估计器，例如 `LinearRegressor` 和 `DNNClassifier`，使训练和测试机器学习变得容易。`DNNLinearCombinedClassifier` 特别有帮助，因为它让你能够利用宽和深学习。

##### Dataset

TensorFlow API 最近的变化之一是将 `tf.contrib.data` 包提升为 `tf.data`。该包提供了至关重要的 `Dataset` 类，TensorFlow 推荐用于加载和处理数据。该类提供了许多强大的方法用于批处理和转换数据，并且在许多情况下，你可以以多线程方式执行这些操作。

`Dataset` 类也很重要，因为它是 `TextLineDataset` 和 `TFRecordDataset` 的超类。这两个类使从文本文件和 TFRecord 文件读取数据变得简单。第 10 章 对这些类及其用法进行了详细讨论。

##### Iterator

`Dataset` 类提供了许多强大的功能，但它不允许你直接访问其数据。要从数据集中提取张量，你需要创建 `Iterator` 类的实例。

TensorFlow 提供了四种不同的遍历数据集内容的方式。最简单的是一次性迭代器，只能遍历数据集一次。你可以重用可初始化和可重新初始化迭代器，但你需要先运行特殊的初始化操作。可馈送迭代器是最复杂的，但你可以将它们与多个数据集关联，并且在每次迭代之前不需要初始化它们。

##### Saver

训练的目标是确定哪些变量能产生尽可能小的损失。训练可能需要数小时或数天，因此在训练期间和训练后存储变量的值至关重要。TensorFlow 通过提供 `Saver` 类使这成为可能。

使用该类很简单。在创建 `Saver` 实例后，你可以调用 `save` 将模型状态存储在编号的检查点文件中。你可以通过调用 `restore` 方法从检查点文件加载模型的变量。

#### Chapter 15

#### 训练神经网络的十条建议

本章内容

![check](img/check.png)**预处理数据以确保合适的分析**

![check](img/check.png)**选择神经网络的权重和层**

![check](img/check.png)**选择激活函数以产生可接受的输出**

在大多数软件开发工作中，如果你正确编码，应用程序总会完成其工作。但当你处理神经网络时，情况并非如此。你可以编写完美的代码，但仍然得到糟糕的结果。不管学术界怎么说，神经网络开发并不是一门精确的科学——其中仍然包含很多艺术。

在本章中，我提出了十条建议，可以帮助你提高神经网络的准确性和性能。这些通用规则基于我的经验以及我从其他开发者和研究人员那里学到的东西。但请记住，神经网络永远不是完全可靠的：即使是编码完美的神经网络有时也会失败。

##### 选择一个具有代表性的数据集

这一建议是最简单的，因为它不涉及任何数学或软件开发。关于训练样本，越多越好，但大小不是唯一优先事项。你需要确保你的训练数据集与现实世界相似。此外，如果你的应用程序将样本分类到类别中，你需要确保每个类别都有大量样本。

在图像分类方面，你永远不知道神经网络会关注哪些奇怪的特征。因此，许多开发者会在其输入样本中添加低水平的随机噪声。这种噪声不应模糊图像，但应迫使神经网络关注相关的特征。

##### 标准化你的数据

当你测试机器学习应用或将其用于实际预测时，应确保测试数据在统计上与训练数据相似。也就是说，测试/预测数据应具有与训练数据相同的均值和标准差。

如 Chapter 7 中所讨论的，对数据集的均值和标准差进行设定的过程称为标准化。许多应用通过将均值设为 0 并将标准差设为 1 来标准化其数据。在 TensorFlow 应用中，你可以通过调用 `tf.nn.moments` 和 `tf.nn.batch_normalization` 来实现这一点。

##### Use Proper Weight Initialization

研究人员设计了多种用于初始化神经网络权重的数学方法。其中最流行的方法之一称为 Glorot 方法或 Xavier 方法。你可以通过调用 `tf.contrib.layers.xavier_initializer` 在你的应用中使用此方法。

##### Start with a Small Number of Layers

对于复杂问题，你可能不知道要创建多少个隐藏层。一些开发者认为越大越好，并构建具有许多（超过 10 个）隐藏层的神经网络。但这增加了过拟合的可能性，即神经网络专注于特定的训练数据而无法分析通用数据。

为了避免过拟合，最好从小开始。如果准确率不可接受，请增加网络的深度，直到准确率达到合适的数值。除了降低过拟合的可能性外，起步小的方法还能保证比起步大的方法更快的执行速度。

##### Add Dropout Layers

除了密集层之外，我建议你在神经网络中添加 dropout 层。Dropout 层会在将信号作为输出传递之前将其输入的百分比设为 0。这通过降低进入 dropout 层的输入的相互依赖性来降低过拟合的可能性。

在 TensorFlow 中，你可以通过调用 `tf.nn.dropout` 创建一个 dropout 层。该层接受一个张量，其值标识对应输入应被丢弃的概率。

##### Train with Small, Random Batches

在你预处理数据、初始化权重并确定神经网络的初始结构之后，你就可以开始训练了。与一次性使用整个数据集进行训练不同，你应该将数据拆分为批次。神经网络将在处理每个批次时更新其梯度和权重。

减小批次大小会增加训练时间，但也会降低优化器陷入局部最小值而不是找到全局最小值的可能性。它还降低了分析对样本顺序的依赖性。你可以通过在训练过程中对批次进行洗牌来进一步降低这种依赖性。

##### Normalize Batch Data

即使你对进入神经网络的样本进行了标准化，随着数据从一个隐藏层移动到下一个隐藏层，其均值和方差也会发生变化。因此，开发者会在数据离开每一层后对其进行归一化。

这种归一化涉及将均值设为零并将标准差设为一。但该过程稍微复杂一些，因为你需要近似整个批次的均值和方差。与自己进行数学计算相比，我建议调用 `tf.contrib.layers.batch_norm`。

##### Try Different Optimization Algorithms

你选择的优化器将在决定应用的准确性和性能方面发挥关键作用。在撰写本书时，我在许多在线论坛上搜索了“哪种优化方法最好？”这个问题。但尽管经过数十年的分析，研究人员尚未达成共识。

我个人喜欢从 Adam 和 Adagrad 优化器开始，但如果你没有获得想要的性能和准确性，尝试其他方法是个好主意。在 TensorFlow 应用中，你可以通过创建优化器类的实例，例如 `tf.train.AdamOptimizer`，调用其 `minimize` 方法，并在会话中运行返回的操作来设置优化方法。

##### Set the Right Learning Rate
