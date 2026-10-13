
## Example 8.7: Projected Landweber Method

Let our optimization task be

$$
\text{minimize } \frac{1}{2}{\|\mathbf{y} - X\mathbf{\theta}\|}^{2}, \text{ subject to } \mathbf{\theta} \in C,
$$

where $X \in \mathbb{R}^{(m \times l)}$, $\mathbf{y} \in \mathbb{R}^{(m)}$. Expanding and taking the gradient, we get

$$
J(\mathbf{\theta}) = \frac{1}{2}\mathbf{\theta}^{T}X^{T}X\mathbf{\theta} - \mathbf{y}^{T}X\mathbf{\theta} + \frac{1}{2}\mathbf{y}^{T}\mathbf{y}, \quad \nabla J(\mathbf{\theta}) = X^{T}X\mathbf{\theta} - X^{T}\mathbf{y}.
$$

First we check that $\nabla J(\mathbf{\theta})$ is $\gamma$-Lipschitz. To this end, we have

$$
\|X^{T}X(\mathbf{\theta} - \mathbf{h})\| \leq \|X^{T}X\|\|\mathbf{\theta} - \mathbf{h}\| \leq \lambda_{\text{max}}\|\mathbf{\theta} - \mathbf{h}\|.
$$

If 

$$
\|\nabla J(\mathbf{\theta}) - \nabla J(\mathbf{h})\| \leq \gamma \|\mathbf{\theta} - \mathbf{h}\|, \quad \gamma > 0, \quad \forall \mathbf{\theta}, \mathbf{h} \in \mathbb{R}^{(l)},
$$

and 

$$
\mu \in \left( 0, \frac{2}{\gamma} \right),
$$

then starting from an arbitrary point $\mathbf{\theta}^{(0)}$, the sequence in Eq. [(8.62)](#Chp008_343-416_B9780443292385000147.xhtml#deq128) converges (weakly in a general Hilbert space) to a solution of [(8.50)](#Chp008_343-416_B9780443292385000147.xhtml#deq110) [41,52].
