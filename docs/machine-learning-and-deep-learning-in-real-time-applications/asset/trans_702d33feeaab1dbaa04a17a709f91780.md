

# 使用 PyTorch 进行深度学习

与静态图相比，在动态图中，用户布局图，而在运行时数据传递到已定义的图中并运行。

首先初始化两个张量，如表 2 所示。为了简单起见，将它们视为标量张量。

## 表 2. 创建计算图

```
x = torch.tensor(3.0)
y = torch.tensor(4.0)
Out = x.mul(y)
```

这两个张量相乘，输出被保存在另一个名为 `out` 的张量中：

图 6. 计算图

![](img/c5cbbc72cd5e7b9be32079eac36d685c_92_0.png)

每个张量对象都有属性：data, grad, grad_fn, requires_grad, is_leaf。
`data` 属性存储张量的数据，`requires_grad` 指定在反向图中是否计算梯度，`grad_fn` 存储反向传播函数，`grad` 存储在反向传播的梯度值，`is_leaf` 指定图中的节点是否为中间节点。

在图 6 中，`x.requires_grad` 和 `y.requires_grad` 都被设置为 `False`。因此 `out.requires_grad` 也是 `False`。由于所有张量的 `requires_grad` 均为 `False`，因此没有创建反向图，`grad` 和 `grad_fn` 为 `None`。

如果张量中任意一个 `requires_grad` 属性被设置为 `True`，autograd 会在后台创建一个反向图并开始在反向图中跟踪导数。

如表 3 所示，x 和 y 初始化为标量张量，且 `x.requires_grad=True`：

## 表 3. 初始化属性的代码：data, x.requires_grad

```
x = torch.tensor(3.0, requires_grad=True)
y = torch.tensor(4.0)
Z = x.mul(y)
z.backward()
```

图 7. 反向计算图

![](img/c5cbbc72cd5e7b9be32079eac36d685c_93_0.png)

在上述图中，`x.requires_grad` 被设置为 `True`，因此在这种情况下，创建了反向图，并使用链式法则计算输出张量相对于 x 的导数。在规则 7 中，绿色节点是反向图的一部分。由于 `x.requires_grad` 为 `True`，`out.requires_grad` 也将是 `True`。

`Context_store` 可能存储计算较大且复杂的计算图中梯度所需的某些中间值，并将其传递给 `MulBackward` 的 `saved_tensor`。`MulBackward` 的 `Next_method` 指向传递梯度的方法。

这里，x 的梯度被传递给 `AccumulateGrad`。由于 `y.requires_grad` 被设置为 `False`，y 的 `Next_method` 被设置为 `Null`。

请注意，由于反向图是在后台创建的，其代码是用 C++ 编写的，Python 代码中不存在像 `MulBackward`、`AccumulateGrad` 之类或反向图中的属性。它们仅用于表示性目的。

## 优化包 (Optimization Package)

优化算法是一种通过更新参数来最小化损失函数并降低损失的算法。最简单的优化算法——梯度下降法在前一节中已经讨论过。但梯度下降法的问题在于，它考虑数据集中的每一个示例来计算一步参数更新。一个典型的深度学习数据集包含数百万个示例。因此，梯度下降需要考虑所有示例来沿着曲线向下移动一步。这导致神经网络的训练变慢，或者可能导致内存溢出并在不更新参数的情况下终止。

但如果决定取数据集中的单个示例通过正向传播来计算损失，那么小批量梯度下降（mini-batch gradient descent）的工作方式与之类似，它不是使用单个示例来沿着曲线向下移动一步，而是使用数据集中的一小组示例。

SGD 采用数据集中的单个示例，这正是随机梯度下降（SGD）和小批量梯度下降所执行的。

通常情况下，使用小批量梯度下降是因为 GPU 擅长并行计算，而 PyTorch（以及其他深度学习框架）可以利用并行计算，同时使用多个示例来计算梯度下降的步骤。

## 表 4. 随机梯度下降

```
optimizer = optim.SGD(model.parameters(),lr=0.01)
for input, target in batch(dataset, batch_size):
    optimizer.zero_grad()
    output = model(input)
    loss = criterion(output, target)
    loss.backward()
    optimizer.step()
```

用户定义的 batch 函数将数据集划分为若干个给定 `batch_size` 的批次，并返回生成的每个批。循环遍历每个批，计算损失，使用梯度下降更新参数并减少损失。每个批次贡献于梯度下降的一步。对于 SGD，`batch_size` 为 1。通常，根据所用机器的内存大小，`batch_size` 在 32 到 128 之间。`optimizer.zero_grad()` 为新值将梯度值重置为零。`optimizer.step()` 更新参数。

SGD 和小批量梯度下降解决了内存溢出和步更新缓慢的问题，但在这些优化算法中出现了一个新问题。参数并没有随着每次优化步骤都更接近局部最小值，而是在震荡。某些批次并没有减少损失反而增加了，而另一些批次可能会减少损失。结果是，参数以之字运动收敛到局部最小值。这导致了训练变慢。

图 8. 显示参数在 SGD 中如何收敛到局部最小值的等高线。“+” 是局部最小值

![](img/c5cbbc72cd5e7b9be32079eac36d685c_95_0.png)

为了解决参数以低效之字方式收敛到局部最小值的问题，有几种优化算法。这些算法使得参数收敛更加平滑。接下来的章节将讨论一些重要的算法。

## 动量 (Momentum)

在这种方法中，通过过去的梯度平滑错误方向的震荡，使参数向正确的方向收敛。在图 8 中，只有两个方向（为了简单起见），这可以比作汽车以之字运动到达目的地。动量方法减少了 y 方向的速度并增加了 x 方向的速度，使得运动变得更加平滑并到达目的地。

```
V = \beta V + (1 - \beta)dW.
```

```
W = W - \alphaV.
```

$\beta$ 也是一个超参数。在 PyTorch 中，$\beta$ 的值通常为 0.9。

## 表 5. 在 PyTorch 中定义优化器

| 优化器 (Optimizer) |
| :--- |
| torch.optim.SGD(model.parameters(),lr=0.01, momentum=0.9) |

## Adam

Adam 是一种高效且应用广泛的优化算法。Adam 结合了 RMS prop 和动量的方法。

```
$V_{dw}=\beta_tV_{dw}+(1-\beta_t)d_{dw} \quad S_{dw}=\beta_2S_{dw}+(1-\beta_2)d_{dw}^2 \quad W=W-\alpha\frac{d_{dw}}{\sqrt{S_{dw}}}\dots$ 在 PyTorch 中：\quad (6)
```

Optimizer = torch.optim.Adam(params, lr=0.001, beta=(0.9, 0.999), eps=1e-08, weight_decay=0, amgrad=False)

## 表 6. 定义 Adam Optimizer

## 实际应用

在本节中，作者讨论了深度学习在现实世界中的应用。作者还将展示如何使用 PyTorch 创建简单的图像和语言模型。

## 医学图像理解中的图像处理与深度学习 (Litjens et al., 2017)

