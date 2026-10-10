
这在某些情况下非常有用，例如如果你想实现一种在输入变化时对激活进行很大惩罚的正则化：损失将基于激活相对于输入的梯度。由于输入不是变量，你必须告诉磁带观察它们。

如果你计算一个张量列表（例如 `[z1, z2, z3]`）相对于某些变量（例如 `[w1, w2]`）的梯度，TensorFlow 实际上计算的是这些张量梯度的之和（即 `gradient(z1, [w1, w2])` 加上 `gradient(z2, [w1, w2])` 加上 `gradient(z3, [w1, w2])`）。由于反向自动微分的工作方式，在不实际多次调用 `gradient()`（这需要使磁带持久化并在之后删除它）的情况下，无法多次计算单个梯度（`z1` 一次，`z2` 一次而不包含 `z3`）。

此外，实际上可以计算二阶偏导数（Hessian），即偏导数的偏导数！要做到这一点，我们需要记录计算一阶偏导数（雅obian矩阵）时执行的操作：这需要第二个磁带。以下是我们的做法：

```python
with tf.GradientTape(persistent=True) as hessian_tape:

    with tf.GradientTape() as jacobian_tape:

        z = (w1, w2)

        jacobians = jacobian_tape.gradient(z, [w1, w2])

    hessians = [hessian_tape.gradient(jacobian, [w1, w2]) for jacobian in jacobians]

del hessian_tape
```

内部磁带用于计算每个雅obian矩阵的偏导数。由于我们需要计算 `gradient()`，外部磁带用于计算每个雅obian矩阵的偏导数（否则我们将得到所有偏导数的之和。

偏导数等于 36 和 10，该点的梯度向量为 `(36, 10)`。但如果这是一个神经网络，该函数将复杂得多，通常具有成千上万个参数，手动寻找偏导数几乎是一项无法完成的任务。一种解决方案是通过测量当你微调参数时函数输出的变化程度，来计算每个偏导数的近似值：

```python
>>> w1, w2 = 5, 3

>>> eps = 1e-6

>>> (f(w1 + eps, w2) - f(w1, w2)) / eps

36.0000030705065

>>> (f(w1 + w2 + eps) - f(w1, w2)) / eps

10.00000003174137
```

看起来很对！这种方法效果不错，而且实现非常简单，但它只是一个近似值，你为每个参数调用一次 `f()`（而不是两次，因为我们只计算了一次 `f(w1, w2)`）。这种方法对于大型神经网络来说是不可行的。因此，我们应该使用自动微分（见第 10 章和 ???）。TensorFlow 让这变得非常简单：

```python
w1, w2 = tf.Variable(5.), tf.Variable(3)

with tf.GradientTape() as tape:

    z = f(w1, w2)
```

`gradients = tape.gradient(z, [w1, w2])`
定义两个变量 `w1` 和 `w2`，然后我们创建一个 `tf.GradientTape` 上下文，它会自动记录每个涉及变量的操作，最后让这个磁带（tape）计算结果 `z` 相对于这两个变量 `[w1, w2]` 的梯度。让我们看看 TensorFlow 计算的梯度：

```python
>>> gradients

[tf.Tensor: id=828234, shape=(), dtype=float32, numpy=36.0,

 tf.Tensor: id=828229, shape=(), dtype=float32, numpy=10.0)]
```

完美了！结果不仅是准确的（精度仅受限于浮点误差），而且 `gradient()` 方法只对计算过的计算只通过一次（反序），无论有多少个变量，因此它是极其高效的。这就像魔法一样！

![](img/0684d2da98e09085c0a622d4fd69aaad_415_0.png)

只在 `tf.GradientTape()` 块中放入最少的内容，以节省内存。或者，你可以在 `tf.GradientTape` 块内部创建一个 `tf.stop_recording()` 块来暂停记录。

磁带在你调用其 `gradient()` 方法后会自动擦除，所以如果你尝试调用两次 `gradient()`，将会得到异常：

```python
with tf.GradientTape() as tape:

z = f(w1, w2)
```

```python
dz_dw1 = tape.gradient(z, w1) # = tensor 36.0

dz_dw2 = tape.gradient(z, w2) # RuntimeError
```

如果你需要多次调用 `gradient()`，你必须使磁带变为持久化的，并在完成后删除它以释放资源：

```python
with tf.GradientTape(persistent=True) as tape:

z = f(w1, w2)
```

```python
dz_dw1 = tape.gradient(z, w1) # = tensor 36.0

dz_dw2 = tape.gradient(z, w2) # = tensor 10.0, 现在运行正常！

del tape
```

默认情况下，磁带只会跟踪涉及变量的操作，所以如果你尝试计算 `z` 相对于变量之外任何内容的梯度，结果将是 `None`：

```python
c1, c2 = tf.constant(5.), tf.constant(3)

with tf.GradientTape() as tape:

z = f(c1, c2)
```

```python
gradients = tape.gradient(z, [c1, c2]) # 返回 [None, None]
```

然而，你可以强制磁带观察你喜欢的任何张量，以记录涉及它们的每一个操作。你可以相对于这些张量计算梯度，就像它们是变量一样：

```python
with tf.GradientTape() as tape:

tape.watch(c1)

tape.watch(c2)

z = f(c1, c2)
```

```python
gradients = tape.gradient(z, [c1, c2]) # 返回 [36., 10.]
```

