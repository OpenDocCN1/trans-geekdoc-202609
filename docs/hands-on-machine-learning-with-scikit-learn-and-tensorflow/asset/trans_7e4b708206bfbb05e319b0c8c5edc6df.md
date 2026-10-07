
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

代码中有很多操作，让我们逐过一遍：

- 我们创建了两个嵌套循环：针对轮（epochs），以及针对轮内的批量（batches）。
- 然后，我们从训练集中采样一个随机批量。
- 在 `tf.GradientTape()` 块中，我们使用模型作为函数对一个批量进行预测，并计算损失：它等于主损失加上其他损失（在模型模型中，每层有一个正则化损失）。由于 `mean_squared_error()` 函数为每个实例返回一个损失，我们使用 `tf.reduce_mean()` 计算批次上的平均值（如果你想对每个实例应用不同的权重，可以这样做这样做）。正则化损失已经归约为每个一个单一标量，因此我们只需要将它们相加（使用 `tf.add_n()`，它会求和多个形状和数据类型相同的张量）。
- 接下来，我们要求胶带计算损失相对于每个可训练变量的梯度（不是所有变量！），并将其应用于优化器中以执行梯度下降步骤。
- 接下来，我们更新平均损失和指标。
- 在每个轮结束时，我们重置状态。
