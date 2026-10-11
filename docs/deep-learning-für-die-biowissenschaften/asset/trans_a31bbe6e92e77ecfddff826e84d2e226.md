

# 使用卷积神经网络进行数据处理

为了处理数据，我们使用一个卷积神经网络，就像我们在[第 3 章](#Chapter03_9783960103516.xhtml#ch3)中识别手写数字时所做的那样。实际上，这两个模型非常相似。这一次我们使用 1-D 卷积，因为我们面对的是 1-D 数据（DNA 序列）而不是 2-D 数据（图像）。然而，模型的基本组件是相同的：输入、多个卷积层、一个或多个用于计算输出的 Dense 层（全连接层），以及作为误差函数的交叉熵。

## 模型创建与输入定义

首先，我们创建一个 `TensorGraph` 并定义输入：

```
model = dc.models.TensorGraph(batch_size=1000)

features = layers.Feature(shape=(None, 101, 4))
labels = layers.Label(shape=(None, 1))
weights = layers.Weights(shape=(None, 1))
```

请注意输入的尺寸。每个样本具有一个大小为 101（碱基数量）乘以 4（每个碱基的独热编码）的特征向量。此外，我们有一个用于标签的单个数值（0 或 1，指示是否包含结合位点）和一个用于权重的单个数值。在误差函数中使用权重对于此示例很重要，因为数据非常不平衡。不到 1% 的样本包含结合位点。因此，模型只需对每个样本输出 0，就能达到 99% 以上的准确率。为了防止这种情况，正样本获得的权重高于负样本。

## 卷积层

在下一步中，我们创建三个具有相同参数的卷积层：

```
prev = features

for i in range(3):
    prev = layers.Conv1D(filters=15, kernel_size=10,
                         activation=tf.nn.relu, padding='same',
                         in_layers=prev)
    prev = layers.Dropout(dropout_prob=0.5, in_layers=prev)
```

我们将卷积核的大小设为 10，并将每层的滤波器数量（= 输出数量）指定为 15。第一层接收原始特征（每个碱基四个数值）作为输入。总共有 40 个输入值，因为每次都会考虑连续十个碱基的区域。对于每个区域，这 40 个值通过一个卷积核转换为 15 个输出值。第二层同样每次考虑十个碱基，但输入是由第一层创建的 15 个值。为每个碱基计算一组新的 15 个值，以此类推。

为了防止过拟合，我们在每个卷积层后添加一个 Dropout 层。Dropout 概率设置为 0.5，因此每次有 50% 的输出值被随机设为 0。

## 输出计算

接下来，我们使用一个 Dense 层来计算输出：

```
logits = layers.Dense(out_channels=1, in_layers=layers.Flatten(prev))
output = layers.Sigmoid(logits)
model.add_output(output)
```

输出值应介于 0 和 1 之间，以便我们将其解释为某个样本包含结合位点的概率。`Dense` 层会产生任意值。因此，我们将它们通过逻辑 Sigmoid 函数，以获得所需的输出范围。该函数的输入通常称为 `Logits`。该名称指的是数学上的 Logit 函数，它是逻辑 Sigmoid 函数的反函数。

## 损失函数

最后，我们计算每个样本的交叉熵，并将其与权重相乘以获得误差：

```
loss = layers.SigmoidCrossEntropy(in_layers=[labels, logits])
weighted_loss = layers.WeightedError(in_layers=[loss, weights])
model.set_loss(weighted_loss)
```

为了保证数值稳定性，交叉熵层接受 `Logits` 作为输入，而不是 Sigmoid 函数的输出。

## 训练与评估

现在我们可以训练和评估模型。作为评估指标，我们选择 ROC AUC。每训练十个周期，就在训练数据和验证数据上评估一次模型：

```
train = dc.data.DiskDataset('train_dataset')
valid = dc.data.DiskDataset('valid_dataset')

metric = dc.metrics.Metric(dc.metrics.roc_auc_score)

for i in range(20):
    model.fit(train, nb_epoch=10)
    print(model.evaluate(train, [metric]))
    print(model.evaluate(valid, [metric]))
```

结果如[图 6-2](#Chapter06_9783960103516.xhtml#abb6-2)所示。验证数据的性能在第 50 个周期达到最高值 0.75，随后略有下降。训练数据的性能继续上升，最终稳定在 0.87 左右。因此我们知道，训练超过 50 个周期会导致过拟合，我们应在此点停止训练。

![image](Images/p93-1.png)

*图 6-2：训练过程中 ROC AUC 分数的变化，训练数据（虚线）和验证数据（实线）。*

ROC AUC 分数 0.75 还不错，但也不算特别好。通过改进模型，我们大概能提高它。为此，我们可以尝试改变各种超参数：卷积层的数量、每层的核大小、每层的滤波器数量、Dropout 率等。我们可以尝试许多不同的组合，或许能找到一个性能更好的组合。

但我们也知道，模型能变得多好是有限度的。唯一考虑的输入值是 DNA 序列。然而，转录因子结合还取决于许多其他因素：可及性、甲基化、形状、其他分子的存在等。任何忽略这些因素的模型在其预测能力上都会受限。因此，我们添加第二个输入，并测试结果是否因此得到改善。

## 染色质可及性

`Chromatin`（染色质）一词指构成染色体的所有物质：DNA、组蛋白以及各种其他蛋白质和 RNA 分子。“染色质可及性”指的是染色体的每个部分对外部分子的可及程度。当 DNA 紧紧缠绕在组蛋白上时，它对转录因子和其他分子是不可及的。它们无法接触到这些 DNA，因此 DNA 处于非活性状态。一旦它不再缠绕在组蛋白上，它就会再次变得可及，并恢复其在细胞中的核心作用。

染色质可及性既不均匀也不静态。它因细胞类型和细胞生命周期阶段而异。环境因素也会影响它。它是细胞控制其基因组活性的工具之一。如果染色体的相应区域被收起来，任何基因都可以被关闭。

可及性也在不断变化，因为 DNA 随着细胞内发生的过程而展开和缠绕。与其将可及性视为二元状态（可及或不可及），不如将其视为连续变量（每个区域可及多长时间）。

我们在上一节分析的数据基于一种名为 `HepG2` 的特定细胞的实验。实验确定了转录因子 `JUND` 在基因组中结合的位点。结果受染色质可及性的影响。如果某个区域在 `HepG2` 细胞中几乎总是不可及的，那么 `JUND` 在那里结合的可能性就非常小，即使 DNA 序列本身原本是一个理想的结合位点。因此，让我们尝试将可及性纳入我们的模型。

