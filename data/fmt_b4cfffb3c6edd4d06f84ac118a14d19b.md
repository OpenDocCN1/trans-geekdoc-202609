
其中 $\mathcal{N}_k$ 是与第 $k$ 个智能体的邻居对应的索引集合，即在相应图中与第 $k$ 个节点共享链路的节点（参见第 5.13 节）。矩阵 $A = [a_{mk}],\ m,k = 1,2,\dots,K$ 是一个混合矩阵，它必须满足某些性质，例如是左随机或双随机矩阵（第 5.13.2 节）。

在上述框架中，基于递减步长序列提出了许多算法，这些算法收敛于解 $\boldsymbol{\theta}_\ast$，即

$$
\boldsymbol{\theta}_\ast = \arg\min_{\boldsymbol{\theta}} J(\boldsymbol{\theta}).
$$

例如在文献 [39] 中，在有界梯度和步长 $\mu_i = \frac{1}{\sqrt{i}}$ 的假设下，达到了 $\mathcal{O}(\frac{\ln i}{\sqrt{i}})$ 的收敛速度。对于在动态图上实现的所谓 *push* 方法 [62]，也有类似的结果。在强凸性假设 [63] 下，可以获得更快的收敛速度。

文献 [85] 引入了一种称为 EXTRA 版本的修正，该修正针对公式 (8.144) 中给出的基本迭代方案，它采用常数步长 $\mu_i = \mu$，并且可以达到 $\mathcal{O}(\frac{1}{i})$ 的收敛速度，在代价函数的强凸性假设下甚至可以达到线性收敛速度。文献 [110,111] 发展了扩散类算法的一种关系，与原始的 EXTRA 算法相比，它也放松了关于矩阵 $A$ 的一些假设。

在本书第三版编写时，分布式优化是一个正在进行激烈研究的课题。本节的目的不是展示和总结相关文献，而是更多地让读者了解该领域的一些关键贡献和研究方向。

## 习题

1. **8.1** 证明广义希尔伯特空间中的柯西-施瓦茨不等式。

2. **8.2** 证明 (a) 希尔伯特空间 $\mathbb{H}$ 中的点集

   $$C = \{\boldsymbol{x}: \|\boldsymbol{x}\| \le 1\}$$

   是凸集，以及 (b) 点集

   $$C = \{\boldsymbol{x}: \|\boldsymbol{x}\| = 1\}$$

   是非凸集。

3. **8.3** 证明一阶凸性条件。

4. **8.4** 证明如果一维函数

   $$g(t) := f(\boldsymbol{x} + t\boldsymbol{y})$$

   对于 $f$ 定义域内的 $\forall \boldsymbol{x}, \boldsymbol{y}$ 都是凸的，则函数 $f$ 是凸的。

5. **8.5** 证明二阶凸性条件。

   *提示*：先针对一维情况证明该断言，然后利用上一题的结果进行推广。

6. **8.6** 证明函数

   $$f: \mathbb{R}^{(l)} \mapsto \mathbb{R}$$

   是凸的当且仅当其超图是凸的。

7. **8.7** 证明如果一个函数是凸的，则对于任意 $\xi$，其下水平集是凸的。

### 8.8

证明在希尔伯特空间 $\mathbb{H}$ 中，平行四边形法则

$$
\|\mathbf{x} + \mathbf{y}\|^2 + \|\mathbf{x} - \mathbf{y}\|^2 = 2(\|\mathbf{x}\|^2 + \|\mathbf{y}\|^2), \quad \forall \mathbf{x}, \mathbf{y} \in \mathbb{H}
$$

成立。

### 8.9

证明如果 $\mathbf{x}, \mathbf{y} \in \mathbb{H}$，其中 $\mathbb{H}$ 是希尔伯特空间，则内积诱导的范数满足三角不等式，这是任意范数所要求的，即

$$
\|\mathbf{x} + \mathbf{y}\| \le \|\mathbf{x}\| + \|\mathbf{y}\|.
$$

### 8.10

证明如果点 $\mathbf{x}^*$ 是凸函数的局部极小值点，则它必然是全局极小值点。此外，如果函数是严格凸的，则它是唯一的极小值点。

