

# 在多个数据集上拟合模型：p = 0

![](img/99defe26aebed215976e83d281581f33_30_0.png)

让我们将所有这些假设整合在一幅图中，以观察模型的偏差（bias）和方差（variance）。

# 模型选择中的偏差与方差：p = 0

![](img/99defe26aebed215976e83d281581f33_30_1.png)

在左上角的图中，我们看到了所有的假设和用到的所有训练集。左下角的图显示了青色的平均假设。如所见，该模型对于图中中心的 $x$ 具有低偏差，但对于远离图中心的 $x$ 偏差非常高。右下角的图显示，对于所有的 $x$ 值，假设的方差都相当高。

现在让我们来看一个 1 线性（线性）回归模型。

# 在多个数据集上拟合模型：$p = 1$

![](img/99defe26aebed215976e83d281581f33_31_0.png)

# 模型选择中的偏差与方差：$p = 1$

![](img/99defe26aebed215976e83d281581f33_31_1.png)

现在，对于所有的 $x$，偏差都非常低。对于图中中间的 $x$，方差较低，但对于远离图中心的 $x$，方差较高。

## 2.2 偏差-方差权衡

最后，让我们来看一个 2 次（二次）回归模型。

# 在多个数据集上拟合模型：p = 2

![](img/99defe26aebed215976e83d281581f33_32_0.png)

# 模型选择中的偏差与方差：p = 2

![](img/99defe26aebed215976e83d281581f33_32_1.png)

对于所有的 $x$，偏差仍然非常低。然而，对于所有的 $x$ 值，方差都高得多。

让我们总结一下结果。我们通过经验找到了偏差和方差，并为所有的 $x$ 值绘制了图表，如前两张图所示。最后，我们对所有 **$x$** 值的偏差和方差取了期望，如第三张图所示。

![](img/99defe26aebed215976e83d281581f33_33_0.png)

# 启示

让我们从偏差-方差分解的一些含义来看：

- 1. 欠拟合（Underfitting）等同于高偏差；大多数过拟合与高方差相关。
- 2. 训练误差反映偏差但不反映方差。测试误差反映反映两者。在实践中，如果训练误差远小于测试误差，则存在过拟合。
- 3. 当 $n\rightarrow\infty$ 时，方差 $\rightarrow 0$。
- 4. 如果 $f$ 属于假设函数集，偏差会随着数据的增加而减少。如果 $f$ 不属于假设函数集，则存在欠拟合问题，更多数据也无益。
- 5. 添加良好的特征会减少偏差，但添加糟糕的特征很少增加偏差（只需将该特征的系数设置为 0 即可）。
- 6. 添加特征通常会增加方差，因此只有当一个特征减少偏差的程度大于增加方差的时，才应该添加它。
- 7. 不可约误差（Irreducible error）无法减少。
- 8. 测试集中的噪声只影响 Var(N)，但训练集中的噪声也会影响偏差和方差。
- 9. 对于真实世界的数据，$f$ 很少已知，且噪声模型可能是错误的，因此我们无法计算偏差和方差。但我们可以在合成数据上测试算法。

## 2.3 加权最小二法

到此为止，我们在高斯噪声的背景下使用极大似然估计（MLE）来证明回归问题的优化公式，如普通最小二法（OLS）。让我们把这种双重优化-概率哲学应用于其他回归问题，例如加权最小二法。

### 优化视角

加权最小二法的基本思想是：我们更关注某些数据点对损失的贡献——也就是说，我们更在乎拟合某些数据点而非其他点。从优化的角度来看，问题可以表示为：

$$w_{WLS} = \arg\min_{w \in \mathbb{R}^d} \sum_{i=1}^n \omega_i(y_i - x_i^T w)^2$$

该目标与 OLS 相同，但和中的每一项都由系数 $\omega_i$ 加权。一如既常，我们可以对此问题进行向量化：

$$w_{WLS} = \arg\min_{w \in \mathbb{R}^d} (y - Xw)^T \Omega (y - Xw)$$

其中 $X$ 的第 $i$ 行是 $x_i^T$，$\Omega \in \mathbb{R}^{n \times n}$ 是一个对角矩阵，$\Omega_{i,i} = \omega_i$。我们重写 WLS 目标为

$$w_{WLS} = \arg\min_{w \in \mathbb{R}^d} (y - Xw)^T \Omega^{1/2} \Omega^{1/2} (y - Xw)$$
$= \arg\min_{w \in \mathbb{R}^d} (\Omega^{1/2}y - \Omega^{1/2}Xw)^T (\Omega^{1/2}y - \Omega^{1/2}Xw)$$

该公式与 OLS 相同，只是我们将矩阵和观测向量乘以了 $\Omega^{1/2}$，得出：

$$w_{WLS} = ((\Omega^{1/2}X)^T \Omega^{1/2}X)^{-1} (\Omega^{1/2}X)^T \Omega^{1/2}y = (X^T\Omega X)^{-1} X^T\Omega y$$

### 概率视角

正如 MLE，假设观测值 $y$ 有噪声；现在假设某些 $y_i$ 比其他的噪声更大。如何在我们的算法中考虑这一点以获得更好的权重？概率模型类似于 $y_i = x_i^T w + Z_i$，其中 $Z_i$ 是高斯分布但并非同分布 $Z_i \sim \mathcal{N}(0, \sigma_i^2)$。我们可以通过缩放数据以 $\sigma_i$ 将问题转化为 MLE，使得所有 $Z_i$ 同分布：

