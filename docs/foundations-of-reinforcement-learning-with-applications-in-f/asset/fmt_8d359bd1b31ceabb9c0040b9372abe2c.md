
This is called the *Residual Gradient* algorithm, due to Leemon Baird ([Baird 1995](#bib01.xhtml#refbib_6)). It requires two independent samples of *s*^′ transitioning from *s*. If we do have that, it converges to **w**[*B**E*] robustly (even for non-linear function approximations). But this algorithm is slow, and doesn't converge to a desirable place. Another issue is that **w**[*B**E*] is not learnable if we can only access the features, and not underlying states. These issues led researchers to consider alternative TD algorithms.

We denote the third Value Function vector of interest in the **Φ** subspace as **w**[*T**D**E*] and define it as the vector in the **Φ** subspace for which the expected square of the TD error *δ* (when following policy *π*) is minimized. Formally,

$$
\begin{array}{r}
{\mathbf{\mathbf{w}}_{TDE} = \text{arg}\,\text{min}_{\mathbf{\mathbf{w}}}{\sum\limits_{s \in \mathcal{S}}\mathbf{\mathbf{\mu}}_{\mathbf{\mathbf{\pi}}}(s){\sum\limits_{r,s^{\prime}}{\mathbb{P}}_{\pi}}(r,s^{\prime}|s) \cdot {(r + \gamma \cdot \phi{(s^{\prime})}^{T} \cdot \mathbf{\mathbf{w}} - \phi{(s)}^{T} \cdot \mathbf{\mathbf{w}})}^{2}}}
\end{array}
$$

To perform Stochastic Gradient Descent, we have to estimate the gradient of the expected square of TD error by sampling. The weight update for each gradient sample in the Stochastic Gradient Descent is:

$$
\begin{aligned}
{\Delta\mathbf{\mathbf{w}}} & {= - \alpha \cdot \frac{1}{2} \cdot \nabla_{\mathbf{\mathbf{w}}}{(r + \gamma \cdot \phi{(s^{\prime})}^{T} \cdot \mathbf{\mathbf{w}} - \phi{(s)}^{T} \cdot \mathbf{\mathbf{w}})}^{2}} \\
& {= \alpha \cdot (r + \gamma \cdot \phi{(s^{\prime})}^{T} \cdot \mathbf{\mathbf{w}} - \phi{(s)}^{T} \cdot \mathbf{\mathbf{w}}) \cdot (\phi(s) - \gamma \cdot \phi(s^{\prime}))}
\end{aligned}
$$

This algorithm is called *Naive Residual Gradient*, due to Leemon Baird ([Baird 1995](#bib01.xhtml#refbib_6)). Naive Residual Gradient converges robustly, but again, not to a desirable place. So researchers had to look even further.

This brings us to the fourth (and final) Value Function vector of interest in the **Φ** subspace. We denote this Value Function vector as *w*[*P**B**E*]. The acronym *PBE* stands for *Projected Bellman Error*. To understand this, first consider the composition of the Projection Operator **Π**[**Φ**] and the Bellman Policy Operator **B**^(*π*), i.e., **Π**[**Φ**] ⋅ **B**^(*π*) (we call this composed operator as the *Projected Bellman* operator). Visualize the application of this *Projected Bellman* operator on a Value Function vector **V**[**w**] in the **Φ** subspace. Applying **B**^(*π*) on **V**[**w**] typically throws **V**[**w**] out of the **Φ** subspace and then further applying **Π**[**Φ**] brings it back to the **Φ** subspace (call this resultant Value Function vector **V**[**w**^′]). The idea is to find a Value Function vector **V**[**w**] in the **Φ** subspace for which the “distance” between **V**[**w**] and **V**[**w**^′] is minimized, i.e. we minimize the “error vector” *P**B**E* = **Π**[**Φ**] ⋅ **B**^(*π*) ⋅ **V**[**w**] − **V**[**w**] ([Figure 13.6](#chapter13.xhtml#fig13_6) provides the visualization). Hence, we say we are minimizing the *Projected Bellman Error* (or simply that we are minimizing *PBE*), and we refer to *w*[*P**B**E*] as the Value Function vector in the **Φ** subspace for which *PBE* is minimized. It turns out that the minimum of PBE is actually zero, i.e., **Φ** ⋅ **w**[*P**B**E*] is a fixed point of operator **Π**[**Φ**] ⋅ **B**^(*π*). Let us write out this statement formally. We know:

$$
\begin{array}{r}
{\mathbf{\mathbf{\Pi}}_{\mathbf{\mathbf{\Phi}}} = \mathbf{\mathbf{\Phi}} \cdot {(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}})}^{- 1} \cdot \mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}}}
\end{array}
$$

$$
\begin{array}{r}
{\mathbf{\mathbf{B}}^{\pi} \cdot \mathbf{\mathbf{V}} = \mathcal{R}^{\pi} + \gamma\mathcal{P}^{\pi} \cdot \mathbf{\mathbf{V}}}
\end{array}
$$

Therefore, the statement that **Φ** ⋅ **w**[*P**B**E*] is a fixed point of operator **Π**[**Φ**] ⋅ **B**^(*π*) can be written as follows:

$$
\begin{array}{r}
{\mathbf{\mathbf{\Phi}} \cdot {(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}})}^{- 1} \cdot \mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot (\mathcal{R}^{\pi} + \gamma\mathcal{P}^{\pi} \cdot \mathbf{\mathbf{\Phi}} \cdot \mathbf{\mathbf{w}}_{PBE}) = \mathbf{\mathbf{\Phi}} \cdot \mathbf{\mathbf{w}}_{PBE}}
\end{array}
$$

