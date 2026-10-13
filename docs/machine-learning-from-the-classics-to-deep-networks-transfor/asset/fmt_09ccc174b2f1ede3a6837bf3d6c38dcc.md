
$$
p(x) = \frac{\int_{-\infty}^{+\infty}\chi_{[0,\phi(x)]}(u)\ du}{\int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty}\chi_{[0,\phi(x)]}(u)\ du\ dx}.
$$

![Equation](images/B9780443292385000202/si109.png) (14.24)

In other words, even if $p(x)$ is not exactly known, $p(x)$ can still be obtained, this time in terms of the uniform distribution, $\chi_{[0,\phi(x)]}(x, u)$, normalized appropriately. However, rescaling the uniform does not affect the marginal. It suffices to sample uniformly at random the region $\mathcal{A}$, which now should be defined in terms of $\phi(x)$ instead of $p(x)$. What we have said so far applies also to random vectors, $\mathbf{x} \in \mathbb{R}^{(l)}$, by considering the extended space $(\mathbf{x}, u)$, and we talk about the volume under the surface $\phi(\mathbf{x})$ (or $p(\mathbf{x})$).

![Figure 14.5 (A) Filling in the shaded area uniformly at random with points (xn,un), after neglecting the coordinate un, is equivalent to drawing points xn from p(x). (B) The proposal distribution, cq(x), is everywhere larger than or equal to ϕ(x).](images/B9780443292385000202/gr005.jpg)

**Figure 14.5** (A) Filling in the shaded area uniformly at random with points $(x_n, u_n)$, after neglecting the coordinate $u_n$, is equivalent to drawing points $x_n$ from $p(x)$. (B) The proposal distribution, $c q(x)$, is everywhere larger than or equal to $\phi(x)$.

We now turn our attention to see how one can fill in the volume under the surface formed by $u = \phi(\mathbf{x})$ (or $u = p(\mathbf{x})$ if it is fully available), with points uniformly at random. Let $q(\mathbf{x})$ be a distribution from which we know how to draw samples; we refer to it as the *proposal distribution*. We select a constant $c$ such that^[^107]

$$
\phi(\mathbf{x}) \le c q(\mathbf{x}),\ \forall \mathbf{x} \in \mathbb{R}^{(l)}.
$$

![Equation](images/B9780443292385000202/si117.png)
