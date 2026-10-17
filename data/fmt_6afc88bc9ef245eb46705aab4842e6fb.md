
`self.fc4 = nn.Linear(20, nb_movies)`

现在这是最后一层，输出层中的神经元数量将与输入层相同，因为我们正在再次重建输入向量。

因此，输出向量的维度应该与输入向量相同。
因此，输出层中的神经元数量也是 `nb_movies`。

### 激活函数
现在我们必须指定一个激活函数，当观测值进入网络时激活神经元。

- 例如，如果有人对恐怖电影给出好评，这将激活恐怖电影类型的特定特征。这将通过某个特定的函数完成。
- 有不同的激活函数，我们尝试了整流器激活函数（Rectifier Activation）和 Sigmoid 激活函数，结果证明在全连接之间使用 Sigmoid 激活获得了更好的结果。

```python
self.activation = nn.Sigmoid()
```

所以，为了获得 Sigmoid 激活，我们使用模块中的 `nn.Sigmoid()`，它不需要任何参数。
稍我们可以尝试整流器激活函数和 Sigmoid 激活函数的组合，以获得更好的结果。

```python
class StackedAutoEncoders(nn.Module):
    def __init__(self):
        super(StackedAutoEncoders, self).__init__()
        self.fc1 = nn.Linear(nb_movies, 20)
        self.fc2 = nn.Linear(20, 10)
        self.fc3 = nn.Linear(10, 20)
        self.fc4 = nn.Linear(20, nb_movies)
```

## 15.4 SAE准则：用于 SAE 架构的优化器

现在我们创建一个名为 *sae* 的对象。由于我们没有在 `StackedAutoEncoders` 的 `__init__` 函数中指定任何参数，因此在这里不需要传递任何参数。

```python
sae = StackedAutoEncoders()
```

- **Criterion（准则）**：我们需要这个准则来训练模型。

```python
criterion = nn.MSELoss()
```

- 它基本上是*损失函数*的*准则*，而*损失函数*将是均方误差，因此我们使用了来自 nn 模块的 `nn.MSELoss()` 类。

- **Optimizer（优化器）**：最后我们需要的是*优化器*。它非常像 *Keras*。优化器将应用随机梯度下降来控制不同的权重，以减少每个 epoch（轮次）的*误差*。
- 我们将使用 *torch* 来实现我们的优化器。可以使用 *ADAM* 或 *RMSProp-optimizer*。根据实验，*RMSProp* 提供了更好的结果。

```python
optimizer = optim.RMSprop(sae.parameters(), lr=0.01, weight_decay=0.5)
```

- **Arguments（参数）**：我们有件事：
  我们必须放入 *AutoEncoders* 的所有参数，即构建我们的 *StackedAutoEncoders* 架构的参数。
  我们不需要重写所有它们。简单的方法是使用 `sae.parameters()`，它可以从我们的 sae 中获取所有参数。
  `lr`：学习率。它取决于 epochs，我发现的一个良好值是 **0.01**。当然，我们可以调整它来获得更好的结果。
  `weight_decay`：权重衰减。指定衰减。衰减用于在每几个 *epochs* 之后降低*学习率*，以调节*收敛*。我们也可以调整它。根据我的实验，我发现的一个良好值是 0.5。

> Note：我们将参数应用在 sae 上，而不是 StackedAutoEncoders 类上。

```python
# 创建 SAE 的神经网络架构----
class StackedAutoEncoders(nn.Module):
    def __init__(self, nb):
        super(StackedAutoEncoders, self).__init__()
        self.fc1 = nn.Linear(nb_movies, 20)
        self.fc2 = nn.Linear(20, 10)
        self.fc3 = nn.Linear(10, 20)
        self.fc4 = nn.Linear(20, nb_movies)
        self.activation = nn.Sigmoid()

    def forward(self, x):
        x = self.activation(self.fc1(x))
        x = self.activation(self.fc2(x))
        x = self.activation(self.fc3(x))
        x = self.fc4(x)
        return x

sae = StackedAutoEncoders(nb)
criterion = nn.MSELoss()
optimizer = optim.RMSprop(sae.parameters(), lr=0.01, weight_decay=0.5)
```

现在我们的*神经网络*架构部分就结束了。接下来我们将实现训练，

## 15.5 训练 SAE 模型：嵌套循环和输入

我们的代码将帮助你优化代码，以便你可以在高维数据集上使用。在这里我们将使用一个包含 200,000 条评分的数据集。如果你想将此代码用于 100 万条评分的数据集或更大的数据集，需要一种尽可能节省内存的优化代码。

- 我们不会深入讨论某些技术细节，而且此外这个主题与 PyTorch 相关。最重要的是你理解：
  - 神经网络的架构是如何工作的。
  - 如何通过更改 `StackedAutoEncoders` 类中的层数和隐藏层中神经元的数量来填充我们的 `StackedAutoEncoders` 架构。
  - 你可以通过操作与激活函数相关的对象来尝试不同的激活函数组合。

