

```python
epochs=100,
batch_size=32
):
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
        Dense(
            64,
            activation='relu',
            input_shape=self.input_shape
        ),
        Dropout(0.5),
        Dense(
            32,
            activation='relu'
        ),
        Dropout(0.5),
        Dense(
            16,
            activation='relu'
        ),
        Dropout(0.5),
        Dense(1)
    ])
    self.model.compile(optimizer='adam', loss='mse')
    history = self.model.fit(
        train_features,
        train_labels,
        epochs=epochs,
        batch_size=batch_size,
        verbose=0
    )
    return history
```

我们对基准模型进行了以下修改：

- 在文件开头添加了 `from tensorflow.keras.layers import Dropout`。
- 在模型架构的全连接层之间引入了 `Dropout(0.5)` 层。Dropout 率设置为 0.5，这意味着在训练过程中，前一个全连接层输出的 50% 将被随机丢弃。根据所需的正则化程度，此比率可以调整为其他值（例如 0.2 或 0.3）。

在应用上述 Dropout 修改运行基准模型后，我们得到了以下输出：

- 测试损失：72.67
- R2 分数：0.9939

0.5 的 Dropout 率并不罕见，但在某些情况下可能过于激进。Dropout 率通常介于 0.2 到 0.5 之间，具体取决于模型和数据的具体需求及特征。

使用 0.2 的 Dropout 率运行模型后，我们得到了以下输出：

- 测试损失：41.8448
- R2 分数：0.9965

尽管与 0.5 的 Dropout 率相比，在 0.2 的 Dropout 率下我们看到了指标的提升（更低的损失和更高的 R2 分数），但在生产环境中，我们通常通过比较训练指标和测试指标来检查模型是否存在欠拟合或过拟合。如果模型欠拟合（即在训练数据和测试数据上的表现都较差），Dropout 可能过于激进，降低其比率可能有所帮助。如果模型过拟合（即在训练数据上表现良好，但在测试数据上表现较差），我们可能需要更多的 Dropout。

## L1 和 L2 正则化

L1 和 L2 正则化技术根据模型参数的大小在损失函数中引入一个惩罚项。L1 正则化包含参数的绝对值，而 L2 正则化涉及参数的平方值。这促使模型保持较小的参数值，从而缓解过拟合。

要将 L1 和 L2 正则化整合到基准神经网络模型中，我们必须调整 `create_and_train_model` 方法。具体来说，需要在模型架构中定义全连接层的地方添加正则化。

以下是更新了 L1 正则化的 `create_and_train_model` 方法：

```python
from tensorflow.keras.regularizers import l1

def create_and_train_model(
    self,
    train_features,
    train_labels,
    epochs=100,
    batch_size=32
):
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
        Dense(
            64,
            activation='relu',
            kernel_regularizer=l1(0.01),
            input_shape=self.input_shape
        ),
        Dense(
            32,
            activation='relu',
            kernel_regularizer=l1(0.01)
        ),
        Dense(
            16,
            activation='relu',
            kernel_regularizer=l1(0.01)
        ),
        Dense(1)
    ])
    self.model.compile(optimizer='adam', loss='mse')
    history = self.model.fit(
        train_features,
        train_labels,
        epochs=epochs,
        batch_size=batch_size,
        verbose=0
    )
    return history
```

在此修改中，我们在基准模型中添加以下内容：

- `from tensorflow.keras.regularizers import l1`
- 在每个全连接层的定义中，我们添加了 `kernel_regularizer` 参数并将其设置为 `l1(0.01)`。这将对每个全连接层的权重应用 L1 正则化，正则化强度为 0.01。此值提供适中的正则化效果。它通常被选为起点，并根据训练过程中的模型表现进行调整。典型值范围从 0.001 到 0.1，并根据模型训练期间的经验观察进行调整。

要添加 L2 正则化，我们可以采用类似的方法，但使用 Keras 中的 `l2` 函数：

```python
from tensorflow.keras.regularizers import l2

def create_and_train_model(
    self,
    train_features,
    train_labels,
    epochs=100,
    batch_size=32
):
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
        Dense(
            64,
            activation='relu',
            kernel_regularizer=l2(0.01),
            input_shape=self.input_shape
        ),
        Dense(
            32,
            activation='relu',
            kernel_regularizer=l2(0.01)
        ),
        Dense(
            16,
            activation='relu',
            kernel_regularizer=l2(0.01)
        ),
        Dense(1)
    ])
    self.model.compile(optimizer='adam', loss='mse')
    history = self.model.fit(
        train_features,
        train_labels,
        epochs=epochs,
        batch_size=batch_size,
        verbose=0
    )
    return history
```

在此修改中，我们在基准模型中添加以下内容：

- `from tensorflow.keras.regularizers import l2`
- 在每个全连接层的定义中，我们添加了 `kernel_regularizer` 参数并将其设置为 `l2(0.01)`。这将对每个全连接层的权重应用 L2 正则化，正则化强度为 0.01。我们可以根据需要调整正则化强度。

在将 L1 和 L2 正则化技术整合到基准 TensorFlow 模型后，我们评估了具有不同正则化强度的模型性能。输出提供了不同正则化强度如何影响模型性能指标（特别是测试损失和 R2 分数）的见解。

当应用强度为 0.01 的 L1 正则化时，我们得到以下结果：

- 测试损失：20.1664
- R2 分数：0.9988

与基准模型值相比，我们观察到测试损失适度增加，R2 分数略微下降：

- 测试损失（基准）：15.5924
- R2 分数（基准）：0.9987

这种增加表明 L1 正则化并未显著改善模型的泛化能力，这表明模型很可能没有过拟合。然而，R2 分数保持在 0.9987 的高位，表明即使有正则化，模型也保留了其预测能力。

值得注意的是，观察到的性能指标值可能会受到模型权重随机初始化和数据采样变化等因素的影响，在比较基准和正则化结果时应考虑这些因素。

将 L1 正则化强度增加到 0.1 导致测试损失产生更明显的影响：

- 测试损失：61.8990
- R2 分数：0.9989

这种增加表明，更强的 L1 正则化导致模型拟合训练数据的能力降低，可能表明存在轻微的欠拟合。然而，R2 分数保持在 0.9989 的相对较高水平，表明模型仍然捕捉到了数据中方差的大部分。

另一方面，应用强度为 0.01 的 L2 正则化导致测试损失略低于 L1 正则化：

- 测试损失：19.9371
- R2 分数：0.9988

这表明与 L1 正则化相比，L2 正则化在缓解过拟合（如果存在）方面略有帮助。同样，R2 分数保持在 0.9988 的高位，表明模型保持了其预测性能。

将 L2 正则化强度增加到 0.1 导致测试损失与使用较高 L1 正则化强度获得的结果相似：

- 测试损失：61.4426
- R2 分数：0.9989

在过拟合的模型中，这表明较强的 L2 正则在减少过拟合方面具有与较强 L1 正则化相似的效果。尽管正则化强度较高，R2 分数仍保持在 0.9989 的高位，表明模型仍然保持其预测能力。

总体而言，输出展示了正则化强度与模型性能之间的权衡。虽然较强的正则化有助于防止过拟合并改善泛化能力，但过强的正则化可能导致欠拟合和预测性能的下降。因此，根据数据集的具体特征以及偏差与方差之间期望的平衡，选择合适的正则化强度至关重要。

