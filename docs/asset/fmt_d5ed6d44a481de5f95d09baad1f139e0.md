
```python
def __init__(self, units, activation=None, **kwargs):

    super().__init__(**kwargs)

    self.units = units

    self.activation = keras.activations.get(activation)

def build(self, batch_input_shape):

    self.kernel = self.add_weight(

        name="kernel", shape=[batch_input_shape[-1], self.units],

        initializer="glorot_normal")

    self.bias = self.add_weight(

        name="bias", shape=[self.units], initializer="zeros")

    super().build(batch_input_shape) # 必须在最后

def call(self, X):

    return self.activation(X @ self.kernel + self.bias)

def compute_output_shape(self, batch_input_shape):

    return tf.TensorShape(batch_input_shape.as_list()[:-1] + [self.units])
```

```python
def get_config(self):
    base_config = super().get_config()
    return (**base_config, "units": self.units,
            "activation": keras.activations.serialize(self.activation))
```

让我们逐步分析这段代码：

- 构造函数接收所有超参数作为参数（在本例中为 `units` 和 `activation`），重要的是，它还接收一个 `**kwargs` 参数。它调用父类构造函数并传递 `kwargs`：这处理了如 `input_shape`、`trainable`、`name` 等参数。然后它将超参数保存为属性，并将 `activation` 参数转换为 `keras.activations.get()` 函数（该函数接受函数、如 `"relu"` 或 `"selu"` 等标准字符串，或简单地 `None`）。

- `build(input)` 方法的作用是创建层变量，为每个权重调用 `add_weight()` 方法。`build()` 方法在第一次被使用时被调用。此时，Keras 知道输入的形状。（注：此处原文存在大量重复句，翻译时已按逻辑精简并保留核心含义）。

到此，你现在可以构建任何需要的自定义层了！现在让我们来创建自定义模型。

## 自定义模型

在第 10 章讨论子类 API 时，我们已经查看过自定义模型类。这实际上非常简单，只需对 `keras.models.Model` 类进行子类，在构造函数中创建层和变量，并实现 `call()` 方法来实现你想让模型执行的任何操作。例如，假设你想构建图 12-3 所示的模型：

![](img/0684d2da98e09085c0a622d4fd69aaad_411_0.png)

图 12-3。自定义模型示例

输入首先通过第一个全连接层，然后通过一个由两个全连接层和一个加法操作组成的残差块（正如我们在第 14 章中看到的，残差块会将输入加到它的输出上），然后再次通过这个残差块 3 次，再通过第二个残差块，最后的结果通过一个全连接输出层。注意，这个模型并没有意义，它只是一个示例，说明你可以轻松地构建任何种类型的模型，甚至包含循环和跳跃连接。为了实现这个模型，最好是创建一个 `ResidualBlock`，因为我们要创建几个相同的块（我们可能想在另一个模型中重用它）：

```python
class ResidualBlock(keras.Layer):
    def __init__(self, n_layers, n_neurons, **kwargs):
        super().__init__(**kwargs)
        self.hidden = [keras.Dense(n_neurons, activation='elu',
                        kernel_initializer='he_normal')
                       for _ in range(n_layers)]

    def call(self, inputs):
        Z = inputs
        for layer in self.hidden:
            Z = layer(Z)
        return inputs + Z
```

这个层是特殊的，因为它包含了其他层。Keras 会透明地处理这一点：它会自动检测到 `hidden` 属性包含可处理的对象（在本例中为层），因此它们的变量会自动添加到该层的变量列表中。该类的定义言而易见。接下来，让我们使用子类 API 来定义模型：

```python
class ResidualRegressor(keras.models.Model):
    def __init__(self, output_dim, **kwargs):
        super().__init__(**kwargs)
        self.hidden1 = keras.Dense(30, activation='elu',
                        kernel_initializer='he_normal')
        self.block1 = ResidualBlock(2, 30)
        self.block2 = ResidualBlock(2, 30)
        self.out = keras.Dense(output_dim)

    def call(self, inputs):
        Z = self.hidden1(inputs)
        for _ in range(1 + 3):
            Z = self.block1(Z)
            Z = self.block2(Z)
        return self.out(Z)
```

