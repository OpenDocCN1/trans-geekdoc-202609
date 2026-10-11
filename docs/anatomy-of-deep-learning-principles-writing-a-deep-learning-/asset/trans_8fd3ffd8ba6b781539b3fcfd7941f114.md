

```python
x0 = np.array([3., 4.])
print("initial point", x0, "gradient", df(x0))

path = gradient_descent(df, x0, 0.000005, 300000)
print("Extreme point：", path[-1])
```

初始点 `[3. 4.]` 的梯度 `[25625.25 57519.]`

极值点：`[2.70735828 0.41689171]`

由于 `x` 的初始梯度值非常大，学习率 `α` 必须取一个很小的数（如 `0.000005`），否则会导致震荡或无穷大值，最终收敛到 `[2.70735828 0.41689171]`。但这并非最优点；通过绘制迭代过程中 `x` 的变化可以更直观地看到这一情况。

```python
def plot_path(path, x, y, z, minima_, xmin, xmax, ymin, ymax):
    fig, ax = plt.subplots(figsize=(10, 6))
    ax.contour(x, y, z, levels=np.logspace(0, 5, 35), norm=LogNorm(), cmap=plt.cm.jet)
    # ax.scatter(path[0], path[1]);
    ax.quiver(path[:-1, 0], path[:-1, 1], path[1:, 0] - path[:-1, 0], path[1:, 1] - path[:-1, 1], scale_units='xy', angles='xy', scale=1, color='k')
    ax.plot(*minima_, 'r*', markersize=18)

    ax.set_xlabel('$x$')
    ax.set_ylabel('$y$')
    ax.set_xlim((xmin, xmax))
    ax.set_ylim((ymin, ymax))

path = np.asarray(path)
plot_path(path, x, y, z, minima_, xmin, xmax, ymin, ymax)
```

![](EPUB/media/file30.png "fig:")

图 2-10 迭代过程中，梯度值越来越小，收敛越来越慢

在迭代过程中，梯度值越来越小，相同的学习率导致 `x` 的更新非常缓慢。即使经过 100,000 次迭代，仍无法逼近最优解。一种自然的方法是使用自适应学习率，即当梯度变小时增大学习率。作为练习，读者可以尝试修改梯度下降算法，以更好、更快地到达最优解。

## 2.3 梯度下降法的参数优化策略

基础梯度下降算法中的学习率是一个固定值，而在迭代过程中梯度大小不断变化。如果学习率过大，待求变量会来回震荡；如果学习率过小，收敛会非常缓慢甚至停滞。初始学习率适中，但随着收敛逼近最优解，其梯度也接近 0，这也会导致停滞。因此，学习率应在迭代逐渐收敛的过程中进行调整，即使用变化的学习率在迭代过程中更新待求变量 `x`。

为了能更好、更快地逼近最优解，针对梯度下降法提出了许多改进。这些改进采用变化的学习率或策略来更新解变量（也称为参数）。变量（参数）的更新策略或方法包括：Momentum（动量法）、Nesterov 加速梯度、Adagrad、Adadelta、RMSprop、Adam、AdaMax、Nadam、AMSGrad 等。

需要注意的是，函数可能是多元函数；因此，其变量 `x` 可以是由多个值组成的向量 `xx`。下面仅介绍一些常用的优化策略。

### 2.3.1 Momentum 动量法

梯度下降法使用学习率 `α` 和梯度的负方向，即 `−α∇f(x)` 来每次更新 `x`。更新向量 `−α∇f(x)ofx` 完全取决于当前计算出的梯度。Momentum 动量法更新 `x` 的向量不仅考虑当前梯度，还考虑上一次的更新向量；即认为更新向量具有惯性。假设 `v[t−1]` 是上一次用于更新的向量，则当前更新向量为：

`v[t] = γv[t−1] + α∇f(x)`

用此 `v` 更新 `x`：

`x = x − v[t]`

这个用于更新 `x` 的向量称为**动量**。动量法将更新向量视为运动物体的速度，速度具有惯性。由于结合了之前的更新向量和当前梯度，它缓解了不同时间梯度的剧烈变化，使更新向量更平滑；即保持之前运动的惯性，使得在梯度较小的地方仍有较大的运动量。速度不会因梯度的突然增大而超调。这种方法就像一个有重量的球滚下山坡，在寻找最陡峭下降路径的同时保持一定的惯性。普通梯度下降仅根据陡峭程度决定移动速度，就像在陡峭处冲得快、在平坦处几乎不动。

`vv` 的初始值为 0，用 Python 代码表示为：

```python
v = np.zeros_like(x)
```

即 `vv` 是一个与 `xx` 形状相同、初始值为 0 的张量。在迭代过程中，先更新 `vv`，再更新函数的参数 `xx`：

```python
v = gamma * v + alpha * df(x)
x = x - v
```

以下是基于动量法的梯度下降法：

```python
def gradient_descent_momentum(df, x, alpha=0.01, gamma=0.8, iterations=100, epsilon=1e-6):
    history = [x]
    v = np.zeros_like(x)            # momentum
    for i in range(iterations):
        if np.max(np.abs(df(x))) < epsilon:
            print("The gradient is small enough!")
            break
        v = gamma * v + alpha * df(x)           # update momentum
        x = x - v                    # Update variables (parameters)
        
        history.append(x)
    return history
```

使用这种动量法的梯度下降法求解上述问题：

```python
path = gradient_descent_momentum(df, x0, 0.000005, 0.8, 300000)
print(path[-1])
path = np.asarray(path)
```

`[2.96324633 0.49067782]`

可以看出，动量法的解非常接近最优解，如图所示。

```python
plot_path(path, x, y, z, minima_, xmin, xmax, ymin, ymax)
```

![](EPUB/media/file31.png "fig:")

图 2-11 动量法快速收敛到近似最优解

### 2.3.2 Adagrad 方法

根据梯度下降法的变量更新公式 `xx = xx − α∇f(xx)`，影响变量更新的是学习率与梯度的乘积 `α∇f(xx)`。梯度过大或过小、学习率过大或过小都会影响算法的收敛。

对于多元函数，每个变量的偏导数大小可能差异很大。例如，两个变量函数 `f(x[1], x[2])` 在某点 `(x[1], x[2])` 处的偏导数 $\frac{\partial f}{\partial x_{1}},\frac{\partial f}{\partial x_{2}}$ 绝对值可能相差很大。对它们使用相同的学习率是不合适的。对某个分量合适的学习率，对另一个分量可能过大或过小，导致震荡和停滞。即直接用以下公式更新是不合适的：

$x_{1} = x_{1} - \alpha\frac{\partial f}{\partial x_{1}}$

$x_{2} = x_{2} - \alpha\frac{\partial f}{\partial x_{2}}$

Adagrad 方法从名词可译为“自适应梯度”，它将每个梯度分量除以该梯度分量的历史累积值，从而消除不同分量梯度大小不平衡的问题。对于 2 个分量 `(x[1], x[2])`，若分别计算各自分量的历史累积值 `(G[1], G[2])`，则 2 个分量的更新公式为：

$x_{1} = x_{1} - \alpha\frac{1}{G_{1}}\frac{\partial f}{\partial x_{1}}$

