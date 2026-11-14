

能量函数可以分解为数据样本之和：

\(\mathcal{E}(\boldsymbol{\theta}) = \sum_{n=1}^N \mathcal{E}_n(\boldsymbol{\theta})\) (12.118)

\(\mathcal{E}_n(\boldsymbol{\theta}) = -\log p(\boldsymbol{x}_n|\boldsymbol{\theta}) - \frac{1}{N} \log p_0(\boldsymbol{\theta})\) (12.119)

计算完整的能量（例如，在 Metropolis-Hastings 算法中计算接受概率，或在 HMC 中计算梯度）需要 \(O(N)\) 时间，这无法扩展到大规模数据。在本节中，我们将讨论解决此问题的一些方案。

## 12.7.1 随机梯度朗之汀动力学 (SGLD)

回顾方程 (12.83)，朗之汀扩散 SDE 具有以下形式

\(d\boldsymbol{\theta}_t = -\nabla \mathcal{E}(\boldsymbol{\theta}_t)dt + \sqrt{2}d\mathbf{W}_t\) (12.120)

其中 \(d\mathbf{W}_t\) 是维纳噪声（也称为布朗噪声）过程。在离散时间中，我们可以使用以下欧拉近似：

\(\boldsymbol{\theta}_{t+1} \approx \boldsymbol{\theta}_t - \eta_t \nabla \mathcal{E}(\boldsymbol{\theta}_t) + \sqrt{2\eta_t}\mathcal{N}(\mathbf{0},\mathbf{I})\) (12.121)

在每一步计算梯度 \(\boldsymbol{g}(\boldsymbol{\theta}_t) = \nabla \mathcal{E}(\boldsymbol{\theta}_t)\) 需要 \(O(N)\) 时间。我们可以利用以下方法在 \(O(B)\) 时间内计算梯度项的无偏小批量近似：

\(\hat{\boldsymbol{g}}(\boldsymbol{\theta}_t) = \frac{N}{B} \sum_{n \in \mathcal{B}_t} \nabla \mathcal{E}_n(\boldsymbol{\theta}_t) = -\frac{N}{B} \left( \sum_{n \in \mathcal{B}_t} \nabla \log p(\boldsymbol{x}_n|\boldsymbol{\theta}_t) + \frac{B}{N} \nabla \log p_0(\boldsymbol{\theta}_t) \right)\) (12.122)

其中 \(\mathcal{B}_t\) 是步骤 \(t\) 中的小批量。这导致了以下近似更新：

\(\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \eta_t \hat{\boldsymbol{g}}(\boldsymbol{\theta}_t) + \sqrt{2\eta_t} \mathcal{N}(\mathbf{0}, \mathbf{I})\) (12.123)

这称为随机梯度朗之汀动力学或 SGLD [Wel11]。得到的更新步骤与 SGD 相同，只是添加了一个高斯噪声项。（参见 [Neg+21] 对该方法的一些最新分析；他们还建议设置 \(\eta_t \propto N^{-2/3}\)。）

## 12.7.2 预条件化

与 SGD 一样，如果我们使用预条件化来缩放梯度更新，可以获得更好的结果（尤其是对于神经网络等模型）。在 [PT13] 中，他们使用 Fisher 信息矩阵（FIM）作为预条件子；这种方法称为随机梯度黎曼朗之汀动力学或 SGRLD。

不幸的是，计算 FIM 通常很困难。在 [Li+16] 中，他们建议使用与 RMSprop 使用的相同类型的对角近似；这称为预条件化 SGLD。另一种方法是使用类似 Adam 的预条件子，如 [KSL21] 所提议。这称为 SGLD-Adam。更多详情见 [CSN21]。

## 12.7.3 减小梯度估计的方差

小批量引入的噪声方差可能相当大，这可能会损害 SGLD 等方法的性能 [BDM18]。在 [Bak+17] 中，他们建议通过使用**控制变量**估计器来减小该估计的方差；因此这种方法称为 **SGLD-CV**。具体而言，他们使用以下梯度近似：

$$\hat{\nabla}_{cv}\mathcal{E}(\theta_t) = \nabla \mathcal{E}(\hat{\theta}) + \frac{N}{B} \sum_{n \in S_t} \left( \nabla \mathcal{E}_n(\theta_t) - \nabla \mathcal{E}_n(\hat{\theta}) \right)$$ (12.124)

这里 \(\hat{\theta}\) 是任意固定值，但通常被视为近似 MAP 估计（例如，基于一轮 SGD）。方程 (12.124) 之所以有效，是因为我们加上和减去的项在期望上相等，因此我们得到一个无偏估计：

$$\mathbb{E} \left[ \hat{\nabla}_{cv} \mathcal{E}(\theta_t) \right] = \nabla \mathcal{E}(\hat{\theta}) + \mathbb{E} \left[ \frac{N}{B} \sum_{n \in S_t} \left( \nabla \mathcal{E}_n(\theta_t) - \nabla \mathcal{E}_n(\hat{\theta}) \right) \right]$$ (12.125)
$$ = \nabla \mathcal{E}(\hat{\theta}) + \nabla \mathcal{E}(\theta_t) - \nabla \mathcal{E}(\hat{\theta}) = \nabla \mathcal{E}(\theta_t)$$ (12.126)

请注意，第一项 \(\nabla \mathcal{E}(\hat{\theta}) = \sum_{n=1}^N \nabla \mathcal{E}_n(\hat{\theta})\) 需要遍历整个数据集一次，但只需计算一次（例如，在估计 \(\hat{\theta}\) 时）。

