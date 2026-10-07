

```python
import tensorflow as tf

x1 = tf.RaggedTensor.from_row_splits(
    values=[1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
    row_splits=[0, 5, 10])
print("x1",x1)

x2 = tf.RaggedTensor.from_row_splits(
    values=[1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
    row_splits=[0, 4, 7, 10])
print("x2",x2)

x3 = tf.RaggedTensor.from_row_splits(
    values=[1, 2, 3, 4, 5, 6, 7, 8],
    row_splits=[0, 4, 4, 7, 8, 8])
print("x3",x3)
```

列表 6.3 定义了基于 0 到 10（包含）整数的 TF 规则张量 x1、x2 和 x3。`values` 参数指定了一组值，这些值将被“分割”一组向量，使用 `row_splits` 参数中的数字作为每个向量的起始索引和结束索引。

例如，x1 指定了值为 `[0, 5, 10]` 的 `row_splits`，这决定了两个向量：值自 x1 索引 0 到索引 4 的向量，以及值自 x1 索引 5 到索引 9 的向量。这两个向量的内容分别为 `[1, 2, 3, 4, 5]` 和 `[6, 7, 8, 9, 10]`（见下文输出）。

另一个例子是，x2 指定了值为 `[0, 4, 7, 10]` 的 `row_splits`，这决定了三个向量：值自 x1 索引 0 到索引 3 的向量、值自 x1 索引 4 到索引 6 的向量，以及值自 x1 索引 7 到索引 9 的向量。这些向量的内容分别为 `[1,2,3,4]`、`[5,6,7]` 和 `[8, 9, 10]`（见下文输出）。

你可以对 x3 进行类似的分析，请记住起始索引和结束索引为 `[4,4]` 的向量是一个空向量。运行列表 6.3 中代码的输出如下：

```
x1: <tf.RaggedTensor [[1, 2, 3, 4, 5], [6, 7, 8, 10]]>
x2: <tf.RaggedTensor [[1, 2, 3, 4], [5, 6, 7], [8, 9, 10]]>
x3: <tf.RaggedTensor [[1, 2, 3, 4], []], [5, 6, 7], [8], []]]
```

如果你想生成一个值列表，请调用 `to_list()` 操作符。例如，假设你如下定义 x4：

```python
x4 = tf.RaggedTensor.from_row_splits(values=[1, 2, 3, 4, 5, 6, 7, 8, 9], row_splits=[0, 5, 10]).to_list()
print("x4:", x4)
```

上一个代码段的输出如下（你可以与上一个输出块中 x1 的输出进行比较）：

```
x4: [[1, 2, 3, 4, 5], [6, 7, 8, 9, 10]]
```

你还可以在 TF 中创建高维规则张量。例如，以下代码段在 TF 中创建了一个二维的规则张量：

```python
RaggedTensor.from_nested_row_splits(flat_values=[3, 1, 4, 1, 5, 9, 2, 6], nested_row_splits=([0, 3, 3, 5], [0, 4, 4, 7, 8, 8])).to_list()
```

上一个代码段生成了以下输出：

```
[[3, 1, 4, 1], [], [5, 9, 2]], [], [[6], []]]
```

# 什么是 lambda 表达式？

简而言之，lambda 表达式是一个匿名函数。使用 lambda 表达式定义局部函数，这些函数可以作为参数传递或作为函数调用的返回值。

非正式地说，lambda 表达式接收一个输入变量并对变量执行某种操作（由你指定）。例如，这里有一个“基础版”的 lambda 表达式，它向输入变量 x 加 1：

```python
lambda x: x + 1
```

你可以在有效的 TensorFlow 代码段中使用上述 lambda 表达式，如下所示（dx 是在其他处定义的 TensorFlow Dataset）：

```python
dx.map(lambda x: x + 1)
```

即使你不熟悉 TensorFlow Datasets 或 `map()` 操作符，你仍然可以理解上述代码段。下一节将包含一个完整的 TensorFlow 代码示例，阐述如何使用上述 lambda 表达式。

# TensorFlow 中的 lambda 表达式

列表 6.4 演示了如何使用 lambda 表达式。

# 列表 6.4: tf-plus.py

```python
import tensorflow as tf
# (列表 6.4 的示例代码)
```

下一节将包含一个完整的 TensorFlow 代码示例，阐述如何使用上述 lambda 表达式。

# 什么是迭代器？

迭代器类似于其他语言中的游标。你可以将迭代器想象为指向数据集中下一个元素的实体。TensorFlow 支持四种迭代器：

- 一次性 (One-shot)
- 可初始化的 (Initializable)
- 可重初始化的 (Reinitializable)
- 可填充的 (Feedable)

一次性迭代器只能迭代一次。当我们到达数据集末尾时，它将抛出异常；不再产生更多元素。

可初始化迭代器可以动态更新：调用其初始化器并通过 `feed_dict` 传递新数据。假设 dx 是 `tf.Dataset` 的实例。

可重初始化迭代器可以从不同的数据集初始化。当数据集需要某些额外转换时，这种迭代器非常有用。

可填充迭代器允许你从项目集中进行选择，这种迭代器本质上是一个选择器。

与迭代器配合涉及以下步骤：

1. 创建数据集
2. 创建迭代器
3. 指向迭代器
4. 推进迭代器
5. 处理数据集末尾

注意 TensorFlow 提供了多种迭代器，如上所述。

# TensorFlow 迭代器

列表 6.5 显示了 `tf-init-iterator.py` 的内容，它演示了如何定义一个可重初始化的迭代器。

# 列表 6.5: tf-init-iterator.py

```python
import tensorflow as tf
import numpy as np
x = np.arange(0, 10)
dx = tf.data.Dataset.from_tensor_slices(x)
# 创建可初始化迭代器
iterator = dx.make_initializable_iterator()
# 提取元素
next_element = iterator.get_next()
with tf.Session() as sess:
    sess.run(iterator.initializer)
    for i in range(15):
        val = sess.run(next_element)
        if i % 5 == 0 and i > 0:
            sess.run(iterator.initializer)
```

列表 6.5 将变量 x 初始化为 NumPy 数组。下一节将解释如何在 TensorFlow 中定义可重初始化的迭代器。运行列表 6.5代码的输出如下：

```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 0, 1, 2, 3, 4]
```

