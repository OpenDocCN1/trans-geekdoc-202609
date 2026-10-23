
这里，ConvolutionLayer.Builder() 中的 10 的值是核的大小，而 .nOut() 中的 6 的值是核的数量。此外，.stride() 定义了核的步幅大小。第 4 章《Dropout 和卷积神经网络》中我们从头实现的代码的功能仅等价于 .stride(1, 1)。数值越大，所需时间越短，因为它减少了卷积所需的计算量，但同时我们也必须小心，它可能会降低模型的精度。无论如何，我们现在可以用更灵活的方式实现卷积。

子采样层描述如下：

```
.layer(1, new
SubsamplingLayer.Builder(SubsamplingLayer.PoolingType.MAX, new int[]
{2,2})
    .build()
```

这里，{2, 2} 是池化窗口的大小。你可能已经注意到，我们不需要为每一层（包括输出层）设置输入的大小。这些值在模型设置好后会自动设定。

输出层可以像其他模型中一样写成：

```
.layer(2, new OutputLayer.Builder(LossFunctions.LossFunction.
NEGATIVELOGLIKELIHOOD)
    .nOut(outputNum)
    .weightInit(WeightInit.XAVIER)
    .activation("softmax")
    .build()
```

本示例的图形模型如下：

![](img/9315e45972ec0fbaf15f9144035bca79_185_0.png)

构建之后是训练。由于我们有多个小批量，因此需要遍历所有批次进行训练。在本例中，可以通过在 DataSetIterator 上使用 .hasNext() 以及 mnistIter 轻松实现。整个训练过程可以写成如下：

```
model.setListeners(Arrays.asList((IterationListener) new ScoreIterationListener(listenerFreq)));
while(mnistIter.hasNext()) {
    mnist = mnistIter.next();
    trainTest = mnist.splitTestAndTrain(splitTrainNum, new Random(seed));
    trainInput = trainTest.getTrain();
    testInput.add(trainTest.getTest().getFeatureMatrix());
    testLabels.add(trainTest.getTest().getLabels());
    model.fit(trainInput);
}
```

这里，测试数据和测试标签被保存以供后续使用。

在测试时，同样由于我们有多个小批量，需要迭代测试数据的评估过程：

```
for(int i = 0; i < testInput.size(); i++) {
    INDArray output = model.output(testInput.get(i));
    eval.eval(testLabels.get(i), output);
}
```

然后，我们像其他示例中一样使用：

```
log.info(eval.stats());
```

这将返回如下结果：

```
=====================Scores=====================
Accuracy:  0.832
Precision: 0.8783
Recall:    0.8334
F1 Score:  0.8552464933704985
=====================
```

刚才给出的示例是具有一个卷积层和一个子采样层的模型，但你可以使用 LenetMnistExample.java 实现深度卷积神经网络。在此示例中，有两个卷积层和子采样层，后面跟着全连接的多层感知机：

```
MultiLayerConfiguration.Builder builder = new NeuralNetConfiguration.Builder()
    .seed(seed)
    .batchSize(batchSize)
    .iterations(iterations)
    .regularization(true).l2(0.0005)
    .learningRate(0.01)
    .optimizationAlgo(OptimizationAlgorithm.STOCHASTIC_GRADIENT_DESCENT)
    .updater(Updater.NESTEROVS).momentum(0.9)
    .list(6)
    .layer(0, new ConvolutionLayer.Builder(5, 5)
        .nIn(nChannels)
        .stride(1, 1)
        .nOut(20).dropOut(0.5)
        .weightInit(WeightInit.XAVIER)
        .activation("relu")
        .build())
```

```java
.layer(1, new
SubsamplingLayer.Builder(SubsamplingLayer.PoolingType.MAX,
new int[]{2, 2})
        .build())
.layer(2, new ConvolutionLayer.Builder(5, 5)
        .nIn(20)
        .nOut(50)
        .stride(2,2)
        .weightInit(WeightInit.XAVIER)
        .activation("relu")
        .build())
.layer(3, new
SubsamplingLayer.Builder(SubsamplingLayer.PoolingType.MAX,
new int[]{2, 2})
        .build())
.layer(4, new DenseLayer.Builder().activation("tanh")
        .nOut(500).build())
.layer(5, new
OutputLayer.Builder(LossFunctions.LossFunction
.NEGATIVELOGLIKELIHOOD)
        .nOut(outputNum)
        .weightInit(WeightInit.XAVIER)
        .activation("softmax")
        .build())
.backprop(true).pretrain(false);
new ConvolutionLayerSetup(builder,28,28,1);
```

正如第一个卷积层所示，使用 DL4J 可以轻松地将 dropout 应用于 CNN。

