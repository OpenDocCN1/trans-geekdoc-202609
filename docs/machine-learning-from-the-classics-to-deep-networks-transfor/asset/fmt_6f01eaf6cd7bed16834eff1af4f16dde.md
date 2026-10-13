
Assuming $l = 2$ (**x** = [$x_1$, $x_2$]^T), Eq. [(11.2)](#Chp011_519-582_B9780443292385000172.xhtml#deq2) can be brought into the form of Eq. [(11.1)](#Chp011_519-582_B9780443292385000172.xhtml#deq1) by setting $K = 5$ and $\phi_1(\mathbf{x}) = x_1$, $\phi_2(\mathbf{x}) = x_2$, $\phi_3(\mathbf{x}) = x_1 x_2$, $\phi_4(\mathbf{x}) = x_1^2$, $\phi_5(\mathbf{x}) = x_2^2$.

The generalization of Eq. [(11.2)](#Chp011_519-582_B9780443292385000172.xhtml#deq2) to $r$th-order polynomials is readily obtained and it will contain products of the form $x_1^{p_1} x_2^{p_2} \cdots x_l^{p_l}$, with $p_1 + p_2 + \cdots + p_l \le r$. It turns out that the number of free parameters, $K$, for an $r$th-order polynomial is equal to

```
K = \frac{(l + r)!}{r! l!}.
```

Just to get a feeling for $l = 10$ and $r = 3$, $K = 286$. The use of polynomial expansions is justified by the Weierstrass theorem, stating that every continuous function defined on a compact (closed and bounded) subset $S \subset \mathbb{R}^l$ can be uniformly approximated as closely as desired, with an arbitrarily small error, $\epsilon$, by a polynomial function (for example, [95]). Of course, in order to achieve a good enough approximation, one may have to use a large value of $r$. Besides polynomial functions, other types of functions can also be used, such as splines and trigonometric functions.