这在某些情况下非常有用，例如如果你想实现一种在输入变化时对激活进行很大惩罚的正则化：损失将基于激活相对于输入的梯度。由于输入不是变量，你必须告诉磁带观察它们。

如果你计算一个张量列表（例如 `[z1, z2, z3]`）相对于某些变量（例如 `[w1, w2]`）的梯度，TensorFlow 实际上计算的是这些张量梯度的之和（即 `gradient(z1, [w1, w2])` 加上 `gradient(z2, [w1, w2])` 加上 `gradient(z3, [w1, w2])`）。由于反向自动微分的工作方式，在不实际多次调用 `gradient()`（这需要使磁带持久化并在之后删除它）的情况下，无法多次计算单个梯度（`z1` 一次，`z2` 一次而不包含 `z3`）。

此外，实际上可以计算二阶偏导数（Hessian），即偏导数的偏导数！要做到这一点，我们需要记录计算一阶偏导数（雅obian矩阵）时执行的操作：这需要第二个磁带。以下是我们的做法：

```python
with tf.GradientTape(persistent=True) as hessian_tape:

    with tf.GradientTape() as jacobian_tape:

        z = (w1, w2)

        jacobians = jacobian_tape.gradient(z, [w1, w2])

    hessians = [hessian_tape.gradient(jacobian, [w1, w2]) for jacobian in jacobians]

del hessian_tape
```

内部磁带用于计算每个雅obian矩阵的偏导数。由于我们需要计算 `gradient()`，外部磁带用于计算每个雅obian矩阵的偏导数（否则我们将得到所有偏导数的之和。

## 自定义训练循环

在某些情况下，`fit()` 方法可能不够灵活，无法满足你的需求。例如，我们在第 10 章讨论过的 Wide and Deep 论文实际上使用了两个不同的优化器：一个用于宽路径，另一个用于深度路径。由于 `fit()` 方法只使用一个优化器（我们指定的那个）
（编译模型），实现这篇论文需要编写你自定义的循环。

你可能也想自己编写自己的训练循环，仅仅是为了更有信心地这正是你意图执行的操作（也许你对 `fit()` 方法的某些细节不确定）。然而，请记住，编写自定义训练循环会让你的代码更长、更容易出错且更难维护。

接下来，除非你真的需要额外的灵活性，否则你应该倾向于使用 `fit()` 方法而不是实现你自己的训练循环，特别是当你团队中工作时。

![](img/0684d2da98e09085c0a622d4fd69aaad_419_0.png)

让我们构建一个简单的模型。不需要编译它，因为我们将手动处理训练循环：

```python
l2_reg = keras.regularizers.l2(0.05)

model = keras.models.Sequential([

    keras.layers.Dense(30, activation="elu", kernel_initializer="he_normal",

    kernel_regularizer=l2_reg),

    keras.layers.Dense(1, kernel_regularizer=l2_reg)

])
```

接下来，让我们创建一个函数，从训练集中随机采样一个批量实例（在第 13 章中我们将讨论 Data API，它提供了一个更好的替代方案）：

```python
def random_batch(X, y, batch_size=32):

    idx = np.random.randint(len(X), size=batch_size)

    return X[idx], y[idx]
```

让我们定义一个函数来显示训练状态，包括步数、自上一个轮（epoch）开始以来的总步数（即我们将使用 Mean 指标来计算）以及其他指标：

```python
def print_status_bar(iteration, total, loss, metrics=None):

    metrics = " - ".join(["{:4f}".format(m.name, m.result())

                          for m in metrics] if metrics else []])

    end = "" if iteration < total else "\n"

    print("r{}".format(iteration, total) + metrics,

          end=end)
```

这段代码是不言自明的，除非你不熟悉 Python 字符串格式化：`{:.4f}` 将将浮点数格式化为小数点后 4 位。此外，使用 `\r`（回车符）配合 `end` 可以确保状态始终打印在同一行上。在笔记本中，`print_status_bar()` 函数还包含一个进度条，但你可以使用 `tqdm` 库。

好了，让我们进入正题吧！首先，我们需要定义一些超参数，选择优化器、损失函数和指标（在本例中仅有 MAE）：

```python
n_epochs = 5

batch_size = 32

n_steps = len(X_train) // batch_size

optimizer = keras.optimizers.Nadam(lr=0.01)

loss_fn = keras.losses.mean_squared_error

mean_loss = keras.metrics.Mean()

metrics = [keras.metrics.MeanAbsoluteError()]
```

我们已经准备好构建自定义循环了！

```python
for epoch in range(1, n_epochs + 1):

    print("{}/{}".format(epoch, n_epochs))

    for step in range(1, n_steps):

        X_batch, y_batch = random_batch(X_train, y_train, batch_size)

        with tf.GradientTape() as tape:

            y_pred = model(X_batch)

            main_loss = tf.reduce_mean(loss_fn(y_batch, y_pred))

            loss = tf.add_n([main_loss] + model.losses)

        gradients = tape.gradient(loss, model.trainable_variables)

        optimizer.apply_gradients(zip(gradients, model.trainable_variables))

        mean_loss(loss)

        for metric in metrics:

            metric(y_batch, y_pred)

            print_status_bar(step * batch_size, len(y_train), mean_loss, metrics)

        for metric in [mean_loss] + metrics:

            metric.reset_states()
```
