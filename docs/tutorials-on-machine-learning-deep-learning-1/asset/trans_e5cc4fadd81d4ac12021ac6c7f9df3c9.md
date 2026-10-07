
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