我们在构造函数中创建层，并在 `call()` 方法中使用它们。这个模型可以像任何其他模型一样使用（编译、拟合、评估并使用它进行预测）。如果你还能够使用 `save()` 方法保存模型，并使用 `keras.models.load_model()` 函数加载它，你必须在 `ResidualBlock` 类和 `ResidualRegressor` 类中都实现 `get_config()` 方法（正如我们之前做的那样）。或者，你也可以使用 `save_weights()` 和 `load_weights()` 直接保存和加载权重。

`Model` 类实际上是 `Layer` 类的子类，因此模型可以完全像层一样定义和使用。但模型还具有一些功能，包括它的 `compile()`、`fit()`、`evaluate()` 和 `predict()`（以及一些变体，如 `train_batch()` 或 `fit_generator()`），加上 `get_layers()` 方法（可以按名称或索引返回模型的任何层）以及 `save()` 方法（以及对 `keras.models.load_model()` 和 `keras.model_.clone_model()` 的支持）。如果模型为层提供了功能，那么为什么不把每个层都定义为模型呢？嗯，从技术上讲，你可以这样做，但将你的模型的内部组件（层或可重用的层块）从模型本身中解构出来可能更整洁。前者应该子类 `Layer` 类，而后者应该子类 `Model` 类。

到此，你就可以自然而简洁地使用 `sequential` API、`functional` API、`regularization` API（正则化 API）或 `subclass` API 构建任何你在论文中发现的任何模型了。“几乎”任何模型？是的，我们还需要查看几点：首先，如何根据模型内部结构定义损失函数或指标，其次是如何构建自定义的训练循环。

## 基于模型内部的损失和指标

之前定义的自定义损失和指标都是基于标签和预测（以及可选的样本权重）。然而，你偶尔可能想在模型的其他部分定义损失，例如其层的权重或激活值。这对于正则化目的或监控你模型的某些内部方面可能很有用。

要定义基于模型内部的自定义损失，请在你想的模型的任何部分上计算它，并将结果传递给 `add_loss()` 方法。例如，下面的自定义模型代表了一个具有 5 个隐藏层的标准 MLP，但它还实现了一个重构损失（见 ???）：我们在最后一层之上添加了一个 `Dense` 层，它的作用是重建模型的输入。因为我们需要在 `build()` 方法中创建这个 `Dense` 层以便访问输入的形状。在 `call()` 方法中，我们同时计算了 MLP 的常规输出以及重构层的输出。然后，我们计算重构结果与输入之间的均方差，并通过调用 `add_loss()` 将此值（乘以 0.05）添加到模型的损失列表中。在训练期间，Keras 将将此添加到主损失中（这就是为什么我们缩小了重构损失，以确保主损失占据主导地位）。结果是，模型将被强制通过隐藏层保留尽可能的信息，即使是那些对回归任务本身没有直接帮助的信息。在实践中，这种损失改进了泛化能力；它是一种正则化损失

```python
class ReconstructingRegressor(keras.models.Model):
    def __init__(self, output_dim, **kwargs):
        self.hidden = [keras.layers.Dense(30, activation="selu", kernel_initializer="lecun_normal")
        for _ in range(s)]
        self.out = keras.layers.Dense(output_dim)

    def build(self, batch_input_shape):
        n_inputs = batch_input_shape[-1]
        self.reconstruct = keras.layers.Dense(n_inputs)
        super().build(batch_input_shape)

    def call(self, inputs):
        Z = inputs
        for layer in self.hidden:
            Z = layer(Z)
        reconstruction = self.reconstruct(Z)
        recon_loss = tf.reduce_mean(tf.square(reconstruction - inputs))
        self.add_loss(0.05 * recon_loss)
        return self.out(Z)
```

同样，你可以通过任何你想的方式为模型添加自定义指标，只要结果是指标对象的输出。例如，你可以在构造函数中创建一个 `keras.metrics.Mean()` 对象，然后在 `call()` 方法中调用它并传递 `recon_loss`，最后通过调用模型的 `add_metric()` 方法将其添加。当你训练模型时，Keras 将显示每个 epoch 的平均损失（损失是主损失加上 0.05 重构损失）以及每个 epoch 的平均重构误差。这在训练期间会下降：

```
Epoch 1/5
11610/11610 [===========] loss: 4.3092 - reconstruction_error: 1.7360
Epoch 2/5
11610/11610 [==========] loss: 1.1232 - reconstruction_error: 0.8964
```

