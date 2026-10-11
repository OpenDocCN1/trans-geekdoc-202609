

### 10.4.2 BiG-FL 的算法设计

精确求解公式 [(10.17)](#Chp010_181-197_B9780443190377000181.xhtml#deq21) 以获得最优解是不切实际的。相反，遵循 FL 算法，我们应用 SGD 进行若干步迭代，从而获得 LL 问题的近似解。具体而言，LL 优化变量按如下方式更新：

```
\mathbf{\theta}_{i}^{k + 1} = \mathbf{\theta}_{i}^{k} - \frac{\beta^{t}}{m}\sum\limits_{j = 1}^{m}\nabla_{\mathbf{\theta}_{i}}G_{i}(\mathbf{\varphi}^{t},\mathbf{\theta}_{i}^{k},\mathbf{\theta}_{- i}^{k};\xi_{j}),\quad\forall i \in \lbrack n\rbrack,
```

![Image](OEBPS/images/B9780443190377000181/si97_u6.png)(10.19)

其中 `k` 表示内层循环的索引，初始化为 `\mathbf{\theta}_{i}^{0} = \mathbf{\theta}_{i}^{(t)}`，`\beta^{(t)}` 为 LL 步长，`\nabla G_{i}(\mathbf{\varphi}^{(t)},\mathbf{\theta}_{i}^{(k)},\mathbf{\theta}_{- i}^{(k)};\xi_{j})` 表示第 `i` 个 BiG-FL LL 经验损失函数在点 `(\mathbf{\varphi}^{(t)},\mathbf{\theta}_{i}^{(k)},\mathbf{\theta}_{- i}^{(k)})` 处利用第 `j` 个数据样本（即 `\xi_{j} \triangleq (X_{j}, Y_{j}) \sim \mathcal{D}_{j}`）计算的梯度。经过连续 `\tau` 步内层循环更新后，我们令 `\mathbf{\theta}_{i}^{(t + 1)} = \mathbf{\theta}_{i}^{(\tau)}`。

类似地，LL 变量通过计算超梯度 [[5]](#Chp010_181-197_B9780443190377000181.xhtml#br0025) 利用 SGD 进行更新，具体如下：

```
\mathbf{\varphi}^{t + 1} = \mathbf{\varphi}^{t} - \frac{\alpha^{t}}{m}\sum\limits_{j = 1}^{m}\left( \nabla_{\mathbf{\varphi}}F_{j}^{t} - \nabla_{\mathbf{\varphi}\mathbf{\theta}}^{2}\mathbf{G}_{j}^{t}\left( \nabla_{\mathbf{\theta}\mathbf{\theta}}^{2}\mathbf{G}_{j}^{t} \right)^{- 1}\nabla_{\mathbf{\theta}}F_{j}^{t} \right),
```

![Image](OEBPS/images/B9780443190377000181/si104_u7.png)(10.20)

其中 `\alpha^{(t)}` 表示 UL 步长，`\nabla_{\varphi}F_{j}^{(t)}`（`\nabla_{\mathbf{\varphi}}F(\mathbf{\varphi}^{(t)},\{\mathbf{\theta}_{i}^{(t)}\};\xi_{j})` 的缩写）是 UL 经验损失函数在点 `(\mathbf{\varphi}^{(t)},\{\mathbf{\theta}_{i}^{(t)}\})` 处利用头节点 `i` 的第 `j` 个负样本尾节点（即 `j \sim \mathcal{P}_{i}`）计算的梯度，`\nabla_{\mathbf{\varphi}\mathbf{\theta}}^{2}\mathbf{G}_{j}^{(t)}` 和 `(\nabla_{\mathbf{\theta}\mathbf{\theta}}^{2}\mathbf{G}_{j}^{(t)})^{-1}` 分别代表 LL 损失函数关于 `\varphi` 和 `\{\mathbf{\theta}_{i}\}` 的雅可比矩阵的随机近似以及 LL 损失函数海森矩阵的逆矩阵。此处，我们假设 LL 损失函数是强凸的（例如，如果 `\kappa` 足够大），这意味着 `\nabla_{\mathbf{\theta}\mathbf{\theta}}^{2}\mathbf{G}_{j}^{(t)}` 可逆。BiG-FL 的完整实现如 [算法 4](#Chp010_181-197_B9780443190377000181.xhtml#f0030) 所示，其中 `\theta` 是 `\{\mathbf{\theta}_{i}, \forall i\}` 的拼接。

![算法 4 基于双层优化增强的 GFL (BiG-FL)。](OEBPS/images/B9780443190377000181/gr005_u2.jpg)

**算法 4** 基于双层优化增强的 GFL (BiG-FL)。

