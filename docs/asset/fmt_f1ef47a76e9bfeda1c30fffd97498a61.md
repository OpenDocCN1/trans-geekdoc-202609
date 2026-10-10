
在实践中，你很少需要手动创建变量，因为 Keras 提供了 `add_weight()` 方法，正如我们看到的，它可以处理这些。此外，模型参数通常由优化器直接更新，因此你很少需要手动更新变量。

![](img/0684d2da98e09085c0a622d4fd69aaad_400.png)

## 其他数据结构

TensorFlow 支持其他几种数据结构，包括（详情请参见笔记本）：

- 稀疏张量 (`SparseTensor`) 高效地表示包含大量零的张量。`tf.sparse` 包包含稀疏张量的操作。
- 张量数组 (`TensorArray`) 是张量的列表。它们默认具有固定大小，但也可以是动态的。所有张量必须具有相同的形状和类型。
- 不规则张量 (`RaggedTensor`) 表示张量的嵌套列表，其中每个张量具有相同的形状和数据类型。`tf.ragged` 包包含不规则张量的操作。
- 字符串张量（String tensors）是普通的张量，它们实际上表示字符串，所以如果你创建一个字符串（例如 "café"），它将自动编码为 UTF-8。或者，你可以使用 `type=int32` 表示 Unicode 码点（例如 [99, 97, 102, 101]）。`tf.string` 包由字节字符串和字符串组成。
- 集合 (Sets) 表示表示包含一个或多个集合的普通张量，你可以使用 `tf.sets` 中的操作来处理它们。
- 队列 (Queues)，包括先进先出队列 (FIFO)、优先考虑某些项目的队列 (PriorityQueue)、随机洗乱队列 (ShuffleQueue) 以及可以填充不同形状的队列 (PaddingQueue)。这些类都在 `tf.queue` 包中。

有了张量、操作、变量和各种数据结构，我们现在准备好自定义模型和算法了！

## 自定义模型和训练算法

让我们从创建一个自定义损失函数开始，这是一个简单常用的用例。

### 自定义损失函数

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

### 保存和加载包含自定义的模型

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

Keras API 仅规定了如何使用子化来定义层、模型、回调和正则化器。如果你使用子化构建其他组件（如损失函数、指标、初始化器或约束条件），它们可能无法迁移到其他 Keras 实现中。

让我们来看一下这段代码：

- 构造函数接受 `kwargs` 并将其传递给父类构造函数，该构造函数处理标准的超参数：损失的名称以及用于聚合实例损失的归约算法。默认情况下，它是 "sum_over_batch_size"，这意味着损失将是实例损失之和（如果存在权重，则可能对其进行加权），然后除以批次大小（而不是除以权重之和，因此这不是加权平均值）。其他可能的值是 "sum" 和 `None`。
- `call()` 方法接收标签和预测值，计算所有实例损失并返回它们。
- `get_config()` 方法返回一个将每个参数映射到其值的字典。它首先调用父类的 `get_config()` 方法，并将新的超参数添加到此字典中（注意在 Python 3.5 中添加了内容 `{}`）。

你可以在编译模型时使用这个类：

```
model.compile(loss=HuberLoss(2.), optimizer="nadam")
```

当你保存模型时，阈值会随模型一起保存；当加载模型时，只需要将类名映射到类本身即可：

```
model = keras.models.load_model("my_model_with_a_custom_loss_class.h5",
custom_objects={'HuberLoss': HuberLoss})
```

当保存模型时，Keras 会调用 `instance_get_config()` 方法并将配置以 JSON 格式保存在 HDF5 文件中。加载模型时，它会调用 `HuberLoss` 类的 `from_config()` 方法：这由基类（Loss）实现，并创建一个类的实例，将 **config 传递给构造函数**。

损失部分就这些！这并不难，对吧？对于自定义激活函数、初始化器、正则化器和约束条件，也很简单。让我们现在来看这些。

5 使用加权平均值不是一个好主意：如果我们这样做，两个具有相同权重但在不同批次中的实例对训练的影响将不同，取决于每个批次的总权重。