$$\frac{y_i}{\sigma_i} = \frac{x_i^T w}{\sigma_i} + \frac{Z_i}{\sigma_i}$$

注意缩放后的噪声现在是独立同分布的（i.i.d）：$\frac{Z_i}{\sigma_i} \overset{i.i.d}{\}\mathcal{N}(0,1)$。我们将原始问题重写为 MLE 问题：

$$w_{WLS}^* = \arg \min_{w \in \mathbb{R}^d} \sum_{i=1}^n \frac{(\frac{y_i}{\sigma_i} - \frac{x_i^T w}{\sigma_i})^2}{2} + n \log \sqrt{2\pi}$$

该缩放问题的 MLE 估计等同于原始问题的 OLS：

$$w_{WLS}^* = (\mathbf{X}^T \Sigma_z^{-1} \mathbf{X})^{-1} \mathbf{X}^T \Sigma_z^{-1} \mathbf{y}$$

其中

$$\Sigma_z = \begin{bmatrix} \sigma_1^2 & 0 & \dots & 0 \\ 0 & \sigma_2^2 & \dots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & \sigma_n^2 \end{bmatrix}$$

注意当 $\sigma_i>0$ 时，$\Sigma_z$ 是可逆。注意优化视角的 $\omega_i$ 与概率视角的 $\sigma_i^2$ 直接相关：$\omega_i = \frac{1}{\sigma_i^2}$。随着对应数据点 $i$ 的噪声方差 $\sigma_i^2$ 减少，权重 $\omega_i$ 增加：我们更关注拟合数据点 $i$，因为它可能匹配去噪点。相反，随着方差 $\sigma_i^2$ 增加，权重 $\omega_i$ 减少：我们不太关注拟合数据点 $i$，因为它有噪声且不应信赖。

### 依赖噪声

如果 $Z_i$ 不是独立的呢？这通常发生在时间序列数据中。同样，我们假设一个噪声行为的模型。噪声项不是独立的，但有一个已知的过程：例如 $y_{i+1} = rZ_i + U_i$，其中 $U_i \sim \mathcal{N}(0,1)$ i.i.d，$-1 \le r \le 1$（为了防止发散），或“滑动窗口”示例（如音频回声），$Z_i = \sum r_j U_{i-j}, U_i \sim \mathcal{N}(0,1)$。

## 2.4 高斯分布

一般来说，我们总是可以将噪声表示为 $\mathbf{Z} = \mathbf{RU}$，其中 $\mathbf{Z} \in \mathbb{R}^n, \mathbf{R} \in \mathbb{R}^{n \times n}, \mathbf{U} \in \mathbb{R}^n$，且 $\mathbf{U}_i \overset{i.i.d}{\}\mathcal{N}(0,1)$。$\mathbf{Z}$ 是联合高斯随机向量。我们现在的目标是推导出其概率密度公式。

联合高斯（JG）随机向量有三个等价定义：

- 1. 随机向量 $\mathbf{Z} = (Z_1, Z_2, \dots, Z_k)^T$ 是联合高斯的，如果存在一个基础随机向量 $\mathbf{U} = (U_1, U_2, \dots, U_l)$（分量为独立标准正态随机变量）、转移矩阵 $\mathbf{R} \in \mathbb{R}^{k \times l}$ 以及均值 $\mu \in \mathbb{R}^k$，使得 $\mathbf{Z} = \mathbf{RU} + \mu$。
- 2. 随机向量 $\mathbf{Z} = (Z_1, Z_2, \dots, Z_k)^T$ 是联合高斯的，如果对于每个 $a = (a_1, a_2, \dots, a_k)^T$，$\sum_{i=1}^k a_i Z_i$ 都服从正态分布。
- 3. （非退化情况）$\mathbf{Z} = (Z_1, Z_2, \dots, Z_k)^T$ 是联合高斯的，如果 $f_{\mathbf{Z}}(\mathbf{z}) = \frac{1}{\sqrt{(2\pi)^k\det(\Sigma)}} e^{-\frac{1}{2}(\mathbf{z}-\mu)^T\Sigma^{-1}(\mathbf{z}-\mu)}$，其中 $\Sigma = \begin{bmatrix} \sigma_1^2 & 0 & \dots & 0 \\ 0 & \sigma_2^2 & \dots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & \sigma_n^2 \end{bmatrix}$。

注意当 $\sigma_i>0$ 时，$\Sigma_z$ 是可逆的。注意优化视角的 $\omega_i$ 与概率视角的 $\sigma_i^2$ 直接相关：$\omega_i = \frac{1}{\sigma_i^2}$。随着对应数据点 $i$ 的噪声方差 $\sigma_i^2$ 减少，权重 $\omega_i$ 增加：我们更关注拟合数据点 $i$，因为它可能匹配去噪点。相反，随着方差 $\sigma_i^2$ 增加，权重 $\omega_i$ 减少：我们不太关注拟合数据点 $i$，因为它有噪声且不应信赖。

# 证明 (1) $\implies$ (3)

在我们之前定义的问题背景下，我们从条件 (1) 开始，即 $\mathbf{Z} = \mathbf{RU}$（在此情况下 $l=n$），我们想推导出 $\mathbf{Z}$ 的概率。注意我们在机器学习中去除了对 $\mu$ 的考虑，我们总是假设噪声的均值为 0。我们留给读者去证明任意 $\mu$ 情况的情况。

