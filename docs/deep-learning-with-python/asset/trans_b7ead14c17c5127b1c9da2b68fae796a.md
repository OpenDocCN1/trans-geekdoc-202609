

根据当前状态来指导决策。Keras `callbacks` API 可以帮助你将 `model.fit()` 的调用从纸飞机转变为智能自主无人机，能够自我内省并动态采取行动。

回调是一个对象（一个实现特定方法的类实例），在调用 `fit()` 时将其传递给模型，并在训练期间的各个点由模型调用。它可以访问关于模型状态和性能的所有可用数据，并可以采取行动：中断训练、保存模型、加载不同的权重集，或以其他方式改变模型的状态。

以下是你可以使用回调的一些示例：

- 模型检查点——在训练期间的不同点保存模型的当前状态。
- 早停——当验证损失不再改善时中断训练（当然，还要保存训练期间获得的最佳模型）。
- 在训练期间动态调整某些参数的值——例如优化器的学习率。
- 在训练期间记录训练和验证指标，或可视化模型学习到的表示随更新而变化——你熟悉的 `fit()` 进度条实际上就是一个回调！

`keras.callbacks` 模块包含许多内置回调（这不是穷尽列表）：

```
keras.callbacks.ModelCheckpoint
keras.callbacks.EarlyStopping
keras.callbacks.LearningRateScheduler
keras.callbacks.ReduceLROnPlateau
keras.callbacks.CSVLogger
```

让我们回顾其中两个，以便你了解如何使用它们：`EarlyStopping` 和 `ModelCheckpoint`。

## 早停和模型检查点回调

在训练模型时，有许多事情你无法从一开始就预测。特别是，你无法预知需要多少个 epoch 才能达到最佳验证损失。迄今为止的示例都采用了这样的策略：训练足够多的 epoch 直到开始过拟合，使用第一次运行来确定应该训练的 epoch 数量，最后使用这个最佳数量从头开始启动一个新的训练运行。当然，这种方法是浪费性的。更好的处理方法是：当你测量到验证损失不再改善时停止训练。这可以通过使用 `EarlyStopping` 回调来实现。

`EarlyStopping` 回调会在被监控的目标指标连续固定数量的 epoch 不再改善时中断训练。例如，此回调允许你在一旦开始过拟合时即中断训练，从而避免不得不为较少的 epoch 数重新训练模型。此回调通常与 ModelCheckpoint 配合使用，ModelCheckpoint 让你在训练期间不断保存模型（并且，可选地，仅保存到目前为止的当前最佳模型：即在 epoch 结束时达到最佳性能的模型版本）。

### 清单 7.19 在 fit() 方法中使用 callbacks 参数

回调通过 fit() 中的 callbacks 参数传递给模型，该参数接受一个回调列表。你可以传递任意数量的回调。

```
callbacks_list = [
  keras.callbacks.EarlyStopping(
      monitor="val_accuracy",
      patience=2,
  ),
  keras.callbacks.ModelCheckpoint(
      filepath="checkpoint_path.keras",
      monitor="val_loss",
      save_best_only=True,
  )
]

model = get_mnist_model()
model.compile(optimizer="rmsprop",
              loss="sparse_categorical_crossentropy",
              metrics=["accuracy"])
model.fit(train_images, train_labels,
          epochs=10,
          callbacks=callbacks_list,
          validation_data=(val_images, val_labels))
```

请注意，你也可以在训练后随时手动保存模型——只需调用 model.save('my_checkpoint_path')。要重新加载已保存的模型，只需使用

```
model = keras.models.load_model("checkpoint_path.keras")
```

### 7.3.3 编写你自己的回调

如果你需要在训练期间执行内置回调未涵盖的特定操作，可以编写自己的回调。回调通过子类化 keras.callbacks.Callback 类来实现。然后你可以实现任意数量的以下命名透明的方法，这些方法会在训练期间的各个点被调用：

- **在每个 epoch 开始时调用**：`on_epoch_begin(epoch, logs)`
- **在每个 epoch 结束时调用**：`on_epoch_end(epoch, logs)`
- **在处理每个批次之前立即调用**：`on_batch_begin(batch, logs)`
- **在处理每个批次之后立即调用**：`on_batch_end(batch, logs)`
- **在训练开始时调用**：`on_train_begin(logs)`
- **在训练结束时调用**：`on_train_end(logs)`

这些方法都使用 `logs` 参数调用，该参数是一个包含关于上一个批次、epoch 或训练运行信息的字典——训练和验证指标等等。`on_epoch_*` 和 `on_batch_*` 方法还将 epoch 或批次索引作为其第一个参数（一个整数）。

下面是一个简单示例，它在训练期间保存每个批次的损失值列表，并在每个 epoch 结束时保存这些值的图表。

### 清单 7.20 通过子类化 Callback 类创建自定义回调

```
from matplotlib import pyplot as plt

class LossHistory(keras.callbacks.Callback):
    def on_train_begin(self, logs):
        self.per_batch_losses = []

    def on_batch_end(self, batch, logs):
        self.per_batch_losses.append(logs.get("loss"))

    def on_epoch_end(self, epoch, logs):
        plt.clf()
        plt.plot(range(len(self.per_batch_losses)), self.per_batch_losses,
                 label="Training loss for each batch")
        plt.xlabel(f"Batch (epoch {epoch})")
        plt.ylabel("Loss")
        plt.legend()
        plt.savefig(f"plot_at_epoch_{epoch}")
        self.per_batch_losses = []
```

让我们试运行一下：

```
model = get_mnist_model()
model.compile(optimizer="rmsprop",
              loss="sparse_categorical_crossentropy",
              metrics=["accuracy"])
model.fit(train_images, train_labels,
          epochs=10,
          callbacks=[LossHistory()],
          validation_data=(val_images, val_labels))
```

我们得到的图表类似于图 7.5。

### 7.3.4 使用 TensorBoard 进行监控和可视化

要进行良好的研究或开发出好的模型，你需要在实验期间获得关于模型内部情况的丰富、频繁的反馈。运行实验的目的就是为了获得关于模型表现如何的信息——尽可能多的信息。取得进展是一个迭代过程，一个循环——你从一个想法开始，将其表达为一个实验，试图验证或反驳你的想法。你运行这个实验并处理它生成的信息。这会启发你的下一个想法。你能运行的这个循环迭代次数越多，

![](img/ab452ecf572a1f1372915be13bd8088f_215_0.png)

图 7.5 我们自定义历史记录绘图回调的输出

你的想法就越精细且强大。Keras 帮助你在最短的时间内从想法进入实验，快速的 GPU 可以帮助你尽快从实验得到结果。但是处理实验结果呢？这就是 TensorBoard 派上用场的地方（见图 7.6）。

![](img/ab452ecf572a1f1372915be13bd8088f_215_1.png)

图 7.6 进步循环

TensorBoard (www.tensorflow.org/tensorboard) 是一个可在本地运行的基于浏览器的应用程序。它是监控训练期间模型内部所有活动的最佳方式。使用 TensorBoard，你可以

- 在训练期间可视化监控指标
- 可视化你的模型架构
- 可视化激活值和梯度的直方图
- 在 3D 中探索嵌入

如果你监控的信息不仅仅是模型的最终损失，你就能更清晰地了解模型做了什么和没做什么，并能更快地取得进展。

