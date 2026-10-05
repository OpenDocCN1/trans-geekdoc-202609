# APPENDIX: THE ROLE OF DEPTH AND SPATIAL ADAPTIVITY

therefore

```
$K_{RFK}^{(2+1)}\(\{1-u_{i_2,i_3}\}_{{i_2,i_3}}\right) = 1-\frac{1}{s_2p_2}\sum_{i_2,i_3}u_{i_2,i_3}-\frac{c}{p_2}\sum_{i_3}\frac{c}{s_2}\sum_{i_3}u_{i_2,i_3}+\mathcal{O}(u^{5/2}_{i_2,i_3})\n\n(213)$
```

The proof of the general case follows by induction by applying the function $\kappa_1$ to the singular expansion of the kernel with $L-1$ hidden layers, then using Equation 208.

**Proposition 3** (RFK when $\mathbf{x}=-\mathbf{y}$). The RFK of a hierarchical network of depth $L+1$, filters $(s_1, \dots, s_L)$ and $p_1 \geq 1$ has the following singular expansion when all $l_{i_2-L+1} \to -1$. If $u_{i_2-L+1}=1, c=2\sqrt{2}/(3\pi)$ and $\prod_{i_1}s_1=1$ is the empty set,

```
$K_{RFK}^{(L+1)}\(\{{1-u_{i_2-L+1}\}_{{i_2-L+1}}\right) = b_L+\frac{c_L}{\left(\prod_{2\leq i_2\leq L-1}s_{i_2}\right)}p_L\sum_{i_2\leq L-1}u^{3/2}_{i_2-L+1}+\mathcal{O}(u^{5/2}_{i_2-L+1}),\n\n(214)$
```

with $b_L=\kappa_1(b_{L-1}), b_1=0$; and $c_L=c_{L-1}-\kappa_1(b_{L-1}), c_1=c_1$.

*Proof.* This can be proved by induction. For $L=1$,

```
$K_{RFK}^{(1+1)}\(\{-1+u_{i_2}\right)=cu^{3/2}_{i_2}+\mathcal{O}(u^{5/2}_{i_2})\Rightarrow\nK_{RFK}^{(1+1)}\(\{-1+u_{i_2}\}\right)=\frac{c}{p_1}\sum_{i_2}u^{3/2}_{i_2}+\mathcal{O}(u^{5/2}_{i_2}),\n\n(215)$
```

Thus, for $L=2$,

```
$K_{RFK}^{(2)}\(\{-1+u_{i_2,i_3}\}_{{i_2,i_3}}\right)=\kappa_1\frac{c}{s_2}\sum_{i_2}u^{3/2}_{i_2,i_3},\n\n=\kappa_1(0)+\kappa_1'(0)\left(\frac{c}{s_2}\sum_{i_2}u^{3/2}_{i_2,i_3}\right)+\mathcal{O}(u^{5/2}_{i_2,i_3}),\n\n(216)$
```

so that

```
$K_{RFK}^{(2+1)}\(\{-1+u_{i_2,i_3}\}_{{i_2,i_3}}\right)=\kappa_1(0)+\frac{\kappa_1'(0)}{s_2p_2}\sum_{i_2,i_3}u^{3/2}_{i_2,i_3}+\mathcal{O}(u^{5/2}_{i_2,i_3}),\n\n(217)$
```

The proof is completed by applying the function $\kappa_1$ to the expansion of the kernel with $L-1$ hidden layers.