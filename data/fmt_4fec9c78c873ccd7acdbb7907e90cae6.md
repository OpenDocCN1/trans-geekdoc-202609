
(10.37) ![equation](img/c10-disp-0037.png) <math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>ED</mi><mo>=</mo><mfrac><mn>1</mn><msub><mi>N</mi><mi>d</mi></msub></mfrac><munderover><mo>&#8721;</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><msub><mi>N</mi><mi>d</mi></msub></munderover><munder><mo>min</mo><mi>j</mi></munder><mfenced open="{" close="}"><mfenced open="&#8214;" close="&#8214;"><mrow><msub><mover accent="true"><mi mathvariant="bold">s</mi><mo stretchy="true">~</mo></mover><mi>i</mi></msub><mo>&#8722;</mo><msub><mi mathvariant="bold">s</mi><mi>j</mi></msub></mrow></mfenced></mfenced><mo>+</mo><mfrac><mn>1</mn><msub><mi>N</mi><mi mathvariant="italic">ud</mi></msub></mfrac><munderover><mo>&#8721;</mo><mrow><mi>j</mi><mo>=</mo><mn>1</mn></mrow><msub><mi>N</mi><mi mathvariant="italic">ud</mi></msub></munderover><munder><mo>min</mo><mi>i</mi></munder><mfenced open="{" close="}"><mfenced open="&#8214;" close="&#8214;"><mrow><msub><mover accent="true"><mi mathvariant="bold">s</mi><mo stretchy="true">~</mo></mover><mi>i</mi></msub><mo>&#8722;</mo><msub><mi mathvariant="bold">s</mi><mi>j</mi></msub></mrow></mfenced></mfenced></math>

其中 `i` 和 `j` 分别是估计源和实际源位置的索引，`N[d]` 和 `N[ud]` 分别是估计源和未检测源的总数。

USP 和 FSP 分别定义为 `USP = N[un] / Nreal × 100%` 和 `FSP = N[false] / N[estimated] × 100%`，其中 `N[un]`、`N[real]`、`N[false]` 和 `N[estimated]` 分别是未检测源、真实源、误检源和估计源的数量。

