
MLP 的参数是隐藏层 HiddenLayer 和输出层 LogisticRegression 的权重 w 和偏置 b。 由于输出层与之前介绍的相同，这里不对其代码进行查看。 HiddenLayer 的构造函数如下：

```java
public HiddenLayer(int nIn, int nOut, double[][] W, double[] b, Random rng, String activation) {

    if (rng == null) rng = new Random(1234);  // seed random

    if (W == null) {

        W = new double[nOut][nIn];
        double w_ = 1. / nIn;

        for(int j = 0; j < nOut; j++) {
            for(int i = 0; i < nIn; i++) {
                W[j][i] = uniform(-w_, w_, rng);  // initialize W with uniform distribution
            }
        }

    }

    if (b == null) b = new double[nOut];

    this.nIn = nIn;
    this.nOut = nOut;
    this.W = W;
    this.b = b;
    this.rng = rng;

    if (activation == "sigmoid" || activation == null) {

        this.activation = (double x) -> sigmoid(x);
        this.dactivation = (double x) -> dsigmoid(x);

    } else if (activation == "tanh") {

        this.activation = (double x) -> tanh(x);
        this.dactivation = (double x) -> dtanh(x);

    } else {
        throw new IllegalArgumentException("activation function not supported");
    }
}
```

W 会根据单元的数量随机初始化。这种初始化实际上很棘手，如果初始值分布不佳，更容易遇到局部最小值问题。因此，在实际场景中，模型通常会使用一些随机种子进行测试。激活函数可以应用于 sigmoid 函数或双曲正切函数。

MLP 的训练可以通过神经网络按顺序进行前向传播和反向传播来实现：

```java
public void train(double[][] X, int T[][], int minibatchSize, double learningRate) {
    double[][] Z = new double[minibatchSize][nIn];  // outputs of hidden layer (= inputs of output layer)
    double[][] dY;
    // forward hidden layer
    for (int n = 0; n < minibatchSize; n++) {
        Z[n] = hiddenLayer.forward(X[n]);  // activate input units
    }
    // forward & backward output layer
    dY = logisticLayer.train(Z, T, minibatchSize, learningRate);
    // backward hidden layer (backpropagate)
    hiddenLayer.backward(X, Z, dY, logisticLayer.W, minibatchSize, learningRate);
}
```

hiddenLayer.backward 部分实现了来自逻辑回归的预测误差 dY 的隐藏层反向传播。请注意，逻辑回归的输入数据对于反向传播也是必要的：

```java
public double[][] backward(double[][] X, double[][] Z, double[][] dY, double[][] Wprev, int minibatchSize, double learningRate) {
    double[][] dZ = new double[minibatchSize][nOut];  // backpropagation error
    double[][] grad_W = new double[nOut][nIn];
    double[] grad_b = new double[nOut];

    // train with SGD
    // calculate backpropagation error to get gradient of W, b
    for (int n = 0; n < minibatchSize; n++) {

        for (int j = 0; j < nOut; j++) {

            for (int k = 0; k < dY[0].length; k++) { // k < ( nOut of previous layer )
                dZ[n][j] += Wprev[k][j] * dY[n][k];
            }
            dZ[n][j] *= dactivation.apply(Z[n][j]);

            for (int i = 0; i < nIn; i++) {
                grad_W[j][i] += dZ[n][j] * X[n][i];
            }

            grad_b[j] += dZ[n][j];
        }
    }

    // update params
    for (int j = 0; j < nOut; j++) {
        for(int i = 0; i < nIn; i++) {
            W[j][i] -= learningRate * grad_W[j][i] / minibatchSize;
        }
        b[j] -= learningRate * grad_b[j] / minibatchSize;
    }

    return dZ;
}
```

你可能会觉得算法复杂且难以理解，因为参数看起来很复杂，但我们在这里做的几乎与逻辑回归的 train 方法相同：我们以 mini-batch 为单位计算 W 和 b 的梯度并更新模型参数。就这样。那么 MLP 能否学习 XOR 问题呢？通过运行 MultiLayerPerceptrons.java 来检查结果。

