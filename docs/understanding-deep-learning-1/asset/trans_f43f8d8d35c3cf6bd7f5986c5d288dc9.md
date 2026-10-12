

# 当深度变得非常大时，神经网络更难拟合

由于梯度爆炸和消失（图 7.7）以及梯度破碎（图 11.3），当深度变得非常大时，神经网络更难拟合。然而，这些（可以说）是实际的数值问题。没有确凿证据表明，随着网络深度的增加，底层损失函数在根本上变得更凸或更不凸。[图 20.2](#c020.xhtml#c20-fig-0002) 确实显示，对于具有随机标签和 He 初始化的 MNIST 数据，更深的网络在更少的迭代次数中完成训练。然而，这可能是因为（i）更深网络中的梯度更陡峭，或者（ii）He 初始化只是让更宽、更浅的网络起始于离最优参数更远的位置。

Frankle & Carbin (2019) 表明，对于像 `VGG` 这样的小型网络，如果你（i）训练网络，（ii）剪除幅度最小的权重，以及（iii）从相同的初始权重重新训练，可以获得相同或更好的性能。如果权重被随机重新初始化，这行不通。他们得出结论，原始的过参数化网络包含小型的可训练子网络，这些子网络足以提供性能。他们将其称为*彩票假设*，并将这些子网络称为*中奖彩票*。这表明有效子网络的数量可能在拟合中起关键作用。这（也许）随固定参数量下的网络深度而变化，但对此想法缺乏精确的表征。

---

## Notebook 20.3: 彩票假设

---

## 20.3 损失函数的性质

上一节讨论了影响神经网络训练难易程度的因素。参数数量（过参数化程度）和激活函数的选择都很重要。令人惊讶的是，数据集的选择、拟合算法的随机性以及正则化的使用似乎都不重要。没有确凿证据表明（在参数量固定的情况下）网络深度很重要（除了由梯度爆炸/消失/破碎引起的数值问题）。本节从另一个角度探讨同一主题，通过考察损失函数的经验性质。大多数证据来自全连接网络和 CNN；Transformer 网络的损失函数了解较少。

### 20.3.1 多个全局最小值

我们*预期*深度网络的损失函数拥有一大族等价的全局最小值。在全连接网络中，每一层的隐藏单元及其相关权重可以排列组合而不改变输出。在卷积网络中，适当地排列通道和卷积核不会改变输出。我们可以在任何 `ReLU` 函数之前乘以权重，在之后除以一个正数，而不改变输出。使用 `BatchNorm` 会诱导出另一组冗余，因为每个隐藏单元或通道的均值和方差被重置。

上述修改对*每个*输入都产生相同的输出。然而，全局最小值仅取决于训练数据点的输出。在过参数化网络中，也将存在在数据点处表现相同但在数据点之间表现不同的解族。所有这些也是全局最小值。

### 20.3.2 通往最小值的路径

Goodfellow 等人 (2015b) 考察了初始参数和最终值之间的直线。他们表明，沿这条线的损失函数通常单调下降（除了起始附近有时有一个小凸起）。这种现象在几种不同类型的网络和激活函数中均被观察到（[图 20.5a](#c020.xhtml#c20-fig-0005)）。

![Figure 20.5 Linear slices through loss function. a) A two-layer fully connected ReLU network is trained on MNIST. The loss along a straight line starting at the initial parameters (δ=0) and finishing at the trained parameters (δ=1) descends monotonically. b) However, in this two-layer fully connected MaxOut network on MNIST, there is an increase in the loss along a straight line between one solution (δ=0) and another (δ=1). Adapted from Goodfellow et al. (2015b).](images/c20-fig-0005.jpg)

[图 20.5](#c020.xhtml#c20-fig-0005a) 损失函数的线性切片。a) 一个两层全连接 `ReLU` 网络在 MNIST 上训练。沿着从初始参数（*δ*=0）开始到训练后参数（*δ*=1）结束的直线，损失单调下降。b) 然而，在这个 MNIST 上的两层全连接 `MaxOut` 网络中，沿着一个解（*δ*=0）和另一个解（*δ*=1）之间的直线，损失有所增加。改编自 Goodfellow 等人 (2015b)。

当然，真实的优化轨迹并非沿直线进行。然而，Li 等人 (2018b) 发现它们确实位于低维子空间中。他们将其归因于损失地形中存在大的、近似凸的区域，这些区域早早地捕获轨迹并将其引导至几个重要方向。令人惊讶的是，Li 等人 (2018a) 表明，如果优化*被约束*在随机低维子空间中，网络仍能良好训练（[图 20.6](#c020.xhtml#c20-fig-0006)）。

![Figure 20.6 Subspace training. A fully connected network with two hidden layers, each with 200 units was trained on MNIST. Parameters were initialized using a standard method but then constrained to lie within a random subspace. Performance reaches 90% of the unconstrained level when this subspace is 750D (termed the intrinsic dimension), which is 0.4% of the original parameters. Adapted from Li et al. (2018a).](images/c20-fig-0006.jpg)

[图 20.6](#c020.xhtml#c20-fig-0006a) 子空间训练。一个具有两个隐藏层（每层 200 个单元）的全连接网络在 MNIST 上训练。参数使用标准方法初始化，但随后被约束在随机子空间内。当该子空间为 750D（称为*内在维度*）时，性能达到无约束水平的 90%，这仅占原始参数的 0.4%。改编自 Li 等人 (2018a)。

Li & Liang (2018) 表明，训练期间参数的相对变化随着网络宽度的增加而减小；对于更大的宽度，参数从较小的值开始，按这些值的较小比例变化，并在更少的步骤内收敛。

### 20.3.3 最小值之间的连接

Goodfellow 等人 (2015b) 检查了两个独立找到的最小值之间直线上的损失函数。他们在两者之间看到了损失的显著增加（[图 20.5b](#c020.xhtml#c20-fig-0005)）；好的最小值通常不是线性连通的。然而，Frankle 等人 (2020) 表明，如果网络最初以相同方式训练，随后通过使用不同的 SGD 噪声和增强被允许发散，这种增加就会消失。这表明解在训练早期受到约束，并且*某些*最小值族是线性连通的。

Draxler 等人 (2018) 在 CIFAR-10 数据集上找到了性能良好（但不同）的最小值。他们随后表明，可以从一个构建路径到另一个，使得损失函数沿此路径保持较低。他们得出结论，存在一个单一的连通低损失流形（[图 20.7](#c020.xhtml#c20-fig-0007)）。随着网络宽度和深度的增加，这似乎越来越真实。Garipov 等人 (2018) 和 Fort & Jastrzębski (2019) 提出了其他连接最小值的方案。