### 8.11

设 $C$ 是希尔伯特空间 $\mathbb{H}$ 中的一个闭凸集。然后证明 $\forall \mathbf{x} \in \mathbb{H}$，存在一点，记为 $P_C(\mathbf{x}) \in C$，使得

$$
\|\mathbf{x} - P_C(\mathbf{x})\| = \min_{\mathbf{y} \in C} \|\mathbf{x} - \mathbf{y}\|.
$$

### 8.12

证明希尔伯特空间 $\mathbb{H}$ 中一点 $\mathbf{x}$ 在非空闭凸集 $C \subset \mathbb{H}$ 上的投影位于 $C$ 的边界上。

### 8.13

推导（实）希尔伯特空间 $\mathbb{H}$ 中点到超平面的投影公式。

### 8.14

推导点到闭球 $B[0, \delta]$ 的投影公式。

### 8.15

找出一个点的例子，其在 $\ell_1$ 球上的投影不唯一。

### 8.16

证明如果 $C \subset \mathbb{H}$ 是希尔伯特空间中的一个闭凸集，则 $\forall \mathbf{x} \in \mathbb{H}$ 和 $\forall \mathbf{y} \in C$，投影 $P_C(\mathbf{x})$ 满足以下性质：

#### 数学性质与证明

* **不等式 1**：

  `Real{⟨x − P_C(x), y − P_C(x)⟩} ≤ 0`

* **不等式 2**：

  `‖P_C(x) − P_C(y)‖² ≤ Real{⟨x − y, P_C(x) − P_C(y)⟩}`

#### 8.17 证明题

证明：如果 `S` 是希尔伯特空间 `H` 中的一个闭子空间（`S ⊂ H`），则对任意 `x, y ∈ H`，有：

```
⟨x, P_S(y)⟩ = ⟨P_S(x), y⟩ = ⟨P_S(x), P_S(y)⟩
```

1. 以及

   `P_S(a x + b y) = a P_S(x) + b P_S(y)`。

> **提示**：使用题目 8.18 的结论。

### 8.18

设 $S$ 为希尔伯特空间 $\mathbb{H}$ 中的一个闭凸子空间，$S \subset \mathbb{H}$。设 $S^\perp$ 为所有与 $S$ 正交的元素 $\mathbf{x} \in \mathbb{H}$ 组成的集合。证明：

(a) $S^\perp$ 也是一个闭子空间；

(b) $S \cap S^\perp = \{0\}$；

(c) $\mathbb{H} = S \oplus S^\perp$，即 $\forall \mathbf{x} \in \mathbb{H}, \exists \mathbf{x}_1 \in S$ 和 $\mathbf{x}_2 \in S^\perp: \mathbf{x} = \mathbf{x}_1 + \mathbf{x}_2$，其中 $\mathbf{x}_1, \mathbf{x}_2$ 是唯一的。

### 8.19

证明松弛投影算子是一个非扩张映射。

### 8.20

证明松弛投影算子是一个强吸引映射。

### 8.21

给出希尔伯特空间 $\mathbb{H}$ 中一个弱收敛但不强收敛的序列的例子。

### 8.22

证明如果 $C_1, C_2, \dots, C_K$ 是希尔伯特空间 $\mathbb{H}$ 中的闭凸集，则算子

$$T = T_{C_K} \cdots T_{C_1}$$

1. 是一个*正则*算子；即

   $$\|T^{(n-1)}(\mathbf{x}) - T^{(n)}(\mathbf{x})\| \to 0, \quad n \to \infty,$$

   其中 $T^{(n)} := T T \dots T$ 表示 $T$ 连续应用 $n$ 次。

### 8.23

证明基本 POCS 定理在希尔伯特空间 $\mathbb{H}$ 中闭子空间情况下的情形。

### 8.24

推导度量距离函数 $d_C(\mathbf{x})$ 的次微分，其中 $C$ 是闭凸集 $C \subseteq \mathbb{R}^l$ 且 $\mathbf{x} \in \mathbb{R}^l$。

### 8.25

推导公式 (8.55) 中的界。