- 我们将在 PyTorch 中使用相当先进的技术。
  - No. Epochs（轮次数）：第一步是定义 EPOCH 的数量，这是基于实验的。我们将训练 `StackedAutoEncoders` 200 个 EPOCHS。

- 外层循环 train_loss：第二步是建立嵌套 for 循环。外层遍历 epochs，内层循环将遍历每个 EPOCH 中的所有观测值。即所有用户将使用每个观测值与用户评分的相关性。
  - 在开始第二个循环之前，我们需要初始化 train_loss 和计数器。就像我们在 RBM 中做的那样。我们将对测试集的损失进行测试。
  - Counters（计数器）：计数器将统计至少评分过一部电影的用户数。其目的是优化内存，我们不会对没有评分过任何电影的用户进行计算。
  - 为了做到这一点，我们需要跟踪至少评分过一部电影的用户数。在这里，我们使用 `s = 0.` 来使其成为浮点类型。
  - 因为我们最终将使用 RMSE，所以使用浮点是为了确保整型型和浮点型不会引起任何问题。
  - 既然均方根误差是浮点数，那么计算均方根误差的所有元素都应该是浮点数。这并不是强制的，但只是为了避免（潜在问题）。

下一步是开始第二个循环：它将遍历所有观测值，即所有用户。内层循环将引入单个 EPOCH 中将发生的所有操作。
在第二个 for 循环内部：我们将使用之前之前创建的对象，通过我们的 `StackedAutoEncoders` 类来获取预测评分。

> 我们将在每个 EPOCH 上计算误差，以观察训练的演变。因为我们想优化这一点，所以跟踪它是否随着 EPOCHS 的增加而减少。

我们将应用优化器 `optim.RMSprop` 到随机梯度下降，以更新权重并引导收敛。

- 我们称为 id_User 的变量是 `range(nb_users)`，没有上限/下限，它为每个用户循环。
  - 因为我们需要训练集中观测值的索引，而我们训练观测值的索引不是从 0 到 193，而是从 0 到 942，`range(nb_users)` 将使这个范围从 0 到 942。

```python
for id_user in range(nb_users):
```

现在我们在循环内部应用输入向量，该特征的输入向量包含了该特定用户给出的所有电影的评分。

```python
input = Variable(train_tensor(id_user)).unsqueeze(0)
```

- `train_tensor[id_user]` 将获取 id_user 给所有电影的评分。id_user 是我们在循环中正在处理的用户。
  - 但 `train_tensor[id_user]` 是一个向量，PyTorch 甚至 Keras 中的网络无法接受单个的一维向量（即输入批次 Batch）。

对于我们的示例，`forward()` 函数将不会接受简单的一维向量作为输入。因此，我们需要添加一个额外的维度，将其转换为批次（这在 RBM 中是存在的，但方式不同）。

此外记住，我们已经在 CNN 中这样做过了，当我们使用 `predict` 函数预测图像是否包含猫或狗时。我们添加了一个维度，那个额外的维度用于批次：我们将我们的猫的输入图像放入批次中。

> 我们将在每个 EPOCH 上计算误差，以观察训练的演变。因为我们想优化这一点，所以跟踪它是否随着 EPOCHS 的增加而减少。

我们将应用优化器 `optim.RMSprop` 到随机梯度下降，以更新权重并引导收敛。

- 我们称为 id_User 的变量是 `range(nb_users)`，没有上限/下限，它为每个用户循环。
  - 因为我们需要训练集中观测值的索引，而我们训练观测值的索引不是从 0 到 193，而是从 0 到 942，`range(nb_users)` 将使这个范围从 0 到 942。

```python
for id_user in range(nb_users):
```

现在我们在循环内部应用输入向量，该特征的输入向量包含了该特定用户给出的所有电影的评分。

```python
input = Variable(train_tensor(id_user)).unsqueeze(0)
```

- `train_tensor[id_user]` 将获取 id_user 给所有电影的评分。id_user 是我们在循环中正在处理的用户。
  - 但 `train_tensor[id_user]` 是一个向量，PyTorch 甚至 Keras 中的网络无法接受单个的一维向量（即输入批次 Batch）。

输出：为了获取我们的预测评分向量，即网络最右侧的输出。我们将引入一个新变量名为

我们已经有了 `sae` 对象。因为该对象是 `StackedAutoEncoders` 类的实例，输入向量向网络的正传播过程在此完成。

`forward()` 返回网络的输出，即预测评分的向量。由于这个 `forward()` 函数是 `StackedAutoEncoders` 类的一部分，且我们在 `def __init__(self, ...)` 中使用了可变参数，因此我们可以使用 `sae` 对象的参数 `sae(x)`，这个 `x` 将传递给 `forward(x)`，`forward()` 将应用并返回修改后的 `x`。

在 `forward()` 函数中，输入将进行编码。这最终会返回预测评分向量。

```python
output = sae(input)
```

为了简单起见，我们重写了该条件：

```python
for epoch in range(1, nb_epoch+1):
    train_loss = 0
    for id_user in range(nb_users):
        input = Variable(train_set_tensor(id_user)).unsqueeze(0)
        target = input.clone()
```

