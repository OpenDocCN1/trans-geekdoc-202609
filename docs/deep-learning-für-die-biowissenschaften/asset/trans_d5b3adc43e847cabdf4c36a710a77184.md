
# 医学中的深度学习

## 代码示例：用于图像分割的 U-Net

```python
learning_rate = dc.models.tensorgraph.optimizers.ExponentialDecay(0.01, 0.9, 250)

model = dc.models.TensorGraph(learning_rate=learning_rate,
                              model_dir='segmentation')

features = layers.Feature(shape=(None, 520, 696, 1)) / 255.0
labels = layers.Label(shape=(None, 520, 696, 1)) / 255.0

# 三次下采样
conv1 = layers.Conv2D(16, kernel_size=5, stride=2, in_layers=features)
conv2 = layers.Conv2D(32, kernel_size=5, stride=2, in_layers=conv1)
conv3 = layers.Conv2D(64, kernel_size=5, stride=2, in_layers=conv2)

# 1x1 卷积（瓶颈层）
conv4 = layers.Conv2D(64, kernel_size=1, stride=1, in_layers=conv3)

# 三次上采样（带跳跃连接）
concat1 = layers.Concat(in_layers=[conv3, conv4], axis=3)
deconv1 = layers.Conv2DTranspose(32, kernel_size=5, stride=2, in_layers=concat1)

concat2 = layers.Concat(in_layers=[conv2, deconv1], axis=3)
deconv2 = layers.Conv2DTranspose(16, kernel_size=5, stride=2, in_layers=concat2)

concat3 = layers.Concat(in_layers=[conv1, deconv2], axis=3)
deconv3 = layers.Conv2DTranspose(1, kernel_size=5, stride=2, in_layers=concat3)

# 计算输出
concat4 = layers.Concat(in_layers=[features, deconv3], axis=3)
logits = layers.Conv2D(1, kernel_size=5, stride=1, activation_fn=None,
                       in_layers=concat4)
output = layers.Sigmoid(logits)

model.add_output(output)

loss = layers.ReduceSum(layers.SigmoidCrossEntropy(in_layers=(labels, logits)))
model.set_loss(loss)
```

这种结构比用于细胞计数的结构稍微复杂一些，但我们使用了相同的堆叠卷积层基本结构来获得我们想要的模型。同样，我们利用预训练模型来测试该结构。关于下载预训练模型的说明请参见本书的代码仓库（*https://github.com/deepchem/DeepLearningLifeSciences*）。一旦您传输了预训练权重，即可加载权重：

```python
model.restore()
```

借助该模型，我们生成一些掩码。通过 `model.predict_on_batch()`，我们可以预测输入批次的掩码。我们通过将生成的掩码与真实标签数据集的掩码进行比较并检查重叠比例，来验证预测的准确性：

```python
scores = []

for x, y, w, id in test_dataset.itersamples():
    y_pred = model.predict_on_batch([x]).squeeze()
    scores.append(np.mean((y > 0) == (y_pred > 0.5)))

print(np.mean(scores))
```

输出值应约为 `0.9899`。这意味着近 99% 的像素被正确预测！这是一个不错的结果，但请记住，这只是一个非常简单的示例。基于图像亮度阈值的图像处理算法可能效果同样好。然而，此处展示的步骤也应适用于更复杂的图像数据集。

在研究了预训练模型之后，我们要训练一个 U-Net 50 个周期：

```python
model.fit(train_dataset, nb_epoch=50, checkpoint_interval=100)
```

该训练计算量大，在性能良好的 GPU 上将运行数小时。在 CPU 系统上可能无法训练此模型。训练完成后，请自行评估结果。您能达到预训练模型的准确度吗？

## 计算辅助分析

细胞计数和分割是相对简单的视觉任务。因此，机器学习模型在这些任务上表现良好并不令人惊讶。人们可能会问，这难道就是机器学习的全部能力吗？

幸运的是，答案是：不是！机器学习模型能够捕捉数据集中的细微信号。例如，一项研究表明，深度学习模型能够仅根据源图像预测荧光标记的结果。[^3] 正如我们在“为显微镜准备生物样本”（第 112 页）中所见，荧光染色过程可能非常繁琐。深度学习有可能承担部分所需的准备工作，这令人惊叹。

尽管这是一个令人振奋的结果，但我们仍处于起步阶段。仍需大量工作来“稳健化”这些方法，以便它们能得到更广泛的应用。

## 总结

在本章中，我们介绍了显微镜学的基础知识以及一些针对显微镜系统的基本机器学习方法。我们全面介绍了现代显微镜学的一些基本问题（特别是与生物学问题相关的），并探讨了深度学习已应用的领域及未来潜在的应用领域。

此外，我们详细概述了显微镜学的一些物理和生物学方面，并试图阐明为何这些知识对主要关注构建有效管线以处理显微镜图像和模型的开发者也很有用。了解衍射极限等物理规律，有助于理解为何使用不同的显微镜技术，以及深度学习未来如何在此发挥重要作用。了解生物样本制备技术，有助于理解开发显微镜系统所需的元数据和注释类型。

虽然我们对深度学习方法在显微镜学中的潜在应用感到兴奋，但重要的是要强调，这些方法并非没有保留。首先，多项较新研究强调了视觉卷积模型的敏感性。[^4] 简单的伪影就可能使此类模型失效并导致严重问题。例如，如果停车标志的图像模糊不清，模型可能会将其分类为绿灯。对于自动驾驶汽车来说，那将是灾难性的！

因此，询问深度显微镜学存在哪些困难是值得的。深度显微镜模型是否可能只是从存储的先前数据点中“填补”而来？虽然这不能完全解释其性能，但这些模型的性能至少一部分很可能源于此类存储数据的回流。这可能导致虚假相关性。因此，在对显微镜数据集进行科学分析时，质疑结果是归因于模型中的伪影还是实际的生物学现象至关重要。在接下来的章节中，我们将介绍一些工具，供您批判性地检查模型，以确定模型究竟学到了什么。

在下一章中，我们将探讨深度学习在医学中的应用。我们将重用本章涵盖的许多视觉深度学习主题。

# 第 8 章

## 医学中的深度学习

正如我们在上一章所见，从视觉数据集中提取有意义信息的能力对于分析显微镜图像很有用。视觉数据处理对于医学应用同样宝贵。如今，医生必须能够批判性地分析医学扫描。深度学习可以使这些分析更简单、更快捷（但可能更难以解读）。

[^3]: 脚注引用 3
[^4]: 脚注引用 4
