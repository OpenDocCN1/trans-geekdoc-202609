
梯度消失问题被极大缓解，以至于它们可以使用饱和激活函数，如 tanh 甚至是 logistic 激活函数。网络对权重初始化的敏感性也大大降低。它们可以使用大得多的学习率，显著加快了学习过程。具体来说，他们注意到：“应用于最先进的图像分类模型，批归一化（Batch Normalization）以减少 14 倍的训练步数实现了相同的准确率，并大幅优于原始模型。[...] 使用批归一化网络的集成，我们改进了 ImageNet 分类上的最佳结果：达到了 4.9% 的 top-5 验证误差（以及 4.8% 的测试误差），超过了人类评分者的准确率。”最后，批归一化像一份礼物一样，还起到正则化的作用，减少了对其他正则化技术（在本章稍后描述）的需求。

然而，批归一化确实为模型增加了一些复杂性（尽管前面提到，它可以消除对归一化输入数据的需要）。此外，存在运行时开销：由于每层额外的额外计算，神经网络的预测速度会变慢。因此，如果你需要极快的预测，在使用批归一化之前，你可能想检查 ELU + He 初始化的性能。

你可能会发现训练很慢，因为当使用批归一化时，每个 epoch 所花费的时间多得多。然而，这通常会被 BN 收敛速度快这一事实所抵消，因此达到相同的性能所需的 epoch 更少。总之，墙时间（wall time）会更短（这是通过墙上时钟测量的时间）。

![](img/0684d2da98e09085c0a622d4fd69aaad_360_0.png)

# 使用 Keras 实现批归一化

与 Keras 的大多数操作一样，实现批归一化非常简单。只需在每个隐藏层的激活函数之前或之后添加 `BatchNormalization` 层，并可选地将一个 BN 层作为模型的第一层添加。例如，该模型在每个隐藏层之后应用 BN，并作为模型的第一层（在展平输入图像之后）：

```python
model = keras.models.Sequential([
    keras.layers.Flatten(input_shape=[28, 28]),
    keras.layers.BatchNormalization(),
    keras.layers.Dense(300, activation="elu", kernel_initializer="he_normal"),
    keras.layers.BatchNormalization(),
    keras.layers.Dense(100, activation="elu", kernel_initializer="he_normal"),
    keras.layers.BatchNormalization(),
    keras.layers.Dense(10, activation="softmax")
])
```

就这些了！在这个只有两个隐藏层的微型示例中，批归一化不太可能产生非常积极的影响，但对于更深的网络，它可以产生巨大的差异。

让我们再仔细看看。如果你显示模型摘要（summary），你可以看到每个 BN 层为每个输入添加了 4 个参数：y、$\mu$ 和 $\sigma$（例如，第一个 BN 层添加了 316 个参数，是 78 的 4 倍）。最后两个参数 $\mu$ 和 $\sigma$ 是移动平均值，它们不受反向传播的影响，因为 Keras 将它们称为“不可训练的（Non-trainable）”（如果你计算 BN 参数的总数 3136 + 1200 + 400 并除以 2，你会得到 2,368，这是该模型中不可训练参数的总数）。

```python
>>> model.summary()
Model: "sequential_3"
Layer (type) | Output Shape | Param #
=================================
flatten_3 (Flatten) | (None, 784) | 0
batch_normalization_v2 (Bat) (None, 784) | 3136
dense_50 (Dense) | (None, 300) | 235500
batch_normalization_v2_1 (Ba) (None, 300) | 1200
dense_51 (Dense) | (None, 100) | 30100
batch_normalization_v2_2 (Ba) (None, 100) | 400
dense_52 (Dense) | (None, 10) | 1010
=================================
Total params: 271,346
Trainable params: 268,978
Non-trainable params: 2,368
```

让我们看看第一个 BN 层的参数。两个是可训练的（通过反向传播），两个不是：

```python
>>> [(var.name, var.trainable) for var in model.layers[1].variables]
('batch_normalization_v2/gamma:0', True),
('batch_normalization_v2/beta:0', True),
('batch_normalization_v2/moving_mean:0', False),
('batch_normalization_v2/moving_variance:0', False)
```