在实践中，可以使用三种类型的头部体积导体模型：均匀球体头部体积导体模型、BEM 或 FEM 模型。由于 FEM 计算量非常大，目前使用的是受试者特定的 BEM 模型，尽管它是针对过度简化的球体头部模型 [[59]](#c10.xhtml#c10-bib-0059)。

在 ED、USP 和 FSP 方面，LRT1（即 `p = 1`）已被验证能给出最佳的定位结果。

利用脑信号的时间特性来提高定位性能也已被尝试。可以增加一个额外的时间约束，假设对于每个位置，源幅度随时间的变化是最小的。要添加的约束是 ![images](img/c10-i0026.png) <math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mo>min</mo><msubsup><mfenced open="&#8214;" close="&#8214;"><mrow><mi mathvariant="bold">s</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>&#8722;</mo><mi mathvariant="bold">s</mi><mfenced open="(" close=")"><mrow><mi>n</mi><mo>&#8722;</mo><mn>1</mn></mrow></mfenced></mrow></mfenced><mi>F</mi><mn>2</mn></msubsup></math>，其中 `n` 表示时间索引。

### 10.4.8 联合 ICA–LORETA 方法

在另一项研究 [[60]](#c10.xhtml#c10-bib-0060) 中，基于 Infomax ICA 的盲源分离（BSS）已作为预处理方案，在应用 LORETA 定位失配负波（MMN）的潜在源之前实施。MMN 是一种非自主的听觉 ERP，当规律模式被打破时，在 100–200 ms 处达到峰值。这种 ERP 似乎对应于一种原始智能。MMN 信号主要产生在上颞皮层 [61–65]。

LORETA 分析是利用与选定 ICA 成分相关的头皮图来寻找这些图的发生源。只有大于标准化数据标准差 2.5 倍的值（在 LORETA 空间分辨率中）被接受为激活。

逆问题也已在贝叶斯框架内得到解决 [[66]](#c10.xhtml#c10-bib-0066)。在这类方法中，通常需要一些关于先验概率的信息。我们再次考虑 EEG 生成模型：

(10.38) ![equation](img/c10-disp-0038.png) <math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi mathvariant="bold">x</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>=</mo><mi mathvariant="bold">Hs</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>+</mo><mi mathvariant="normal">v</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></math>

其中 `x(n)` 是一个 `n[e] × 1` 向量，包含时间 `n` 处的 EEG 采样值，`H` 是一个 `n[e] × m` 矩阵，表示头部介质模型，`s(n)` 包含时间 `n` 处源的 `m × 1` 向量采样值，`v(n)` 是时间 `n` 处噪声采样的 `n[e] × 1` 向量。关于源的先验信息对其位置和时间特性施加了一些约束。估计可以使用最大后验（MAP）准则来执行，其中估计器试图找到 `s(n)` 以最大化给定测量值 `x(n)` 时 `s(n)` 的概率分布。估计器表示为：

(10.39) ![equation](img/c10-disp-0039.png) <math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mover accent="true"><mi mathvariant="bold-italic">s</mi><mo stretchy="true">&#38;c.circ;</mo></mover><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>=</mo><mo mathvariant="italic">max</mo><mfenced open="\[" close="\]"><mrow><mi>p</mi><mo stretchy="true">(</mo><mi mathvariant="bold-italic">s</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>&#8739;</mo><mi mathvariant="bold-italic">x</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo stretchy="true">)</mo></mrow></mfenced></math>

根据贝叶斯规则，后验概率为：

(10.40) ![equation](img/c10-disp-0040.png) <math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>p</mi><mfenced open="(" close=")"><mrow><mi mathvariant="bold-italic">s</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>&#8739;</mo><mi mathvariant="bold-italic">x</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></mrow></mfenced><mo>=</mo><mi>p</mi><mfenced open="(" close=")"><mrow><mi mathvariant="bold-italic">x</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>&#8739;</mo><mi mathvariant="bold-italic">s</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></mrow></mfenced><mi>p</mi><mfenced open="(" close=")"><mrow><mi mathvariant="bold-italic">s</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></mrow></mfenced><mo>/</mo><mi>p</mi><mfenced open="(" close=")"><mrow><mi mathvariant="bold-italic">x</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></mrow></mfenced></math>

其中 `p(x(n) | s(n))` 是似然函数，`p(x(n))` 是测量值的边缘分布，`p(s(n))` 是先验概率。后验概率可以用能量函数来表示，即：

(10.41) ![equation](img/c10-disp-0041.png) <math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>p</mi><mfenced open="(" close=")"><mrow><mi mathvariant="bold-italic">s</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>&#8739;</mo><mi>z</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></mrow></mfenced><mo>=</mo><mfrac><mn>1</mn><mrow><mi>z</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></mrow></mfrac><mo mathvariant="italic">exp</mo><mfenced open="\[" close="\]"><mrow><mo form="prefix">&#8722;</mo><mi>U</mi><mfenced open="(" close=")"><mrow><mi mathvariant="bold-italic">s</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></mrow></mfenced></mrow></mfenced></math>

且 `U(s(n)) = (1 − λ)U1) + λU2)`，其中 `U[1]` 和 `U[2]` 分别对应似然函数和先验概率，且 `0 ≤ λ ≤ 1`。先验可分为两个函数：空间先验 `U[s]` 和时间先验 `U[t]`。空间先验函数可考虑源空间变化的平滑性。确定空间平滑性的代价函数为：

(10.42)

```
φ(u) = u² / (1 + (u/K)²)
```

其中 `K` 为缩放因子，决定所需的平滑度。因此，空间约束的先验函数可写为：

(10.43)

```
U_s(s(n)) = Σ_{k=1}^{n_e} [ φ_kx(∇_x s(n) ⋄ k) + φ_ky(∇_y s(n) ⋄ k) ]
```

其中下标 `x` 和 `y` 分别对应水平和垂直梯度。

时间约束通过假设 `s(n)` 在垂直于 `s(n − 1)` 的空间上的投影很小来施加。因此，作为第二个约束的时间先验函数可写为：

(10.44)

```
U_t(s(n)) = || P_{n−1}^⊥ s(n) ||²
```

其中 `P_{n−1}^⊥` 是向垂直于 `s(n − 1)` 的空间的投影。因此，`s(n)` 估计的整体最小化准则变为：

(10.45)

```
ŝ(n) = arg min_S { || x(n) − H s(n) ||² + α Σ_{k=1}^{n_e} [ φ_kx(∇_x s(n) ⋄ k) + φ_ky(∇_y s(n) ⋄ k) ] + β || P_{n−1}^⊥ s(n) ||² }
```

其中 `α` 和 `β` 为惩罚项（正则化参数）。

根据该研究结果，独立成分可由一个或多个空间分离的源产生。这证实了每个偶极子以某种方式与一个偶极子发生器相关联 [[67]](#c10.xhtml#c10-bib-0067)。此外，文中指出特定脑结构可参与不同成分，在不同观测中同时工作。ICA 与 LORETA 的结合利用了大脑的时空动力学以及源定位。

在 [[51]](#c10.xhtml#c10-bib-0051) 中，比较了四种不同的反问题方法，即 WMN、sLORETA、FOCUSS 和 SSLOFO（基于球形头模型假设且在无噪声情况下）。结果表明，在其原始形式下，当 WMN 和 sLORETA 无法获得唯一且准确的解时，SSLOFO 能给出更准确的定位。

反之，虽然 sLORETA 在仅存在一个源时性能最佳，但对于两个或多个源，`p` 等于 1.5 的 LORETA 优于其他方法。当其中一个源的相对强度降低时，所有算法重构该源的难度都会增加。然而，`p = 1.5` 的 LORETA 仍继续优于其他算法。若仅关注最强源，推荐使用 sLORETA；若关注两个或多个皮层源，则推荐使用 `p = 1.5` 的 LORETA。在 [[68]](#c10.xhtml#c10-bib-0068) 中，这些结果被用作选择 CSD 算法以定位 EEG 多个皮层源以及解释这些算法结果的指导。

## 10.5 定位问题的正向解

在这些方法中，通常已知期望源的形状（形态）的近似值。一些示例如下。

### 10.5.1 部分约束 BSS 方法

在最近的一项工作 [[69]](#c10.xhtml#c10-bib-0069) 中，已知源（如某些正常脑节律）的位置被用作先验，以便利用约束 BSS 找到异常或其他脑源信号的位置。BSS 算法的代价函数受此信息约束，且已知源被迭代计算。

考虑 `Ã = [A_k ⋮ A_uk]` 为混合矩阵，包含关于已知源 `A_k` 和未知源 `A_uk` 的几何信息。`A_k` 是 `n_e × k` 矩阵，`A_uk` 是 `n_e × (m - k)` 矩阵。给定 `A_k`，`A_uk` 可按如下方式估计：

(10.46)

```
A_uk_{n+1} = A_uk_n - ξ ∇_{A_uk} J_c
```

其中

(10.47)

```
∇_{A_uk} J_c = 2 ( [A_k ⋮ A_uk] - R_{n+1} W_{n+1}^{-1} )
```

(10.48)

```
R_{n+1} = R_n - γ ∇_R (J_c)
```

以及

(10.49)

```
J_c = || Ã_n - R_{n+1} W_{n+1}^{-1} ||_F²
```

(10.50)
