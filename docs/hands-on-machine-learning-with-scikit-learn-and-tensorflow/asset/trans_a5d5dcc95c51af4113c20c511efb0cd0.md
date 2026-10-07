

请注意 NumPy 默认使用 64 位精度，而 TensorFlow 使用 32 位精度。这是因为 32 位精度对于神经网络来说通常足够了，而且运行更快，占用的内存更少。因此，当你从 NumPy 数组创建张量时，请确保设置 `dtype=tf.float32`。

# 类型转换

类型转换会严重损害性能，而且当自动执行时，很容易产生意料之外的结果。为了避免这种情况，TensorFlow 不会自动执行任何类型转换：如果你尝试对不兼容类型的张量执行操作，它会抛出异常。例如，你不能将浮点张量和整数张量相加，甚至不能将 32 位浮点和 64 位浮点相加：

```
>>> tf.constant(2.0) + tf.constant(40)
Traceback[...InvalidArgumentError: expected to be a float...]
>>> tf.constant(2.0) + tf.constant(40, dtype=tf.float64)
Traceback[...InvalidArgumentError: expected to be a double...]
```

这可能有点恼人，但请记住这是为了你好！当你需要转换张量时，可以使用 `tf.cast()`：

```
>>> t2 = tf.constant(40, dtype=tf.float64)
>>> tf.constant(2.0) + tf.cast(t2, tf.float32)
<tf.Tensor: id=136, dtype=float32, numpy=42.0>
```

# 变量

到目前为止，我们使用的是常量：如其名所示，你无法修改它们。神经网络中的权重需要通过反向传播进行调整，其他参数也可能随时间改变（例如，动量优化器会跟踪梯度参数）。什么是变量：

```
>>> v = tf.Variable([[1, 2, 3], [4, 5, 6]])
>>> v
<tf.Variable 'Variable='0' shape=(2, 3) dtype=int32, numpy=array([[1, 2, 3], [4, 5, 6]])>
```

变量的作用非常像常量张量：你可以对它执行相同的操作，就像使用 NumPy 一样，这取决于你所选择的操作。你还可以使用 `assign()` 方法（或 `assign_add()` 或 `assign_sub()`，它们会根据给定值增加或减少变量）来原地修改它。你也可以使用单元格（或切片）的 `assign()` 方法修改单个单元格（直接赋值将无效），或者使用 `scatter_update()` 和 `scatter_nd_`：

```
v.assign(2 *) # = [[2, 4, 6], [8, 10, 12]]
v[0, 1].assign(42) # = [[2, 42, 6], [8, 10, 12]]
```

![](img/0684d2da98e09085c0a622d4fd69aaad_399_0.png)

```
v[:, 2].assign([0, 1.]) # = [[2., 42., 0.], [8., 10., 1.]]
v.scatter_nd_update(indices=[[0, 0], [1, 2]], updates=[100., 200.])
# = [[100., 42., 0.], [8., 10., 200.]]
```

在实践中，你很少需要手动创建变量，因为 Keras 提供了 `add_weight()` 方法，正如我们看到的，它可以处理这些。此外，模型参数通常由优化器直接更新，因此你很少需要手动更新变量。

![](img/0684d2da98e09085c0a622d4fd69aaad_400.png)

# 其他数据结构

TensorFlow 支持其他几种数据结构，包括（详情请参见笔记本）：

- 稀疏张量 (`SparseTensor`) 高效地表示包含大量零的张量。`tf.sparse` 包包含稀疏张量的操作。
- 张量数组 (`TensorArray`) 是张量的列表。它们默认具有固定大小，但也可以是动态的。所有张量必须具有相同的形状和类型。
- 不规则张量 (`RaggedTensor`) 表示张量的嵌套列表，其中每个张量具有相同的形状和数据类型。`tf.ragged` 包包含不规则张量的操作。
- 字符串张量（String tensors）是普通的张量，它们实际上表示字符串，所以如果你创建一个字符串（例如 "café"），它将自动编码为 UTF-8。或者，你可以使用 `type=int32` 表示 Unicode 码点（例如 [99, 97, 102, 101]）。`tf.string` 包由字节字符串和字符串组成。
- 集合 (Sets) 表示表示包含一个或多个集合的普通张量，你可以使用 `tf.sets` 中的操作来处理它们。
- 队列 (Queues)，包括先进先出队列 (FIFO)、优先考虑某些项目的队列 (PriorityQueue)、随机洗乱队列 (ShuffleQueue) 以及可以填充不同形状的队列 (PaddingQueue)。这些类都在 `tf.queue` 包中。

有了张量、操作、变量和各种数据结构，我们现在准备好自定义模型和算法了！

# 自定义模型和训练算法

让我们从创建一个自定义损失函数开始，这是一个简单常用的用例。

## 自定义损失函数

假设你想训练一个回归模型，但你的数据集有一些噪声。当然，你可能会尝试通过删除或修复离群值来清理数据集，但结果仍然不足，数据集仍然充满噪声。你应该使用哪种损失函数？均方误差可能会惩罚过大，导致你的模型变得不精确。平均绝对误差不会那么惩罚离群值，但训练可能需要一段时间才能收敛，且训练出的模型可能不精确。这可能是使用 Huber 损失（在第10章引入）的好时机。Huber 损失目前不是官方 Keras API 的，但在 `tf.keras` 中是可用的。假设它不存在：实现它易如反掌！只需创建一个接受标签和预测作为参数的函数，并使用 TensorFlow 计算任何实例：

```
def huber_fn(y_true, y_pred):
    error = y_true - y_pred
    is_small = tf.abs(error) < 1
    squared_loss = tf.square(error) / 2
    linear_loss = tf.abs(error) * 0.5
    return tf.where(is_small, squared_loss, linear_loss)
```

> 为了获得更好的性能，请使用示例中的向量化实现。此外，如果你想从 TensorFlow 的图特性中受益，你应该只使用 TensorFlow 操作。

![](img/0684d2da98e09085c0a622d4fd69aaad_401_0.png)

返回张量比返回平均值更好。接下来，在编译时可以使用这种损失：

```python
model.compile(loss=huber_fn, optimizer="nadam")
```

就是这样！训练期间的每个批次，Keras 都会调用 `huber_fn()` 函数并用它来跟踪总损失。

# 保存和加载包含自定义的模型

保存包含自定义损失的模型实际上可以正常工作，因为 Keras 保存了函数的名称。然而，每当你加载它时，都需要提供一个映射名称到对象的字典。更通常，当你加载包含自定义对象的模型时，你需要指定：

在当前的实现中，-1 到 1 之间的任何误差被认为是“小的”。但如果我们想要一个不同的阈值呢？一种策略是创建一个创建损失函数的函数：

```python
def create_huber(threshold=1.0):
    def huber_fn(y_true, y_pred):
        error = y_true - y_pred
        is_small_error = tf.abs(error) < threshold
        squared_loss = tf.square(error) / 2
        linear_loss = threshold * tf.abs(error) - threshold**2 / 2
        return tf.where(is_small_error, squared_loss, linear_loss)
    return huber_fn
```

```python
model.compile(loss=create_huber(2.0), optimizer="nadam")
```

遗憾的是，当你保存模型时，这不会被保存。这意味着你在加载模型时必须指定阈值（注意使用的名称是 "huber_fn"，这是我们给 Keras 的函数名称，而不是我们创建的函数名称）：

```python
model = keras.models.load_model("my_model_with_a_custom_loss.h5")
```

你可以通过子类 `keras.losses.Loss` 类并实现它的 `get_config()` 方法来实现这一点。

