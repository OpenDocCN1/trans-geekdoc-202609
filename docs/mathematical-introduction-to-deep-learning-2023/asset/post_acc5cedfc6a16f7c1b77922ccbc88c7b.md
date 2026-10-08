
This, (17.46), (17.39), and the fact that for all $t \in (0, T]$, $s \in [0, t)$ it holds that $(t-s)^{-1/2}W_{t-s}\colon \Omega \rightarrow \mathbb{R}^{d}$ is a standard normal random variable show that for all $t \in (0, T]$, $x \in \mathbb{R}^{d}$, $s \in [0, t)$ it holds that

$$(v_{t,x})(s) = \int_{\mathbb{R}^{d}} \left[ D_1(s, x + \sqrt{2 \rho (t-s)} z) - \rho \, \text{Trace} \left( H(s, x + \sqrt{2 \rho (t-s)} z) \right) \right] \gamma(z) \, \mathrm{d}z = \int_{\mathbb{R}^{d}} f(s, x + \sqrt{2 \rho (t-s)} z) \gamma(z) \, \mathrm{d}z = \mathbb{E} \left[ f(s, x + \sqrt{2 \rho} W_{t-s}) \right]. \quad (17.51)$$

The fact that $W_0 = 0$, the fact that for all $t \in [0, T]$, $x \in \mathbb{R}^{d}$ it holds that $v_{t,x}\colon [0, t] \rightarrow \mathbb{R}$ is continuous, and the fundamental theorem of calculus therefore demonstrate that for all $t \in [0, T]$, $x \in \mathbb{R}^{d}$ it holds that

$$u(t, x) = \mathbb{E} \left[ u(t, x + \sqrt{2 \rho} W_{t-t}) \right] = v_{t,x}(t) = v_{t,x}(0) + \int_0^{t} (v_{t,x})'(s) \, \mathrm{d}s = \mathbb{E} \left[ u(0, x + \sqrt{2 \rho} W_{t}) \right] + \int_0^{t} \mathbb{E} \left[ f(s, x + \sqrt{2 \rho} W_{t-s}) \right] \, \mathrm{d}s. \quad (17.52)$$

Fubini's theorem and the fact that $u$ and $f$ are at most polynomially growing hence imply (17.40). The proof of Proposition 17.3.6 is thus complete. $\square$

**Corollary 17.3.7.** Let $d \in \mathbb{N}$, $T, \rho \in (0, \infty)$, $\varrho = \sqrt{2 \rho T}$, $a \in \mathbb{R}$, $b \in (a, \infty)$, let $\varphi\colon \mathbb{R}^{d} \rightarrow \mathbb{R}$ be a function, let $u \in C^{1,2}\left( [0, T] \times \mathbb{R}^{d}, \mathbb{R} \right)$ have at most polynomially growing partial derivatives, assume for all $t \in [0, T]$, $x \in \mathbb{R}^{d}$ that $u(0, x) = \varphi(x)$ and

$$\left( \frac{\partial u}{\partial t} \right)(t, x) = \rho \, (\Delta_x u)(t, x), \quad (17.53)$$

let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, and let $W\colon \Omega \rightarrow \mathbb{R}^{d}$ be a standard normal random variable. Then

- (i) it holds that $\varphi\colon \mathbb{R}^{d} \rightarrow \mathbb{R}$ is twice continuously differentiable with at most polynomially growing partial derivatives and
- (ii) it holds for all $x \in \mathbb{R}^{d}$ that $u(T, x) = \mathbb{E} \left[ \varphi(\varrho W + x) \right]$.

Proof of Corollary 17.3.7. Observe that the assumption that $u \in C^{1,2}\left( [0, T] \times \mathbb{R}^{d}, \mathbb{R} \right)$ has at most polynomially growing partial derivatives and the fact that for all $x \in \mathbb{R}^{d}$ it holds that $\varphi(x) = u(0, x)$ prove item (i). Furthermore, note that Proposition 17.3.6 establishes item (ii). The proof of Corollary 17.3.7 is thus complete. $\square$

**Definition 17.3.8** (Continuous convolutions). Let $d \in \mathbb{N}$ and let $f\colon \mathbb{R}^{d} \rightarrow \mathbb{R}$ and $g\colon \mathbb{R}^{d} \rightarrow \mathbb{R}$ be $\mathcal{B}(\mathbb{R}^{d})\! / \!\mathcal{B}(\mathbb{R})$-measurable. Then we denote by

$$f \circledast g\colon \left\{ x \in \mathbb{R}^{d}\colon \min \left\{ \int_{\mathbb{R}^{d}} \max \left\{ 0, f(x - y)g(y) \right\} \, \mathrm{d}y, \right. \left. - \int_{\mathbb{R}^{d}} \min \left\{ 0, f(x - y)g(y) \right\} \, \mathrm{d}y \right\} < \infty \right\} \rightarrow [-\infty, \infty] \quad (17.54)$$

