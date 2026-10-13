
我们现在将注意力转向 *Q* 的形式。由于变量的（假设）二元性质，一种合理的完全分解形式 *Q* 为 [34]

$$Q(\mathcal{X}^{l};\boldsymbol{\mu}) = \prod\limits_{i:x_{i} \in \mathcal{X}^{l}}\mu_{i}^{x_{i}}{(1 - \mu_{i})}^{(1 - x_{i})},$$

其中显式地展示了对变分参数 $\boldsymbol{\mu}$ 的依赖关系。此外，由于为每个变量采用了伯努利分布，$\mathbb{E}[x_{i}] = \mu_{i}$（第 [2](#Chp002_19-64_B9780443292385000081.xhtml) 章）。现在的目标是针对变分参数优化 KL 散度。将公式 [(16.18)](#Chp016_805-853_B9780443292385000226.xhtml#deq38) 和 [(16.19)](#Chp016_805-853_B9780443292385000226.xhtml#deq39) 代入

$$KL(Q||P) = \sum\limits_{x_{i} \in \mathcal{X}^{l}}Q(\mathcal{X}^{l};\boldsymbol{\mu})\ln\frac{Q(\mathcal{X}^{l};\boldsymbol{\mu})}{P(\mathcal{X}^{l}|\mathcal{X})},$$

我们得到（问题 [16.13](#Chp016_805-853_B9780443292385000226.xhtml#o0105)，[34]）
