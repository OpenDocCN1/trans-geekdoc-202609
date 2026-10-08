the function which satisfies for all $x \in \mathbb{R}^{d}$ with

$\min \left\{ \int_{\mathbb{R}^{d}} \max \left\{ 0, f(x-y)g(y) \right\} \, \mathrm{d}y, -\int_{\mathbb{R}^{d}} \min \left\{ 0, f(x-y)g(y) \right\} \, \mathrm{d}y \right\} < \infty$ (17.55)

that

$(f \otimes g)(x) = \int_{\mathbb{R}^{d}} f(x-y)g(y) \, \mathrm{d}y$. (17.56)

# Exercise 17.3.1.

Let $d \in \mathbb{N}$, $T \in (0, \infty)$, for every $\sigma \in (0, \infty)$ let $\gamma_{\sigma}: \mathbb{R}^{d} \to \mathbb{R}$ satisfy for all $x \in \mathbb{R}^{d}$ that

$\gamma_{\sigma}(x) = (2 \pi \sigma^{2})^{-\frac{d}{2}} \exp \left( \frac{-\|x\|_{2}^{2}}{2 \sigma^{2}} \right)$, (17.57)

and for every $\rho \in (0, \infty)$, $\varphi \in C^{2}\left( \mathbb{R}^{d}, \mathbb{R} \right)$ with $\sup_{x \in \mathbb{R}^{d}} \left[ \sum_{i,j=1}^{d} \left( |\varphi(x)| + \left| \left( \frac{\partial}{\partial x_{i}} \varphi \right)(x) \right| + \left| \left( \frac{\partial^{2}}{\partial x_{i} \partial x_{j}} \varphi \right)(x) \right| \right) \right] < \infty$ let $u_{\rho, \varphi}: [0, T] \times \mathbb{R}^{d} \to \mathbb{R}$ satisfy for all $t \in (0, T]$, $x \in \mathbb{R}^{d}$ that

$u_{\rho, \varphi}(0, x) = \varphi(x) \quad \text{and} \quad u_{\rho, \varphi}(t, x) = (\varphi \otimes \gamma_{\sqrt{2 \rho t}})(x)$ (17.58)

(cf. Definitions 3.3.4 and 17.3.8). Prove or disprove the following statement: For all $\rho \in (0, \infty)$, $\varphi \in C^{2}\left( \mathbb{R}^{d}, \mathbb{R} \right)$ with $\sup_{x \in \mathbb{R}^{d}} \left[ \sum_{i,j=1}^{d} \left( |\varphi(x)| + \left| \left( \frac{\partial}{\partial x_{i}} \varphi \right)(x) \right| + \left| \left( \frac{\partial^{2}}{\partial x_{i} \partial x_{j}} \varphi \right)(x) \right| \right) \right] < \infty$ it holds for all $t \in (0, T)$, $x \in \mathbb{R}^{d}$ that $u_{\rho, \varphi} \in C^{1,2}\left( [0, T] \times \mathbb{R}^{d}, \mathbb{R} \right)$ and

$\left( \frac{\partial u_{\rho, \varphi}}{\partial t} \right)(t, x) = \rho \left( \Delta_{x} u_{\rho, \varphi} \right)(t, x)$. (17.59)

# Exercise 17.3.2.

Prove or disprove the following statement: For every $x \in \mathbb{R}$ it holds that

$e^{-x^{2}/2} = \frac{1}{\sqrt{2 \pi}} \left[ \int_{\mathbb{R}} e^{-t^{2}/2} e^{-ixt} \, \mathrm{d}t \right]$. (17.60)

# Exercise 17.3.3.

Let $d \in \mathbb{N}$, $T \in (0, \infty)$, for every $\sigma \in (0, \infty)$ let $\gamma_{\sigma}: \mathbb{R}^{d} \to \mathbb{R}$ satisfy for all $x \in \mathbb{R}^{d}$ that

$\gamma_{\sigma}(x) = (2 \pi \sigma^{2})^{-\frac{d}{2}} \exp \left( \frac{-\|x\|_{2}^{2}}{2 \sigma^{2}} \right)$, (17.61)

for every $\varphi \in C^{2}\left( \mathbb{R}^{d}, \mathbb{R} \right)$ with $\sup_{x \in \mathbb{R}^{d}} \left[ \sum_{i,j=1}^{d} \left( |\varphi(x)| + \left| \left( \frac{\partial}{\partial x_{i}} \varphi \right)(x) \right| + \left| \left( \frac{\partial^{2}}{\partial x_{i} \partial x_{j}} \varphi \right)(x) \right| \right) \right] < \infty$ let $u_{\varphi}: [0, T] \times \mathbb{R}^{d} \to \mathbb{R}$ satisfy for all $t \in (0, T]$, $x \in \mathbb{R}^{d}$ that

$u_{\varphi}(0, x) = \varphi(x) \quad \text{and} \quad u_{\varphi}(t, x) = (\varphi \otimes \gamma_{\sqrt{2t}})(x)$, (17.62)

and for every $i=(i_{1}, \dots, i_{d}) \in \mathbb{N}^{d}$ let $\psi_{i}: \mathbb{R}^{d} \to \mathbb{R}$ satisfy for all $x=(x_{1}, \dots, x_{d}) \in \mathbb{R}^{d}$ that

$\psi_{i}(x) = 2^{\frac{d}{2}} \left[ \prod_{k=1}^{d} \sin(i_{k} \pi x_{k}) \right] (17.63)$

(cf. Definitions 3.3.4 and 17.3.8). Prove or disprove the following statement: For all $i=(i_{1}, \dots, i_{d}) \in \mathbb{N}^{d}$, $t \in [0, T]$, $x \in \mathbb{R}^{d}$ it holds that

$u_{\psi_{i}}(t, x) = \exp \left( -\pi^{2} \left[ \sum_{k=1}^{d} |i_{k}|^{2} t \right] \right) \psi_{i}(x)$. (17.64)