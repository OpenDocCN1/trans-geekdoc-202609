
Following policy `π`, each time we perform an individual transition from `s` to `s′` getting reward `r`, we get a sample estimate of `A` and `b`. The sample estimate of `A` is the outer-product of vectors `ϕ(s)` and `ϕ(s) − γ ⋅ ϕ(s′)`. The sample estimate of `b` is scalar `r` times vector `ϕ(s)`. We average these sample estimates across many such individual transitions. Note that this algorithm is exactly the Least Squares Temporal Difference (LSTD) algorithm we've covered earlier in this chapter. Thus, we now know that LSTD converges to `w[PBE]`, i.e., minimizes (in fact, takes down to 0) `PBE`. If the number of features `m` is large or if we are doing non-linear function approximation or Off-Policy, then we seek a gradient-based TD algorithm. It turns out that our usual Semi-Gradient TD algorithm converges to `w[PBE]` in the case of on-policy linear function approximation. Note that the update for the usual Semi-Gradient TD algorithm in the case of on-policy linear function approximation is as follows:

```
\begin{array}{r} {\Delta\mathbf{\mathbf{w}} = \alpha \cdot (r + \gamma \cdot \phi{(s^{\prime})}^{T} \cdot \mathbf{\mathbf{w}} - \phi{(s)}^{T} \cdot \mathbf{\mathbf{w}}) \cdot \phi(s)} \\ \end{array}
```

This converges to `w[PBE]` because at convergence, we have: 𝔼[*π*]\[*Δ***w**\] = 0, which can be expressed as:

```
\begin{array}{r} {\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot (\mathcal{R}^{\pi} + \gamma\mathcal{P}^{\pi} \cdot \mathbf{\mathbf{\Phi}} \cdot \mathbf{\mathbf{w}} - \mathbf{\mathbf{\Phi}} \cdot \mathbf{\mathbf{w}}) = 0} \\ \end{array}
```

```
\begin{array}{r} \left. \Rightarrow\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot (\mathbf{\mathbf{\Phi}} - \gamma\mathcal{P}^{\pi} \cdot \mathbf{\mathbf{\Phi}}) \cdot \mathbf{\mathbf{w}} = \mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathcal{R}^{\pi} \right. \\ \end{array}
```

which is satisfied for `w = w[PBE]` (as seen from Equation (13.4)).

## 13.8 GRADIENT TEMPORAL-DIFFERENCE (GRADIENT TD)

For on-policy linear function approximation, the semi-gradient TD algorithm gives us `w[PBE]`. But to obtain `w[PBE]` in the case of non-linear function approximation or in the case of Off-Policy, we need a different approach. The different approach is Gradient Temporal-Difference (abbreviated, Gradient TD), the subject of this section.

The original Gradient TD algorithm, due to Sutton, Szepesvari, Maei ([R. S. Sutton, Szepesvári, and Maei 2008](#bib01.xhtml#refbib_60)) is typically abbreviated as GTD. Researchers then came up with a second-generation Gradient TD algorithm ([R. S. Sutton et al. 2009](#bib01.xhtml#refbib_59)), which is typically abbreviated as GTD-2. The same researchers also came up with a TD algorithm with Gradient Correction ([R. S. Sutton et al. 2009](#bib01.xhtml#refbib_59)), which is typically abbreviated as TDC.

We now cover the TDC algorithm. For simplicity of articulation and ease of understanding, we restrict to the case of linear function approximation in our coverage of the TDC algorithm below. However, do bear in mind that much of the concepts below extend to non-linear function approximation (which is where we reap the benefits of Gradient TD).

Our first task is to set up the appropriate loss function whose gradient will drive the Stochastic Gradient Descent.

```
\begin{array}{r} {\mathbf{\mathbf{w}}_{PBE} = \text{arg}\,\text{min}_{\mathbf{\mathbf{w}}}d(\mathbf{\mathbf{\Pi}}_{\mathbf{\mathbf{\Phi}}} \cdot \mathbf{\mathbf{B}}^{\pi} \cdot \mathbf{\mathbf{V}}_{\mathbf{\mathbf{w}}},\mathbf{\mathbf{V}}_{\mathbf{\mathbf{w}}}) = \text{arg}\,\text{min}_{\mathbf{\mathbf{w}}}d(\mathbf{\mathbf{\Pi}}_{\mathbf{\mathbf{\Phi}}} \cdot \mathbf{\mathbf{B}}^{\pi} \cdot \mathbf{\mathbf{V}}_{\mathbf{\mathbf{w}}},\mathbf{\mathbf{\Pi}}_{\mathbf{\mathbf{\Phi}}} \cdot \mathbf{\mathbf{V}}_{\mathbf{\mathbf{w}}})} \\ \end{array}
```

So we define the loss function (denoting `B^(π) ⋅ V[w] − V[w]` as `δ[w]`) as:

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

We derive the TDC Algorithm based on ∇[**w**]ℒ(**w**).

```
\begin{array}{r} {\nabla_{\mathbf{\mathbf{w}}}\mathcal{L}(\mathbf{\mathbf{w}}) = 2 \cdot (\nabla_{\mathbf{\mathbf{w}}}{(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}})}^{T}) \cdot {(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}})}^{- 1} \cdot (\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\delta}}_{\mathbf{\mathbf{w}}})} \\ \end{array}
```
