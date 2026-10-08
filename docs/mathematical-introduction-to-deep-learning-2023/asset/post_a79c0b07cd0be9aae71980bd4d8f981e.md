
(iii) it holds for every $x \in [a, b]^d$ that $U(x) = u(T, x)$.

Proof of Proposition 17.4.1. First, observe that (17.69), the assumption that $\mathcal{W}$ is a standard normal random variable, and Corollary 17.3.7 ensure that for all $x \in \mathbb{R}^d$ it holds that $\varphi: \mathbb{R}^d \rightarrow \mathbb{R}$ is twice continuously differentiable with at most polynomially growing partial derivatives and

$u(T, x) = \mathbb{E}[u(0, \varrho \mathcal{W} + x)] = \mathbb{E}[\varphi(\varrho \mathcal{W} + x)].$ (17.71)

Furthermore, note that the assumption that $\mathcal{W}$ is a standard normal random variable, the fact that $\varphi$ is continuous, and the fact that $\varphi$ has at most polynomially growing partial derivatives and is continuous show that

- I) it holds that $[a, b]^d \times \Omega \ni (x, \omega) \mapsto \varphi(\varrho \mathcal{W}(\omega) + x) \in \mathbb{R}$ is $(\mathcal{B}([a, b]^d) \otimes \mathcal{F})/\mathcal{B}(\mathbb{R})$ measurable and
- II) it holds for all $x \in [a, b]^d$ that $\mathbb{E}[|\varphi(\varrho \mathcal{W} + x)|^2] < \infty$.

Proposition 17.2.1 and (17.71) hence ensure that

- A) there exists a unique continuous function $U: [a, b]^d \rightarrow \mathbb{R}$ which satisfies that

$\int_{[a, b]^d} \mathbb{E}[|\varphi(\varrho \mathcal{W} + x) - U(x)|^2] \, \mathrm{d}x = \underset{v \in C([a, b]^d, \mathbb{R})}{\inf} \left( \int_{[a, b]^d} \mathbb{E}[|\varphi(\varrho \mathcal{W} + x) - v(x)|^2] \, \mathrm{d}x \right)$ (17.72)

- B) it holds for all $x \in [a, b]^d$ that $U(x) = u(T, x)$.

Moreover, observe that the assumption that $\mathcal{W}$ and $\mathcal{X}$ are independent, item I), and the assumption that $\mathcal{X}$ is continuously uniformly distributed on $[a, b]^d$ demonstrate that for all $v \in C([a, b]^d, \mathbb{R})$ it holds that

$\mathbb{E}[|\varphi(\varrho \mathcal{W} + \mathcal{X}) - v(\mathcal{X})|^2] = \frac{1}{(b - a)^d} \int_{[a, b]^d} \mathbb{E}[|\varphi(\varrho \mathcal{W} + x) - v(x)|^2] \, \mathrm{d}x.$ (17.73)

Combining this with item A) implies item (ii). Note that items A) and B) and (17.73) prove item (iii). The proof of Proposition 17.4.1 is thus complete. $\square$

While Proposition 17.4.1 above recasts the solutions of the PDE in (17.69) at a particular point in time as the solutions of a stochastic optimization problem, we can also derive from this a corollary which shows that the solutions of the PDE over an entire timespan are similarly the solutions of a stochastic optimization problem.

### Corollary 17.4.2.

Let $d \in \mathbb{N}$, $T, \rho \in (0, \infty)$, $\varrho = \sqrt{2\rho}$, $a \in \mathbb{R}$, $b \in (a, \infty)$, let $\varphi: \mathbb{R}^d \rightarrow \mathbb{R}$ be a function, let $u \in C^{1,2}([0, T] \times \mathbb{R}^d, \mathbb{R})$ be a function with at most polynomially growing partial derivatives which satisfies for all $t \in [0, T]$, $x \in \mathbb{R}^d$ that $u(0, x) = \varphi(x)$ and

