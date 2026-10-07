

# 第 13 章

## 使用 TensorFlow 加载和预处理数据

通过早发版（Early Release）电子书，你可以获得处于最早形态的书——即作者在写作时所享有的原始且未经编辑内容的优势——因此你可以在这些标题正式发布很久之前利用这些技术。以下内容将是该书正式版本中的第 13 章。

![](img/0684d2da98e09085c0a622d4fd69aaad_428_0.png)

到为止，我们只使用了可以放入内存的数据集，但深度学习系统通常在无法放入内存（RAM）的大型数据集上进行训练。高效地导入并预处理大型数据集在其他深度学习库中实现可能非常困难，但得益于 Data API，TensorFlow 变得简单：你只需要创建一个数据集，告诉它从哪里获取数据，按你需要的任何方式对其进行转换，TensorFlow 就会处理所有的实现细节，例如多线程、队列、批处理（batching）、预取（prefetching）等。

Data API 开箱即用读取文本文件（如 CSV 文件）、具有固定大小记录的二进制文件以及使用 TensorFlow 的 TFRec 格式的二进制文件（后者支持不同大小的记录）。TFRec 是一种基于 Protocol Buffers（一种开源二进制格式）的灵活且高效的二进制格式。Data API 还支持从 SQL 数据库读取。此外，许多开源扩展可以读取各种数据源，例如 Google 的 BigQuery 服务。

然而，高效读取巨大数据集并不是唯一的困难：数据还需要进行预处理。数据并不总是严格地由方便的数值字段组成：有时会有文本特征、类别特征等。为了处理这些，TensorFlow 提供了 Features API：它让你能够轻松将这些特征转换为神经网络可以消耗的数值特征。例如，具有大量类别的类别特征（如城市或单词）可以使用嵌入（embeddings）进行编码（正如我们将要看到的，嵌入是一个表示类别的可训练稠密向量）。

Data API 和 Features API 都能与 tf.keras 无缝衔接。

在本章中，我们将详细介绍 Data API、TFRecord 格式和 Features API。我们还将快速查看 TensorFlow 生态系统的几个相关项目：

- TF Transform (tf.Transform) 使编写单个预处理函数成为可能，该函数可以在完整训练集上以两种模式运行：在训练之前（为了加速训练），以及导出为 TF Function 并整合到已训练模型中，这样一旦部署到生产环境中，它就可以实时处理新实例。
- TF Datasets (TFDS) 提供了一个方便的函数来下载各种常见的数据集，包括像 ImageNet 这样的大数据集，并提供了方便的数据集在使用 Data API 对其进行操作。

让我们开始吧！

## Data API

整个 Data API 围绕着数据集（dataset）的概念展开：正如你所怀疑的，它代表一个数据项序列。通常使用从磁盘逐渐读取的数据集，但为了简单起见，让我们使用 `tf.data.Dataset.from_tensor_slices()` 在内存中创建一个数据集：

```python
>>> X = tf.range(10) # 数据张量
>>> dataset = tf.data.Dataset.from_tensor_slices(X)
>>> dataset
<TensorSliceDataset shapes: (), types:int32>
```

from_tensor_slices() 接收一个张量并创建一个 tf.data.Dataset，其元素是 X 的所有切片（第一维），因此该数据集包含 10 个项目：张量 0, 1, 2, ..., 9。在这种情况下，如果我们使用 `tf.data.Dataset.range(10)`，将得到相同的数据集。

你可以这样迭代数据集的项：

```python
>>> for item in dataset:
    print(item)
```

```python
tf.Tensor(0, shape=(), dtype=int32)
tf.Tensor(1, shape=(), dtype=int32)
tf.Tensor(2, shape=(), dtype=int32)
...
tf.Tensor(9, shape=(), dtype=int32)
```

## 链式变换

一旦你有了数据集，就可以通过调用它的变换方法对其应用各种变换。每个方法都返回一个新的数据集，因此你可以像这样链式调用变换（如图 13-1 所示）：

```python
>>> dataset = dataset.repeat(3).batch(7)
>>> for item in dataset:
    print(item)
...
tf.Tensor([0 1 2 3 4 5 6], shape=(7,), dtype=int32)
tf.Tensor([7 8 9 0 1 2 3], shape=(7,), dtype=int32)
tf.Tensor([4 5 6 7 8 9 0], shape=(7,), dtype=int32)
tf.Tensor([1 2 3 4 5 6 7], shape=(7,), dtype=int32)
tf.Tensor([8 9], shape=(2,), dtype=int32)
```

![](img/0684d2da98e09085c0a622d4fd69aaad_430_0.png)

图 13-1. 数据集变换链链

