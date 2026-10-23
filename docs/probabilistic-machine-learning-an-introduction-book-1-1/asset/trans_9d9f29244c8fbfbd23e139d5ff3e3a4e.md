
此外，我们有

$$|\mathbf{M}|=|\mathbf{M}/\mathbf{H}|\,|\mathbf{H}|=|\mathbf{M}/\mathbf{E}|\,|\mathbf{E}| \tag{C.129}$$

$$|\mathbf{M}/\mathbf{H}|=\frac{|\mathbf{M}/\mathbf{E}|\,|\mathbf{E}|}{|\mathbf{H}|} \tag{C.130}$$

$$|\mathbf{E}-\mathbf{F}\mathbf{H}^{-1}\mathbf{G}|=|\mathbf{H}-\mathbf{G}\mathbf{E}^{-1}\mathbf{F}|\,|\mathbf{H}^{-1}|\,|\mathbf{E}| \tag{C.131}$$

因此（设 $\mathbf{E}=\mathbf{A}$，$\mathbf{F}=-\mathbf{u}$，$\mathbf{G}=\mathbf{v}^{\top}$，$\mathbf{H}=1$）我们有

$$|\mathbf{A}+\mathbf{u}\mathbf{v}^{\top}|=(1+\mathbf{v}^{\top}\mathbf{A}^{-1}\mathbf{u})|\mathbf{A}| \tag{C.132}$$

这被称为 **矩阵行列式引理**。

## C.4 特征值分解 (EVD)

本节中，我们回顾关于 **特征值分解** 或 **EVD** 的一些标准材料，针对方阵（实值）。

### C.4.1 基础

给定方阵 $\mathbf{A}\in\mathbb{R}^{n\times n}$，我们称 $\lambda\in\mathbb{R}$ 是 $\mathbf{A}$ 的 **特征值**，而 $\mathbf{u}\in\mathbb{R}^{n}$ 是对应的 **特征向量**，如果

$$\mathbf{A}\mathbf{u}=\lambda\mathbf{u},\quad \mathbf{u}\neq 0. \tag{C.133}$$

直观上，这个定义意味着用 $\mathbf{A}$ 乘以向量 $\mathbf{u}$ 得到的新向量与 $\mathbf{u}$ 指向同一方向，但按因子 $\lambda$ 缩放。例如，如果 $\mathbf{A}$ 是旋转矩阵，则 $\mathbf{u}$ 是旋转轴且 $\lambda=1$。

注意，对于任意特征向量 $\mathbf{u}\in\mathbb{R}^{n}$ 和标量 $c\in\mathbb{R}$，

$$\mathbf{A}(c\mathbf{u})=c\mathbf{A}\mathbf{u}=c\lambda\mathbf{u}=\lambda(c\mathbf{u}) \tag{C.134}$$

因此 $c\mathbf{u}$ 也是一个特征向量。因此当我们谈论与 $\lambda$ 相关联的“该”特征向量时，我们通常假设特征向量被归一化为长度为 1（这仍然会产生一些歧义，因为 $\mathbf{u}$ 和 $-\mathbf{u}$ 都是特征向量，但我们只能接受这一点）。

我们可以将上式改写为：$(\lambda,\mathbf{x})$ 是 $\mathbf{A}$ 的特征值-特征向量对，如果

$$(\lambda\mathbf{I}-\mathbf{A})\mathbf{u}=0,\quad \mathbf{u}\neq 0. \tag{C.135}$$

现在 $(\lambda\mathbf{I}-\mathbf{A})\mathbf{u}=0$ 对 $\mathbf{u}$ 有非零解，当且仅当 $(\lambda\mathbf{I}-\mathbf{A})$ 有非空零空间，而这仅在 $(\lambda\mathbf{I}-\mathbf{A})$ 是奇异时成立，即

$$\det(\lambda\mathbf{I}-\mathbf{A})=0. \tag{C.136}$$

这被称为 $\mathbf{A}$ 的 **特征方程**。（参见练习 C.2。）该方程的 $n$ 个解是 $n$ 个（可能为复值）特征值 $\lambda_i$，而 $\mathbf{u}_i$ 是对应的特征向量。通常按特征值大小对特征向量排序，幅度最大的排在前面。

以下是特征值和特征向量的性质。

因此，对任意对称矩阵 **A** 进行乘法可以解释为先乘以旋转矩阵 **U**ᵀ，再乘以缩放矩阵 **Λ**，最后乘以逆旋转 **U**。

