
**Remark 7.5.10** (Surprising behavior of width in high dimensions). As we can see from Examples 7.5.6–7.5.8, the Gaussian width of the cube $B_\infty^n$ is roughly (up to a constant factor) the same as that of its *circumscribed* ball $\sqrt{n}B_2^n$. But for the cross-polytope $B_1^n$, the width is roughly (up to a log factor) like that of its *inscribed* ball $\frac{1}{\sqrt{n}}B_2^n$, which is tiny! Why?

The cube $B_\infty^n$ has so many vertices ($2^n$) that in most directions it sticks out to roughly the circumscribed ball, which drives the width. But the cross-polytope $B_1^n$ only has $2n$ vertices, so a random direction $g\sim N(0,I_n)$ likely to be far from all of them. The width is not driven by those lonely $2n$ “spikes” — it’s driven by the “bulk”, which is roughly the inscribed ball.

Figure 7.4a shows Milman’s *hyperbolic sketch* of $B_1^n$, highlighting how the bulk (the inscribed ball) dominates since the set has few vertices (spikes). You can make similar sketches for general convex sets, too (Figure 7.4b) — they are great for building high-dimensional intuition, even if you lose convexity in the picture.

For more practice, try Exercise 7.17 to compute the Gaussian width of any $\ell^p$ ball, covering all three examples above at once — the ball ($p=2$), the cube ($p=\infty$), and the cross-polytope ($p=1$). Also work through Exercises 7.18–7.19 to compute the Gaussian width of the set of $n\times n$ matrices with operator norm at most 1.

![](img/b122213aed28c1888de83a894123323e_217_0.png)

### 7.5.3 Gaussian complexity and effective dimension

There are a couple of helpful cousins of the Gaussian width $w(T)$. Normally, we would take the expected max of $\langle g,t\rangle$, but sometimes it’s easier to work with $L^1$ or $L^2$ averages:

$$w(T)=\mathbb{E}\sup_{x\in T}\langle g,x\rangle,\qquad \gamma(T):=\mathbb{E}\sup_{x\in T}|\langle g,x\rangle|,\qquad h(T):=\left(\mathbb{E}\sup_{x\in T}\langle g,x\rangle^2\right)^{1/2},$$

where $g\sim N(0,I_n)$. We call $\gamma(T)$ the *Gaussian complexity* of $T$. Clearly,

$$w(T)\leq\gamma(T)\leq h(T),$$

and the reverse bounds are basically true too:

**Lemma 7.5.11** (Almost equivalent versions of Gaussian width). *For any bounded set $T \subset \mathbb{R}^n$, we have.*⁸

- (a) $\gamma(T - T) = 2w(T)$.
- (b) $h(T) \asymp \gamma(T) \asymp w(T) + \|y\|_2$ for any point $y \in T$.

*In particular, if $T$ contains the origin, all three versions are equivalent.*

$h(T) \asymp \gamma(T) \asymp w(T)$.

*Proof* (a) follows from Proposition 7.5.2(e), since $T - T$ is origin-symmetric.
(b) Let’s just prove the first part and leave the equivalence $\gamma(T) \asymp w(T) + \|y\|_2$ for you to prove in Exercise 7.20. We trivially have $\gamma(T) \le h(T)$. For the reverse, look at the function $z \mapsto \sup_{x\in T} |\langle z, x\rangle|$ on $\mathbb{R}^n$. Its Lipschitz norm is bounded by the radius $\sup_{x\in T} \|x\|_2 = r(T)$ (check!). Then, by Gaussian concentration (5.5),

$\big\|\sup_{x\in T} |\langle g, x\rangle| - \gamma(T)\big\|_{\psi_2} \lesssim r(T)$.

So, by triangle inequality and Proposition 2.6.6(ii), we get

$h(T) = \big\|\sup_{x\in T} |\langle g, x\rangle|\big\|_{L^2} \lesssim \big\|\sup_{x\in T} |\langle g, x\rangle|\big\|_{\psi_2} \lesssim \gamma(T) + r(T) \lesssim \gamma(T)$.

