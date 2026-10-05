where the factor $\psi^{(\ell+1)}(y, a_1, \dots, a_s)$ reads

```
$$\psi^{(\ell+1)}(y, a_1, \dots, a_s) = \begin{cases} 1 & \text{if } y \to (a_1, \dots, a_s) \text{ is a rule at layer } (\ell+1) \to \ell \ 0, & \text{otherwise.} \end{cases}$$
```

(335)

This upward process is iterated from the leaf nodes at $\ell = 0$ until the root node at $\ell = L$. Afterward, BP computes the downward messages. The initialization at the root node is given by a uniform prior over the symbols of $\mathcal{V}^{(L)}$, i.e.

```
$v_l^{(L)}(h_l^{(L)}) = \frac{1}{\sqrt{\mathcal{V}^{(L)}}} a \in \mathcal{V}^{(L)}.$
```

(336)

For the same-patch at layer $\ell$ and parent node at layer $\ell+1$ as before, the downward message for $h_i^{(\ell)}$ is given

```
$$\hat{v}_i^{(\ell)}(h_i^{(\ell)}) = a_1 = \sum_{a_2, \dots, a_s \in \mathcal{V}^{(\ell+1)}} \psi^{(\ell+1)}(y, a_1, \dots, a_s) v_y^{(\ell+1)}(h_i^{(\ell+1)})$
```

(337)

```
$\nu_i^{(\ell)}(h_i^{(\ell)}) = a = \frac{\sum_{a' \in \mathcal{V}^{(\ell)}} \hat{v}_i^{(\ell)}(h_i^{(\ell)})}{\hat{
u}_i^{(\ell)}(h_i^{(\ell)})}$
```

(338)

With the end of the upward-downward iteration, each variable $h_i^{(\ell)}$ is associated with two BP messages for each symbol of the vocabulary $\mathcal{V}^{(\ell)}; \nu_i^{(\ell)}$ and $v_i^{(\ell)}$. Their product gives the marginal probability of the value of the node:

```
$p(h_i^{(\ell)} = a) \propto v_i^{(\ell)}(h_i^{(\ell)}) \nu_i^{(\ell)}(h_i^{(\ell)}), a \in \mathcal{V}^{(\ell)}.$
```

(339)

These marginal probabilities are conditioned on the BP messages at the leaf nodes, which can come from a noisy observation of the RHM datum, as is the case for denoising diffusion.

Similarly, sampling from the posterior probabilities by BP is done by starting from the marginal at the root and then iteratively updating the marginal probabilities every time a new node is sampled [MMo9].

# D.1.1.2 Priors at the leaves

MASKING DIFFUSION Let's consider a token $x_0$ of the RHM undergoing masking diffusion. At any time $t_i$, the tokens of $x_i$ can have value

```
$x_{l,i} = x_{0,i},$ if token $i$ has not been masked;\n$x_{l,i} = [MASK],$ if token $i$ has already been masked.
```

(340)