## 自定义激活函数、初始化器、正则化器和约束条件

Keras 的大多数功能（如损失、正则化器、初始化器、指标、激活函数、层甚至整个模型）都可以以非常相同的方式进行自定义。大多数情况下，你只需要编写一个具有适当输入输出的简单函数。例如，这里是自定义激活函数（等于 `keras.activations.softplus` 或 `tf.nn.softplus`）、自定义 Glorot 初始化器（等于 `keras.initializers.glot_normal`）、自定义正则化器（等于 `keras.regularizers.l1(0.01)`）以及确保权重全正数的自定义约束（等于 `keras.constraints.nonneg()` 或 `tf.nn.relu`）的示例。

```
def my_softplus(z): # 返回值就是 tf.nn.softplus(z)
return tf.math.log(tf.exp(z) + 1.0)
```

```
def my_lorot_initializer(shape, dtype=float32):
stddev = tf.sqrt(2. / (shape[0] + shape[1]))
return tf.random.normal(shape, stddev=stddev, dtype=dtype)
```

```
def my_l1_regularizer(weights):
return tf.reduce_sum(abs(0.01 * weights))
```

```
def my_positive_weights(weights): # 返回值就是 tf.nn.relu(weights)
return tf.where(weights < 0, tf.zeros_like(weights), weights)
```

如你所见，参数取决于自定义函数的类型。这些自定义函数随后可以被它们使用，例如：

```
layer = keras.layers.Dense(30, activation=my_softplus,
kernel_initializer=my_lorot_initializer,
kernel_regularizer=my_l1_regularizer,
kernel_constraint=my_positive_weights)
```

激活函数将应用于下一层的输出。层的权重将使用初始化器返回的值进行初始化。在每个训练步骤中，权重将通过传递给正则化函数以计算正则化损失，该损失将加到主损失中，以获得训练的最终损失。最后，在每个训练步骤后将调用约束函数，并将层的权重替换为受约束的权重。

如果函数具有某些需要随模型保存的超参数，那么你需要子化相应的类，例如 `keras.regularizers.Constraint`、`keras.initializers.Initializer` 或 `keras.layers`（对于任何层，包括激活函数）。例如，就像我们为自定义损失那样，这里有一个用于 l1 正则化的类，它保存了因子超参数（这次我们不需要调用父类构造函数或 `get_config` 方法，因为它们没有由父类定义）：

```
class MyRegularizer(keras.regularizers.Regularizer):
    def __init__(self, factor):
        self.factor = factor
    def __call__(self, weights):
        return tf.reduce_sum(tf.abs(self.factor * weights))
    def get_config(self):
        return {'factor': self.factor}
```

注意，对损失和层（包括激活函数）使用 `call()` 方法，对正则化器和初始化器使用 `__call__` 方法。对于指标，情况稍有不同，我们现在看到。

## 自定义指标

损失和指标在概念上是不相同的：损失用于梯度下降训练模型，它们必须是可微的（至少在评估时）。相比之下，指标用于评估模型，它们必须是易于解释的，并且可能不可微（例如 `cross-entropy`）。在这种情况下，定义自定义指标函数与我们之前创建的损失函数完全一样，并不总是如此！保存为 "huber_fn"：

```
model.compile(loss='mse', optimizer='adam', metrics=[create_huber(2.0)])
```

对于每个批次训练，Keras 将计算此指标并跟踪自 epoch 开始的平均值。大多数情况下，这正是我们需要的。但并不总是如此！考虑一个二分类器的精确率。正如我们在第 3 章看到的，精确率是正例除以预测数（包括正例和负例）。假设模型在第一个批次中做了 5 个正预测，4 个是正确的：精确率为 80%。然后假设模型在第二个批次中做了 3 个正预测，它们都是错误的：第二个批次的精确率为 0%。如果你只是计算这两个精确率的平均值，结果是 40%。等一下，这并不是模型在这两个上的上的上的精确！事实上，总共有 4 个正例（4 + 0），在 8 个正预测（5 + 3）中，因此整体精确率为 50%。我们需要一个能够跟踪正例数量和负例数量的对象，并在请求时计算它们的比例。这正是 `keras.metrics.Precision` 所完成的：