$$\left( \frac{\partial u}{\partial t} \right)(t, x) = \rho(\Delta_x u)(t, x), \tag{17.74}$$

let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $\mathcal{W}: \Omega \rightarrow \mathbb{R}^d$ be a standard normal random variable, let $\tau: \Omega \rightarrow [0, T]$ be a continuously uniformly distributed random variable, let $\mathcal{X}: \Omega \rightarrow [a, b]^d$ be a continuously uniformly distributed random variable, and assume that $\mathcal{W}$, $\tau$, and $\mathcal{X}$ are independent. Then

- (i) there exists a unique $U \in C([0, T] \times [a, b]^d, \mathbb{R})$ which satisfies that

$$\mathbb{E}\left[|\varphi(\varrho \sqrt{\tau}\mathcal{W} + \mathcal{X}) - U(\tau, \mathcal{X})|^2\right] = \inf_{v \in C([0,T]\times[a,b]^d,\mathbb{R})} \mathbb{E}\left[|\varphi(\varrho\sqrt{\tau}\mathcal{W} + \mathcal{X}) - v(\tau, \mathcal{X})|^2\right] \tag{17.75}$$

- (ii) it holds for all $t \in [0, T]$, $x \in [a, b]^d$ that $U(t, x) = u(t, x)$.

Proof of Corollary 17.4.2. Throughout this proof, let $F: C([0, T] \times [a, b]^d, \mathbb{R}) \rightarrow [0, \infty]$ satisfy for all $v \in C([0, T] \times [a, b]^d, \mathbb{R})$ that

$$F(v) = \mathbb{E}\left[|\varphi(\varrho \sqrt{\tau}\mathcal{W} + \mathcal{X}) - v(\tau, \mathcal{X})|^2\right]. \tag{17.76}$$

Observe that Proposition 17.4.1 establishes that for all $v \in C([0, T] \times [a, b]^d, \mathbb{R})$, $s \in [0, T]$ it holds that

$$\mathbb{E}\left[|\varphi(\varrho \sqrt{s}\mathcal{W} + \mathcal{X}) - v(s, \mathcal{X})|^2\right] \ge \mathbb{E}\left[|\varphi(\varrho \sqrt{s}\mathcal{W} + \mathcal{X}) - u(s, \mathcal{X})|^2\right]. \tag{17.77}$$

Furthermore, note that the assumption that $\mathcal{W}$, $\tau$, and $\mathcal{X}$ are independent, the assumption that $\tau: \Omega \rightarrow [0, T]$ is continuously uniformly distributed, and Fubini’s theorem ensure that for all $v \in C([0, T] \times [a, b]^d, \mathbb{R})$ it holds that

$$F(v) = \mathbb{E}\left[|\varphi(\varrho \sqrt{\tau}\mathcal{W} + \mathcal{X}) - v(\tau, \mathcal{X})|^2\right] = \int_{[0,T]} \mathbb{E}\left[|\varphi(\varrho \sqrt{s}\mathcal{W} + \mathcal{X}) - v(s, \mathcal{X})|^2\right] \mathrm{d}s. \tag{17.78}$$

This and (17.77) show that for all $v \in C([0, T] \times [a, b]^d, \mathbb{R})$ it holds that

$$F(v) \ge \int_{[0,T]} \mathbb{E}\left[|\varphi(\varrho \sqrt{s}\mathcal{W} + \mathcal{X}) - u(s, \mathcal{X})|^2\right] \mathrm{d}s. \tag{17.79}$$

Combining this with (17.78) demonstrates that for all $v \in C([0, T] \times [a, b]^d, \mathbb{R})$ it holds that $F(v) \ge F(u)$. Therefore, we obtain that

$$F(u) = \inf_{v \in C([0,T]\times[a,b]^d,\mathbb{R})} F(v). \tag{17.80}$$

