

运行此程序会读取50,000张MNIST训练图像，并准备一个包含250,000张训练图像的扩展训练集。然后我们可以使用这些训练图像来训练我们的网络。我们将使用与上面相同的网络，采用整流线性单元。在我的初始实验中，我减少了训练时代数——这很合理，因为我们使用了5倍的数据量。但事实上，扩展数据被证明能显著减轻过拟合的影响。经过一些实验后，我最终又回到了训练60个时代。无论如何，让我们来训练：

```
>>> expanded_training_data, _, _ = network3.load_data_shared(
"../data/mnist_expanded.pkl.gz")
>>> net = Network([
ConvPoolLayer(image_shape=(mini_batch_size, 1, 28, 28),
filter_shape=(20, 1, 5, 5),
poolsize=(2, 2),
activation_fn=ReLU),
ConvPoolLayer(image_shape=(mini_batch_size, 20, 12, 12),
filter_shape=(40, 20, 5, 5),
poolsize=(2, 2),
activation_fn=ReLU),
FullyConnectedLayer(n_in=40*4*4, n_out=100, activation_fn=ReLU),
SoftmaxLayer(n_in=100, n_out=10))
>>> net.SGD(expanded_training_data, 60, mini_batch_size, 0.03,
validation_data, test_data, lmbda=0.1)
```

使用扩展训练数据，我获得了99.37%的训练准确率。因此，这个几乎微不足道的改变在分类准确率上带来了实质性的提升。确实，如前面讨论过的，通过算法扩展数据的想法可以进一步深入。为了提醒你之前讨论中的一些结果风格：2003年，Simard、Steinkraus和Platt*使用了一个与我们网络非常相似的神经网络（包含两个卷积-池化层，接着是一个拥有100个神经元的隐藏全连接层），将其MNIST性能提升到了99.6%。他们的架构存在一些细节差异——例如，他们没有使用整流线性单元的优势——但性能提升的关键在于扩展训练数据。他们通过旋转、平移和倾斜MNIST训练图像来实现这一点。他们还开发了一种“弹性失真”过程，用于模拟人书写时手部肌肉所经历的随机震荡。通过结合所有这些过程，他们大幅增加了训练数据的有效规模，从而达到了99.6%的准确率。

> *应用于可视文档分析的卷积神经网络最佳实践，作者：Patrice Simard, Dave Steinkraus, 和 John Platt (2003)*

## 问题

- 卷积层的理念是跨图像以不变方式行为。因此，当我们所做的只是翻译输入数据时，网络能学到更多似乎令人惊讶。你能解释一下为什么这实际上很合理吗？

插入一个额外的全连接层：我们能做得更好吗？一种可能性是使用与上面完全相同的程序，但扩展全连接层的大小。我尝试了300个和1,000个神经元，分别获得了99.46%和99.43%的结果。这很有趣，但并不真正构成对先前结果（99.37%）的令人信服的胜利。

添加一个额外的全连接层呢？让我们尝试插入一个额外的全连接层，这样我们就有两个拥有100个隐藏神经元的全连接层了：

```
>>> net = Network([
    ConvPoolLayer(image_shape=(mini_batch_size, 1, 28, 28),
                  filter_shape=(20, 1, 5, 5),
                  poolsize=(2, 2),
                  activation_fn=ReLU),
    ConvPoolLayer(image_shape=(mini_batch_size, 20, 12, 12),
                  filter_shape=(40, 20, 5, 5),
                  poolsize=(2, 2),
                  activation_fn=ReLU),
    FullyConnectedLayer(n_in=40*4*4, n_out=100, activation_fn=ReLU),
    FullyConnectedLayer(n_in=100, n_out=100, activation_fn=ReLU),
    SoftmaxLayer(n_in=100, n_out=10)], mini_batch_size)
>>> net.SGD(expanded_training_data, 60, mini_batch_size, 0.03,
           validation_data, test_data, lmbda=0.1)
```

