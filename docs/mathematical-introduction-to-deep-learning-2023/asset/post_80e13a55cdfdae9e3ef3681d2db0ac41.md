
```python
6    BM = np.cumsum(increments)
7    BM = np.insert(BM, 0, 0)
8    return BM
9
10   T = 1
11   N = 1000
12   t_values = np.linspace(0, T, N+1)
13
14   fig, axarr = plt.subplots(2, 2)
15
16   for i in range(2):
17       for j in range(2):
18           BM = generate_brownian_motion(T, N)
19           axarr[i, j].plot(t_values, BM)
20
21   plt.tight_layout()
22   plt.savefig('../plots/brownian_motions.pdf')
23   plt.show()
```

Source code 17.1 (`code/brownian_motion.py`): Python code producing four trajectories of a 1-dimensional standard Brownian motion.

# Corollary 17.3.4.

Let $T \in (0, \infty)$, $d, m \in \mathbb{N}$, $B \in \mathbb{R}^{d \times m}$, $\varphi \in C^{2}(\mathbb{R}^{d}, \mathbb{R})$ satisfy
$$
\sup_{x \in \mathbb{R}^{d}}\left[\sum_{i, j=1}^{d}\left(|\varphi(x)|+\left|\left(\frac{\partial}{\partial x_{i}}\varphi\right)(x)\right|+\left|\left(\frac{\partial^{2}}{\partial x_{i} \partial x_{j}}\varphi\right)(x)\right|\right)\right]<\infty,
$$
let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $W: [0, T] \times \Omega \rightarrow \mathbb{R}^{m}$ be a standard Brownian motion, and let $u: [0, T] \times \mathbb{R}^{d} \rightarrow \mathbb{R}$ satisfy for all $t \in [0, T]$, $x \in \mathbb{R}^{d}$ that
$$
u(t, x)=\mathbb{E}\left[\varphi\left(x+B W_{t}\right)\right]
$$
(cf. Definition 17.3.3). Then
- (i) it holds that $u \in C^{1,2}([0, T] \times \mathbb{R}^{d}, \mathbb{R})$ and
- (ii) it holds for all $t \in [0, T]$, $x \in \mathbb{R}^{d}$ that
$$
\left(\frac{\partial u}{\partial t}\right)(t, x)=\frac{1}{2} \operatorname{Trace}\left(B B^{*}\left(\operatorname{Hess}_{x} u\right)(t, x)\right)
$$
(cf. Definition 2.4.5).

# Proof of Corollary 17.3.4.

First, observe that the assumption that $W: [0, T] \times \Omega \rightarrow \mathbb{R}^{m}$ is a standard Brownian motion demonstrates that for all $t \in [0, T]$, $x \in \mathbb{R}^{d}$ it holds that
$$
u(t, x)=\mathbb{E}\left[\varphi\left(x+B W_{t}\right)\right]=\mathbb{E}\left[\varphi\left(x+\sqrt{t} B \frac{W_{T}}{\sqrt{T}}\right)\right].
$$
The fact that $\frac{W_{T}}{\sqrt{T}}: \Omega \rightarrow \mathbb{R}^{m}$ is a standard normal random variable and Proposition 17.3.2 hence establish items (i) and (ii). The proof of Corollary 17.3.4 is thus complete.

![](img/dec290f673e6357c31893c67b579ffe1_528_0.png)

Figure 17.1 (plots/brownian_motions.pdf): Four trajectories of a 1-dimensional standard Brownian motion

## 17.3.2 Feynman–Kac formulas providing uniqueness of solutions

**Lemma 17.3.5 (A special case of Vitali’s convergence theorem).** Let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $X_n: \Omega \rightarrow \mathbb{R}$, $n \in \mathbb{N}_0$, be random variables with
$$
\mathbb{P}(\lim \sup _{n \rightarrow \infty}\left|X_n-X_0\right|=0)=1, \quad (17.37)
$$
and let $p \in(1, \infty)$ satisfy $\sup _{n \in \mathbb{N}} \mathbb{E}\left[\left|X_n\right|^p\right]<\infty$. Then
- (i) it holds that $\lim \sup _{n \rightarrow \infty} \mathbb{E}\left[\left|X_n-X_0\right|\right]=0$,
- (ii) it holds that $\mathbb{E}\left[\left|X_0\right|\right]<\infty$, and
- (iii) it holds that $\lim \sup _{n \rightarrow \infty}\left|\mathbb{E}\left[X_n\right]-\mathbb{E}\left[X_0\right]\right|=0$.

**Proof of Lemma 17.3.5.** First, note that the assumption that
$$
\sup _{n \in \mathbb{N}} \mathbb{E}\left[\left|X_n\right|^p\right]<\infty \quad (17.38)
$$
and, for example, the consequence of de la Vallée-Poussin’s theorem in Klenke [248, Corollary 6.21] imply that $\{ X _ n : n \in \mathbb{N} \}$ is uniformly integrable. This, (17.37), and Vitali’s convergence theorem in, for instance, Klenke [248, Theorem 6.25] prove items (i) and (ii). Observe that items (i) and (ii) establish item (iii). The proof of Lemma 17.3.5 is thus complete.