This and (17.78) imply that for all $U \in C([0, T] \times [a, b]^d, \mathbb{R})$ with

$F(U) = \inf_{v \in C([0,T] \times [a,b]^d, \mathbb{R})} F(v)$ (17.81)

it holds that

$\int_{[0, T]} \mathbb{E}[|\varphi(\varrho\sqrt{s}\mathcal{W}+\mathcal{X}) - U(s, \mathcal{X})|^2] \, \mathrm{d}s = \int_{[0, T]} \mathbb{E}[|\varphi(\varrho\sqrt{s}\mathcal{W}+\mathcal{X}) - u(s, \mathcal{X})|^2] \, \mathrm{d}s.$ (17.82)

Combining this with (17.77) proves that for all $U \in C([0, T] \times [a, b]^d, \mathbb{R})$ with $F(U) = \inf_{v \in C([0,T] \times [a,b]^d, \mathbb{R})} F(v)$ there exists $A \subseteq [0, T]$ with $\int_A 1 \, \mathrm{d}x = T$ such that for all $s \in A$ it holds that

$\mathbb{E}[|\varphi(\varrho\sqrt{s}\mathcal{W}+\mathcal{X}) - U(s, \mathcal{X})|^2] = \mathbb{E}[|\varphi(\varrho\sqrt{s}\mathcal{W}+\mathcal{X}) - u(s, \mathcal{X})|^2].$ (17.83)

Proposition 17.4.1 therefore establishes that for all $U \in C([0, T] \times [a, b]^d, \mathbb{R})$ with $F(U) = \inf_{v \in C([0,T] \times [a,b]^d, \mathbb{R})} F(v)$ there exists $A \subseteq [0, T]$ with $\int_A 1 \, \mathrm{d}x = T$ such that for all $s \in A$ it holds that $U(s) = u(s)$. The fact that $u \in C([0, T] \times [a, b]^d, \mathbb{R})$ hence ensures that for all $U \in C([0, T] \times [a, b]^d, \mathbb{R})$ with $F(U) = \inf_{v \in C([0,T] \times [a,b]^d, \mathbb{R})} F(v)$ it holds that $U = u$. Combining this with (17.80) proves items (i) and (ii). The proof of Corollary 17.4.2 is thus complete. $\square$

## 17.5 Derivation of DKMs

In this section we present in the special case of the heat equation a rough derivation of the DKMs introduced in Beck et al. [19]. This derivation will proceed along the analogous steps as the derivation of PINNs and DGMs in Section 16.2. Firstly, we will employ Proposition 17.4.1 to reformulate the PDE problem under consideration as an infinite dimensional stochastic optimization problem, secondly, we will employ ANNs to reduce the infinite dimensional stochastic optimization problem to a finite dimensional stochastic optimization problem, and thirdly, we will aim to approximately solve this finite dimensional stochastic optimization problem by means of SGD-type optimization methods. We start by introducing the setting of the problem. Let $d \in \mathbb{N}$, $T, \varrho \in (0, \infty)$, $a \in \mathbb{R}$, $b \in (a, \infty)$, let $\varphi: \mathbb{R}^d \to \mathbb{R}$ be a function, let $u \in C^{1, 2}([0, T] \times \mathbb{R}^d, \mathbb{R})$ have at most polynomially growing partial derivatives, and assume for all $t \in [0, T]$, $x \in \mathbb{R}^d$ that $u(0, x) = \varphi(x)$ and

$\left(\frac{\partial u}{\partial t}\right)(t, x) = \varrho\left(\Delta_x u\right)(t, x).$ (17.84)

In the framework described in the previous sentence, we think of $u$ as the unknown PDE solution. The objective of this derivation is to develop deep learning methods which aim to approximate the unknown PDE solution $u(T, \cdot)|_{[a, b]^d}: [a, b]^d \to \mathbb{R}$ at time $T$ restricted on $[a, b]^d$.
