

## 高斯分布的 KL 散度

我们也可以以闭式计算高斯密度的 KL 散度：

```
$KL(\mathcal{N}_0|\mathcal{N}_1) = \frac{1}{2} \left\{ \text{tr}(\mathbf{\Sigma}_1^{-1} \mathbf{\Sigma}_0) + \log \frac{|\mathbf{\Sigma}_1|}{|\mathbf{\Sigma}_0|} + (\mathbf{\mu}_1 - \mathbf{\mu}_0)^T \mathbf{\Sigma}_1^{-1} (\mathbf{\mu}_1 - \mathbf{\mu}_0) - k \right\}$
```

![](img/f01928df50903c99ce023dd3c527a33d_588_0.png)

- **第一项**：比较分布的“形状/旋转”
- **第二项**：比较分布的熵
- **第三项**：比较分布的均值
  - 在 $\mathbf{\Sigma}_1^{-1}$ 定义的度量空间中测量
  - 如果在均值更新方向上 $\mathcal{N}_1$ 的方差较小，则不相似性更高

## 反向 KL 的最小化

这种最小化通常被称为分布 $p(x^*)$ 的（信息）投影 ( (Information-projection )

```
KL(q(x)||p^*(x)) = \int_{x} q(x) \log \frac{q(x)}{p^*(x)}dx = \int_{x} q(x) \log \frac{q(x)}{p^*(x)} + \log Z
```

![](img/f01928df50903c99ce023dd3c527a33d_589_0.png)

- 不需要评估归一化 Z
- **零强制 (Zero forcing)**：如果 $p^*(x)$ 很小，则 $q(x)$ 也很小
  - 这导致了**模式寻求行为 (mode-seeking behaviour)**

- **非凸优化**，即使对于简单的分布 $q(x)$ 也是如此
  - 难以优化
  - 通常有多个局部最优

- **直观上**：
  - 良好的生成模型（用于采样）
  - 但某些高概率区域可能会忽略

KL(q||p)

![](img/f01928df50903c99ce023dd3c527a33d_589_1.png)

## 前向 KL 的最小化

这种最小化通常被称为分布 $p^*(x)$ 的（矩）投影 ( (Moment-projection )

```
$KL(p^*(x)||q(x)) = \int_x p^*(x) \log \frac{p^*(x)}{q(x)} dx = -\int_x p^*(x) \log q(x) dx + const \quad p^*(x)\napprox -\frac{1}{N} \sum_{x_i\sim p^*(x)} \log q(x_i) + const$
```

![](img/f01928df50903c99ce023dd3c527a33d_590_0.png)

- **概率强制 (Probability forcing)**：如果 $p^*(x)$ 很高，则 $q(x)$ 也必须很高
- 结果是它在无法表示的模式上取平均！
- 需要来自 $p^*(x)$ 的样本（不适用于变分推理 VI）
- 它与最大似然解是一样的！

```
$argmax_q \LogLike(\mathcal{D}, q) = argmax_q \sum_{x_i\sim p^*(x)} \log q(x_i)\napprox argmin_q KL(p^*(x)||q(x))$
```

KL(p||q)

![](img/f01928df50903c99ce023dd3c527a33d_590_1.png)

## 有趣的事实：为什么被称为矩投影？

当使用指数族分布作为模型时，

$q_{\theta}(x) = \frac{\exp(\phi(x)^T\theta)}{Z}, \quad \text{with } Z = \int \exp(\phi(x)^T\theta)dx$

很容易证明，匹配数据平均特征向量 $\bar{\phi}$ 的最大似然拟合：

$$\frac{d}{d\theta}LogLik(\mathcal{D}, \theta) = \sum_{i} \frac{d}{d\theta}\log q_{\theta}(x_i) = \sum_{i} \frac{d}{d\theta}(\phi(x_i)^T\theta) - N\frac{d}{d\theta}\log\left(\int \exp(\phi(x)^T\theta)dx\right)$$

$= \sum_{i} \phi(x_i) - N \frac{\exp(\phi(x)^T\theta)}{Z} \phi(x)dx = N\bar{\phi} - N E_{q_{\theta}(x)}[\phi(x)]$$

**根据 $\theta$ 的最优性条件（导数 = 0）得出：** $E_{q_{\theta}(x)}[\phi(x)] = \bar{\phi}$

- 即模型 $q$ 的期望特征必须匹配观测到的平均特征
- 例如，对于高斯分布，$\phi(x) = [x, x^2]^T$，我们匹配一阶和二阶矩

## VI 投影的比较

| 信息投影 | 矩投影 |
| :--- | :--- |
| ![](img/f01928df50903c99ce023dd3c527a33d_592_0.png) | ![](img/f01928df50903c99ce023dd3c527a33d_592_1.png) |
| $KL(q(x)||p^*(x)) = \int_{x} q(x) \log \frac{q(x)}{p^*(x)} dx$ | $KL(p^*(x)||q(x)) = \int_{x} p^*(x) \log \frac{p^*(x)}{q(x)} dx$ |
| 不需要知道 $p^*(x)$ 的归一化因子 | 于优化 |
| 模式寻求 | 覆盖所有高概率区域 |
| 良好的生成模型（所有样本都代表性） | 需要来自 $p^*(x)$ 的样本 |
| 即使对于简单的 $q$ 也难以优化 | 生成模型可能很差 |
| 可能会错过高概率区域 | $q$ 在 $p^*(x)$ 较低的地方可能具有高密度 |

## f-散度

**有趣的事实：** 大多数散度都是 f-散度的特例

```
$D_f(p(x)||q(x)) = \int f\left(\frac{p(x)}{q(x)}\right) q(x)$
```

- 不同的 $f$ 选择
- 这对于正向和反向 KL 都成立！

## f-散度

| 散度 | 对应的 $f(t)$ | 离散形式 |
| :--- | :--- | :--- |
| $\chi^\alpha$-散度, $\alpha \ge 1$ | $\frac{t^\alpha}{\alpha}$ | $\sum \frac{p_i^\alpha}{q_i}$ |
| 总变分 (Total variation) $(\alpha = 1)$ | $\frac{1}{2}|t-1|$ | $\sum \frac{1}{2}|p_i-q_i|$ |
| $\alpha$-散度 | $\begin{cases} \frac{t^\alpha}{\alpha} & \alpha \neq 0 \\ \ln t & \alpha = 0 \end{cases}$ | |
| KL 散度 $(\alpha = 1)$ | $\ln t$ | $\sum p_i \ln \frac{p_i}{q_i}$ |
| 反向 KL 散度 $(\alpha = 0)$ | $-\ln t$ | $\sum q_i \ln \frac{q_i}{p_i}$ |
| Jensen 散度 | $\frac{1}{2}(t\ln t + (1-t)\ln(1-t))$ | |
| KL 散度 (Jeffreys) | $\frac{1}{2}(t-1)^2$ | $\sum \frac{1}{2}(p_i-q_i)^2$ |
| Jeffrey' 散度 | $(t-1)\ln t$ | $\sum (p_i-q_i)\ln p_i$ |

- **注意：**大多数 f-散度并不重要，但 f-散度是成立的 [1] Generative Models, Sebastian Nowoz, NeurIPS 2016
- [1] Generative Models, Ryota Tomioka, ICML2015

## 回顾最大似然

对于最大似然的损失

$KL(p^*(x)||q(x)) \approx -\frac{1}{N} \sum_{x_i\sim p^*(x)} \log q(x_i)$

梯度下降的收敛取决于散度

- ... 以及我们用作模型的 $q(x)$
- 理想情况下，在最值值之外具有显著的梯度
  - 引导算法走向正确的方向