### 8.26

证明如果一个函数是 $\gamma$-Lipschitz 的，则其任意次梯度都是有界的。

### 8.27

证明公式 (8.61) 中通用投影次梯度算法的收敛性。

### 8.28

考虑公式 (8.64) 中 PDMb 的在线版本，即

$$
\mathbf{\theta}_{n} = \begin{cases} 
P_{C}\left( \mathbf{\theta}_{n - 1} - \mu_{n}\frac{J(\mathbf{\theta}_{n - 1})}{||J^{\prime}(\mathbf{\theta}_{n - 1})||^{2}}J^{\prime}(\mathbf{\theta}_{n - 1}) \right), & \text{若 } J^{\prime}(\mathbf{\theta}_{n - 1}) \neq 0, \\ 
P_{C}(\mathbf{\theta}_{n - 1}), & \text{若 } J^{\prime}(\mathbf{\theta}_{n - 1}) = 0,
\end{cases}
$$

(8.144)

1. 其中我们假设 `J[*] = 0`。如果并非如此，则可以通过平移来适应这种差异。因此，我们假设已知最小值。例如，许多任务都属于这种情况，如假设线性可分类别的 hinge 损失函数，或针对有界噪声的线性 `ϵ` 不敏感损失函数。假设

$$
\mathcal{L}_{n}(\mathbf{\theta}) = \sum\limits_{k = n - q + 1}^{n}\frac{\omega_{k}d_{C_{k}}(\mathbf{\theta}_{n - 1})}{\sum_{k = n - q + 1}^{n}\omega_{k}d_{C_{k}}(\mathbf{\theta}_{n - 1})}d_{C_{k}}(\mathbf{\theta}).
$$

1. 然后推导公式 (8.39) 的 APSM 算法。

### 8.29

推导公式 (8.83) 中次梯度算法的遗憾界。

### 8.30

证明函数 `f(x)` 是 *σ*-强凸的，当且仅当函数 `f(x) - (σ/2)||x||²` 是凸的。

### 8.31

证明如果损失函数是 *σ*-强凸的，那么如果 `μ_n = 1/(σ n)`，次梯度算法的遗憾界变为

```
(1/N) ∑_{n=1}^N L_n(θ_{n-1}) ≤ (1/N) ∑_{n=1}^N L_n(θ_*) + G²(1 + ln N) / (2σ N).
```

(8.145)

### 8.32

推导公式 (8.100)。

### 8.33

考虑一个批处理算法，它通过一个对应二次收敛速率的序列 `θ^(i)` 来计算经验损失函数的最小值 `θ_*(N)`，即

```
ln ln (1 / ||θ^(i) - θ_*(N)||) ~ i.
```

1. 证明一个运行 *n* 个时间瞬间、以消耗与批处理算法相同的计算处理资源的在线算法，对于较大的 *N* 值，能取得比批处理算法更好的性能，如 [12] 所示

   ```
   ||θ_n - θ_*||² ~ 1 / (N ln ln N) ≪ 1/N ~ ||θ_*(N) - θ_*||².
   ```

#### 2.

*提示*：利用以下事实

$$
\|\mathbf{\theta}_n - \mathbf{\theta}_*\|^2 \sim \frac{1}{n} \quad \text{and} \quad \|\mathbf{\theta}_*(N) - \mathbf{\theta}_*\|^2 \sim \frac{1}{N}.
$$

![Equation](img/si656.png)

### 8.34

证明近端算子的性质 (8.111)。

### 8.35

证明近端算子的性质 (8.112)。

### 8.36

证明反射近端算子是非扩张的，然后证明方程 (8.118) 中的递归收敛到 $f$ 的一个极小值点。

### 8.37

从方程 (8.121) 推导出方程 (8.122)。

## 计算机练习

### 8.38

考虑回归模型，

$$
y[n] = \mathbf{\theta}_o^T \mathbf{x}[n] + \eta[n],
$$

![Equation](img/si657.png)