在这个示例中，我们首先在原始数据集上调用 `repeat()` 方法，它返回一个将原始数据集项重复 3 次的新数据集。当然，这并不会在内存中复制 3 次数据！事实上，如果你不带参数调用此方法，新数据集将把上一个数据集的项按 7 个一组进行分组。然后我们在这个新数据集上调用 `batch()` 方法，再次创建一个新数据集。如你所见，batch() 方法必须输出大小为 2 的批次而不是 7，但如果你希望所有批次的大小完全一致，可以在调用时设置 `drop_remainder=True`。

数据集方法不会修改数据集，而是创建新的数据集，因此请确保保留对这些数据集的引用（例如 `dataset = ...`），否则什么都不会发生。你还可以通过调用 `map()` 方法对项应用任何你需要的变换。这会创建一个所有项都翻倍的新数据集：

```python
>>> dataset = dataset.map(lambda x: x * 2) # 项：[0,2,4,6,8,10]
```

有时，这会包含可能非常密集的计算，例如重塑图像，因此你可能希望开启多个线程来加速：通过设置 `num_parallel_calls` 参数。虽然 `map()` 对每个项应用变换，但 `apply()` 方法是整个整个数据集应用变换。例如，下面的代码通过对数据集应用 `unbatch()` 函数来取消批处理（unbatches）数据集（该函数目前是实验性的，但它可能会在未来的版本中移动到核心 API）。新数据集中的每个项将是一个单个张量，而不是大小为 7 的批次：

```python
>>> dataset = dataset.apply(tf.data.experimental.unbatch()) # 项：0,2,4...
```

还可以使用 `filter` 方法过滤数据集：

```python
>>> dataset = dataset.filter(lambda x: x < 10) # 项：0, 2, 4, 6, 8
```

如果你想查看数据集中的几项，可以使用 `take()` 方法：

```python
>>> for item in dataset.take(3):
    print(item)
...
tf.Tensor(0, shape=(), dtype=int64)
tf.Tensor(2, shape=(), dtype=int64)
tf.Tensor(4, shape=(), dtype=int64)
```

## 数据洗牌数据

如你所知，当训练集中的实例是独立同分布的时（参见第 4 章），梯度下降的效果最好。为了这一点，你只需要使用 `shuffle()` 方法。它会创建一个新数据集，首先用源数据集的前几项填充缓冲区，然后当被需要一个项时，它会从缓冲区中随机取出并用源数据集中的新项替换它，直到遍历完源数据集。在此时，它将继续从缓冲区中随机提取项，直到缓冲区为空。你必须指定缓冲区大小，并且确保它足够大，否则洗牌效率将很不高。然而，显然不要超过你拥有的 RAM，即使你有充足的内存，也没有必要远超数据集的大小。如果你希望每次运行程序时顺序都相同，可以提供一个随机种子。

```python
>>> dataset = tf.data.range(10).repeat(3) # 0 到 9，三次
>>> dataset = dataset.shuffle(buffer_size=5, seed=42).batch(7)
>>> for item in dataset:
    print(item)
...
tf.Tensor([0 2 3 6 7 4 1], shape=(7,), dtype=int64)
tf.Tensor([5 8 1 1 8 6 5], shape=(7,), dtype=int64)
tf.Tensor([4 8 7 2 3 0 9], shape=(7,), dtype=int64)
tf.Tensor([5 4 2 7 8 9 2], shape=(7,), dtype=int64)
tf.Tensor([3], shape=(2,), dtype=int64)
```

如果你在洗牌过的数据集上调用 `repeat()`，默认情况下它会在每次迭代时生成一个新顺序。这通常是一个好主意，但如果你在每次迭代中喜欢相同的顺序（例如用于测试或调试），可以设置 `shuffle_iteration=False`。

![](img/0684d2da98e09085c0a622d4fd69aaad_432_0.png)

对于无法放入内存的大型数据集，这种简单的缓冲区洗牌方法可能不够，因为缓冲区相对于数据集很小。一种解决方案是洗牌数据本身（例如，在 Linux 上可以使用 `shuffle` 命令洗牌文件）。这无疑将提高洗牌效果！然而，即使数据经过洗牌，你通常仍然希望进一步洗牌，否则顺序会在每个 epoch 中重复，模型可能会因为源数据中存在的虚假模式而产生偏差。为了洗牌实例，一种常用方法是将数据集分成多个文件，然后在训练期间按随机顺序读取它们。然而，位于相同文件中的实例仍然彼此相邻。为了避免这种情况，你可以随机选择多个文件并同时读取它们，交错读取它们的行。在此基础上，你还可以使用 `shuffle()` 方法添加一个洗牌缓冲区。