The last step used the fact that $\gamma(T) \gtrsim r(T)$, which comes from the second part of (b) – just take the supremum over $y \in T$.

The Gaussian width helps us define a robust version of the notion of dimension. The usual linear-algebraic dimension of a set $T \subset \mathbb{R}^n$, which is the dimension of the smallest affine space containing it, can change a lot with tiny perturbations of $T$. Here is a more robust alternative:

**Definition 7.5.12** (Effective dimension). The *effective dimension* of a bounded set $T \subset \mathbb{R}^n$ is

$d(T) := \frac{h(T - T)^2}{\operatorname{diam}(T)^2} \asymp \frac{w(T)^2}{\operatorname{diam}(T)^2}$.

The equivalence follows from Lemma 7.5.11. The effective dimension is bounded by the linear-algebraic one:

$d(T) \le \dim(T)$,
with equality when $T$ is a Euclidean ball in some subspace (see Exercise 7.21). Unlike the usual dimension, the effective one is stable – small perturbations to $T$ only slightly change its width and diameter.

To get some practice with effective dimension, compute it for ellipsoids (Exercise 7.23) and bound it for general finite sets (Exercise 7.22).

⁸ Here, as usual, the notation $\asymp$ hides positive absolute constant factors.

## 7.6 Application: random projections of sets

What happens if we project a set \(T \subset \mathbb{R}^n\) onto a random \(m\)-dimensional subspace in \(\mathbb{R}^n\) (picked uniformly from the Grassmannian \(G_{n,m}\)), like in Figure 5.2? In practice, we might see \(T\) as data and \(P\) as a way of dimension reduction, like in Johnson-Lindenstrauss lemma. What can we say about the size (diameter) of the projected set \(PT\)?

For a finite set \(T\), the Johnson-Lindenstrauss Lemma (Theorem 5.3.1) says that if \(m \gtrsim \log |T|\), the random projection \(P\) acts essentially as a scaling of \(T\): it shrinks all distances between points in \(T\) by a factor \(\approx \sqrt{m/n}\). In particular,

\[\operatorname{diam}(PT) \approx \sqrt{\frac{m}{n}}\,\operatorname{diam}(T). \tag{7.20}\]

But if the cardinality of \(T\) is too large or infinite, (7.20) may fail. For instance, if \(T = B_2^n\) is a Euclidean ball, no projection can shrink its size:

\[\operatorname{diam}(PT) = \operatorname{diam}(T). \tag{7.21}\]

What about general sets \(T\)? The next result states that a random projection shrinks \(T\) as in (7.20), but it cannot shrink it beyond the spherical width \(w_s(T)\):

**Theorem 7.6.1 (Sizes of random projections of sets).** Let \(T \subset \mathbb{R}^n\) be a bounded set, and \(P\) be the orthogonal projection in \(\mathbb{R}^n\) onto a random \(m\)-dimensional subspace \(E \sim \operatorname{Unif}(G_{n,m})\). Then

\[\mathbb{E}\,\operatorname{diam}(PT) \lesssim w_s(T) + \sqrt{\frac{m}{n}}\,\operatorname{diam}(T),\]

where the notation \(\lesssim\) hides positive absolute constant factors.

*Proof*  Let’s prove the upper bound and leave the lower bound to you (see Exercise 7.26).

**Step 1: Change the model.** Let’s switch the view just like in the proof of Proposition 5.3.2. A random subspace \(E \subset \mathbb{R}^n\) can be obtained by randomly rotating some fixed subspace, such as \(\mathbb{R}^m\). But instead of fixing \(T\) and randomly rotating \(\mathbb{R}^m\), we can fix \(E = \mathbb{R}^m\) and randomly rotate \(T\). A random rotation of a vector \(x \in T\) is \(Ux\) where \(U \sim \operatorname{Unif}(O(n))\) is a random orthogonal matrix. Projecting \(Ux\) onto \(E = \mathbb{R}^m\) means keeping the first \(m\) coordinates, i.e. \(Qx\) where \(Q\) is the \(m \times n\) matrix consisting of the first \(m\) columns of \(U\). So, we can work with \(Q\) instead of \(P\).

