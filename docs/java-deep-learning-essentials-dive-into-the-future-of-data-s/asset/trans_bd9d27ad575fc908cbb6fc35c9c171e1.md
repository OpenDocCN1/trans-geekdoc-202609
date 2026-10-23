
```java
double[][] dZ = new double[0][0];

for (int layer = nLayers - 1; layer >= 0; layer--) {
    if (layer == nLayers - 1) {
        Wprev = logisticLayer.W;
    } else {
        Wprev = sigmoidLayers[layer+1].W;
        dY = dZ.clone();
    }
    dZ = sigmoidLayers[layer].backward(layerInputs.get(layer),
        layerInputs.get(layer+1), dY, Wprev, minibatchSize,
        learningRate);
}
```

DBN 的训练部分就是前面代码中看到的那样。困难的部分可能在于 RBM 的理论和实现，所以当你只是看 DBN 的代码时，可能会觉得它并不太难。

由于训练后的 DBN 可以被视为一个（深度）神经网络，因此当你尝试预测未知数据属于哪个类别时，只需在每一层中对数据进行前向传播：

```java
public Integer[] predict(double[] x) {
    double[] z = new double[0];
    for (int layer = 0; layer < nLayers; layer++) {
        double[] x_;
        if (layer == 0) {
            x_ = x;
        } else {
            x_ = z.clone();
        }
        z = sigmoidLayers[layer].forward(x_);
    }
    return logisticLayer.predict(z);
}
```

![](img/9315e45972ec0fbaf15f9144035bca79_113_0.png)

这里，\( \tilde{x} \) 是损坏的数据，即带噪声的输入数据。然后，前向传播到隐藏层和输出层可以表示如下：

$$
z_j = \sigma\left(\sum_{i=1}^{N} w_{ji}\tilde{x}_i + c_j\right)
$$

$$
y_i = \sigma\left(\sum_{j=1}^{M} w_{ji}z_j + b_i\right)
$$

这里，\( c_j \) 表示隐藏层的偏置，\( b_i \) 表示可见层的偏置。此外，\( \sigma \) 表示 sigmoid 函数。如前图所示，对输入数据进行损坏并映射到隐藏层称为 **编码**，将编码后的数据映射以恢复到原始输入数据称为 **解码**。然后，DA 的评价函数可以用原始输入数据和解码数据的负对数似然函数表示：

$$
E := -\ln L(\theta) = -\sum_{i=1}^{N}\left\{x_i\ln y_i + (1-x_i)\ln(1-y_i)\right\}
$$

这里，\( \theta \) 是模型参数，即可见层和隐藏层的权重和偏置。我们需要做的只是求这些参数相对于评价函数的梯度。为了便于变形方程，我们在这里定义以下函数：

$$
h_j := \sum_{i=1}^{N} w_{ji} \tilde{x}_i + c_j
$$

$$
g_i := \sum_{j=1}^{M} w_{ji} z_j + b_i
$$

那么，我们得到：

$$
z_j = \sigma(h_j)
$$

$$
y_i = \sigma(g_i)
$$

使用这些函数，每个参数的梯度可以表示如下：

$$
\frac{\partial E}{\partial w_{ji}} = \frac{\partial E}{\partial h_j} \frac{\partial h_j}{\partial w_{ji}} + \frac{\partial E}{\partial g_i} \frac{\partial g_i}{\partial w_{ji}} = \frac{\partial E}{\partial h_j} \tilde{x}_i + \frac{\partial E}{\partial g_i} z_j
$$

$$
\frac{\partial E}{\partial b_i} = \frac{\partial E}{\partial g_i} \frac{\partial g_i}{\partial b_i} = \frac{\partial E}{\partial g_i}
$$

$$
\frac{\partial E}{\partial c_j} = \frac{\partial E}{\partial h_j} \frac{\partial h_j}{\partial c_j} = \frac{\partial E}{\partial h_j}
$$

因此，只需要两个项。让我们逐一推导：

$$
\frac{\partial E}{\partial h_j} = \frac{\partial E}{\partial z_j}\frac{\partial z_j}{\partial h_j} = \frac{\partial E}{\partial z_j} z_j(1 - z_j)
$$

这里，我们利用了 sigmoid 函数的导数：

$$
\frac{d}{dx}\sigma(x) = \sigma(x)(1 - \sigma(x))
$$

此外，我们得到：

$$
\frac{\partial E}{\partial z_j} = \sum_{i=1}^{N}\frac{\partial E}{\partial y_i}\frac{\partial y_i}{\partial z_j} = \sum_{i=1}^{N} w_{ji}\left(x_i - y_i\right)
$$

因此，可以得到以下方程：

