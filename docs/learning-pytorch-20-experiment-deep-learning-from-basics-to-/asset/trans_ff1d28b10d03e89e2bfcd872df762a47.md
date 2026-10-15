
```python
model = torch.nn.Linear(10, 5)

# Define the loss function

loss_fn = torch.nn.MSELoss()

# Define the optimizer - still using SGD

optimizer = torch.optim.SGD(model.parameters(),
	lr=0.01)

# Example data

input = torch.randn(100, 10)
target = torch.randn(100, 5)

# Define the batch size

batch_size = 10

# Training loop
```
```
for i in range(100):
    for j in range(0, input.shape[0], batch_size):
        # Compute the predicted output
        output = model(input[j:j+batch_size])
        # Compute the loss
        loss = loss_fn(output, target[j:j+batch_size])
        # Zero the gradients
        optimizer.zero_grad()
        # Compute the gradients
        loss.backward()
        # Update the parameters
        optimizer.step()
```

在上述演示中，j 循环以 batch_size 为步长递增，对每个小批量取输入数据和目标数据的一个切片。实际上，在每个 epoch 开始时，你也希望对输入数据进行洗牌，以确保模型不会从样本的顺序中学习到任何信息。

## 动量

动量是一个源自物理学的概念，已被巧妙地应用于优化算法领域以加速学习过程。动量的思想很简单：运动中的物体倾向于保持其轨迹，除非受到外力的作用。这一原理被应用于机器学习中的优化过程，以有效引导优化器，确保更平滑、更快速地收敛到损失函数的全局最小值。

在优化的上下文中，动量通过将上一时间步的一部分更新向量带到当前时间步发挥作用。这种机制有助于优化器更有效地沿相关方向移动，从而减轻不必要的振荡。动量项有效地充当了之前梯度的记忆，有助于通过减弱梯度方向的快速变化来引导优化过程。动量可以成为优化中的一种强有力工具，尤其是在曲率较高、梯度虽小但一致或梯度噪声较大的情况下。高曲率可能导致梯度方向快速变化，使优化过程剧烈振荡并可能错过最优解。虽小但一致的梯度可能导致向最优解的缓慢收敛。噪声会引入随机性，使优化器更难找到最优解。

在每种情况下，动量都可以显著提供帮助。它会增加梯度在同一方向上持续指向的维度的更新，加速这些维度的收敛。同时，它会减少梯度方向频繁变化的维度的更新，有助于抑制振荡。这种双重作用有助于使优化器的轨迹更直接、更不易振荡，从而实现更快的收敛并可能获得更好的解。

### 使用 SGD 时的动量

在 PyTorch 中向我们的 SGD 优化器添加动量与在实例化优化器时添加一个额外参数一样简单。

我们将看看在实践中它是什么样的：

```
# Define a simple linear model
model = torch.nn.Linear(10, 5)

# Define the loss function
loss_fn = torch.nn.MSELoss()

# Define the optimizer - SGD with momentum
optimizer = torch.optim.SGD(model.parameters(),
lr=0.01, momentum=0.9)

# Example data
input = torch.randn(100, 10)

target = torch.randn(100, 5)
```
```
# Define the batch size

batch_size = 10

# Training loop

for i in range(100):

    for j in range(0, input.shape[0], batch_size):

        # Compute the predicted output

        output = model(input[j:j+batch_size])

        # Compute the loss

        loss = loss_fn(output, target[j:j+batch_size])

        # Zero the gradients

        optimizer.zero_grad()

        # Compute the gradients
```
```
loss.backward()

# Update the parameters

optimizer.step()
```

在上面的示例中，momentum=0.9 表示上一步的梯度占动量的 90%，这可以被视为梯度对之前梯度的一种记忆。然后当前梯度被加到这个 90% 的累积梯度上，结果用于更新参数。这一概念可以帮助 SGD 穿越峡谷，即表面在某一维度比另一维度弯曲更陡峭的区域，这些区域在局部最优值附近很常见。在这些情况下，带动量的 SGD 会在峡谷的斜坡上振荡，同时在底部朝着局部最优值缓慢进展。

## 自适应梯度算法

自适应梯度算法，或 Adagrad，是一种值得注意的优化算法，旨在灵活地为各个参数调整学习率。这种
差异化适应对于处理稀疏数据特别有益，因为它可以确保即使在面对出现频率低的特征时，优化过程仍然稳健。

Adagrad 的运行原理是并非所有参数对更新的敏感度相同。在数据稀疏且特征出现不均匀的高维空间中，一些参数可能与频繁出现的特征相关，而另一些则与不频繁的特征相关。Adagrad 通过对与频繁出现特征相关的参数进行较小的更新，而对与不频繁特征相关的参数进行较大的更新，巧妙地解决了这种差异。这种个性化处理有助于提升模型的性能，尤其是在涉及稀疏数据集的上下文中。

Adagrad 的一个独特特点在于其调整学习率的方法。它维护所有过去平方梯度的累积记录，并将其用作学习率的缩放因子。特征出现的频率越高，累积的梯度越大，因此有效学习率越小。这确保了与频繁特征相关的参数不会剧烈波动，从而提供稳定的学习过程。

然而，这种累积方法也存在潜在的缺点。由于所有过去的平方梯度都会无限制地累积，在长时间的训练中总和可能变得很大，导致有效学习率过小。这种学习率的快速衰减可能在长时间运行的任务中过早地停滞学习过程，使 Adagrad 在某些深度学习应用中不太适用。

### 使用 Adagrad 算法

以下是 PyTorch 中使用 Adagrad 优化器的示例：

```
# Define a simple linear model

model = torch.nn.Linear(10, 5)

# Define the loss function

loss_fn = torch.nn.MSELoss()

# Define the optimizer - Adagrad

optimizer = torch.optim.Adagrad(model.parameters(), lr=0.01)
```
# 示例数据
```
input = torch.randn(100, 10)
```
```
target = torch.randn(100, 5)
```
# 定义批大小
```
batch_size = 10
```
# 训练循环
```
for i in range(100):
```
```
for j in range(0, input.shape[0], batch_size):
```
# 计算预测输出
```
output = model(input[j:j+batch_size])
```
# 计算损失
```
loss = loss_fn(output, target[j:j+batch_size])

# Zero the gradients

optimizer.zero_grad()

# Compute the gradients

loss.backward()

# Update the parameters

optimizer.step()
```

在上面的示例程序中，使用 torch.optim.Adagrad 实例化 Adagrad 优化器。与 SGD 类似，Adagrad 优化器的主要参数是要优化的参数集合，它还接受学习率 (lr) 作为可选参数。

## 自适应矩估计

自适应矩估计（Adam）是一种流行的优化算法，用于训练许多类型的深度学习模型。Adam 结合了来自
两个其他流行算法的元素：AdaGrad，可处理稀疏梯度；以及 RMSProp，可处理非平稳（即快速变化）的目标。

名称“Adam”源自“adaptive moment estimation”，该算法旨在为不同参数计算单独的自适应学习率。它计算梯度和平方梯度的指数移动平均值，而参数 beta1 和 beta2 控制这些移动平均值的衰减率。

Adam 的主要优点包括：

- 易于实现。
- 计算效率高，内存需求小。
- 对梯度的对角线重缩放不变。
- 适用于数据或参数规模大的问题。
- 适用于非平稳目标。
- 在梯度非常嘈杂或稀疏的问题上表现良好。
- 提供一定的正则化效果。

现在，我们将看一个在 PyTorch 中使用 Adam 优化器的示例：
