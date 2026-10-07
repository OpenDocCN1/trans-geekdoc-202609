

# 第 14 章：第 5 部分
深度学习

BM 项目 - 第 2 部分：构建 RBM

## 14.5.1 RBM模型

为了创建我们参数为：*可见节点数 = nv* 和 *隐藏节点数 = nh* 的第一个 RBM 对象。

- 该对象将在调用 *__init__()* 时初始化，带有偏置 *a, b* 和权重 *W*。
- 训练过程中，其他函数 *sample_h()*、*sample_v()* 和 *train()* 将在训练期间使用，除非它们被调用，否则它们不会执行任何操作。

*train_tensor[0]* 是 *train_tensor* 第一列的长度，对应于*电影 (movies)*。我们有 1682 个可见节点。

- 关于隐藏节点：在这里我们可以为 *nh* 选择任意数字。隐藏节点对应于 RBM 模型将检测的某些*特征*。这些特征可以是*类型 (GENRE)**演员 (ACTORS)**导演 (DIRECTORS)*、电影是否获得奥斯卡等。
隐藏节点的数量对应于我们想要检测的特征数量。
nh = 100

所以，假设我们想从检测 100 个特征开始。现在很难说特征的最佳数量。我们的代码可以*之后进行调整*。

- 批次大小 (Batch size)：在创建批次 *a & b* 添加额外维度时，我们已经提到了批的概念。这里的维度由 1 表示。因此，1 对应于*批 (batch)*。
```python
self.a = torch.randn(1, nh)
self.b = torch.randn(1, nv)
```

- 当我们训练算法时，将在*批次观测 (batch observations)* 之后（而不是每次观测）更新*权重*。每个批次包含一定数量的观测。
这也是暂时的。我们可以调整它来改进模型。

- 现在，我们可以设置 *batch_size = 1*，在这种情况下，我们会在每次进入网络的*观测后后更新权重*。对于大量数据，这将非常慢。

- 为了快速训练，我们使用较大的批次大小，例如 *batch_size = 100*。由于我们有 943 次观测，当批次大小为 100 时，训练将运行非常快。
```python
batch_size = 100
```

最后，我们使用参数 *nv nh* 创建 RBM 对象。

```python
# creating RBM model
v = len(train_tensor[0])
h = 100
batch_size = 100

rbm = RBM(nv, nh)
```

## 14.5.2 训练 RBM模型 - 第 1 部分

为了模拟每个时期 (epoch)，我们使用一个循环。该循环将运行特定的 epoch。我们只需要将不同的函数（我们在 RBM 类中创建的）包含在这个循环内部即可。

我们首先设置 epoch 的数量。让我们选择 10 个 epoch。因为我们只有 943 次观测，而且除此之外我们只有二值的 0 和 1，很快就能达到收敛。

```python
# Training the RBM
nb_epoch = 10
for epoch in range(1, nb_epoch + 1):
    train_loss = 0
    s = 0.0
```

- 对于每个 epoch，我们所有的观测将进入网络。
- 在每个批次观测通过网络后，我们更新权重。
- 最后，我们将看到对于原始未评分电影具有新评分的最终节点。

在循环内部：注意，对于我们使用的任何学习算法，我们都使用损失函数来衡量预测与真实评分之间的误差。

- 损失 (Loss)：在这次训练中，我们将预测评分与训练set的评分进行比较。
- 基本上，我们衡量预测评分（即 0 或 1）与真实评分（也为 0 或 1）之间的差异。
- 为了衡量损失，我们可以使用不同的方法。在 RBM 中，我们使用绝对值的简单差，它衡量预测评分与真实评分之间的绝对差。
- 但最常用的损失方法是 RMSE，即均方根误差，它是预测评分与真实评分之间平方差平均值的平方根。我们将在下一章中使用 RMSE 构建自动编码器 (AutoEncoders)。

```python
train_loss = 0
```

我们在开始之前将其初始化为零，在开始之前损失等于 0。然后当我们在预测评分与真实评分之间发现错误时，损失将会增加。计数器：我们需要一个计数器，将其命名为 "s"。

