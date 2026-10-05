# APPENDIX: PROBING HIDDEN HIERARCHIES IN DATA

# D.1 THE RANDOM HIERARCHY MODEL

# D.1.1 Denoising the RHM with Belief Propagation

In the RHM, knowing the production rules of its tree structure, the Bayes-optimal denoising of its data can be done exactly using the Belief Propagation (BP) algorithm [SFW25].

In the factor graph of the RHM, all latent and visible variables $h_i^{(f)}$ represent variable nodes, while the RHM rules connecting them are factor nodes. Each variable node is associated to two BP messages, $v_f(h_i^{(f)})$, and one coming from below, $v_\ell(h_i^{(f)})$. The starting point of the BP algorithm is the definition of the messages below the tree, with the upward messages at the leaves $v_\ell(h_i^{(0)})$ and the downward message at the root $v_f(h_i^{(L)})$. Since we consider class-unconditional diffusion processes, we consider the latter as being uniform over the values of $y^{(\ell)}$. The initialization at the leaves, instead, corresponds to the prior belief on the values of the single tokens, which is given by the noisy observation. The noisy observation $x$ gives prior beliefs $v_\Upsilon(h_i^{(0)}) = p(y_0|x_{ij})$, which can be computed for the single token by Bayes' rule and depends on the specific diffusion process under consideration.

# D.1.1.1 BP iteration

The initialization of BP is given by the leaf messages $v_\Upsilon(h_i^{(0)}), i \in [s^L]$. For each s-patch level $\ell$, e.g., $\{h_i^{(\ell)}\}_{i=1,\dots,s}$ having a common parent node at level $\ell+1$, e.g., $h_{(\ell+1)}$, the upward message in the upper level is computed as

```
$$\hat{v}_\Upsilon\left(h_1^{(\ell+1)}\right) = \sum_{a_1,\dots,a_s\in\mathcal{V}(v^{(\ell)})} \psi^{(\ell+1)}(y,a_1,\dots,a_s)\prod_{i=1}^s v_\Upsilon\left(h_i^{(\ell)}=a_i\right), \quad (333)$
```

```
$v_\Upsilon\left(h_1^{(\ell+1)}\right) = \frac{\hat{v}_\Upsilon\left(h_1^{(\ell+1)}\right)}{\sum_{y'\in\mathcal{V}(\hat{v}_\Upsilon^{(\ell)})})} \hat{v}_\Upsilon\left(h_1^{(\ell+1)}=y'\right)}, \quad (334)$
```