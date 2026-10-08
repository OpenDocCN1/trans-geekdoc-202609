
let $c \in [2, \infty)$, satisfy for all $x, y \in [0,1]^d$ that $|\mathcal{E}(x) - \mathcal{E}(y)| \le c \|x - y\|_1$, let $(\mathbf{J}_n)_{n \in \mathbb{N}} \subseteq \mathbb{N}$, for every $k, n$ let $\mathcal{G}^{k,n}$: $\mathbb{R}^d \times \Omega \to \mathbb{R}^d$ satisfy for all $\omega \in \Omega$, $\theta \in \{\vartheta \in \mathbb{R}^d : (\mathcal{R}^{k,n}_{\mathbf{J}_n}(:, \omega):\mathbb{R}^d \to [0, \infty)$ is differentiable at $\vartheta\}$ that

$$\mathcal{G}^{k,n}(\theta, \omega) = (\nabla_\theta \mathcal{R}^{k,n}_{\mathbf{J}_n})(\theta, \omega), \tag{15.74}$$

let $K \in \mathbb{N}$, for every $k, n \in \mathbb{N}_0$ let $\Theta_{k,n}$: $\Omega \to \mathbb{R}^d$ be a random variable, assume $\bigcup_{k=1}^{\infty} \Theta_{k,0}(\Omega) \subseteq [-c, c]^d$, assume that $\Theta_{k,0}$, $k \in \{1, 2, \dots, K\}$, are i.i.d., assume that $\Theta_{1,0}$ is continuously uniformly distributed on $[-c, c]^d$, let $(\gamma_n)_{n \in \mathbb{N}} \subseteq \mathbb{R}$ satisfy for all $k, n \in \mathbb{N}$ that

$$\Theta_{k,n} = \Theta_{k,n-1} - \gamma_n \mathcal{G}^{k,n}(\Theta_{k,n-1}), \tag{15.75}$$

let $N \in \mathbb{N}$, $\mathbf{T} \subseteq \{0, 1, \dots, N\}$ satisfy $0 \in \mathbf{T}$, let $\mathbf{k}$: $\Omega \to (\mathbb{N}_0)^2$ be a random variable, and assume for all $\omega \in \Omega$ that

$$\mathbf{k}(\omega) \in \{(k, n) \in \{1, 2, \dots, K\} \times \mathbf{T}: \|\Theta_{k,n}(\omega)\|_\infty \le B\} \tag{15.76}$$

$$\text{and} \qquad \mathcal{R}(\Theta_{\mathbf{k}(\omega)}(\omega)) = \min_{(k,n) \in \{1,2,\dots,K\} \times \mathbf{T}: \|\Theta_{k,n}(\omega)\|_\infty \le B} \mathcal{R}(\Theta_{k,n}(\omega)) \tag{15.77}$$

(cf. Definitions 3.3.4 and 4.4.1.) Then

$$\begin{aligned}\mathbb{E}\left[\int_{[0,1]^d} |\mathcal{K}^{\epsilon}_{0,1} \Theta_{\mathbf{k},1}(x) - \mathcal{E}(x)| \mathbb{P}_{X_1^{0,0}}(\mathrm{d}x)\right] \le \frac{6dc^2}{[\min\{\mathbf{L}_1, \mathbf{L}_2, \dots, \mathbf{L}_{K-1}\}]^{1/d}} + \frac{5c^2\mathbf{L}(\|\mathbf{I}\|_\infty + 1) \ln(enM)}{M^{1/4}} + \frac{\mathbf{L}(\|\mathbf{I}\|_\infty + 1) \mathbf{L}c\mathbf{L}^{+1}}{K^{(2\mathbf{L})^{-1}(\|\mathbf{I}\|_\infty + 1)^{-2}}}\end{aligned} \tag{15.78}$$

(cf. Lemma 15.1.1).

Proof of Corollary 15.2.3. Note that Corollary 15.2.2 (applied with $a \sim 0$, $u \sim 0$, $b \sim 1$, $v \sim 1$, $L \sim c$, $c \sim c$, $B \sim c$ in the notation of Corollary 15.2.2), the fact that $c \ge 2$ and $M \ge 1$, and Lemma 15.1.4 show (15.78). The proof of Corollary 15.2.3 is thus complete. $\square$

# Part VI
## Deep learning for partial differential equations (PDEs)

# Chapter 16
## Physics-informed neural networks (PINNs)

Deep learning methods have not only become very popular for data-driven learning problems, but are nowadays also heavily used for solving mathematical equations such as ordinary and partial differential equations (cf., for example, [119, 187, 347, 379]). In particular, we refer to the overview articles [24, 56, 88, 145, 237, 355] and the references therein for numerical simulations and theoretical investigations for deep learning methods for PDEs.

Often deep learning methods for PDEs are obtained, first, by reformulating the PDE problem under consideration as an infinite dimensional stochastic optimization problem, then, by approximating the infinite dimensional stochastic optimization problem through finite dimensional stochastic optimization problems involving deep ANNs as approximations for the PDE solution and/or its derivatives, and thereafter, by approximately solving the resulting finite dimensional stochastic optimization problems through SGD-type optimization methods.

Among the most basic schemes of such deep learning methods for PDEs are PINNs and DGMS; see [347, 379]. In this chapter we present in Theorem 16.1.1 in Section 16.1 a reformulation of PDE problems as stochastic optimization problems, we use the theoretical considerations from Section 16.1 to briefly sketch in Section 16.2 a possible derivation of PINNs and DGMs, and we present in Sections 16.3 and 16.4 numerical simulations for PINNs and DGMs. For simplicity and conciseness we restrict ourselves in this chapter to the case of semilinear heat PDEs. The specific presentation of this chapter is based on Beck et al. [24].

### 16.1 Reformulation of PDE problems as stochastic optimization problems

Both **PINNs** and **DGMs** are based on reformulations of the considered **PDEs** as suitable infinite dimensional stochastic optimization problems. In Theorem 16.1.1 below we present the theoretical result behind this reformulation in the special case of semilinear heat **PDEs**.

**Theorem 16.1.1.** *Let* $T \in (0, \infty)$, $d \in \mathbb{N}$, $g \in C^2(\mathbb{R}^d, \mathbb{R})$, $u \in C^{1,2}([0,T] \times \mathbb{R}^d, \mathbb{R})$, $\iota \in C([0,T], (0, \infty))$, $\boldsymbol{x} \in C(\mathbb{R}^d, (0, \infty))$, *assume that* $g$ *has at most polynomially growing* partial *derivatives*, *let* $(\Omega, \mathcal{F}, \mathbb{P})$ *be a probability space*, *let* $\mathcal{T}: \Omega \rightarrow [0, T]$ *and* $\mathcal{X}: \Omega \rightarrow \mathbb{R}^d$ *be independent random variables*, *assume for all* $A \in \mathcal{B}([0,T])$, $B \in \mathcal{B}(\mathbb{R}^d)$ *that*

$$\mathbb{P}(\mathcal{T} \in A) = \int_A \boldsymbol{\iota}(t) \, \mathrm{d}t \quad \text{ and } \quad \mathbb{P}(\mathcal{X} \in B) = \int_B \boldsymbol{x}(x) \, \mathrm{d}x, \qquad \qquad (16.1)$$

*let* $\boldsymbol{f}: \mathbb{R} \rightarrow \mathbb{R}$ *be Lipschitz continuous*, *and let* $\mathfrak{L}: C^{1,2}([0,T] \times \mathbb{R}^d, \mathbb{R}) \rightarrow [0, \infty)$ *satisfy for all* $v = (v(t, x))_{(t,x) \in [0,T] \times \mathbb{R}^d} \in C^{1,2}([0,T] \times \mathbb{R}^d, \mathbb{R})$ *that*

$$\mathfrak{L}(v) = \mathbb{E}\left[ |v(0, \mathcal{X}) - g(\mathcal{X})|^2 + \left| \left(\frac{\partial v}{\partial t}\right)(\mathcal{T}, \mathcal{X}) - (\Delta_x v)(\mathcal{T}, \mathcal{X}) - f(v(\mathcal{T}, \mathcal{X})) \right|^2 \right]. \qquad \qquad (16.2)$$

*Then the following two statements are equivalent:*

- $(i)$ It holds that $\mathfrak{L}(u) = \inf_{v \in C^{1,2}([0,T] \times \mathbb{R}^d, \mathbb{R})} \mathfrak{L}(v)$.
- $(ii)$ It holds for all $t \in [0, T]$, $x \in \mathbb{R}^d$ that $u(0, x) = g(x)$ and

$$\left( \frac{\partial u}{\partial t} \right)(t, x) = (\Delta_x u)(t, x) + f(u(t, x)). \qquad \qquad (16.3)$$

*Proof of Theorem 16.1.1.* *Observe that* (16.2) *proves that for all* $v \in C^{1,2}([0,T] \times \mathbb{R}^d, \mathbb{R})$ *with* $\forall x \in \mathbb{R}^d: u(0, x) = g(x)$ *and* $\forall t \in [0, T]$, $x \in \mathbb{R}^d: \left( \frac{\partial u}{\partial t} \right)(t, x) = (\Delta_x u)(t, x) + f(u(t, x))$ *it holds that*

$$\mathfrak{L}(v) = 0. \qquad \qquad (16.4)$$

This and the fact that for all $v \in C^{1,2}([0,T] \times \mathbb{R}^d, \mathbb{R})$ it holds that $\mathfrak{L}(v) \ge 0$ establish that $(ii) \rightarrow (i)$. Note that the assumption that $\boldsymbol{f}$ is Lipschitz continuous, the assumption that $g$ is twice continuously differentiable, and the assumption that $g$ has at most polynomially growing partial derivatives demonstrate that there exists $v \in C^{1,2}([0,T] \times \mathbb{R}^d, \mathbb{R})$ which satisfies for all $t \in [0, T]$, $x \in \mathbb{R}^d$ that $v(0, x) = g(x)$ and

$$\left( \frac{\partial v}{\partial t} \right)(t, x) = (\Delta_x v)(t, x) + f(v(t, x)) \qquad \qquad (16.5)$$

(cf., for instance, Beck et al. [23, Corollary 3.4]). This and (16.4) show that

$$\inf_{v \in C^{1,2}([0,T] \times \mathbb{R}^d, \mathbb{R})} \mathfrak{L}(v) = 0. \qquad \qquad (16.6)$$

Furthermore, observe that (16.2), (16.1), and the assumption that $\mathcal{T}$ and $\mathcal{X}$ are independent imply that for all $v \in C^{1,2}([0, T] \times \mathbb{R}^d, \mathbb{R})$ it holds that

$$\mathfrak{L}(v)= \int_{[0, T] \times \mathbb{R}^{d}}\left(|v(0, x)-g(x)|^{2}+\left|\left(\frac{\partial v}{\partial t}\right)(t, x)-\left(\Delta_{x} v\right)(t, x)- f(v(t, x))\right|^{2} \mathcal{I}(t) \mathcal{X}(x) \mathrm{d}(t, x), \tag{16.7}\right.$$

The assumption that $\mathcal{I}$ and $\mathcal{X}$ are continuous and the fact that for all $t \in[0, T], x \in \mathbb{R}^{d}$ it holds that $\mathcal{I}(t) \geq 0$ and $\mathcal{X}(x) \geq 0$ therefore ensure that for all $v \in C^{1,2}([0, T] \times \mathbb{R}^{d}, \mathbb{R})$, $t \in[0, T], x \in \mathbb{R}^{d}$ with $\mathfrak{L}(v)=0$ it holds that

$$\left(|v(0, x)-g(x)|^{2}+\left|\left(\frac{\partial v}{\partial t}\right)(t, x)-\left(\Delta_{x} v\right)(t, x)- f(v(t, x))\right|^{2}\right) \mathcal{I}(t) \mathcal{X}(x)=0. \tag{16.8}$$

This and the assumption that for all $t \in[0, T], x \in \mathbb{R}^{d}$ it holds that $\mathcal{I}(t)>0$ and $\mathcal{X}(x)>0$ show that for all $v \in C^{1,2}([0, T] \times \mathbb{R}^{d}, \mathbb{R}), t \in[0, T], x \in \mathbb{R}^{d}$ with $\mathfrak{L}(v)=0$ it holds that

$$|v(0, x)-g(x)|^{2}+\left|\left(\frac{\partial v}{\partial t}\right)(t, x)-\left(\Delta_{x} v\right)(t, x)- f(v(t, x))\right|^{2}=0. \tag{16.9}$$

Combining this with (16.6) proves that $(i) \rightarrow (ii)$. The proof of Theorem 16.1.1 is thus complete. $\square$

### 16.2 Derivation of PINNs and deep Galerkin methods (DGMs)

In this section we employ the reformulation of semilinear PDEs as optimization problems from Theorem 16.1.1 to sketch an informal derivation of deep learning schemes to approximate solutions of semilinear heat PDEs. For this let $T \in(0, \infty), d \in \mathbb{N}$, $u \in C^{1,2}([0, T] \times \mathbb{R}^{d}, \mathbb{R}), g \in C^{2}\left(\mathbb{R}^{d}, \mathbb{R}\right)$ satisfy that $g$ has at most polynomially growing partial derivatives, let $f: \mathbb{R} \rightarrow \mathbb{R}$ be Lipschitz continuous, and assume for all $t \in[0, T], x \in \mathbb{R}^{d}$ that $u(0, x)=g(x)$ and

$$\left(\frac{\partial u}{\partial t}\right)(t, x)=\left(\Delta_{x} u\right)(t, x)+f(u(t, x)). \tag{16.10}$$

In the framework described in the previous sentence, we think of $u$ as the unknown PDE solution. The objective of this derivation is to develop deep learning methods which aim to approximate the unknown function $u$.

In the first step we employ Theorem 16.1.1 to reformulate the PDE problem associated to (16.10) as an infinite dimensional stochastic optimization problem over a function space. For this let $\mathcal{I} \in C([0, T],(0, \infty)), \mathcal{X} \in C\left(\mathbb{R}^{d},(0, \infty)\right)$, let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $\mathcal{T}: \Omega \rightarrow[0, T]$ and $\mathcal{X}: \Omega \rightarrow \mathbb{R}^{d}$ be independent random variables, assume for all $A \in \mathcal{B}([0, T]), B \in \mathcal{B}\left(\mathbb{R}^{d}\right)$ that

$$\mathbb{P}(\mathcal{T} \in A)=\int_{A} \mathcal{I}(t) \mathrm{d} t\quad\text { and }\quad \mathbb{P}\left(\mathcal{X} \in B\right)=\int_{B} \mathcal{X}(x) \mathrm{d} x, \tag{16.11}$$
