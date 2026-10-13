
本章迄今为止，我们已经探讨了投影算子的概念。在本节中，我们将更进一步，介绍投影概念的一个优雅推广。请注意，当我们提到算子时，是指从 $\mathbb{R}^l \mapsto \mathbb{R}^l$ 的映射，这与函数（即从 $\mathbb{R}^l \mapsto \mathbb{R}$ 的映射）形成对比。

### 定义 8.9

设 $f : \mathbb{R}^l \mapsto \mathbb{R}$ 为一凸函数，且 $\lambda > 0$。对应的索引为 $\lambda$ 的**近端算子**或**邻近算子** [60,71]，

$$\text{Prox}_{\lambda f} : \mathbb{R}^l \mapsto \mathbb{R}^l,$$

定义为：

```
(8.105)
```

我们强调近端算子是 $\mathbb{R}^l$ 中的一个点。该定义也可推广至定义为 $f : \mathbb{R}^l \mapsto \mathbb{R} \cup \{+\infty\}$ 的函数。与近端算子密切相关的一个概念如下。

### 定义 8.10

设 $f$ 为如前所述的凸函数。我们称 $f$ 的 **Moreau 包络** 为函数：

```
(8.106)
```

注意，Moreau 包络 [59] 是一个与近端**算子**相关的**函数**，关系如下：

$$e_{\lambda f}(\mathbf{x}) = f\left( \text{Prox}_{\lambda f}(\mathbf{x}) \right) + \frac{1}{2\lambda}||\mathbf{x} - \text{Prox}_{\lambda f}(\mathbf{x})||^{2}.$$

```
(8.107)
```

Moreau 包络也可被视为一种正则化极小化，也称为 **Moreau-Yosida 正则化** [109]。此外，可以证明它是可微的（例如见 [7]）。

首先需要澄清的是公式 [(8.106)](#Chp008_343-416_B9780443292385000147.xhtml#deq200) 中的最小值是否存在。请注意，括号中的两项均为凸函数；即 $f(\mathbf{v})$ 和二次项 $||\mathbf{x} - \mathbf{v}||^2$。因此，根据凸性的定义，它们的和也是凸的。此外，后一项是严格凸的，因此它们的和也是严格凸的，这保证了存在**唯一**最小值。

### 示例 8.9

让我们计算 $\text{Prox}_{\lambda \iota_C}$，其中 $\iota_C : \mathbb{R}^l \mapsto \mathbb{R} \cup \{+\infty\}$ 代表非空闭凸子集 $C \subset \mathbb{R}^l$ 的指示函数，定义为：