一旦我们对矩阵进行了对角化，求逆就很容易了。由于 **A** = **UΛU**ᵀ，其中 **U**ᵀ = **U**⁻¹，我们有

$$\mathbf{A}^{-1}=\mathbf{U}\Lambda^{-1}\mathbf{U}^{\mathsf T}=\sum_{i=1}^{d}\frac{1}{\lambda_i}\mathbf{u}_i\mathbf{u}_i^{\mathsf T} \tag{C.144}$$

这相当于先旋转，再去缩放，然后再旋转回来。

### C.4.3.1 正定性检查

我们也可以利用对角化性质来证明对称矩阵正定当且仅当其所有特征值都为正。为此，注意到

$$\mathbf{x}^{\mathsf T}\mathbf{A}\mathbf{x}=\mathbf{x}^{\mathsf T}\mathbf{U}\Lambda\mathbf{U}^{\mathsf T}\mathbf{x}=\mathbf{y}^{\mathsf T}\Lambda\mathbf{y}=\sum_{i=1}^{n}\lambda_i y_i^2 \tag{C.145}$$

其中 **y** = **U**ᵀ**x**。由于 $y_i^2$ 总是非负的，该表达式的符号完全取决于 $\lambda_i$。如果所有 $\lambda_i>0$，则矩阵为正定；如果所有 $\lambda_i\geq 0$，则为半正定。同样，如果所有 $\lambda_i<0$ 或 $\lambda_i\leq 0$，则 **A** 分别为负定或负半定。最后，如果 **A** 同时具有正负特征值，则为不定。

### C.4.4 二次型的几何

**二次型** 是可以写成如下形式 的函数

$$f(\mathbf{x})=\mathbf{x}^{\mathsf T}\mathbf{A}\mathbf{x} \tag{C.146}$$