```python
s = 0.0
```

为了创建一个浮点数，我们使用 0.0。或者 0.，也可以的。

嵌套 for 循环批次：当我们针对一个用户制作 sample(h), sample_v(c) 和 train() 函数时。

- 但采样和对比散度算法 (contrastive of divergence) 必须对所有用户进行，记住是对批次中的所有用户。
- 为了获取这些用户批次，我们需要另一个 for 循环（嵌套 for 循环）。

我们遍历所有用户按 batch_size 增加计数。这将数据集分成批次。

```python
for u_id in range(0, nb_users - batch_size):
```

由于我们按 batch_size 递增循环，上限必须是 nb_users - batch_size。这创建了批次，对于计数器 0 到 99，100 到 199。

这就是我们从零开始学习的方式。一切发生在这个循环中。

```python
# For loop syntax:
for i in range(lower_bound, upper_bound, Increment):
```

在嵌套循环内部：
我们将分别获取我们的输入和目标。

- 我们的输入是当前循环处理的特定用户对所有电影的评分。
- 目标是在开头与输入相同。

由于输入将进入吉布斯链 (Gibbs chain) 并在每个可见节点更新以获取新评分，因此输入将改变，而目标将保持其初始值。

输入向量：我们使用向量 vk，它将通过吉布斯链并在每轮循环中更新。vk 将是吉布斯采样的输出。此时，vk 实际上与输入批次相同（已存在的批次中的用户评分）。为了获取从 u_id 到 batch_size 的批次中的所有用户，我们使用以下代码：

```python
vk = train_set_tensor[u_id:u_id + batch_size]
```

我们从 train_set 中从 u_id 到 u_id + batch_size 选择运行。

目标：target 作为输入的初始值，但它将保持不变。它是我们最后想要比较的原始评分，或者是我们的预测评分。我们需要衡量预测与真实评分之间的误差来计算 train_loss。所以，我们将得到 v0，即我们在该批次中 100 个用户已评分的电影评分：

```python
v0 = train_set_tensor[u_id:u_id + batch_size]
```

初始概率：在开始带有吉布斯采样的对比散度 (Contrastive Divergence) 之前，我们需要指定初始概率。初始概率实际上是 phi(h)，即开始 1 的隐藏节点给出真实评分的概率 p(H_1|r(0)) = phi。

我们使用 RBM 类中的 sample(h) 函数。因为我们正在获取给定初始可见节点隐藏节点 = 1 的概率。因为 sample(h) 返回 p_h_given_v，这意味着它将使用 _ 返回 p_h_given_v0，由于此 sample(h) 同时也返回概率和样本（伯努利采样）“return p_h_given_v, torch.bernoulli(p_h_given__)”，我们必须使用一个 Python 技巧来只获取函数返回的第一个元素，即 p_h_given_v，这个 Python 技巧是在这里添加一个逗号和下划线。

```python
ph0_ = rbm.sample_h(v0)
```

sample_h() 的参数是 x，x 对应于可见节点，因为我们想要采样隐藏节点。哪些可见节点：我们将采样开始时的可见节点，即 v0。那是我们批次中所有用户电影的原始评分。

```python
# Training the RBM
b_epoch = 10
for epoch in range(nb_epoch + epoch + 1):
    s = 0.0
    for u_id in range(0, nb_users - batch_size, batch_size):
        vk = train_set_tensor[u_id:u_id + batch_size]
        v0 = train_set_tensor[u_id:u_id + batch_size]
        ph0_ = rbm.sample_h(v0)
        for k in range(10):
```

## 14.5.3 训练 RBM模型 - 第 2 部分：k 步 CD

另一个嵌套 for 循环：用于 k 步对比散度 (k-step CD)。在这个循环中我们将制作吉布斯链，我们将使用 k 步随机游走。让循环变量 k 保持在 range(10) 中。

实际上，我们 k 步的随机游走吉布斯采样是一种 MCMC 技术（马尔可夫链蒙特卡洛技术）。

