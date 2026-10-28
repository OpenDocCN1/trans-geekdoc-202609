![](bbox=[0.346, 0.149, 0.714, 0.218])

**Figure 3.6** A convex body $K$ (left) is transformed into an isotropic convex body $T(K)$ (right). The preconditioner is $T=\Sigma^{-1/2}$, where $\Sigma$ is the covariance matrix of $K$.

# 3.3.5 Frames

The notion of a frame, widely used in signal processing, extends the concept of a basis but drops the requirement of linear independence. Frames are intimately connected to discrete isotropic distributions:

+   **Proposition 3.3.11** (Parseval frames). *For any vectors* $u_1,\ldots,u_N\in\mathbb{R}^n$, *the following are equivalent:*
+   
+   (i) (Parseval identity) $\|x\|^2=\sum_{i=1}^N\langle u_i,x\rangle^2$ for each $x\in\mathbb{R}^n$.
+   
+   (ii) (Frame expansion) $x=\sum_{i=1}^N\langle u_i,x\rangle u_i$ for each $x\in\mathbb{R}^n$.
+   
+   (iii) (Decomposition of identity) $I_n=\sum_{i=1}^N u_i u_i^\mathsf{T}$.
+   
+   (iv) (Isotropy) The random vector $X\sim\operatorname{Unif}\{\sqrt{N}u_1,\ldots,\sqrt{N}u_N\}$ is isotropic.
+   
+   A set of vectors satisfying these equivalent properties is called a Parseval frame.

*Proof* **(i)$\Rightarrow$(iv)** The identity in (i) can be written as

$$\|x\|^2=\frac{1}{N}\sum_{i=1}^N\langle\sqrt{N}u_i,x\rangle^2=\mathbb{E}\langle X,x\rangle^2.$$

Since this holds for all $x\in\mathbb{R}^n$, the random vector $X$ is isotropic by (3.9).

**(iv)$\Rightarrow$(iii)** because isotropy of $X$ means that

$$I_n=\mathbb{E}XX^\mathsf{T}=\frac{1}{N}\sum_{i=1}^N(\sqrt{N}u_i)(\sqrt{N}u_i)^\mathsf{T}=\sum_{i=1}^N u_i u_i^\mathsf{T}.$$

**(iii)$\Rightarrow$(ii)** follows by multiplying on both sides by $x$. Finally, **(ii)$\Rightarrow$(i)** comes from taking the inner product with $x$.

**Example 3.3.12** (Coordinate distribution). The standard basis $\{e_1,\ldots,e_n\}$ in $\mathbb{R}^n$ is a Parseval frame. Therefore, a *coordinate random vector*

$$X\sim\operatorname{Unif}\{\sqrt{n}e_1,\ldots,\sqrt{n}e_n\},$$

is isotropic. Among all high-dimensional distributions, Gaussian is often the easiest to work with—think of it as “the best.” The coordinate distribution, being highly discrete, is often “the worst.”

**Example 3.3.13** (The Mercedes-Benz frame). An iconic example of a Parseval frame that is not linearly independent is the set of $N$ equispaced points on the circle of radius $\sqrt{2/N}$, such as the one in Figure 3.7 (try Exercise 3.30).