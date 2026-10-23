
RBM 是基于能量的模型，可见层或隐藏层的状态被视为随机变量。我们将按顺序查看方程。首先，每个可见单元通过网络传播到隐藏单元。此时，每个隐藏单元根据其传播输入生成的概率分布取二值：

$$p(h_j=1|v)=\sigma\left(\sum_{i=1}^{D} w_{ij} v_i + c_j\right)$$

这里，$c_j$ 是隐藏层的偏置，$\sigma$ 表示 sigmoid 函数。

这次，它反过来通过同一网络从隐藏层传播到可见层。与前一种情况一样，每个可见单元根据传播值生成的概率分布取二值。

$$p(v_i=1|h)=\sigma\left(\sum_{j=1}^{M} w_{ij} h_j + b_i\right)$$

这里，$b_i$ 是可见层的偏置。可见单元的值预计与原始输入值匹配。这意味着如果 $W$ 作为模型参数的网络权重，以及可见层和隐藏层的偏置 $b$、$c$，表示为向量参数 $\theta$，它学习 $\theta$，以使上面可以获得的概率 $p(v|\theta)$ 接近 $v$ 的分布。

为此学习，需要定义能量函数，即评价函数。能量函数如下所示：

$$E(v,h) = -b^T v - c^T h - h^T W v$$

$$= -\sum_{i=1}^{D} b_i v_i - \sum_{j=1}^{M} c_j h_j - \sum_{j=1}^{M}\sum_{i=1}^{D} h_j w_{ij} v_i$$

此外，显示网络行为的联合概率密度函数可以表示如下：

$$p(v,h)=\frac{1}{Z}\exp(-E(v,h))$$

$$Z=\sum_{v,h}\exp(-E(v,h))$$

根据前面的公式，将确定参数训练的方程。我们可以得到以下方程：

$$p(v\mid\theta)=\sum_{h}p(v,h)=\frac{1}{Z}\sum_{h}\exp(-E(v,h))$$

因此，**对数似然**可以表示如下：

$$\ln L(\theta\mid v)=\ln p(v\mid\theta)$$

$$=\ln\left(\frac{1}{Z}\sum_{h}\exp(-E(v,h))\right)$$

$$=\ln\sum_{h}\exp(-E(v,h))-\ln\sum_{v,h}\exp(-E(v,h))$$

然后，我们将计算相对于模型参数的每个梯度。导数可以按如下方式计算：

$$\frac{\partial \ln L(\theta | v)}{\partial \theta} = \frac{\partial}{\partial \theta}\left( \ln \sum_h \exp(-E(v,h)) \right) - \frac{\partial}{\partial \theta}\left( \ln \sum_{v,h} \exp(-E(v,h)) \right)$$

$$= -\frac{1}{\sum_h \exp(-E(v,h))} \sum_h \exp(-E(v,h)) \frac{\partial E(v,h)}{\partial \theta}$$

$$= +\frac{1}{Z} \sum_{v,h} \exp(-E(v,h)) \frac{\partial E(v,h)}{\partial \theta}$$

$$= -\sum_h p(h|v) \frac{\partial E(v,h)}{\partial \theta} + \sum_{v,h} p(v,h) \frac{\partial E(v,h)}{\partial \theta}$$

中间的一些方程很复杂，但在模型和原始数据的概率分布方面却变得简单。

因此，每个参数的梯度如下所示：

$$\frac{\partial \ln L(\theta | v)}{\partial w_{ij}} = -\sum_h p(h|v) \frac{\partial E(v,h)}{\partial w_{ij}} + \sum_{v,h} p(v,h) \frac{\partial E(v,h)}{\partial w_{ij}}$$

$$= \sum_h p(h|v) h_j v_i - \sum_v p(v) \sum_h p(h|v) h_j v_i$$

$$= p(H_j=1|v) v_i - \sum_v p(v) p(H_j=1|v) v_i$$

$$\frac{\partial \ln L(\theta | v)}{\partial b_i} = v_i - \sum_v p(v) v_i$$

$$\frac{\partial \ln L(\theta | v)}{\partial c_j} = p(H_j=1|v) - \sum_v p(v) p(H_j=1|v)$$

那么，我们可以找到梯度方程，但在直接应用该方程时会遇到问题。考虑 $\sum_v p(v)$ 项。该项意味着我们必须为所有 $\{0, 1\}$ 模式计算概率分布，这些模式可以假设为包含数据中实际上不存在的模式的输入数据。

我们可以很容易想象该项如何导致组合爆炸，这意味着我们无法在现实的时间范围内解决它。为了解决这个问题，引入了使用 Gibbs 采样近似数据的方法，称为 **对比散度 (CD)**。现在让我们看看这种方法。

这里，$v^{(0)}$ 是输入向量。此外，$v^{(k)}$ 是通过使用该输入向量采样 k 次可以获得的输入（输出）向量。

然后，我们得到：

$$h_j^{(k)} \sim p\big(h_j \mid v^{(k)}\big)$$

$$v_i^{(k+1)} \sim p\big(v_i \mid h^{(k)}\big)$$

