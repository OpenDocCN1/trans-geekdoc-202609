
Φ = Ψ = Ψ^(−H)

![Equation](images/B9780443292385000160/si353.png)

这导致了前面所述两种形式化方法之间的等价性。确实，对于这种变换，我们有

```
\underset{\text{Analysis}}{\underset{︸}{\widetilde{\mathbf{s}} = \Phi^{H}\mathbf{s}}}\quad\Leftrightarrow\quad\underset{\text{Synthesis}}{\underset{︸}{\mathbf{s} = \Phi\widetilde{\mathbf{s}}}}.
```

![Equation](images/B9780443292385000160/si354.png)

使用公式 [(10.28)](#Chp010_463-518_B9780443292385000160.xhtml#deq89) 中的最后一个公式，[(9.38)](#Chp009_417-462_B9780443292385000159.xhtml) 或 [(9.39)](#Chp009_417-462_B9780443292385000159.xhtml) 中的任务可以通过将 **θ** 替换为 **s** 而轻松获得。然而，这种推理无法推广到过完备字典的情况；在这些情况下，这两个优化任务可能会导致不同的解。

关于基于合成或基于分析的稀疏表示比较性能的前面讨论不仅具有“哲学”价值。事实证明，在实践中，某些过完备字典的性质往往不允许使用基于合成的形式化方法。这些情况是指过完备字典的列表现出高度相关性；即矩阵的相干性（定义见第 [9.6.1](#Chp009_417-462_B9780443292385000159.xhtml) 节）具有较大值。此类过完备字典的典型例子包括 Gabor 框架、曲波框架和过采样 DFT。使用此类字典可在许多应用中提升性能（例如，[111,112]）。以我们熟悉的 DFT 变换为例。该变换以采样指数正弦波的形式提供信号样本的表示，其积分频率是 $\frac{2\pi}{l}$ 的倍数

![Equation](images/B9780443292385000160/si355.png)

即，

```
\mathbf{s}: = \begin{bmatrix} s_{1} \\ s_{2} \\ \vdots \\ s_{l - 1} \\ \end{bmatrix} = \sum\limits_{i = 0}^{l - 1}{\widetilde{s}}_{i}\mathbf{\psi}_{i},
```

![Equation](images/B9780443292385000160/si356.png)(10.29)

其中，现在，*s̃*[*i*]

![Equation](images/B9780443292385000160/si357.png)

是 DFT 系数，**ψ**[*i*]

![Equation](images/B9780443292385000160/si358.png)

是频率等于 $\frac{2\pi}{l}i$ 的采样正弦波

![Equation](images/B9780443292385000160/si359.png)

即，

```
\mathbf{\psi}_{i} = \begin{bmatrix} 1 \\ {\exp\left( - j\frac{2\pi}{l}i \right)} \\ \vdots \\ {\exp\left( - j\frac{2\pi}{l}i(l - 1) \right)} \\ \end{bmatrix}.
```

![Equation](images/B9780443292385000160/si360.png)(10.30)