其中 **x** ∈ ℝⁿ 且 **A** 是正定对称的 $n$ 阶矩阵。设 **A** = **UΛU**ᵀ 为 **A** 的对角化（参见 Sec. [C.4.3](#)）。因此我们可以写成

$$f(\mathbf{x})=\mathbf{x}^{\mathsf T}\mathbf{A}\mathbf{x}=\mathbf{x}^{\mathsf T}\mathbf{U}\Lambda\mathbf{U}^{\mathsf T}\mathbf{x}=\mathbf{y}^{\mathsf T}\Lambda\mathbf{y}=\sum_{i=1}^{n}\lambda_i y_i^2 \tag{C.147}$$

其中 $y_i=\mathbf{x}^{\mathsf T}\mathbf{u}_i$ 且 $\lambda_i>0$（因为 **A** 为正定）。$f(\mathbf{x})$ 的水平集定义了超椭球。例如，在 2 维中，我们有

$$\lambda_1y_1^2+\lambda_2y_2^2=r \tag{C.148}$$

这是二维椭圆的方程。这在图 [C.6](#) 中有所说明。特征向量决定了椭圆的方向，特征值决定了其拉伸程度。

### C.4.5 数据标准化与白化

假设我们有一个数据集 **X** ∈ ℝᴺˣᴰ。通常对数据进行预处理，使每一列均值为零且方差为一。这称为数据标准化，正如我们在 Sec. [10.2.8](#) 中讨论的那样。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_819_0.png)

Figure C.6: 二次型 $(\mathbf{x} - \boldsymbol{\mu})\top \mathbf{A} (\mathbf{x} - \boldsymbol{\mu})$ 在 $2d$ 中的水平集可视化。椭圆的长轴和短轴由 $\mathbf{A}$ 的前两个特征向量 $\mathbf{u}_1$ 和 $\mathbf{u}_2$ 定义。改编自 [Bis06] 的图 2.7。由 *gaussEvec.m* 生成。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_819_1.png)

Figure C.7: (a) 身高/体重数据。(b) 标准化。(c) PCA 白化。(d) ZCA 白化。数字指的是前 4 个数据点，但总共有 73 个数据点。由 *height_weight_whiten_plot.py* 生成。

虽然标准化使方差为 1，但它并不能消除列之间的相关性。为此，我们必须 **白化** 数据。为此定义经验协方差矩阵为 $\mathbf{\Sigma} = \frac{1}{N} \mathbf{X}^\top \mathbf{X}$，并设 $\mathbf{\Sigma} = \mathbf{E} \mathbf{D} \mathbf{E}^\top$ 为其对角化。等价地，设 $[\mathbf{U}, \mathbf{S}, \mathbf{V}]$ 为 $\mathbf{X}$ 的 SVD（因此 $\mathbf{E} = \mathbf{V}$ 且 $\mathbf{D} = \mathbf{S}^2$，如我们在 Sec. 20.1.3.3 中讨论的那样）。现在定义

$$\mathbf{W}_{pca} = \mathbf{D}^{-\frac{1}{2}} \mathbf{E}^\top \tag{C.149}$$

这称为 **PCA 白化** 矩阵。（我们在 Sec. 20.1 中讨论 PCA。）设 $\mathbf{y} = \mathbf{W}_{pca} \mathbf{x}$ 为变换后的向量。我们可以按如下方式检查其协方差为白：

$$\text{Cov}[\mathbf{y}] = \mathbf{W} \mathbb{E}[\mathbf{x}\mathbf{x}^\top] \mathbf{W}^\top = \mathbf{W} \mathbf{\Sigma} \mathbf{W}^\top = (\mathbf{D}^{-\frac{1}{2}} \mathbf{E}^\top)(\mathbf{E} \mathbf{D} \mathbf{E}^\top)(\mathbf{E} \mathbf{D}^{-\frac{1}{2}}) = \mathbf{I} \tag{C.150}$$

白化矩阵不是唯一的，因为对其进行任意旋转 $\mathbf{W} = \mathbf{R} \mathbf{W}_{pca}$ 仍会保持白化性质，即 $\mathbf{W}^\top \mathbf{W} = \mathbf{\Sigma}^{-1}$。例如，如果取 $\mathbf{R} = \mathbf{E}$，我们得到

$$\mathbf{W}_{zca} = \mathbf{E} \mathbf{D}^{-\frac{1}{2}} \mathbf{E}^\top = \mathbf{\Sigma}^{-\frac{1}{2}} = \mathbf{V} \mathbf{S}^{-1} \mathbf{V}^\top \tag{C.151}$$

这称为马哈拉诺比斯白化或 ZCA。（ZCA 代表“零相位分量分析”，由 [BS97] 提出。）ZCA 白化相对于 PCA 白化的优势在于，变换后的数据在最小二乘意义下尽可能接近原始数据 [Amo17]。它在图 C.7 中有所说明。当应用于图像时，ZCA 变换后的数据向量仍然看起来像图像。这在该方法用于深度学习系统内部时很有用 [KH09]。

### C.4.6 幂方法

我们现在描述一种计算实对称矩阵最大特征值对应特征向量的简单迭代方法；这称为幂方法。当矩阵非常大但稀疏时，这很有用。例如，Google 的 PageRank 使用它来计算万维网转移矩阵的平稳分布（矩阵大小约为 30 亿！）。在 Sec. C.4.7 中，我们将看到如何使用该方法计算后续特征向量和值。

设 A 为具有标准正交特征向量 u_i 和特征值 |λ1| > |λ2| ≥ ⋯ ≥ |λm| ≥ 0 的矩阵，因此 A = U Λ U^T。设 v0 为 A 值域中的任意向量，因此存在 x 使 A x = v0。因此我们可以写成 v0 = U Λ U^T x = a1 u1 + ⋯ + am um (C.152)，其中 a_i 为常数。现在我们可以反复用 A 乘以 v 并重新归一化：v_t ∝ A v_{t-1} (C.153)（我们在每次迭代中进行归一化以保证数值稳定性。）

由于 v_t 是 A^t v0 的倍数，我们有 v_t ∝ a1 λ1^t u1 + a2 λ2^t u2 + ⋯ + am λm^t um = λ1^t (a1 u1 + a2 (λ2/λ1) u2 + ⋯ + am (λm/λ1) um) → λ1^t a1 u1 (C.156)，因为当 k > 1 时 |λk/λ1| < 1（假设特征值按降序排列）。因此我们看到它收敛到 u1，尽管收敛速度不快（误差在每次迭代中大约减少 |λ2|/|λ1|）。唯一的要求是初始猜测满足 v0^T u1 ≠ 0，这对于随机 v0 来说以高概率成立。

我们现在讨论如何计算对应的特征值 λ1。定义瑞利商为 R(A, x) ≜ x^T A x / x^T x (C.157)。因此 R(A, u_i) = u_i^T A u_i / u_i^T u_i = λ_i (C.158)。因此我们可以很容易地从 u1 和 A 计算 λ1。参见 power_method_demo.py 获取示例代码。