1. 其中 $\mathbf{\theta}_o \in \mathbb{R}^{200}$ ($l = 200$)，未知向量的系数通过高斯分布 $\mathcal{N}(0, 1)$ 随机获得。噪声样本也是独立同分布的，具有零均值和方差 $\sigma_\eta^2 = 0.01$。输入序列为白噪声，通过高斯分布 $\mathcal{N}(0, 1)$ 独立同分布生成。

2. 使用训练数据样本 $(y[n], \mathbf{x}[n]) \in \mathbb{R} \times \mathbb{R}^{200}$，$n = 1, 2, \dots$，运行 APA (算法 5.2)、NLMS (算法 5.3)、RLS (算法 6.1) 和 APSM (算法 8.2) 算法来估计未知的 $\mathbf{\theta}_o$。

### 参数设置与实验

对于 **APA**，选择 `μ = 0.2`、`δ = 0.001` 和 `q = 30`。

对于 **APSM**，设置 `μ = 0.5 × M[n]`、`ε = √2 σ` 和 `q = 30`。

此外，在 **NLMS** 中设置 `μ = 1.2` 和 `δ = 0.001`。

最后，对于 **RLS**，将遗忘因子 `β` 设置为 1。

运行 100 次独立实验，并绘制每次迭代的平均误差（dB），即 `10log10(e[n]²)`，其中 `e[n]² = (y[n] − x[n]^(T) θ[n − 1])²`。比较各算法的性能。

### 噪声方差变化实验

保持相同参数，但将噪声方差改为 0.3。按上一个实验绘制每次迭代的平均误差。与之前的低噪声场景相比，观察到 APA 性能有何变化？

### 参数敏感性分析

尝试不同的参数值，研究其对收敛速度和算法收敛时的误差底噪的影响。

### 习题 8.39：自组网分布式估计

创建一个包含 10 个节点、共 32 条连接的自组网。在每个节点生成符合以下模型的数据：

```
yk = θ[o]^(T) xk + ηk,  k = 1, …, 10.
```

1. 未知向量 `θ[o] ∈ ℝ⁶⁰`，其分量通过高斯分布 `𝒩(0, 1)` 随机生成。输入向量为 i.i.d.，服从 `𝒩(0, 1)`。此外，噪声样本为 i.i.d.，由零均值高斯分布生成，方差对应不同的信噪比，在节点间随机变化，范围为 20 到 25 dB。

#### 未知向量估计算法

对于未知向量估计，采用以下算法：

- 组合后自适应扩散 APSM (算法 8.3)
- 自适应后组合 LMS (算法 5.7)
- 组合后自适应 LMS (算法 5.8)
- 非合作 LMS (算法 5.1)

##### 组合后自适应 APSM 参数

按如下方式设置参数：

- `\mu[n] = 0.5 \times M[n]`
- `\epsilon_k = \sqrt{2}\sigma_k`
- `q = 20`

##### LMS 算法参数

对于自适应后组合、组合后自适应和非合作 LMS，将步长设置为 `0.03`。

##### 组合权重

最后，根据梅特罗波利斯规则 (备注 5.4) 选择组合权重 `a[mk]`。

#### 仿真设置

运行 100 次独立实验，并绘制每次迭代的平均 MSD（以 dB 为单位）：

$$
MSD(n) = 10\log_{10}\left( \frac{1}{K}\sum_{k=1}^{K}{\|\mathbf{\theta}_k(n) - \mathbf{\theta}_o\|}^2 \right)
$$

#### 任务

1. 对比组合后自适应 APSM 与基于 LMS 算法的性能。
2. 不断尝试所涉及算法的不同参数值，并观察它们对所获得性能的影响。

#### 练习 8.40

下载 `banknote authentication` 数据集。^(⁶⁰)

## 参考文献

* [1] A. Agarwal, P. Bartlett, P. Ravikumar, M.J. Wainwright, Information-theoretic lower bounds on the oracle complexity of convex optimization, *IEEE Trans. Inf. Theory* 2012;58(5):3235–3249.
* [2] A.E. Albert, L.A. Gardner, *Stochastic Approximation and Nonlinear Regression*. MIT Press; 1967.
* [3] S. Amari, Natural gradient works efficiently in learning, *Neural Comput.* 1998;10(2):251–276.
