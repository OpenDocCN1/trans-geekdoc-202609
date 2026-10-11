
这显示了 $w^{(t)}$ 上 $\mathcal{O}(1/t)$ 的最后迭代收敛速率。这也意味着 $\sum_{t = 0}^{T}t\|\nabla F(w^{t})\|^{2} \leqslant L^{2}\| w^{0} - w^{\star}\|^{2}$（通过使用 $\sum_{t = 0}^{T}\Delta_{t} \leqslant D_{0}$）以及对于所有 $t \ge 0$ 有 $\|w^{(t)} - w^{\star}\| \le \|w^{0} - w^{\star}\|$（通过使用 $D[t] \le D[0]$）。

**(e) 光滑凸问题的加速梯度法。** 我们的最后一个示例遵循 Nesterov 的加速梯度方案：

```
z^{t} := w^{t} + \beta_{t}(w^{t} - w^{t - 1}) \quad \text{and} \quad w^{t + 1} := z^{t} - \frac{1}{L}\nabla F(z^{t}),
```
(1.17)

其中 $\beta_{t} = \frac{\theta_{t - 1} - 1}{\theta_{t}}$，$\theta[t] \ge 1$ 使得 $\theta[t](\theta[t] - 1) \le \theta[t - 1]^{2}$ 且 $\theta[0] := 1$。这是带有动量 $\beta[t](w^{(t)} - w^{(t - 1)})$ 的 [(1.2)](#Chp001_3-28_B9780443190377000089_split_000.xhtml#deq2) 的加速变体。众所周知 [[44]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0220)，经过一些基本变换后，[(1.17)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq24) 可以写为

```
z^{t} := (1 - \frac{1}{\theta_{t}})w^{t} + \frac{1}{\theta_{t}}u^{t}, \quad w^{t + 1} := z^{t} - \frac{1}{L}\nabla F(z^{t}), \quad \text{and} \quad u^{t + 1} = u^{t} - \frac{\theta_{t}}{L}\nabla F(z^{t}).
```

令 $v^{t} := (1 - \frac{1}{\theta_{t}})w^{t} + \frac{1}{\theta_{t}}w^{\star}$。则 $z^{t} - v^{t} = \frac{1}{\theta_{t}}(u^{t} - w^{\star})$。此外，由 $F$ 的凸性，我们有 $F(z^{t}) \leqslant F(v^{t}) + \langle\nabla F(z^{t}),z^{t} - v^{t}\rangle \leqslant (1 - \frac{1}{\theta_{t}})F(w^{t}) + \frac{1}{\theta_{t}}F(w^{\star}) + \frac{1}{\theta_{t}}\langle\nabla F(z^{t}),u^{t} - w^{\star}\rangle$。因此，两边同乘 $\theta[t]^{2}$，我们得到

```
\begin{array}{lcl} {\theta_{t}^{2}[ F(z^{t}) - F(w^{\star})]\ } & {\leqslant \ } & {\theta_{t}(\theta_{t} - 1)[ F(w^{t}) - F(w^{\star})] + \theta_{t}\langle\nabla F(z^{t}),u^{t} - w^{\star}\rangle.} \\ \end{array}
```

分别类似于 [(1.14)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq15) 和 [(1.16)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq18) 的证明，我们有

```
\left\{ \begin{array}{l} {\frac{L}{2}\| u^{t + 1} - w^{\star}\|^{2} + \theta_{t}\langle\nabla F(z^{t}),u^{t} - w^{\star}\rangle = \frac{L}{2}\| u^{t} - w^{\star}\|^{2} + \frac{\theta_{t}^{2}}{2L}\|\nabla F(z^{t})\|^{2},} \\ {\theta_{t}^{2}[ F(w^{t + 1}) - F(w^{\star})] + \frac{\theta_{t}^{2}}{2L}\|\nabla F(z^{t})\|^{2} \leqslant \theta_{t}^{2}[ F(z^{t}) - F(w^{\star})].} \\ \end{array} \right.
```

将最后三个不等式相加，我们得到

```
\underset{D_{t + 1}}{\underset{\text{︸}}{\theta_{t}^{2}[ F(w^{t + 1}) - F(w^{\star})] + \frac{L}{2}\| u^{t + 1} - w^{\star}\|^{2}}} + \underset{\Delta_{t}}{\underset{\text{︸}}{(\theta_{t - 1}^{2} - \theta_{t}(\theta_{t} - 1))[ F(w^{t}) - F(w^{\star})]}} \quad \leqslant \underset{D_{t}}{\underset{\text{︸}}{\theta_{t - 1}^{2}[ F(w^{t}) - F(w^{\star})] + \frac{L}{2}\| u^{t} - w^{\star}\|^{2}}},
```
(1.18)

这正是 [(1.13)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq14)（其中 $E[t] = 0$ 且 $\omega[t] = 1$），前提是 $\theta[t - 1]^{2} - \theta[t](\theta[t] - 1) \ge 0$（注意 $\theta[0] = 1$ 和 $\theta_{- 1} = \frac{1}{2}$ 满足此条件）。递归估计 [(1.18)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq28) 意味着 $D[t] \le D[0]$，从而得到

```
F(w^{t}) - F(w^{\star}) \leqslant \frac{D_{0}}{\theta_{t - 1}^{2}} = \frac{L}{2\theta_{t - 1}^{2}}\| w^{0} - w^{\star}\|^{2}.
```

特别地，如果我们选择 $\theta_{t - 1} := \frac{t + 1}{2}$，则 $\theta_{t - 1}^{2} = \frac{(t + 1)^{2}}{4} \geqslant \theta_{t}(\theta_{t} - 1) = \frac{t(t + 1)}{4}$，从而得到最后迭代收敛保证 $F(w^{t}) - F(w^{\star}) \leqslant \frac{2L\| w^{0} - w^{\star}\|^{2}}{(t + 1)^{2}}$。

我们已经展示了如何利用统一的递归表达式 [(1.13)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq14) 来分析四种不同的确定性梯度型算法。与文献中的经典技术相比，它提供了一种简单的方法，只需几行即可推导出收敛速率分析。我们相信这种方法可以扩展到分析此处未列出的其他方法。

### 1.2.9 收敛速率与复杂度分析

经典优化文献通常刻画基础算法的渐近收敛或线性收敛速率，而次线性速率或预言机复杂度在很大程度上难以捉摸，参见例如 [[3]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0015)、[[21]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0105)、[[22]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0110)、[[31]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0155)、[[38]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0190)、[[53]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0265)。次线性收敛速率已在凸优化方法中被广泛研究，参见例如 [[45]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0225)，而预言机复杂度分析则在 [[43]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0215) 中得到正式研究。最近，由于在现代信号和图像处理、机器学习以及统计学习中的大规模问题应用 [[9]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0045)、[[28]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0140)、[[67]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0335)，这些主题变得越来越流行。让我们在此详细讨论这些概念。