使用此模型，我们得到以下结果：

```
=========================Scores=========================
Accuracy:  0.8656
Precision: 0.8827
Recall:    0.8645
F1 Score:  0.873490476878917
=========================================================
```

你可以在 MNIST 数据集页面 (http://yann.lecun.com/exdb/mnist/) 看到，最先进的结果比上面要好得多。这里，你再次会意识到参数、激活函数和优化算法的组合有多重要。

## 学习率优化

我们迄今为止学习了各种深度学习算法；你可能已经注意到它们有一个共同的参数：学习率。学习率定义在更新模型参数的方程中。那么，为什么不考虑优化学习率的算法呢？最初，这些方程描述如下：

$\theta^{(\tau+1)} = \theta^{(\tau)} + \Delta\theta^{(\tau)}$

这里：

$\Delta\theta^{(\tau)} = -\eta \frac{\partial E}{\partial \theta^{(\tau)}}$

这里，$\tau$ 是步数和 $\eta$ 是学习率。众所周知，随着每次迭代减小学习率的值，可以让模型获得更好的精度，但我们应谨慎确定下降幅度，因为值的突然下降会导致模型崩溃。学习率是模型参数之一，那么为什么不优化它呢？为此，我们需要知道最佳速率可能是什么。

设置速率最简单的方法是使用动量，表示如下：

$\Delta\theta^{(\tau)} = -\eta \frac{\partial E}{\partial \theta^{(\tau)}} + \alpha\Delta\theta^{(\tau-1)}$

这里，$\alpha \in [0,1]$，称为 **动量系数**。这个超参数通常先设为 0.5 或 0.9，然后再进行微调。

动量实际上是一种简单但有效的调整学习率的方法，但由 Duchi 等人提出的 **ADAGRAD**（http://www.magicbroom.info/Papers/DuchiHaSi10.pdf）被认为是一种更好的方法。其方程描述如下：

$\Delta\theta^{(\tau)} = -\frac{\eta}{\sqrt{\sum_{t=0}^{\tau} g_t^2}} g_{\tau}$

这里：

$g_{\tau} = \frac{\partial E}{\partial \theta^{(\tau)}}$

理论上，这效果很好，但实际上，为了防止发散，我们经常使用以下方程：

$\Delta \theta^{(\tau)} = -\frac{\eta}{\sqrt{\sum_{t=0}^{\tau} g_{t}^{2} + 1}} g_{\tau}$

或者我们使用：

$\Delta \theta^{(\tau)} = -\frac{\eta}{\sqrt{\sum_{t=0}^{\tau} g_{t}^{2} + 1}} g_{\tau}$

ADAGRAD 比动量更容易使用，因为值会自动设定，我们不需要设置额外的超参数。

由 Zeiler 提出的 ADADELTA（http://arxiv.org/pdf/1212.5701.pdf）被认为是一种更优秀的优化器。这是一种基于算法的优化器，不能用单一方程表示。以下是 ADADELTA 的描述：

- 初始化：
  - 初始化累积变量：

$E\left[g^{2}\right]_{0} = 0$

And：

$E\left[\Delta \theta^{2}\right]_{0} = 0$

- 迭代 τ = 0,1,2,...,T ：
  - 计算：
    $$g_{\tau} = \frac{\partial E}{\partial \theta^{(\tau)}}$$
  - 累积梯度：
    $$E\left[g^2\right]_{\tau} = \rho E\left[g^2\right]_{\tau-1} + (1-\rho) g_{\tau}^2$$
  - 计算更新：
    $$\Delta \theta^{(\tau)} = -\frac{\sqrt{E\left[\Delta \theta^2\right]_{\tau-1} + \varepsilon}}{\sqrt{E\left[g^2\right]_{\tau} + \varepsilon}} g_{\tau}$$
  - 累积更新：
    $$E\left[\Delta \theta^2\right]_{\tau} = \rho E\left[\Delta \theta^2\right]_{\tau-1} + (1-\rho)\left(\Delta \theta^{(\tau)}\right)^2$$
  - 应用更新：
    $$\theta^{(\tau+1)} = \theta^{(\tau)} + \Delta \theta^{(\tau)}$$

这里，ρ 和 ε 是超参数。你可能会觉得 ADADELTA 相当复杂，但在 DL4J 中实现时无需担心这种复杂性。

DL4J 中仍支持其他优化器，如 RMSProp、RMSProp + 动量 和 Nesterov's Accelerated Gradient Descent。然而，我们不会深入探讨它们，因为实际上，动量、ADAGRAD 和 ADADELTA 已足以优化学习率。