SGLD-CV 的一个缺点是参考点 \(\hat{\theta}\) 必须预先计算，然后固定不变。另一种方法是在线更新参考点，通过定期进行全批量估计。这称为 **SVRG-LD** [Dub+16; Cha+18]，其中 SVRG 代表随机方差减小梯度，LD 代表朗之汀动力学。如果我们用 \(\tilde{\theta}_t\) 表示最近的快照（参考点），则相应的梯度估计由以下公式给出：

$$\hat{\nabla}_{svrg}\mathcal{E}(\theta_t) = \nabla \mathcal{E}(\tilde{\theta}_t) + \frac{N}{B} \sum_{n \in S_t} \left( \nabla \mathcal{E}_n(\theta_t) - \nabla \mathcal{E}_n(\tilde{\theta}_t) \right)$$ (12.127)

我们每 \(\tau\) 步重新计算一次快照（称为 epoch 长度）。伪代码见算法 12.5。

```
Algorithm 12.5: SVRG Langevin descent
1 Initialize $\theta_0$
2 for t = 1 : T do
3   if t mod $\tau$ = 0 then
4     $\hat{\theta} = \theta_t$
5     $\tilde{g} = \sum_{n=1}^N \nabla \mathcal{E}_n(\hat{\theta})$
6   Sample minibatch $\mathcal{B}_t \in \{1, \dots, N\}$
7   $g_t = \tilde{g} + \frac{N}{B} \sum_{n \in B_t} \left( \nabla \mathcal{E}_n(\theta_t) - \nabla \mathcal{E}_n(\hat{\theta}) \right)$
8   $\theta_{t+1} = \theta_t - \eta_t g_t + \sqrt{2 \eta_t} N(0, \mathbf{I})$
```

SVRG 的缺点是它需要每 \(\tau\) 步对数据进行一次完整遍历。另一种方法称为 **SAGA-LD** [Dub+16; Cha+18]（代表随机平均梯度加速），通过存储所有 \(N\) 个梯度向量并进行增量更新来避免此问题。不幸的是，该算法的内存需求通常使其不切实际。

## 12.7.4 SG-HMC

我们在 12.5 节中讨论了哈密顿蒙特卡罗（HMC），它使用辅助动量变量来提高优于朗之汀 MC 的性能。在本节中，我们讨论了一种通过使用小批量近似梯度来加速它的方法。这称为 **SG-HMC** [CFG14; ZG21]，其中 SG 代表“随机梯度”。

回顾一下，跳跃式更新具有以下形式：

```
\(\boldsymbol{v}_{t+1/2} = \boldsymbol{v}_t - \frac{\eta}{2} \nabla \mathcal{E}(\boldsymbol{\theta}_t)\)
\(\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t + \eta \boldsymbol{v}_{t+1/2} = \boldsymbol{\theta}_t + \eta \boldsymbol{v}_t - \frac{\eta}{2} \nabla \mathcal{E}(\boldsymbol{\theta}_t)\)
\(\boldsymbol{v}_{t+1} = \boldsymbol{v}_{t+1/2} - \frac{\eta}{2} \nabla \mathcal{E}(\boldsymbol{\theta}_{t+1}) = \boldsymbol{v}_t - \frac{\eta}{2} \nabla \mathcal{E}(\boldsymbol{\theta}_t) - \frac{\eta}{2} \nabla \mathcal{E}(\boldsymbol{\theta}_{t+1})\)
```

我们可以用随机近似替换全批量梯度，从而得到

```
\(\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t + \eta \boldsymbol{v}_t - \frac{\eta^2}{2} \boldsymbol{g}(\boldsymbol{\theta}_t, \boldsymbol{\xi}_t)\)
\(\boldsymbol{v}_{t+1} = \boldsymbol{v}_t - \frac{\eta}{2} \boldsymbol{g}(\boldsymbol{\theta}_t, \boldsymbol{\xi}_t) - \frac{\eta}{2} \boldsymbol{g}(\boldsymbol{\theta}_{t+1}, \boldsymbol{\xi}_{t+1/2})\)
```

其中 \(\boldsymbol{\xi}_t\) 和 \(\boldsymbol{\xi}_{t+1/2}\) 是独立的随机源（例如，批次索引）。在 [ZG21] 中，他们表明该算法（即使没有 MH 拒绝步骤）对后验提供了良好的近似（在具有小 Wasserstein-2 距离的意义下），适用于能量函数强凸的情况。此外，如果我们使用 12.7.3 节中讨论的方差减小方法，性能可以得到显著提高。

## 12.7.5 欠阻尼朗之汀动力学

**欠阻尼朗之汀动力学**（**ULD**）具有以下 SDE 形式 [CDC15; LMS16; Che+18a; Che+18d]：

```
\(d\boldsymbol{\theta}_t = \boldsymbol{v}_t dt\)
\(d\boldsymbol{v}_t = -\boldsymbol{g}(\boldsymbol{\theta}_t) dt - \gamma \boldsymbol{v}_t dt + \sqrt{2\gamma} d\boldsymbol{W}_t\)
```

其中 \(\boldsymbol{g}(\boldsymbol{\theta}_t) = \nabla \mathcal{E}(\boldsymbol{\theta}_t)\) 是作用在粒子上的梯度或力，\(\gamma > 0\) 是**摩擦**参数，\(d\boldsymbol{W}_t\) 是维纳噪声。

方程 (12.133) 类似于方程 (12.83) 中的朗之汀动力学，但增加了动量项 \(\boldsymbol{v}_t\)。我们可以使用各种积分方法求解该动力学。可以证明（例如，参见 [LMS16]）这些方法的精度为二阶，而求解标准（过阻尼）朗之汀动力学的精度仅为一阶，因此为了达到给定精度，需要更多的采样步骤。