```python
non_zero_ratings = torch.sum(target.data > 0)
if non_zero_ratings > 0:
    output = sae(input)
```

## 15.3.7 训练 sae 模型：loss & _corrector

现在我们在 `target` 中有了评分，在 `output` 中有了预测评分。在这一步中，我们优化内存和计算。

- 当我们应用随机梯度下降（SGD）时，我们确保梯度仅通过输入和目标向量计算。

```python
non_zero_ratings = torch.sum(target.data > 0)
if non_zero_ratings > 0:
    output = sae(input)
    target.require_grad = False
    output[target == 0] = 0
    loss = criterion(output, target)
mean_corrector = nb_movies.float(non_zero_ratings + 1e-10)
```

> `target.require_grad = False` 这里的梯度将确保我们不计算相对于目标的梯度，从而节省大量的计算量并优化代码。

> *output = 0* 仅针对非零值。我们不处理用户未评分的电影（即评分等于0的情况），但这仅针对输出向量。

- 我们取输出向量的值，即那些在目标向量（原始向量）中等于 0 的值。对于输出向量的这些索引，我们将这些索引对应的值设置为0（注意，我们在上一章处理 RBM 模型时也进行过这种操作）。

[评分为 0 的评分在编码和解码后开始发生变化。在这里我们使用 target 向量将它们重置为 0]

- 原因是，我们不想更新初始为 0（即用户未评分）的评分。这样在测量误差后，就不会对权重的更新产生影响：

- 在测量误差后，权重将通过 RMS Optimizer 进行更新，更新这些权重需要一些计算，而在计算过程中，这些 0 评分是——

- 所以，如果它们不等于零，就不会被计入计算。因此，为了节省内存，我们再次将它们设为零。

```python
criterion(output, target) = 使用 criterion 对象计算损失。我们输入的参数是真实值的 target 和预测评分的 output。第一个参数是 output，第二个参数是 target
```

```python
mean_corrector = nb_movies/float(non_zero_ratings * 1e-10) = 这是一个比例，分子为 nb_movies，分母为 non_zero_ratings。
```

- 注意在分母中加上极小的 1e-10 以避免出现数学未定义的数学错误，确保分母始终不为零。如果用户没有评分电影，`non_zero_ratings` 可能为 0。`non_zero_ratings` 表示我们考虑了当前用户所有非零评分的电影。

为什么我们需要创建 `mean_corrector`？
它实际上代表了误差的平均值，仅考虑了评分过的电影。我们这样做是因为这里我们只考虑了非零评分的电影。我们将计算平均值，这必须仅在评分过的电影上计算。即那些获得非零评分的电影。这个 `mean_corrector` 变量是为了适应这种对非零评分电影的考虑。我们需要这样做是为了使其在误差平均值上具有数学意义。

## 15.3.8 训练 SAE 模型：backward, train-loss, train

backward()；我们将对损失调用 `backward()` 方法。该方法来自 `criterion` 对象。通过调用 `backward`，我们只需告知哪个方向更新不同的权重。

```python
loss.backward()
```

- train_loss：我们计算 RMSE 来更新 `train_loss`。通过 `loss.data[]` 我们获取包含该误差的损失索引。访问损失对象中的数据，然后我们需要获取包含训练损失误差的数据索引。

```python
# train_loss += np.sqrt(loss.data[] * mean_corrector)
train_loss += np.sqrt(loss.data * mean_corrector)
```

这并不糟糕：因为我们预测了用户何时会喜欢某部电影，平均而言，我们的错误率是 9 分之一 1。

我们希望得到的损失（loss）能小于一颗星，即真实评分与预测评分之间的平均差异小于 1。因此，我们将更准确地预测用户是否会喜欢某部电影。

我们期望获得小于 1 星的损失（loss < 1 star）。

第二点，我们现在正在计算训练集上的损失，我们还需要在测试集上计算 `test_loss`。这样我们就可以观察是否存在严重的过拟合。

结果：在最后一个 epoch（轮次）中，我们期望的最终损失为 0.91。

所以这并不糟糕。此外，我们是在 10 万条评分上进行训练，如果你在这些评分上进行训练，绝对会获得更好的损失误差。我们的数据集经过了优化，训练过程不会花费太多时间。

现在让我们希望在测试集上获得相同的误差。

增加 epoch（轮次）可能会导致过拟合：当然，通过增加许多轮次，你可以在训练集上获得更低的损失，但随后可能会导致训练集和测试集之间的损失差异增大，从而导致高过拟合。为了避免这种情况，对于我们目前的数据，20 个 epoch 就足够了。

> ImplementedError: Module [StackedAutoEncoders] is missing the required forward function.
如果我们在 SAE 架构类 `StackedAutoEncoders` 中缺少了 `forward()` 函数，就会显示此错误。

# 此处为所有代码（仅训练）

```python
# AE : Recommender, SAE Stacked-Auto-Encoder
# 导入库
```
