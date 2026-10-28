
表4.1 一些鲁棒聚合规则列表，它们对于所示鲁棒性系数 κ 是 (q, κ)-鲁棒平均，只要 q < n/2。最后一列表示当恶意节点数量 q 与 n 相比可忽略时 κ 的阶。

| 聚合规则 | 任意 q < n/2 时的 κ | q ∈ O_n(1) 时的 κ |
|---|---|---|
| CWMed | 4 (1 + q/(n-2q))^2 | O_n(1) |
| GeoMed | 4 (1 + q/(n-2q))^2 | O_n(1) |
| CWTM_q | (6q/(n-2q))(1 + q/(n-2q))^a | O_n(1/n) |
| Multi-Krum_{q,1} | 6 (1 + q/(n-2q)) | O_n(1) |

a CWTM 规则可以在更弱的容差（即更小的 q）下实现更好的鲁棒性（即更小的鲁棒性系数），如正文所述。

正实值常数 c（与 q 和 n 无关）满足

$$\frac{q}{n} \le \frac{1}{2}\left(\frac{c}{1+c}\right) < \frac{1}{2}. \tag{4.12}$$

那么，CWTM_q 的鲁棒性系数为 κ = 3(2+c)q/(n-2q)（见表4.1）。³ 这些鲁棒性系数的上界与前述下界匹配，至多相差常数因子。例如，代入 c = 1，我们得到对于所有 q ≤ n/4，CWTM_q 是 (q, κ)-鲁棒平均，其中 κ 分别为 6q/(n-2q) 和 9q/(n-2q)。我们注意到，对于基于中位数的规则，即 CWMed 和 GeoMed，以及 Multi-Krum_{q,1}，在任意参数 q < n/2 下，κ ∈ O_n(1)。我们将在第5章中介绍一种预聚合方案，该方案可以为基于中位数的规则赋予阶最优鲁棒性（就鲁棒平均而言），但代价是增加一些计算量。

### 注 4.5

在某些场景下，例如在推导聚合规则的鲁棒性性质时，使用鲁棒性条件 (4.11) 的以下等价替代形式更为方便：

$$ \|F(\mathbf{v}_1, \dots, \mathbf{v}_n) - \bar{\mathbf{v}}_S\|^2 \le \frac{\kappa}{2|S|^2} \sum_{i,j \in S} \|\mathbf{v}_i - \mathbf{v}_j\|^2.$$

上述结论源于这样一个事实：2|S| \sum_{i\in S} \|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2 = \sum_{i,j\in S} \|\mathbf{v}_i - \mathbf{v}_j\|^2。提示：\|\mathbf{v}_i - \mathbf{v}_j\|^2 = \|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2 + \|\mathbf{v}_j - \bar{\mathbf{v}}_S\|^2 - 2\langle \mathbf{v}_i - \bar{\mathbf{v}}_S, \mathbf{v}_j - \bar{\mathbf{v}}_S\rangle。对于任意 i \in S，我们有 \sum_{j\in S}\langle \mathbf{v}_i - \bar{\mathbf{v}}_S, \mathbf{v}_j - \bar{\mathbf{v}}_S\rangle = \langle \mathbf{v}_i - \bar{\mathbf{v}}_S, \sum_{j\in S}(\mathbf{v}_j - \bar{\mathbf{v}}_S)\rangle = \langle \mathbf{v}_i - \bar{\mathbf{v}}_S, \mathbf{0}\rangle = 0

## 4.4 鲁棒DMGD的韧性

在本节中，我们分析当聚合规则对应于上述方案之一时，鲁棒DMGD算法的韧性性质。我们首先分析鲁棒DMGD算法的一般收敛性，其中聚合规则 $F$ 满足 $(f, \kappa)$-鲁棒平均的性质。我们考虑两种情况，具体来说，即诚实节点的平均损失函数为强凸或非凸。

### 假设

为了进行收敛性分析，我们对逐点损失函数的平滑性和局部梯度估计的协方差迹做出与假设3.1和假设3.2相同的假设。此外，我们通过节点所持数据的*梯度相异性*的界限来刻画数据之间的异质性。一般来说，如果不假设这样的界限，就不可能获得任何有意义的鲁棒性保证，如后文5.3.2节所示。

**假设4.1（$\zeta$-梯度相异性）** 设 $H$ 是 $[n]$ 的一个子集，包含 $n-f$ 个诚实节点，即 $|H|=n-f$。那么，存在一个实数值 $\zeta$，使得对于所有 $\theta\in\mathbb{R}^d$，以下成立：

$$\frac{1}{n-f}\sum_{i\in H}\|\nabla\mathcal{L}_i(\theta)-\nabla\mathcal{L}_H(\theta)\|^2\leq\zeta.$$

回顾 $\mathcal{L}_H(\theta):=\frac{1}{n-f}\sum_{i\in H}\mathcal{L}_i(\theta)$。