因此，在重复 Gibbs 采样后近似 $p(v)$ 时，对数似然函数的导数可以表示如下：

$$\frac{\partial \ln L(\theta \mid v)}{\partial \theta} = -\sum_h p(h \mid v)\frac{\partial E(v,h)}{\partial \theta} + \sum_{v,h} p(v,h)\frac{\partial E(v,h)}{\partial \theta}$$

$$\approx -\sum_h p(h \mid v^{(0)})\frac{\partial E(v^{(0)},h)}{\partial \theta} + \sum_h p(h \mid v^{(k)})\frac{\partial E(v^{(k)},h)}{\partial \theta}$$

因此，模型参数可以表示如下：

$$w_{ij}^{(\tau+1)} = w_{ij}^{(\tau)} + \eta\big(p\big(H_j = 1 \mid v^{(0)}\big)v_i^{(0)} - p\big(H_j = 1 \mid v^{(k)}\big)v_i^{(k)}\big)$$

$$b_i^{(\tau+1)} = b_i^{(\tau)} + \eta\big(v_i^{(0)} - v_i^{(k)}\big)$$

$$c_j^{(\tau+1)} = c_j^{(\tau)} + \eta\big(p\big(H_j = 1 \mid v^{(0)}\big) - p\big(H_j = 1 \mid v^{(k)}\big)\big)$$

这里，τ 是迭代次数，η 是学习率。如前面的公式所示，通常执行 k 次采样的 CD 表示为 CD-k。众所周知，在将算法应用于实际问题时，CD-1 已足够。

现在，让我们回顾 RBM 的实现。包结构如以下屏幕截图所示：

![](img/9315e45972ec0fbaf15f9144035bca79_100_0.png)

让我们查看 RestrictedBoltzmannMachines.java 文件。因为 main 方法的第一部分只是定义模型所需的变量并生成演示数据，所以我们这里不看它。

因此，在生成模型实例的部分，你可能会注意到参数中有许多 null 值：

```java
// construct RBM
RestrictedBoltzmannMachines nn = new
RestrictedBoltzmannMachines(nVisible, nHidden, null, null, null,
rng);
```

当你查看构造函数时，你可能会知道这些 null 值是 RBM 的权重矩阵、隐藏单元的偏置和可见单元的偏置。我们在这里将参数定义为 null，因为它们是用于 DBN 的实现。在构造函数中，它们按如下方式初始化：

```java
if (W == null) {
    W = new double[nHidden][nVisible];
    double w_ = 1. / nVisible;

    for (int j = 0; j < nHidden; j++) {
        for (int i = 0; i < nVisible; i++) {
            W[j][i] = uniform(-w_, w_, rng);
        }
    }
}

if (hbias == null) {
    hbias = new double[nHidden];

    for (int j = 0; j < nHidden; j++) {
        hbias[j] = 0.;
    }
}

if (vbias == null) {
    vbias = new double[nVisible];

    for (int i = 0; i < nVisible; i++) {
        vbias[i] = 0.;
    }
}
```

下一步是训练。对每个小批量应用 CD-1：

```java
// train with contrastive divergence
for (int epoch = 0; epoch < epochs; epoch++) {
    for (int batch = 0; batch < minibatch_N; batch++) {
        nn.contrastiveDivergence(train_X_minibatch[batch],
minibatchSize, learningRate, 1);
    }
    learningRate *= 0.995;
}
```

现在，让我们深入 RBM 的核心点，即 contrastiveDivergence 方法。CD-1 在实际运行此程序时可以获得足够的解（因此演示中 k = 1），但该方法也定义为处理 CD-k：

```java
// CD-k : CD-1 is enough for sampling (i.e. k = 1)
sampleHgivenV(X[n], phMean_, phSample_);

for (int step = 0; step < k; step++) {

    // Gibbs sampling
    if (step == 0) {
        gibbsHVH(phSample_, nvMeans_, nvSamples_, nhMeans_,
nhSamples_);
    } else {
        gibbsHVH(nhSamples_, nvMeans_, nvSamples_, nhMeans_,
nhSamples_);
    }

}
```

看起来 CD-k 中使用了两种不同类型的方法 sampleHgivenV 和 gibbsHVH，但当你查看 gibbsHVH 时，可以看到：

```java
public void gibbsHVH(int[] h0Sample, double[] nvMeans, int[]
nvSamples, double[] nhMeans, int[] nhSamples) {
    sampleVgivenH(h0Sample, nvMeans, nvSamples);
    sampleHgivenV(nvSamples, nhMeans, nhSamples);
}
```

因此，CD-k 只由两个采样方法 sampleVgivenH 和 sampleHgivenV 组成。

如方法名所示，sampleHgivenV 是根据给定可见单元的值设置隐藏层中生成的概率分布和采样数据的方法，反之亦然：

```java
public void sampleHgivenV(int[] v0Sample, double[] mean, int[] sample)
{

    for (int j = 0; j < nHidden; j++) {
        mean[j] = propup(v0Sample, W[j], hbias[j]);
        sample[j] = binomial(1, mean[j], rng);
    }

}
```
