# ### 11.2 Function Approximation

It is known that neural networks are universal function approximators. In fact, it is known that a two-layer neural network (11.1) is universal if $h(\cdot)$ is not a polynomial (Leshno et al., 1993).

**Theorem 11.1** (Leshno et al., 1993)  If $h$ is a *nonpolynomial continuous function*, then the function class in (11.1) is dense in $C^0(K)$ for all compact subsets $K$ of $\mathbb{R}^d$, where $C^0(K)$ denotes the set of continuous functions on $K$.

A more refined result was obtained in Barron (1993), which considered functions with a certain smoothness property in Fourier representation.

**Definition 11.2**  Consider a real-valued function $f(x): \mathbb{R}^d \to \mathbb{R}$. Assume that $f \in L_1(\mathbb{R}^d)$ has the following Fourier representation:

$$f(x)=\int_{\mathbb{R}^d} e^{i\omega^T x}\,\tilde f(\omega)\,d\omega,$$

where $\tilde f(\omega)$ is the Fourier transform of $f(x)$ that may be a complex function. Define

$$C(f)=\int_{\mathbb{R}^d}\|\omega\|_2\,|\tilde f(\omega)|\,d\omega.$$

**Theorem 11.3** (Barron, 1993)  If $h(z)$ is a *bounded measurable function* on the real line for which $\lim_{z\to-\infty}h(z)=0$ and $\lim_{z\to\infty}h(z)=1$. Consider $B_r=\{x\in\mathbb{R}^d:\|x\|_2\le r\}$, and let $f$ be a real-valued function defined on $B_r$ such that $C(f)<\infty$. Then there exists a neural network (11.1) such that

$$\int (f(x)-f(0)-f_m(w,x))^2\,d\mu(x)\le \frac{(2rC(f))^2}{m},$$

where $\mu$ is an arbitrary probability measure on $B_r$.

**Proof**  A key property of the complexity measure $C(f)$, shown in Barron (1993), is that $f(x)-f(0)$ belongs to the convex closure of functions

$$\{u h(\theta^T x+b): |u|\le 2rC(f)\},$$

where the closure is taken with respect to $\mu$. This result, together with Theorem 10.7, implies Theorem 11.3.

Note that we can take any $b$ so that $h(b)\ne 0$, and

$$f(0)=\bigl(f(0)/h(b)\bigr)h(0^T x+b).$$

It follows that if $f(x)-f(0)$ can be represented by a two-layer neural network (11.1) with $m$ neurons, then $f(x)$ can be represented by a two-layer neural network (11.1) with $m+1$ neurons. Therefore Theorem 11.3 implies that any $f$ with finite $C(f)$ can be approximated by a two-layer neural network. It can be shown that the function class $\{f:C(f)<\infty\}$ is dense on any compact set of $\mathbb{R}^d$. This implies the desired universal approximation result.