$$
\frac{\partial E}{\partial h_j} = \left(\sum_{i=1}^{N} w_{ji}\left(x_i - y_i\right)\right) z_j(1 - z_j)
$$

另一方面，我们也可以得到以下式子：

$$
\frac{\partial E}{\partial g_i} = \frac{\partial E}{\partial y_i}\frac{\partial y_i}{\partial g_i} = x_i - y_i
$$

因此，每个参数的更新方程如下：

$$
w_{ji}^{(k+1)} = w_{ji}^{(k)} + \eta\left[\left(\sum_{i=1}^{N} w_{ji}^{(k)} (x_i - y_i)\right) z_j (1 - z_j) \tilde{x}_i + (x_i - y_i) z_j \right]
$$

$$
b_i^{(k+1)} = b_i^{(k)} + \eta (x_i - y_i)
$$

$$
c_j^{(k+1)} = c_j^{(k)} + \eta\left(\sum_{i=1}^{N} w_{ji}^{(k)} (x_i - y_i)\right) z_j (1 - z_j)
$$

这里，\( k \) 是迭代次数，\( \eta \) 是学习率。虽然 DA 在变形上需要一些技巧，但你可以看到其理论本身与 RBM 相比非常简单。

现在，让我们进行实现。包结构与 RBM 的相同。

![](img/9315e45972ec0fbaf15f9144035bca79_116_0.png)

就模型参数而言，除了隐藏层的单元数外，添加到输入数据的噪声量也是 DA 中的一个参数。这里，损坏级别设置为 0.3。通常，该值常设置为 0.1 ~ 0.3：

```java
double corruptionLevel = 0.3;
```

从构建模型到训练的流程与 RBM 相同。虽然在 RBM 中这种训练方法称为 contrastiveDivergence，但在 DA 中它简单地设为 train：

```java
// construct DA
DenoisingAutoencoders nn = new DenoisingAutoencoders(nVisible,
nHidden, null, null, null, rng);

// train
for (int epoch = 0; epoch < epochs; epoch++) {
    for (int batch = 0; batch < minibatch_N; batch++) {
        nn.train(train_X_minibatch[batch], minibatchSize,
            learningRate, corruptionLevel);
    }
}
```

train 的内容如理论部分所述。首先，对输入数据添加噪声，然后对其进行编码和解码：

```java
// add noise to original inputs
double[] corruptedInput = getCorruptedInput(X[n], corruptionLevel);

// encode
double[] z = getHiddenValues(corruptedInput);

// decode
double[] y = getReconstructedInput(z);
```

添加噪声的过程，如前所述，是将数据对应部分的值强制置为 0：

```java
public double[] getCorruptedInput(double[] x, double corruptionLevel)
{
    double[] corruptedInput = new double[x.length];

    // add masking noise
    for (int i = 0; i < x.length; i++) {
        double rand_ = rng.nextDouble();

        if (rand_ < corruptionLevel) {
            corruptedInput[i] = 0.;
        } else {
            corruptedInput[i] = x[i];
        }
    }

    return corruptedInput;
}
```

其他过程只是简单的激活和传播，这里就不详细说明了。梯度的计算遵循数学方程：

```java
// calculate gradients

// vbias
double[] v_ = new double[nVisible];

for (int i = 0; i < nVisible; i++) {
    v_[i] = X[n][i] - y[i];
    grad_vbias[i] += v_[i];
}

// hbias
double[] h_ = new double[nHidden];

for (int j = 0; j < nHidden; j++) {
    for (int i = 0; i < nVisible; i++) {
        h_[j] = W[j][i] * (X[n][i] - y[i]);
    }
    h_[j] *= z[j] * (1 - z[j]);
    grad_hbias[j] += h_[j];
}

// W
for (int j = 0; j < nHidden; j++) {
    for (int i = 0; i < nVisible; i++) {
        grad_W[j][i] += h_[j] * corruptedInput[i] + v_[i] * z[j];
    }
}
```

与 RBM 相比，DA 的实现也相当简单。当你测试（重构）模型时，不需要损坏数据。如标准神经网络一样，只需根据网络的权重对给定的输入进行前向传播即可：

```java
public double[] reconstruct(double[] x) {
    double[] z = getHiddenValues(x);
    double[] y = getReconstructedInput(z);
    return y;
}
```

## 堆叠去噪自编码器（SDA）

SDA 是堆叠了 DA 层的深度神经网络。与 DBN 由 RBM 和逻辑回归组成相同，SDA 由 DA 和逻辑回归组成：

![](img/9315e45972ec0fbaf15f9144035bca79_119_0.png)

DBN 和 SDA 的实现流程并没有太大不同。尽管 RBM 和 DA 在预训练中存在差异，但微调的内容完全相同。因此，可能不需要太多解释。