```
>>> precision = keras.metrics.Precision()
>>> precision.update_state([1, 1, 1, 1, 0], [1, 1, 1, 1, 0])
>>> precision.result()
0.8
>>> precision.update_state([0, 0, 0], [0, 0, 0])
>>> precision.result()
0.5
```

在任何时候，我们都可以调用 `result()` 方法获取指标的当前值。我们还可以通过 `variables` 属性查看它的变量（跟踪正例和负例的数量），并使用 `reset_states()` 方法重置这些变量：

```
>>> precision.variables
[<Variable 'true_positives' shape=(), dtype=float32, numpy=4],
 <Variable 'false_positives' shape=(), dtype=float32, numpy=1>]
>>> precision.reset_states()
```

让我们逐步分析这段代码：

- 构造函数使用 `add_weight()` 方法来创建在多个批次中跟踪指标状态所需的变量，在本例中，它是所有 Huber 损失的总和（total）以及到目前为止看到的实例数量（count）。如果你愿意的话，你也可以手动创建变量。Keras 会跟踪任何被设置为属性的 `tf.Variable`（更广泛地说，是任何“可跟踪”的对象，例如层或模型）。
- 当你将该类的实例作为函数使用时（正如我们对 `Precision` 对象所做的），会调用 `update_state()` 方法。它会根据一个批次的标签和预测（以及样本权重，但在这种情况下我们忽略了它们）来更新变量。
- `result()` 方法计算并返回最终结果，在本例中，仅为所有实例的 Huber 指标。当你将指标作为函数使用时，会先调用 `update_state()` 方法，然后调用 `result()` 方法，并返回其输出。
- 我们还实现了 `get_config()` 方法，以确保阈值（threshold）随模型一起保存。
- `reset_states()` 方法的默认实现将所有变量重置为 0.0（但如果需要，你可以重写它）。

> Keras 将无缝地处理变量持久化，无需任何操作。

当你使用简单函数定义指标时，Keras 会自动为每个批次调用它，并在每个轮次（epoch）跟踪平均值，就像我们手动执行的那样。我们的 `Metric` 类唯一的优点是阈值会被保存。但当然，某些指标（如精确率 precision）无法在批次之间轻松进行平均：在这种情况下，除了实现流式指标（streaming metric）外没有其他选择。

既然我们已经构建了一个流式指标，构建自定义层看起来就像易如反掌！

## 自定义层

你可能偶尔想要构建一个包含特殊层的架构，而 TensorFlow 并没有为该层提供默认实现。在这种情况下，你需要创建一个自定义层。或者，你可能只是想构建一个非常重复的架构，包含多次重复的相同层块，此时将每个层块视为单个层会非常方便。例如，如果模型是层 A、B、C、A、B、C 的序列，你可能希望定义一个包含层 A、B、C 的自定义层 D，然后你的模型就可以将 B 简化为 D, D。让我们看看如何构建自定义层。

首先，某些层没有权重，例如 `keras.Flatten` 或 `keras.ReLU`。如果你想创建一个没有任何权重的自定义层，最简单的选项是使用一个函数并将其封装在 `keras.layers.Lambda` 层中。例如，下面的层将对你的输入应用指数函数：

```
exponential_layer = keras.layers.Lambda(lambda x: tf.exp(x))
```

这个自定义层可以像其他任何层一样使用，使用顺序 API、函数 API 或子类化 API。你也可以将其作为激活函数（或者你可以使用 `activation=tf.exp`、`activation=keras.activations.activation`，或简单地使用 `activation="exponential"`）。指数层有时用于回归模型的输出层，当你想要预测具有非常不同尺度的值时（例如 0.001, 10, 1000）。

正如你到目前所证明的那样，要构建自定义层（即带有权重的层），你需要创建 `keras.layers.Layer` 类的子类。例如，以下代码实现了 `Dense` 层的简化版本：

```python
class MyDense(keras.layers.Layer):
```