the function which satisfies for all $x \in \mathbb{R}^{d}$ with

$\min \left\{ \int_{\mathbb{R}^{d}} \max \left\{ 0, f(x-y)g(y) \right\} \, \mathrm{d}y, -\int_{\mathbb{R}^{d}} \min \left\{ 0, f(x-y)g(y) \right\} \, \mathrm{d}y \right\} < \infty$ (17.55)

that

$(f \otimes g)(x) = \int_{\mathbb{R}^{d}} f(x-y)g(y) \, \mathrm{d}y$. (17.56)

### Exercise 17.3.1.

Let $d \in \mathbb{N}$, $T \in (0, \infty)$, for every $\sigma \in (0, \infty)$ let $\gamma_{\sigma}: \mathbb{R}^{d} \to \mathbb{R}$ satisfy for all $x \in \mathbb{R}^{d}$ that

$\gamma_{\sigma}(x) = (2 \pi \sigma^{2})^{-\frac{d}{2}} \exp \left( \frac{-\|x\|_{2}^{2}}{2 \sigma^{2}} \right)$, (17.57)

and for every $\rho \in (0, \infty)$, $\varphi \in C^{2}\left( \mathbb{R}^{d}, \mathbb{R} \right)$ with $\sup_{x \in \mathbb{R}^{d}} \left[ \sum_{i,j=1}^{d} \left( |\varphi(x)| + \left| \left( \frac{\partial}{\partial x_{i}} \varphi \right)(x) \right| + \left| \left( \frac{\partial^{2}}{\partial x_{i} \partial x_{j}} \varphi \right)(x) \right| \right) \right] < \infty$ let $u_{\rho, \varphi}: [0, T] \times \mathbb{R}^{d} \to \mathbb{R}$ satisfy for all $t \in (0, T]$, $x \in \mathbb{R}^{d}$ that

$u_{\rho, \varphi}(0, x) = \varphi(x) \quad \text{and} \quad u_{\rho, \varphi}(t, x) = (\varphi \otimes \gamma_{\sqrt{2 \rho t}})(x)$ (17.58)

(cf. Definitions 3.3.4 and 17.3.8). Prove or disprove the following statement: For all $\rho \in (0, \infty)$, $\varphi \in C^{2}\left( \mathbb{R}^{d}, \mathbb{R} \right)$ with $\sup_{x \in \mathbb{R}^{d}} \left[ \sum_{i,j=1}^{d} \left( |\varphi(x)| + \left| \left( \frac{\partial}{\partial x_{i}} \varphi \right)(x) \right| + \left| \left( \frac{\partial^{2}}{\partial x_{i} \partial x_{j}} \varphi \right)(x) \right| \right) \right] < \infty$ it holds for all $t \in (0, T)$, $x \in \mathbb{R}^{d}$ that $u_{\rho, \varphi} \in C^{1,2}\left( [0, T] \times \mathbb{R}^{d}, \mathbb{R} \right)$ and

$\left( \frac{\partial u_{\rho, \varphi}}{\partial t} \right)(t, x) = \rho \left( \Delta_{x} u_{\rho, \varphi} \right)(t, x)$. (17.59)

### Exercise 17.3.2.

Prove or disprove the following statement: For every $x \in \mathbb{R}$ it holds that

$e^{-x^{2}/2} = \frac{1}{\sqrt{2 \pi}} \left[ \int_{\mathbb{R}} e^{-t^{2}/2} e^{-ixt} \, \mathrm{d}t \right]$. (17.60)

### Exercise 17.3.3.

Let $d \in \mathbb{N}$, $T \in (0, \infty)$, for every $\sigma \in (0, \infty)$ let $\gamma_{\sigma}: \mathbb{R}^{d} \to \mathbb{R}$ satisfy for all $x \in \mathbb{R}^{d}$ that

$\gamma_{\sigma}(x) = (2 \pi \sigma^{2})^{-\frac{d}{2}} \exp \left( \frac{-\|x\|_{2}^{2}}{2 \sigma^{2}} \right)$, (17.61)

for every $\varphi \in C^{2}\left( \mathbb{R}^{d}, \mathbb{R} \right)$ with $\sup_{x \in \mathbb{R}^{d}} \left[ \sum_{i,j=1}^{d} \left( |\varphi(x)| + \left| \left( \frac{\partial}{\partial x_{i}} \varphi \right)(x) \right| + \left| \left( \frac{\partial^{2}}{\partial x_{i} \partial x_{j}} \varphi \right)(x) \right| \right) \right] < \infty$ let $u_{\varphi}: [0, T] \times \mathbb{R}^{d} \to \mathbb{R}$ satisfy for all $t \in (0, T]$, $x \in \mathbb{R}^{d}$ that

$u_{\varphi}(0, x) = \varphi(x) \quad \text{and} \quad u_{\varphi}(t, x) = (\varphi \otimes \gamma_{\sqrt{2t}})(x)$, (17.62)