**Proposition 17.3.6.** *Let* $d \in \mathbb{N}$, $T$, $\rho \in (0, \infty)$, $f \in C([0,T] \times \mathbb{R}^d, \mathbb{R})$, *let* $u \in C^{1,2}([0,T] \times \mathbb{R}^d, \mathbb{R})$ *have at most polynomially growing partial derivatives, assume for all* $t \in [0,T], x \in \mathbb{R}^d$ *that*
$$
\left( \frac{\partial u}{\partial t}\right)(t,x) = \rho\Delta u (t,x) + f(t,x), \quad (17.39)
$$
*let* $( \Omega, \mathcal{F}, \mathbb{P} )$ *be a probability space, and let* $W : [0,T] \times \Omega \to \mathbb{R}^d$ *be a standard Brownian motion* (*cf.* *Definition 17.3.3*). *Then it holds for all* $t \in [0,T], x \in \mathbb{R}^d$ *that*
$$
u(t,x) = \mathbb{E}\biggl[ u(0,x + \sqrt{2\rho}W_t) + \int_0^t f(t-s,x + \sqrt{2\rho}W_s) \, \mathrm{d}s \biggr]. \quad (17.40)
$$

*Proof of Proposition 17.3.6.* Throughout this proof, let $D _ 1 : [0,T] \times \mathbb{R}^d \to \mathbb{R}$ *satisfy for all* $t \in [0,T], x \in \mathbb{R}^d$ *that*
$$
D_1(t,x) = \biggl(\frac{\partial u}{\partial t}\biggr)(t,x), \quad (17.41)
$$
let $D _ 2 = ( D _ { 2 , 1 } , D _ { 2 , 2 } , \dots, D _ { 2 , d } ) : [0,T] \times \mathbb{R}^d \to \mathbb{R}^d$ *satisfy for all* $t \in [0,T], x \in \mathbb{R}^d$ *that* $D _ 2(t,x) = ( \nabla _ { x } u)(t,x)$, *let* $H = ( H _ { i , j } ) _ { i , j \in \{ 1 , \dots, d \} } : [0,T] \times \mathbb{R}^d \to \mathbb{R}^{d \times d}$ *satisfy for all* $t \in [0,T], x \in \mathbb{R}^d$ *that*
$$
H(t,x) = \bigl(\mathrm{Hess}_x u\bigr)(t,x), \quad (17.42)
$$
let $\gamma : \mathbb{R}^d \to \mathbb{R}$ *satisfy for all* $z \in \mathbb{R}^d$ *that*
$$
\gamma(z) = (2\pi)^{-d/2} \exp\biggl(-\frac{\|z\|_2^2}{2}\biggr), \quad (17.43)
$$
*and let* $v _ { t , x } : [0,t] \to \mathbb{R}, t \in [0,T], x \in \mathbb{R}^d$, *satisfy for all* $t \in [0,T], x \in \mathbb{R}^d, s \in [0,t]$ *that*
$$
v_{t,x}(s) = \mathbb{E}\bigl[u(s,x + \sqrt{2\rho}W_{t-s})\bigr] \quad (17.44)
$$
(*cf.* *Definition 3.3.4*). *Note that the assumption that* $W$ *is a standard Brownian motion ensures that for all* $t \in (0,T], s \in [0,t]$ *it holds that* $(t-s)^{-1/2} W _ { t-s } : \Omega \to \mathbb{R}^d$ *is a standard normal random variable. This shows that for all* $t \in (0,T], x \in \mathbb{R}^d, s \in [0,t]$ *it holds that*
$$
\begin{aligned}
v_{t,x}(s) &= \mathbb{E}\bigl[u(s,x + \sqrt{2\rho(t-s)}(t-s)^{-1/2}W_{t-s})\bigr] \\
&= \int_{\mathbb{R}^d} u(s,x + \sqrt{2\rho(t-s)})\gamma(z) \, \mathrm{d}z. \quad (17.45)
\end{aligned}
$$
The assumption that $u$ *has at most polynomially growing partial derivatives, the fact that* $(0,\infty) \ni s \mapsto \sqrt{s} \in (0,\infty)$ *is differentiable, the chain rule, and Vitali’s convergence theorem therefore demonstrate that for all* $t \in (0, T]$, $x \in \mathbb{R}^{d}$, $s \in [0, t)$ it holds that $v_{t, x}|_{[0, t)} \in C^{1}([0, t), \mathbb{R})$ and
$$
\left(v_{t, x}\right)^{\prime}(s)=\int_{\mathbb{R}^{d}}\left[D_{1}\left(s, x+\sqrt{2\rho(t-s)} z\right)+\left\langle D_{2}\left(s, x+\sqrt{2\rho(t-s)} z\right), \frac{\rho z}{\sqrt{2\rho(t-s)}}\right\rangle\right] \gamma(z) \mathrm{d} z \quad (17.46)
$$
(cf. Definition 1.4.7). Furthermore, observe that the fact that for all $z \in \mathbb{R}^{d}$ it holds that $(\nabla \gamma)(z)=-\gamma(z) z$ implies that for all $t \in (0, T]$, $x \in \mathbb{R}^{d}$, $s \in [0, t)$ it holds that
$$
\begin{aligned}
\int_{\mathbb{R}^{d}}\left\langle D_{2}\left(s, x+\sqrt{2\rho(t-s)} z\right), \frac{\rho z}{\sqrt{2\rho(t-s)}}\right\rangle \gamma(z) \mathrm{d} z & =\int_{\mathbb{R}^{d}}\left\langle D_{2}\left(s, x+\sqrt{2\rho(t-s)} z\right), \frac{a(\nabla \gamma)(z)}{\sqrt{2\rho(t-s)}}\right\rangle \mathrm{d} z \quad (17.47) \\
&=\frac{\rho}{\sqrt{2\rho(t-s)}} \sum_{i=1}^{d}\left[\int_{\mathbb{R}^{d}} D_{2, i}\left(s, x+\sqrt{2\rho(t-s)} z\right)\left(\frac{\partial \gamma}{\partial z_{i}}\right)\left(z_{1}, z_{2}, \ldots, z_{d}\right) \mathrm{d} z\right].
\end{aligned}
$$
Moreover, note that integration by parts proves that for all $t \in (0, T]$, $x \in \mathbb{R}^{d}$, $s \in [0, t)$, $i \in\{1, 2, \ldots, d\}$, $a \in \mathbb{R}$, $b \in (a, \infty)$ it holds that
$$
\begin{aligned}
\int_{a}^{b} D_{2, i}\left(s, x+\sqrt{2\rho(t-s)}\right)\left(z_{1}, z_{2}, \ldots, z_{d}\right)\left(\frac{\partial \gamma}{\partial z_{i}}\right)\left(z_{1}, z_{2}, \ldots, z_{d}\right) \mathrm{d} z_{i} & =\left[D_{2, i}\left(s, x+\sqrt{2\rho(t-s)}\right)\left(z_{1}, z_{2}, \ldots, z_{d}\right) \gamma\left(z_{1}, z_{2}, \ldots, z_{d}\right)\right]_{z_{i}=a}^{z_{i}=b} \quad (17.48) \\
&-\int_{a}^{b} \sqrt{2\rho(t-s)} H_{i, i}\left(s, x+\sqrt{2\rho(t-s)}\right)\left(z_{1}, z_{2}, \ldots, z_{d}\right) \gamma\left(z_{1}, z_{2}, \ldots, z_{d}\right) \mathrm{d} z_{i}.
\end{aligned}
$$
The assumption that $u$ has at most polynomially growing derivatives hence establishes that for all $t \in (0, T]$, $x \in \mathbb{R}^{d}$, $s \in [0, t)$, $i \in\{1, 2, \ldots, d\}$ it holds that
$$
\begin{aligned}
\int_{\mathbb{R}} D_{2, i}\left(s, x+\sqrt{2\rho(t-s)}\right)\left(z_{1}, z_{2}, \ldots, z_{d}\right)\left(\frac{\partial \gamma}{\partial z_{i}}\right)\left(z_{1}, z_{2}, \ldots, z_{d}\right) \mathrm{d} z_{i} & =-\sqrt{2\rho(t-s)} \int_{\mathbb{R}} H_{i, i}\left(s, x+\sqrt{2\rho(t-s)}\right)\left(z_{1}, z_{2}, \ldots, z_{d}\right) \gamma\left(z_{1}, z_{2}, \ldots, z_{d}\right) \mathrm{d} z_{i}. \quad (17.49)
\end{aligned}
$$
Combining this with (17.47) and Fubini's theorem ensures that for all $t \in (0, T]$, $x \in \mathbb{R}^{d}$, $s \in [0, t)$ it holds that
$$
\begin{aligned}
\int_{\mathbb{R}^{d}}\left\langle D_{2}\left(s, x+\sqrt{2\rho(t-s)} z\right), \frac{\rho z}{\sqrt{2\rho(t-s)}}\right\rangle \gamma(z) \mathrm{d} z & =-\rho \sum_{i=1}^{d} \int_{\mathbb{R}^{d}} H_{i, i}\left(s, x+\sqrt{2\rho(t-s)}\right)(z) \gamma(z) \mathrm{d} z \quad (17.50) \\
&=-\int_{\mathbb{R}^{d}} \rho \operatorname{Trace}\left(H\left(s, x+\sqrt{2\rho(t-s)}(z)\right)\right) \gamma(z) \mathrm{d} z.
\end{aligned}
$$
