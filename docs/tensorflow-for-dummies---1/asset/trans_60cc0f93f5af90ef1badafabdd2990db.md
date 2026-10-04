

主要区别在于 GRU 有两个门，称为重置门和更新门，而 LSTM 有三个门。GRU 的重置门对应于 LSTM 的输入门，而 GRU 的更新门对应于 LSTM 的遗忘门。GRU 不使用门来限制单元的输出。[图 9-6](#14_9788126592555-ch09.xhtml#c09-fig-0006) 描述了 GRU 单元及其门。

![FIGURE 9-6: GRUs are similar to LSTMs, but they have two gates instead of three.](images/9788126592555-fg0906.png)

[FIGURE 9-6:](#14_9788126592555-ch09.xhtml#rc09-fig-0006) GRUs are similar to LSTMs, but they have two gates instead of three.

GRU 缺少输出门乍看似乎是表面上的差异，但更简单的结构意味着应用程序可以显著比 LSTM 更快地训练 GRU。

### 在代码中创建 GRU

基于 GRU 单元创建 RNN 的过程与创建常规 RNN 非常相似。不同之处在于应用程序需要将 RNN 的单元设置为 `tf.nn.rnn_cell.GRUCell` 类的实例。该类的构造函数如下所示：

`GRUCell(num_units, activation=None, reuse=None, kernel_initializer=None, bias_initializer=None)`

第三个参数名为 `kernel_initializer`；它与 [第 8 章](#13_9788126592555-ch08.xhtml) 中讨论的图像过滤核无关。`kernel_initializer` 设置单元的初始权重，而 `bias_initializer` 设置其偏置。

### 使用 GRU 预测文本

`ch9/gru_lovecraft.py` 中的代码执行与 `ch9/rnn_lovecraft.py` 和 `ch9/lstm_lovecraft.py` 中的代码相同的文本预测。唯一的区别是它使用 `GRUCell` 创建了一个 RNN，如以下代码所示：

`cell = tf.nn.rnn_cell.GRUCell(num_hidden)`

`outputs, _ = tf.nn.static_rnn(cell, [input_holder], dtype=tf.float32)`

我的实验表明，与 LSTM 和 vanilla RNN 相比，GRU 在训练方面效率高得多。在我的系统上，GRU 平均需要 29.17 秒达到 95% 的准确率，而 LSTM 平均需要 33.48 秒，RNN 平均需要 35.54 秒达到 95% 的准确率。

Part 3

# 简化并加速 TensorFlow

IN THIS PART …

通过将数据加载到数据集并使用迭代器提取数据来简化您的应用程序。

探索 TensorFlow 的高级 Estimator API 以及可用于机器学习的预构建估计器。

通过在多个线程和设备上部署执行来加速您的机器学习。

利用 Google Machine Learning Engine 的非凡能力，实现高性能 TensorFlow 执行。

# Chapter 10

# 使用数据集和迭代器访问数据

IN THIS CHAPTER

![check](images/check.png)**创建和操作数据集**

![check](images/check.png)**加载和存储 TFRecord 数据**

![check](images/check.png)**探索四种类型的迭代器**

当你刚开始机器学习时，你最渴望的是你的应用程序收敛到一个解决方案。但随着你在该领域的进步，你越来越关注性能。当训练数据占用数 GB 或数 TB 内存时，性能尤其重要。

本章和接下来的两章重点介绍提高 TensorFlow 性能的方法——不再有冗长的方程或几何图示。相反，我专注于可用于加速应用程序的功能。两个重要的功能是数据集和迭代器，它们使加载和处理输入数据变得更容易。

## 数据集

提高应用程序性能的有效方法之一是创建线程。现代处理器具有多个核心，开发人员可以通过将应用程序的工作负载拆分为线程来利用它们。这种多线程在应用程序需要加载大量数据时特别有帮助。

过去，TensorFlow 开发人员通过构造 `QueueRunner` 类的实例来创建线程。但从 1.4 版本开始，TensorFlow 建议使用 `Dataset` 而不是 `QueueRunner`。`Dataset` 不仅仅是一个庞大的数据块——它为加载和处理数据提供了一个高性能管道。

通常在 TensorFlow 应用程序中，使用数据集的过程包括三个步骤：

1.  **从数据或文件创建数据集。**
2.  **将数据集拆分为批次并根据需要预处理批次。**
3.  **在会话中处理数据集的批次。**

你可以通过调用 `Dataset` 类的方法来执行前两个步骤。下面的讨论探讨了这些方法并展示了如何使用它们。

### 创建数据集

实际上，数据集是训练/测试数据的容器，其元素是应用程序用于向会话提供数据的批次。[第 5 章](#09_9788126592555-ch05.xhtml) 详细解释了批处理的主题。

你可以从数据、文本文件或二进制文件创建数据集。以下各节介绍这些方法并解释如何在代码中执行它们。

#### 从数据创建数据集

你可以通过调用 [表 10-1](#16_9788126592555-ch10.xhtml#c10-tbl-0001) 中列出的五个 `Dataset` 方法之一来从数据创建数据集。所有这些方法都是静态的，因此你需要通过 `tf.data.Dataset` 类调用它们。

[TABLE 10-1](#16_9788126592555-ch10.xhtml#rc10-tbl-0001) Functions That Create Datasets

| **Member** || **Description** |

| --- | --- |

| `range(*args)` || Creates a dataset containing a range of values |

| --- | --- |

| `from_tensors(tensors)` || Creates a dataset that combines the input tensors into one element |

| `from_tensor_slices(tensors)` || Creates a dataset containing one element for each row of the input tensors |

| `from_sparse_tensor_slices(sparse_tensor)` || Creates a dataset containing one element for each row of the sparse tensor |

| `from_generator(generator, output_types, output_shapes=None)` || Creates a dataset from the given generator |

这些方法中最简单的是 `range`，它返回一个包含构成步长分隔值范围的值的数据集。你可以用一个、两个或三个参数调用此方法：

*   `range(a)`: 生成从 0 到 `a` 的范围，不包括 `a`
*   `range(a, b)`: 生成从 `a` 到 `b` 的范围，不包括 `b`
*   `range(a, b, c)`: 生成从 `a` 到 `b` 的范围，不包括 `b`，步长为 `c`

以下代码演示了如何在代码中使用 `range`：

`ds1 = tf.data.Dataset.range(5) # [1, 2, 3, 4]`

`ds2 = tf.data.Dataset.range(10, 13) # [10, 11, 12]`

`ds3 = tf.data.Dataset.range(2, 8, 2) # [2, 4, 6]`

`from_tensors` 和 `from_tensor_slices` 特别有用，因此重要的是不要将它们混淆。`from_tensors` 将输入张量组合在一起并返回一个元素的数据集。以下代码演示了如何使用 `from_tensors`：

`t = tf.constant([[1, 2], [3, 4]])`

`ds = tf.data.Dataset.from_tensors(t) # [[1, 2], [3, 4]]`

相比之下，`from_tensor_slices` 为参数的每一行创建一个单独的元素。以下代码演示了如何使用 `from_tensor_slices`：

`t = tf.constant([[1, 2], [3, 4]])`

`ds = tf.data.Dataset.from_tensor_slices(t)`

`# [1, 2], [3, 4]`

此代码从输入张量的每一行创建一个元素。因此，`ds` 包含两个元素，每个元素包含两个值。`from_sparse_tensor_slices` 与 `from_tensor_slices` 类似，但它返回一个包含稀疏张量每一行一个元素的数据集。

`from_generator` 方法让你可以从生成器函数产生的值创建数据集。在 Python 中，*生成器函数* 是产生（或 *yield*）一系列值的函数。使用生成器的过程包括以下步骤：

1.  **在生成器函数中，使用 `yield` 语句提供一个值。**
2.  **通过调用函数获得生成器对象。**