这样做后，我获得了99.43%的测试准确率。同样，扩展的网络帮助不大。使用包含300和1,000个神经元的全连接层运行类似实验，结果分别为99.48%和99.47%。这令人鼓舞，但仍未达到真正决定性的胜利。

这里发生了什么？是扩展或额外的全连接层对MNIST确实没有帮助吗？还是可能我们的网络有能力做得更好，但我们学习的方式不对？例如，也许我们可以使用更强的正则化技术来减少过拟合的倾向。一种可能性是第3章中介绍的dropout技术。回顾一下，dropout的基本理念是在训练网络时随机移除单个激活值。这使得模型对单个证据片段的丢失更具鲁棒性，因此不太可能依赖于训练数据的特定特性。让我们尝试将dropout应用到最后的全连接层：

```
>>> net = Network([
    ConvPoolLayer(image_shape=(mini_batch_size, 1, 28, 28),
    filter_shape=(20, 1, 5, 5),
    pool_size=(2, 2),
    activation_fn=ReLU),
    ConvPoolLayer(image_shape=(mini_batch_size, 20, 12, 12),
    filter_shape=(40, 20, 5, 5),
    pool_size=(2, 2),
    activation_fn=ReLU),
    FullyConnectedLayer(
    n_in=40*4*4, n_out=1000, activation_fn=ReLU, p_dropout=0.5),
    FullyConnectedLayer(
    n_in=1000, n_out=1000, activation_fn=ReLU, p_dropout=0.5),
    SoftmaxLayer(n_in=1000, n_out=10, p_dropout=0.5)],
    mini_batch_size)
>>> net.SGD(expanded_training_data, 40, mini_batch_size, 0.03,
    validation_data, test_data)
```

使用此方法，我们获得了99.60%的准确率，与之前的结果相比是实质性的改进，尤其是与我们的主要基准——拥有100个隐藏神经元的网络（我们达到了99.37%）相比。

有两个变化值得注意。

第一，我将训练时代数减少到40：dropout减少了过拟合，因此我们学习得更快。

第二，全连接隐藏层拥有1,000个神经元，而不是之前使用的100个。当然，dropout在训练期间有效地省略了许多神经元，因此进行一些扩展是可以预期的。事实上，我尝试了300和1,000个隐藏神经元的实验，并用1,000个隐藏神经元获得了（非常略微）更好的验证性能。

### 使用网络集成

进一步提高性能的简便方法是创建多个神经网络，然后让它们投票以确定最佳分类。例如，假设我们使用上面的方法训练了5个不同的神经网络，每个网络的准确率都接近99.6%。尽管这些网络的准确率都相似，但由于随机初始化的不同，它们很可能会犯不同的错误。让我们5个网络进行投票，可能会得出比任何单个网络都更好的分类结果，这似乎是合理的。

这听起来好得令人难以置信，但这种集成方法在神经网络和其他机器学习技术中都是常见的技巧。并且它确实带来了进一步的改进：我们最终达到了99.67%的准确率。换句话说，我们的网络集成在10,000张测试图像中只有33张分类错误。

测试集中剩余的错误如下所示。右上角的标签是根据MNIST数据的正确分类，而右下角则是我们的网络集成输出的标签：

![](img/9499fc06bad8b4a2610710f5e9d6ea39_245_0.png)

详细查看这些错误是值得的。前两个数字，6和5，是我们集成网络的真实错误。然而，它们也是可以理解的错误，是人类可能合理犯下的错误。那个6确实很像0，而5看起来很像3。第三张图像，本应是8，但在我看来更像9。因此，我这里支持网络集成：我认为它比最初画出该数字的人做得更好。另一方面，第四张图像，那个6，似乎确实被我们的网络分类错误了。

依此类推。在大多数情况下，我们网络的选择看起来至少是合理的，在某些情况下，它们对数字的分类比最初书写该数字的人做得更好。总体而言，我们的网络提供了卓越的性能，尤其是考虑到它们正确分类了未显示的9,967张图像。在那