**Step 2: Approximation.** Without loss of generality, \(\operatorname{diam}(T) \le 1\). (Why?) We need to bound

\[\operatorname{diam}(QT) = \sup_{x\in T-T}\|Qx\|_2 = \sup_{x\in T-T}\max_{z\in S^{m-1}}\langle Qx,z\rangle.\]

We will proceed with an \(\varepsilon\)-net argument as in the proof of Theorem 4.4.3. Choose an \((1/2)\)-net \(\mathcal{N}\) of the sphere \(S^{m-1}\) so that

\[|\mathcal{N}| \le 5^m\]

using Corollary 4.2.11. We can replace the supremum over the sphere $S^{m-1}$ by the supremum over the net $\mathcal{N}$ paying a factor 2:

$$\operatorname{diam}(QT) \le 2\sup_{x\in T-T}\max_{z\in\mathcal{N}}\langle Qx,z\rangle = 2\max_{z\in\mathcal{N}}\sup_{x\in T-T}\langle Q^{\mathsf T}z,x\rangle. \tag{7.22}$$

(see Exercise 4.35). Now, here is the plan: we will first bound

$$\sup_{x\in T-T}\langle Q^{\mathsf T}z,x\rangle \tag{7.23}$$

for a fixed $z\in\mathcal{N}$, and then take union bound over all $z$.

**Step 3: Concentration.** So, let’s fix $z\in\mathcal{N}$. By construction, $Q^{\mathsf T}z$ is uniformly distributed on the sphere: $Q^{\mathsf T}z\sim\operatorname{Unif}(S^{n-1})$ (check this carefully in Exercise 7.24). The expectation of (7.23) can be expressed as the spherical width:

$$\mathbb{E}\sup_{x\in T-T}\langle Q^{\mathsf T}z,x\rangle=w_s(T-T)=2w_s(T).$$

(The last equality is just a spherical version of Proposition 7.5.2(e).)
To check that (7.23) concentrates around its mean, we use the concentration inequality on the sphere (Theorem 5.1.3, or more specifically (5.30)). Since $\operatorname{diam}(T)\le 1$ by assumption, the function $z\mapsto\sup_{x\in T-T}\langle z,x\rangle$ on the sphere has Lipschitz norm at most 1 (check!). So (5.30) gives

$$\mathbb{P}\left\{\sup_{x\in T-T}\langle Q^{\mathsf T}z,x\rangle\ge 2w_s(T)+t\right\}\le 2\exp(-cnt^2).$$

**Step 4: Union bound.** Now we unfix $z\in\mathcal{N}$ by taking the union bound:

$$\mathbb{P}\left\{\max_{z\in\mathcal{N}}\sup_{x\in T-T}\langle Q^{\mathsf T}z,x\rangle\ge 2w_s(T)+t\right\}\le |\mathcal{N}|\cdot 2\exp(-cnt^2). \tag{7.24}$$

Recall that $|\mathcal{N}|\le 5^m$. Choosing $t=C_s\sqrt{m/n}$ with constant $C$ large enough, the probability in (7.24) is bounded by $2e^{-ms^2}$ for any $s\ge 1$. So, (7.24) and (7.22) give the result:

$$\mathbb{P}\left\{\frac12\operatorname{diam}(QT)\ge 2w_s(T)+C_s\sqrt{\frac mn}\right\}\le e^{-ms^2}\quad\text{for any }s\ge 1.$$

From this, one can bound the expected value of $\operatorname{diam}(QT)$ using the integrated tail formula (Lemma 1.6.1) – do this!

**Remark 7.6.2 (Phase transition).** Let’s get more insight from Theorem 7.6.1. Since the sum of two terms is equivalent to maximum (up to factor 2), we can write:

$$\operatorname{diam}(PT)\asymp\max\left[w_s(T),\sqrt{\frac mn}\operatorname{diam}(T)\right].$$

Let’s find the “phase transition” point where these two terms are equal. Set them equal and solve for $m$:

$$m=\frac{(\sqrt{n}\,w_s(T))^2}{\operatorname{diam}(T)^2}\asymp\frac{w(T)^2}{\operatorname{diam}(T)^2}\asymp d(T),$$
