# G.2 Spectral analysis of linearized models 265

This condition can be rewritten as

```
$D_{\rho} \left(\sum_{t\in\mathcal{T}} \sum_{ho\in\mathcal{N}} c_{t,\rho} \phi_{ho}(x)\right)^2 dx = 0. \quad (424)$
```

If, for each $t$, the eigen own corresponding to non-zero coefficients are supported within a subset of $D_t$ and all domains $D_t$ are disjoint, then all the sums inside the integral in Equation 424 become zero inside $D_{ho}$, and thus the proof is complete.

As discussed in Section 8.5.1, eigenfunction localization is generally not a necessary condition to achieve task arithmetic. However, we now show that if the eigenfunctions are linearly independent across the different tasks, then the localization property becomes a necessary condition for task arithmetic. The proposition presented before formalizes this concept.

+   **Proposition 7.** Suppose that the task functions $\{f_t\}_{t\in\mathcal{T}}$ belong to the RKHS of the kernel $k$ and their coefficients in the kernel eigenbasis $\{c_{t,\rho}\\}_{rho\in\mathcal{N}}$. Furthermore, let the kernel eigenfunctions be either zero or linearly independent over each domain $D_t$. The kernel $k$ has the task arithmetic property with respect to $\{f_t\}_{t\in\mathcal{T}}$ and $\{D_t\}_{t\in\mathcal{T}}$ if and only if $\forall t, \rho$, $c_{t,\rho}=0$ or $\text{supp}(c_{t,\rho}) \subseteq D_t$.

The initial steps of the proofs follow those of integral in Equation 424. Due to the linear independence of the non-zero kernel eigenfunctions on $D_t$, for this integral to be zero, we have two possibilities:
i) all coefficients $\{c_{t,\rho}\}_{t\in\mathcal{T},\rho\in\mathcal{N}}$ must be zero or ii) the eigenfunctions corresponding to non-zero coefficient $c_{t',\rho}$ ($t \neq t'$) must be zero in $D_t$. Since the proposition is valid for any set of functions, condition (ii) must not hold. Furthermore, since Equation 424 is valid $\forall t' \in [ \mathcal{T} ]$, it follows that $D_{\rho} = \cup_{t\in\mathcal{T}, t\neq t'} D_t$ are zero. Consequently, these eigenfunctions are only supported in $D_t$ or a subset thereof.

In order to understand the implications of this proposition, it is useful to examine simple data geometries and architectures for which the NTK can be analytically diagonal. For instance, when data is uniformly distributed on a ring or a torus, the NTK of fully-connected and convolutional neural networks at initialization can be diagonalized with the Fourier series [Non-19; CFW23; FCW21]. Fourier atoms are linearly independent over any interval [Cc6] and not localized. Consequently, according to Proposition 7, these architectures cannot perform task arithmetic within such settings. straightforward calculation aligns with the observation that task arithmetic emerges as a property of pre-training and is not inherently present at initialization, as we numerically demonstrated for CLIP models in Section 8.5.2.