在后续小节中，我们研究当聚合规则 $F$ 被假定为 $(f,\kappa)$-鲁棒时，鲁棒DMGD算法与经典DMGD算法（先前介绍过）之间的偏差。

### 注 4.6

一般来说，假设4.1中给出的异质性条件相当严格。实际上，对于许多模型参数与数据点交叉耦合的机器学习问题（例如回归模型和神经网络），假设4.1不一定成立。然而，出于教学原因，我们在这种梯度相异性的概念下分析梯度下降方法的鲁棒性。它使我们能够获得关于学习算法在数据异质性下性能的有意义见解。

### 4.4.1 与传统DMGD的偏差

在继续讨论强凸和非凸损失函数的具体情形之前，我们先对鲁棒DMGD算法与其原始版本（即算法4中给出的DMGD方法）之间的偏差做一个观察。回顾在鲁棒DMGD（即算法5）中，在每次迭代 $t$ 时

回顾对于任意诚实节点 $i \in H$，有 $\mathbb{E}_t\big[\mathbf{g}_t^{(i)}\big] = \nabla \mathcal{L}_i(\boldsymbol{\theta}_t)$。因此，由于 $\boldsymbol{\theta}_t$ 是历史 $\mathcal{P}_t$ 的一部分，

$$\mathbb{E}_t\Big[\big\langle \mathbf{g}_t^{(i)} - \nabla \mathcal{L}_i(\boldsymbol{\theta}_t),\; \nabla \mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) \big\rangle\Big]$$

$$= \Big\langle \mathbb{E}_t\big[ \mathbf{g}_t^{(i)} \big] - \nabla \mathcal{L}_i(\boldsymbol{\theta}_t),\; \nabla \mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) \Big\rangle = 0.$$

类似地，由于 $\mathbb{E}_t\big[ \mathbf{g}_t^{\mathrm{H}} \big] = \nabla \mathcal{L}_H(\boldsymbol{\theta}_t)$，我们有

$$\mathbb{E}_t\Big[\big\langle \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) - \mathbf{g}_t^{\mathrm{H}},\; \nabla \mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) \big\rangle\Big] = 0.$$

因此，

$$\mathbb{E}_t\big[ B_t \big] = 2\mathbb{E}_t\Big[\big\langle \mathbf{g}_t^{(i)} - \nabla \mathcal{L}_i(\boldsymbol{\theta}_t),\; \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) - \mathbf{g}_t^{\mathrm{H}} \big\rangle\Big]. \tag{4.19}$$

根据柯西-施瓦茨不等式以及 $2ab \le a^2 + b^2$ 的事实，我们得到

$$2\big\langle \mathbf{g}_t^{(i)} - \nabla \mathcal{L}_i(\boldsymbol{\theta}_t),\; \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) - \mathbf{g}_t^{\mathrm{H}} \big\rangle \le 2 \big\| \mathbf{g}_t^{(i)} - \nabla \mathcal{L}_i(\boldsymbol{\theta}_t) \big\| \big\| \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) - \mathbf{g}_t^{\mathrm{H}} \big\|$$

$$\le \big\| \mathbf{g}_t^{(i)} - \nabla \mathcal{L}_i(\boldsymbol{\theta}_t) \big\|^2 + \big\| \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) - \mathbf{g}_t^{\mathrm{H}} \big\|^2.$$

将上式代入 $(4.19)$，我们得到

$$\mathbb{E}_t\big[ B_t \big] \le \mathbb{E}_t\Big[ \big\| \mathbf{g}_t^{(i)} - \nabla \mathcal{L}_i(\boldsymbol{\theta}_t) \big\|^2 + \big\| \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) - \mathbf{g}_t^{\mathrm{H}} \big\|^2 \Big].$$

由于 $\big\| \mathbf{g}_t^{(i)} - \nabla \mathcal{L}_i(\boldsymbol{\theta}_t) \big\|^2 + \big\| \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) - \mathbf{g}_t^{\mathrm{H}} \big\|^2 = A_t - \big\| \nabla \mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) \big\|^2$，上式意味着

$$\mathbb{E}_t\big[ B_t \big] \le \mathbb{E}_t\big[ A_t \big] - \mathbb{E}_t\Big[ \big\| \nabla \mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) \big\|^2 \Big].$$

将上式代入 $(4.18)$ 得到

$$\mathbb{E}_t\Big[ \big\| \mathbf{g}_t^{(i)} - \mathbf{g}_t^{\mathrm{H}} \big\|^2 \Big] \le 2\mathbb{E}_t\big[ A_t \big] - \mathbb{E}_t\Big[ \big\| \nabla \mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) \big\|^2 \Big].$$

³ 提示：如果 q/n ≤ 1/2 (c/(1+c))，则 q/(n-2q) ≤ c/2。

