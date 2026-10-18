

按照策略 `π`，每次我们从 `s` 进行一次单独的转移到 `s′` 并获得奖励 `r` 时，我们就得到 `A` 和 `b` 的一个样本估计。`A` 的样本估计是向量 `ϕ(s)` 和 `ϕ(s) − γ ⋅ ϕ(s′)` 的外积。`b` 的样本估计是标量 `r` 乘以向量 `ϕ(s)`。我们对许多这样的单独转移对这些样本估计进行平均。请注意，该算法正是我们在本章前面介绍过的最小二乘时序差分（LSTD）算法。因此，我们现在知道 LSTD 收敛到 `w[PBE]`，即最小化（实际上，将其降至 0）`PBE`。如果特征的数量 `m` 很大，或者我们正在进行非线性函数近似或离策略学习，那么我们就寻求基于梯度的 TD 算法。结果表明，在在策略线性函数近似的情况下，我们通常的半梯度 TD 算法收敛到 `w[PBE]`。请注意，在在策略线性函数近似的情况下，通常半梯度 TD 算法的更新如下：

```
\begin{array}{r} {\Delta\mathbf{\mathbf{w}} = \alpha \cdot (r + \gamma \cdot \phi{(s^{\prime})}^{T} \cdot \mathbf{\mathbf{w}} - \phi{(s)}^{T} \cdot \mathbf{\mathbf{w}}) \cdot \phi(s)} \\ \end{array}
```

它收敛到 `w[PBE]` 是因为在收敛时，我们有：𝔼[*π*]\[*Δ***w**\] = 0，可以表示为：

```
\begin{array}{r} {\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot (\mathcal{R}^{\pi} + \gamma\mathcal{P}^{\pi} \cdot \mathbf{\mathbf{\Phi}} \cdot \mathbf{\mathbf{w}} - \mathbf{\mathbf{\Phi}} \cdot \mathbf{\mathbf{w}}) = 0} \\ \end{array}
```

```
\begin{array}{r} \left. \Rightarrow\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot (\mathbf{\mathbf{\Phi}} - \gamma\mathcal{P}^{\pi} \cdot \mathbf{\mathbf{\Phi}}) \cdot \mathbf{\mathbf{w}} = \mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathcal{R}^{\pi} \right. \\ \end{array}
```

对于 `w = w[PBE]` 成立（如方程 (13.4) 所示）。

## 13.8 梯度时序差分（GRADIENT TD）

对于在策略线性函数近似，半梯度 TD 算法给出了 `w[PBE]`。但是，为了在非线性函数近似或离策略学习的情况下获得 `w[PBE]`，我们需要一种不同的方法。这种不同的方法是梯度时序差分（简称梯度 TD），即本节的主题。

原始的梯度 TD 算法由 Sutton、Szepesvari、Maei 提出（[R. S. Sutton, Szepesvári, and Maei 2008](#bib01.xhtml#refbib_60)），通常缩写为 GTD。研究人员随后提出了第二代梯度 TD 算法（[R. S. Sutton et al. 2009](#bib01.xhtml#refbib_59)），通常缩写为 GTD-2。同一批研究人员还提出了带有梯度修正的 TD 算法（[R. S. Sutton et al. 2009](#bib01.xhtml#refbib_59)），通常缩写为 TDC。

我们现在介绍 TDC 算法。为了表述简洁和易于理解，我们在下面对 TDC 算法的介绍中限制在线性函数近似的情况。但是，请记住，下面的许多概念也扩展到非线性函数近似（正是在那里我们获得梯度 TD 的好处）。

我们的第一项任务是设置适当的损失函数，其梯度将驱动随机梯度下降。

```
\begin{array}{r} {\mathbf{\mathbf{w}}_{PBE} = \text{arg}\,\text{min}_{\mathbf{\mathbf{w}}}d(\mathbf{\mathbf{\Pi}}_{\mathbf{\mathbf{\Phi}}} \cdot \mathbf{\mathbf{B}}^{\pi} \cdot \mathbf{\mathbf{V}}_{\mathbf{\mathbf{w}}},\mathbf{\mathbf{V}}_{\mathbf{\mathbf{w}}}) = \text{arg}\,\text{min}_{\mathbf{\mathbf{w}}}d(\mathbf{\mathbf{\Pi}}_{\mathbf{\mathbf{\Phi}}} \cdot \mathbf{\mathbf{B}}^{\pi} \cdot \mathbf{\mathbf{V}}_{\mathbf{\mathbf{w}}},\mathbf{\mathbf{\Pi}}_{\mathbf{\mathbf{\Phi}}} \cdot \mathbf{\mathbf{V}}_{\mathbf{\mathbf{w}}})} \\ \end{array}
```

因此，我们定义损失函数（将 `B^(π) ⋅ V[w] − V[w]` 表示为 `δ[w]`）为：

```
\begin{array}{r} {\mathcal{L}(\mathbf{\mathbf{w}}) = {(\mathbf{\mathbf{\Pi}}_{\mathbf{\mathbf{\Phi}}} \cdot \mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}})}^{T} \cdot \mathbf{\mathbf{D}} \cdot (\mathbf{\mathbf{\Pi}}_{\mathbf{\mathbf{\Phi}}} \cdot \mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}}) = \mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}}{}^{T} \cdot \mathbf{\mathbf{\Pi}}_{\mathbf{\mathbf{\Phi}}}{}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Pi}}_{\mathbf{\mathbf{\Phi}}} \cdot \mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}}} \\ \end{array}
```

```
\begin{array}{r} {= \mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}}{}^{T} \cdot {(\mathbf{\mathbf{\Phi}} \cdot {(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}})}^{- 1} \cdot \mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}})}^{T} \cdot \mathbf{\mathbf{D}} \cdot (\mathbf{\mathbf{\Phi}} \cdot {(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}})}^{- 1} \cdot \mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}}) \cdot \mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}}} \\ \end{array}
```

```
\begin{array}{r} {= \mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}}{}^{T} \cdot (\mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}} \cdot {(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}})}^{- 1} \cdot \mathbf{\mathbf{\Phi}}^{T}) \cdot \mathbf{\mathbf{D}} \cdot (\mathbf{\mathbf{\Phi}} \cdot {(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}})}^{- 1} \cdot \mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}}) \cdot \mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}}} \\ \end{array}
```

```
\begin{array}{r} {= (\mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}}{}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}}) \cdot {(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}})}^{- 1} \cdot (\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}}) \cdot {(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}})}^{- 1} \cdot (\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}})} \\ \end{array}
```

```
\begin{array}{r} {= {(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}})}^{T} \cdot {(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}})}^{- 1} \cdot (\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}})} \\ \end{array}
```

我们基于 ∇[**w**]ℒ(**w**) 推导 TDC 算法。

```
\begin{array}{r} {\nabla_{\mathbf{\mathbf{w}}}\mathcal{L}(\mathbf{\mathbf{w}}) = 2 \cdot (\nabla_{\mathbf{\mathbf{w}}}{(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}})}^{T}) \cdot {(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}})}^{- 1} \cdot (\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}})} \\ \end{array}
```