在 99% 的情况下，我们为止讨论的所有内容都足以实现你想要构建的任何模型，即使具有复杂的架构、损失等。在某些情况下，你可能需要自定义训练循环本身。然而，在在此之前，我们需要查看如何在 TensorFlow 中自动计算梯度。

## 使用 autodiff 计算梯度

为了理解如何使用 autodiff（见第 10 章和 ???）自动计算梯度，让我们考虑一个简单的函数：

```python
def (w1, w2):
    return 3 * w1 ** 2 + 2 * w1 * w2
```

如果你知道微积分，你可以解析地找到该函数关于 w1 的偏导数是 `6 * w1 + 2 * w2`。你也可以找到它关于 w2 的偏导数是 `2 * w1`。例如，在点 `(w1, w2) = (5, 3)` 处，这些偏-

偏导数等于 36 和 10，该点的梯度向量为 `(36, 10)`。但如果这是一个神经网络，该函数将复杂得多，通常具有成千上万个参数，手动寻找偏导数几乎是一项无法完成的任务。一种解决方案是通过测量当你微调参数时函数输出的变化程度，来计算每个偏导数的近似值：

```
>>> w1, w2 = 5, 3
>>> eps = 1e-6
>>> (f(w1 + eps, w2) - f(w1, w2)) / eps
36.0000030705065
>>> (f(w1 + w2 + eps) - f(w1, w2)) / eps
10.00000003174137
```

看起来很对！这种方法效果不错，而且实现非常简单，但它只是一个近似值，你为每个参数调用一次 f()（而不是两次，因为我们只计算了一次 f(w1, w2)）。这种方法对于大型神经网络 来说是不可行的。因此，我们应该使用自动微分（见第 10 章和 ???）。TensorFlow 让这变得非常简单：

```
w1, w2 = tf.Variable(5.), tf.Variable(3)
with tf.GradientTape() as tape:
    z = f(w1, w2)
```

gradients = tape.gradient(z, [w1, w2])
定义两个变量 w1 和 w2，然后我们创建一个 `tf.GradientTape` 上下文，它会自动记录每个涉及变量的操作，最后让这个磁带（tape）计算结果 z 相对于这两个变量 `[w1, w2]` 的梯度。让我们看看 TensorFlow 计算的梯度：

```
>>> gradients
[tf.Tensor: id=828234, shape=(), dtype=float32, numpy=36.0,
 tf.Tensor: id=828229, shape=(), dtype=float32, numpy=10.0)]
```

完美了！结果不仅是准确的（精度仅受限于浮点误差），而且 `gradient()` 方法只对计算过的计算只通过一次（反序），无论有多少个变量，因此它是极其高效的。这就像魔法一样！

![](img/0684d2da98e09085c0a622d4fd69aaad_415_0.png)

只在 `tf.GradientTape()` 块中放入最少的内容，以节省内存。或者，你可以在 `tf.GradientTape` 块内部创建一个 `tf.stop_recording()` 块来暂停记录。

磁带在你调用其 `gradient()` 方法后会自动擦除，所以如果你尝试调用两次 `gradient()`，将会得到异常：

```
with tf.GradientTape() as tape:
z = f(w1, w2)
```

```
dz_dw1 = tape.gradient(z, w1) # = tensor 36.0
dz_dw2 = tape.gradient(z, w2) # RuntimeError
```

如果你需要多次调用 `gradient()`，你必须使磁带变为持久化的，并在完成后删除它以释放资源：

```
with tf.GradientTape(persistent=True) as tape:
z = f(w1, w2)
```

```
dz_dw1 = tape.gradient(z, w1) # = tensor 36.0
dz_dw2 = tape.gradient(z, w2) # = tensor 10.0, 现在运行正常！
del tape
```

默认情况下，磁带只会跟踪涉及变量的操作，所以如果你尝试计算 z 相对于变量之外任何内容的梯度，结果将是 None：

```
c1, c2 = tf.constant(5.), tf.constant(3)
with tf.GradientTape() as tape:
z = f(c1, c2)
```

```
gradients = tape.gradient(z, [c1, c2]) # 返回 [None, None]
```

然而，你可以强制磁带观察你喜欢的任何张量，以记录涉及它们的每一个操作。你可以相对于这些张量计算梯度，就像它们是变量一样：

```
with tf.GradientTape() as tape:
tape.watch(c1)
tape.watch(c2)
z = f(c1, c2)
```

```
gradients = tape.gradient(z, [c1, c2]) # 返回 [36., 10.]
```