and for every $i=(i_{1}, \dots, i_{d}) \in \mathbb{N}^{d}$ let $\psi_{i}: \mathbb{R}^{d} \to \mathbb{R}$ satisfy for all $x=(x_{1}, \dots, x_{d}) \in \mathbb{R}^{d}$ that

$\psi_{i}(x) = 2^{\frac{d}{2}} \left[ \prod_{k=1}^{d} \sin(i_{k} \pi x_{k}) \right]$ (17.63)

(cf. Definitions 3.3.4 and 17.3.8). Prove or disprove the following statement: For all $i=(i_{1}, \dots, i_{d}) \in \mathbb{N}^{d}$, $t \in [0, T]$, $x \in \mathbb{R}^{d}$ it holds that

$u_{\psi_{i}}(t, x) = \exp \left( -\pi^{2} \left[ \sum_{k=1}^{d} |i_{k}|^{2} t \right] \right) \psi_{i}(x)$. (17.64)

### Exercise 17.3.4.

Let $d \in \mathbb{N}$, $T \in (0, \infty)$, for every $\sigma \in (0, \infty)$ let $\gamma_{\sigma}\colon \mathbb{R}^{d} \rightarrow \mathbb{R}$ satisfy for all $x \in \mathbb{R}^{d}$ that

$$\gamma_{\sigma}(x) = (2\pi\sigma^{2})^{-\frac{d}{2}} \exp\left( \frac{-\|x\|_{2}^{2}}{2\sigma^{2}} \right),$$

and for every $i = (i_{1}, \ldots, i_{d}) \in \mathbb{N}^{d}$ let $\psi_{i}\colon \mathbb{R}^{d} \rightarrow \mathbb{R}$ satisfy for all $x = (x_{1}, \ldots, x_{d}) \in \mathbb{R}^{d}$ that

$$\psi_{i}(x) = 2^{\frac{d}{2}} \left[ \prod_{k=1}^{d} \sin(i_{k}\pi x_{k}) \right]$$

(cf. Definition 3.3.4). Prove or disprove the following statement: For every $i = (i_{1}, \ldots, i_{d}) \in \mathbb{N}^{d}$, $s \in [0, T]$, $y \in \mathbb{R}^{d}$ and every function $u \in C^{1,2}([0,T] \times \mathbb{R}^{d}, \mathbb{R})$ with at most polynomially growing partial derivatives which satisfies for all $t \in (0, T]$, $x \in \mathbb{R}^{d}$ that $u(0,x) = \psi_{i}(x)$ and

$$\left( \frac{\partial u}{\partial t} \right)(t,x) = (\Delta_{x}u)(t,x)$$

it holds that

$$u(s,y) = \exp\left( -\pi^{2}\left[\sum_{k=1}^{d} |i_{k}|^{2} s\right] \right) \psi_{i}(y).$$

## 17.4 Reformulation of PDE problems as stochastic optimization problems

The proof of the next result, Proposition 17.4.1 below, is based on an application of Proposition 17.2.1 and Proposition 17.3.6. A more general result than Proposition 17.4.1 with a detailed proof can, for example, be found in Beck et al. [18, Proposition 2.7].

**Proposition 17.4.1.** *Let $d \in \mathbb{N}$, $T, \rho \in (0, \infty)$, $\varrho = \sqrt{2\rho T}$, $a \in \mathbb{R}$, $b \in (a, \infty)$, let $\varphi\colon \mathbb{R}^{d} \rightarrow \mathbb{R}$ be a function, let $u \in C^{1,2}([0,T] \times \mathbb{R}^{d}, \mathbb{R})$ have at most polynomially growing partial derivatives, assume for all $t \in [0,T]$, $x \in \mathbb{R}^{d}$ that $u(0,x) = \varphi(x)$ and*

$$\left( \frac{\partial u}{\partial t} \right)(t,x) = \rho \left( \Delta_{x}u \right)(t,x),$$

*let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $\mathcal{W}\colon \Omega \rightarrow \mathbb{R}^{d}$ be a standard normal random variable, let $\mathcal{X}\colon \Omega \rightarrow [a,b]^{d}$ be a continuously uniformly distributed random variable, and assume that $\mathcal{W}$ and $\mathcal{X}$ are independent. Then*

- * (i) it holds that $\varphi\colon \mathbb{R}^{d} \rightarrow \mathbb{R}$ is twice continuously differentiable with at most polynomially growing partial derivatives,*
- * (ii) there exists a unique continuous function $U\colon [a,b]^{d} \rightarrow \mathbb{R}$ such that

$$\mathbb{E}\left[ |\varphi(\varrho\mathcal{W} + \mathcal{X}) - U(\mathcal{X})|^{2} \right] = \inf_{v \in C([a,b]^{d}, \mathbb{R})} \mathbb{E}\left[ |\varphi(\varrho\mathcal{W} + \mathcal{X}) - v(\mathcal{X})|^{2} \right],$$

*and*