Since the columns of **Φ** are assumed to be independent (full rank),

$$
\begin{aligned}
{{(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}})}^{- 1} \cdot \mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot (\mathcal{R}^{\pi} + \gamma\mathcal{P}^{\pi} \cdot \mathbf{\mathbf{\Phi}} \cdot \mathbf{\mathbf{w}}_{PBE})} & {= \mathbf{\mathbf{w}}_{PBE}i} \\
{\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot (\mathcal{R}^{\pi} + \gamma\mathcal{P}^{\pi} \cdot \mathbf{\mathbf{\Phi}} \cdot \mathbf{\mathbf{w}}_{PBE})} & {= \mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathbf{\mathbf{\Phi}} \cdot \mathbf{\mathbf{w}}_{PBE}} \\
{\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot (\mathbf{\mathbf{\Phi}} - \gamma\mathcal{P}^{\pi} \cdot \mathbf{\mathbf{\Phi}}) \cdot \mathbf{\mathbf{w}}_{PBE}} & {= \mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathcal{R}^{\pi}}
\end{aligned}
$$

(13.4)

This is a square linear system of the form **A** ⋅ **w**[*P**B**E*] = **b** whose solution is:

$$
\begin{array}{r}
{\mathbf{\mathbf{w}}_{PBE} = \mathbf{\mathbf{A}}^{- 1} \cdot \mathbf{\mathbf{b}} = {(\mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot (\mathbf{\mathbf{\Phi}} - \gamma\mathcal{P}^{\pi} \cdot \mathbf{\mathbf{\Phi}}))}^{- 1} \cdot \mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathcal{R}^{\pi}}
\end{array}
$$

The above formulation can be used to compute **w**[*P**B**E*] if we know the model probabilities 𝒫^(*π*) and reward function ℛ^(*π*). But often, in practice, we don't know 𝒫^(*π*) and ℛ^(*π*), in which case we seek model-free learning of **w**[*P**B**E*], specifically with a TD (bootstrapped) algorithm.

The question is how do we construct matrix

$$
\begin{array}{r}
{\mathbf{\mathbf{A}} = \mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot (\mathbf{\mathbf{\Phi}} - \gamma\mathcal{P}^{\pi} \cdot \mathbf{\mathbf{\Phi}})}
\end{array}
$$

and vector

$$
\begin{array}{r}
{\mathbf{\mathbf{b}} = \mathbf{\mathbf{\Phi}}^{T} \cdot \mathbf{\mathbf{D}} \cdot \mathcal{R}^{\pi}}
\end{array}
$$

without a model?