结果仅输出模型的准确率、精确率和召回率的百分比，但例如，如果你使用 LogisticRegression 的 predict 方法转储预测数据，就可以看到它实际预测的概率是多少，如下所示：

```java
double[] y = output(x);   // activate input data through learned networks
Integer[] t = new Integer[nOut];  // output is the probability, so cast it to label

System.out.println( Arrays.toString(y) );
```

我们刚刚证明了 MLP 可以逼近 XOR 的函数。此外，已被证明 MLP 可以逼近任意函数。我们在这里不涉及数学细节，但你可以很容易想象，MLP 拥有的单元越多，就能表达和逼近越复杂的函数。

## Summary

在本章中，作为深度学习的准备，我们深入研究了神经网络，它是机器学习算法之一。你学习了单层神经网络的三种代表性算法：感知器、逻辑回归和多类逻辑回归。我们看到单层神经网络无法解决非线性问题，但这个问题可以通过多层神经网络解决——即在输入层和输出层之间具有隐藏层（s）的网络。对 MLP 为何能解决非线性问题的直观理解是，网络可以通过增加层数和单元数量来学习更复杂的逻辑运算，从而具有表达更复杂函数的能力。让模型具备这种能力的关键是反向传播算法。通过将输出的误差反向传播到整个网络，模型在每次迭代中都会更新和调整以适应训练数据，最终优化以逼近数据的函数。

在下一章，你将学习深度学习的概念和算法。由于你现在已经获得了机器学习算法的基础理解，学习深度学习将不会有任何困难。

## 3 深度信念网络和堆叠去噪自编码器

从本章到下一章，你将学习深度学习的算法。我们将逐步遵循基础数学理论，以充分理解每个算法。一旦你掌握了深度学习的基础概念和理论，就能轻松地将其应用于实际应用。

本章你将学习以下主题：

- 深度学习可能成为突破的原因
- 深度学习与过去机器学习（神经网络）之间的差异
- 深度学习的典型算法 **深度信念网络 (DBN)** 和 **堆叠去噪自编码器 (SDA)** 的理论和实现

## 神经网络的衰落

在上一章中，你学习了神经网络的典型算法，并了解到非线性分类问题无法用感知器解决，但可以通过构建多层建模的神经网络来解决。换句话说，通过在输入层和输出层之间插入隐藏层，非线性问题可以被学习和解决。仅此而已；但通过增加一层中的神经元数量，神经网络整体上可以表达更多模式。如果忽略时间成本或过拟合问题，理论上神经网络可以逼近任意函数。

那么，我们可以这样想吗？如果增加隐藏层的数量——一层层累积隐藏层——神经网络能否解决任何复杂问题？产生这个想法是很自然的。而且，当然，这个想法已经被研究过。然而，结果表明，这次尝试并不成功。仅仅累积层数并不能让神经网络解决世界问题。相反，一些情况下的预测准确率甚至低于层数更少的模型。

为什么会出现这些情况？神经网络层数越多表达能力越强，这并没有错。那么问题出在哪里呢？这是因为前馈网络中学习算法的特性所致。如我们在上一章所见，反向传播算法用于将学习误差高效地传播到整个多层神经网络中。在该算法中，误差在神经网络的每一层中被反转，并按顺序逐一传达至输入层。通过将输出层的误差反向传播到输入层，网络的权重按顺序在每一层进行调整，整个网络的权重得到优化。

问题就出在这里。如果网络的层数较少，从输出层反向传播的误差可以很好地贡献于调整每一层的权重。然而，一旦层数增加，误差在每次反向传播层时逐渐消失，并且不再调整网络的权重。在靠近输入层的层中，误差根本不会被反馈。

层间连接密集的神经网络无法调整权重。因此，整个网络的权重无法得到优化，当然，学习也无法顺利进行。这个严重的问题被称为 **梯度消失问题**，长期困扰着研究人员，直到深度学习的出现。神经网络算法在早期阶段就达到了极限。

## 神经网络的复仇

由于梯度消失问题，神经网络在机器学习领域失去了流行度。我们可以说，与逻辑回归和 SVM 等其他典型算法相比，神经网络在现实世界数据挖掘中使用的案例数量明显较少。
