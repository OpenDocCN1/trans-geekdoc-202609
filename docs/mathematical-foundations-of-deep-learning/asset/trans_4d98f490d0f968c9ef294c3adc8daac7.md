

机器学习模型中，模型的参数和数据必须分布在多个设备上，以确保高效训练。并行化有效地减少了计算时间，因为每个设备在数据和模型参数的不同子集上运行。**GPU/TPU 加速**是 JAX 性能的另一个关键方面，它由 cuBLAS 等库为 GPU 促成，这些库专门用于优化矩阵运算。许多数值计算任务中使用的主要操作是矩阵乘法，JAX 通过利用这些操作的硬件加速实现来优化这一点。考虑两个矩阵 **A** 和 **B** 的矩阵乘法，其中 \(\mathbf{A} \in \mathbb{R}^{n \times m}\) 和 \(\mathbf{B} \in \mathbb{R}^{m \times p}\)，生成一个矩阵 \(\mathbf{C} \in \mathbb{R}^{n \times p}\)：

\(\mathbf{C} = \mathbf{A} \times \mathbf{B}.\) (618)

使用 cuBLAS 或类似库，JAX 可以在 GPU 上执行此操作，利用硬件的大规模并行处理能力高效执行乘法。可以通过考虑 GPU 的特定内存层次结构来进一步优化此操作，其中大型矩阵乘法被分解为适合 GPU 高速内存的较小块。此技术最大限度地减少内存带宽限制，加速计算。除了这些核心操作外，JAX 允许使用 `jax.custom_jvp` 装饰器定义**自定义梯度**，使用户能够手动指定雅克比-向量积 (JVP) 以进行更高效的梯度计算。此功能在机器学习应用中特别有用，其中某些操作可能具有无法自动计算的自定义梯度。例如，在像 softmax 这样非平凡的激活函数中，为了效率，可能会显式提供自定义梯度函数：

\(\frac{\partial \text{softmax}(\mathbf{x})}{\partial \mathbf{x}} = \text{diag}(\text{softmax}(\mathbf{x})) - \text{softmax}(\mathbf{x}) \cdot \text{softmax}(\mathbf{x})^T.\) (619)

因此，JAX 同时提供了灵活性和性能，能够支持既需要高效性又需要定义复杂自定义导数的科学计算应用。

通过提供自动微分、JIT 编译、向量化、并行化、硬件加速和自定义梯度等高级功能，JAX 能够处理广泛的高性能计算任务，使其成为解决复杂科学和工程问题的宝贵工具。该框架不仅确保数值方法的正确性，还利用现代硬件的能力，实现对大规模模拟、机器学习和优化任务至关重要的性能。

## 13 附录

### 13.1 线性代数基础

### 13.1.1 矩阵与向量空间

**矩阵的定义：** 矩阵 \(A\) 是按行和列排列的数字（或来自字段 \(\mathbb{F}\) 的元素）的矩形数组：

\(A = \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1n} \\ a_{21} & a_{22} & \cdots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn} \end{bmatrix} \in \mathbb{F}^{m \times n}\) (620)

其中 \(a_{ij}\) 表示 \(A\) 在第 \(i\) 行和第 \(j\) 列的**元素**。如果 \(m = n\)，则为**方阵**。如果所有非对角元素均为零，则矩阵为**对角矩阵**。对于矩阵 \(A \in \mathbb{F}^{m \times n}\) 和 \(B \in \mathbb{F}^{m \times n}\)，以下是矩阵运算：

- **加法**：按元素定义：
  $$(A + B)_{ij} = A_{ij} + B_{ij}$$ (621)

- **标量乘法**：对于 $\alpha \in \mathbb{F}$，
  $$(\alpha A)_{ij} = \alpha \cdot A_{ij}$$ (622)

- **矩阵乘法**：如果 $A \in \mathbb{F}^{m \times p}$ 和 $B \in \mathbb{F}^{p \times n}$，则乘积 $C = AB$ 由以下给出：
  $$C_{ij} = \sum_{k=1}^p A_{ik} B_{kj}$$ (623)

仅当 $A$ 的列数等于 $B$ 的行数时，此定义才有效。

- **转置**：$A$ 的转置，记作 $A^T$，满足：
  $$(A^T)_{ij} = A_{ji}$$ (624)

- **行列式**：如果 $A \in \mathbb{F}^{n \times n}$，则其行列式递归给出为：
  $$\det(A) = \sum_{j=1}^n (-1)^{1+j} a_{1j} \det(A_{1j})$$ (625)

其中 $A_{1j}$ 是通过删除第一行和第 $j$ 列得到的 $(n - 1) \times (n - 1)$ 子矩阵。

- **逆矩阵**：方阵 $A$ 可逆当且仅当存在 $A^{-1}$ 使得：
  $$AA^{-1} = A^{-1}A = I$$ (626)

其中 $I$ 是单位矩阵。

### 13.1.2 向量空间与线性变换

**向量空间** 关于字段 $\mathbb{F}$ 的向量空间是带有两个运算的集合 $V$：

- **向量加法**：$\mathbf{v} + \mathbf{w}$ 对于 $\mathbf{v}, \mathbf{w} \in V$
- **标量乘法**：$\alpha \mathbf{v}$ 对于 $\alpha \in \mathbb{F}$ 和 $\mathbf{v} \in V$

满足 8 个向量空间公理（结合律、交换律、单位元的存在等）。如果集合 $\{\mathbf{v}_1, \mathbf{v}_2, \dots, \mathbf{v}_n\}$ 满足以下条件，则它是一组基：

- 线性无关：
  $$\sum_{i=1}^n \alpha_i \mathbf{v}_i = 0 \Rightarrow \alpha_i = 0, \forall i$$ (627)

- 张成 $V$，意味着每个 $\mathbf{v} \in V$ 都可以写成：
  $$\mathbf{v} = \sum_{i=1}^n \beta_i \mathbf{v}_i$$ (628)

$V$ 的**维度**，记作 $\dim(V)$，是基向量的数量。**线性变换**：函数 $T: V \to W$ 是线性的，如果：
  $$T(\alpha \mathbf{v} + \beta \mathbf{w}) = \alpha T(\mathbf{v}) + \beta T(\mathbf{w})$$ (629)

$T$ 的**矩阵表示**是矩阵 $A$，使得：
  $$T(\mathbf{x}) = A \mathbf{x}$$ (630)

### 13.1.3 特征值与特征向量

**定义：** 对于方阵 $A \in \mathbb{F}^{n \times n}$，特征值 $\lambda$ 和特征向量 $\mathbf{v} \neq 0$ 满足：

$$A\mathbf{v} = \lambda\mathbf{v}$$ (631)

**特征方程：** 特征值通过求解以下方程得到：

$$\det(A - \lambda I) = 0$$ (632)

这给出了关于 $\lambda$ 的 $n$ 次多项式。$(A - \lambda I)\mathbf{v} = 0$ 的所有解 $\mathbf{v}$ 的集合是与 $\lambda$ 相关的特征空间。

### 13.1.4 奇异值分解 (SVD)

**定义：** 对于任意 $A \in \mathbb{F}^{m \times n}$，**奇异值分解** (SVD) 表示：

$$A = U\Sigma V^T$$ (633)

其中 $U \in \mathbb{F}^{m \times m}$ 是正交矩阵 ($U^T U = I$)，$V \in \mathbb{F}^{n \times n}$ 是正交矩阵 ($V^T V = I$)，$\Sigma$ 是一个 $m \times n$ 对角矩阵：

$$\Sigma = \begin{bmatrix} \sigma_1 & 0 & \cdots & 0 \\ 0 & \sigma_2 & \cdots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \cdots & \sigma_r \end{bmatrix}$$ (634)

其中 $\sigma_i$ 是**奇异值**，由以下给出：

$$\sigma_i = \sqrt{\lambda_i}$$ (635)

其中 $\lambda_i$ 是 $A^T A$ 的特征值。

## 13.2 概率与统计

### 13.2.1 概率分布

**概率分布**是一种数学函数，用于提供实验中不同可能结果发生的概率。随机变量 $X$ 可以取样本空间 $S$ 中的值，概率分布描述了概率在这些可能结果上的分布方式。

**离散概率分布：** 对于从可数集合取值的离散随机变量 $X$，**概率质量函数** (PMF) 定义为：

$$P(X = x_i) = p(x_i), \quad \forall x_i \in S$$ (636)

PMF 满足以下属性：

- 对于每个 $x_i \in S$，$0 \le p(x_i) \le 1$。

- 所有可能结果的概率之和为 1：

$$\sum_{x_i \in S} p(x_i) = 1$$ (637)

离散概率分布的一个例子是**二项分布**，它描述了在固定数量的独立伯努利试验中成功次数。二项分布的 PMF 为：

$$P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}, \quad k = 0, 1, \dots, n$$ (638)

其中 \(n\) 是试验次数，\(p\) 是每次试验的成功概率，\(k\) 是成功次数。

**连续概率分布：** 对于从连续集合（例如实数轴）取值的连续随机变量 \(X\)，使用**概率密度函数** (PDF) 而不是 PMF。PDF \(f(x)\) 的定义方式使得对于任何区间 \([a, b]\)，\(X\) 落在该区间内的概率为：

$$P(a \le X \le b) = \int_a^b f(x) \, dx$$ (639)

PDF 必须满足：

- 对所有 \(x\)，\(f(x) \ge 0\)。

- \(X\) 整个范围上的总概率为 1：
  $$\int_{-\infty}^{\infty} f(x) \, dx = 1$$ (640)

连续概率分布的一个例子是**正态分布**，其 PDF 由以下给出：

$$f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}, \quad x \in \mathbb{R}$$ (641)

其中 \(\mu\) 是均值，\(\sigma^2\) 是分布的方差。

### 13.2.2 贝叶斯定理

贝叶斯定理基于可能与事件相关的条件的先验知识，描述了事件的概率。它是概率论和统计学领域的基本结果。

设 \(A\) 和 \(B\) 为两个事件。那么，贝叶斯定理给出了在 \(B\) 条件下 \(A\) 的条件概率：

$$P(A|B) = \frac{P(B|A)P(A)}{P(B)}$$ (642)

其中 \(P(A|B)\) 是在 \(B\) 条件下 \(A\) 的后验概率，\(P(B|A)\) 是似然，即在 \(A\) 条件下观察到 \(B\) 的概率，\(P(A)\) 是 \(A\) 的先验概率，\(P(B)\) 是 \(B$ 的边缘似然，计算如下：

$$P(B) = \sum_i P(B|A_i)P(A_i)$$ (643)

在连续情况下，贝叶斯定理写为：

$$P(A|B) = \frac{P(B|A)P(A)}{P(B)} = \frac{P(B|A)P(A)}{\int P(B|A')P(A') \, dA'}$$ (644)

这允许根据观察到的证据 \(B\) 更新关于假设 \(A\) 的信念。让我们考虑一种疾病的诊断测试。设 \(A\) 为某人患有该疾病的事件，设 \(B\)

