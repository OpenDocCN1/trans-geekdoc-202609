*Proof of Lemma 7.2.12*. First, observe that the fundamental theorem of calculus ensures that for all $x \in [1, \infty)$ it holds that

$\ln(x) = \ln(x) - \ln(1) = \int_{1}^{x} \frac{1}{t} \mathrm{d}t \geq \int_{1}^{x} \frac{1}{x} \mathrm{d}t = \frac{(x - 1)}{x}$. (7.68)

Furthermore, note that the fundamental theorem of calculus shows that for all $x \in (0, 1]$ it holds that

$\begin{aligned} \ln(x) = \ln(x) - \ln(1) = -(\ln(1) - \ln(x)) &= -\left[ \int_{x}^{1} \frac{1}{t} \mathrm{d}t \right] \\ &= \int_{x}^{1} \left(-\frac{1}{t}\right) \mathrm{d}t \geq \int_{x}^{1} \left(-\frac{1}{x}\right) \mathrm{d}t = (1 - x)\left(-\frac{1}{x}\right) = \frac{(x - 1)}{x}. \end{aligned}$ (7.69)

This and (7.68) prove (7.67). The proof of Lemma 7.2.12 is thus complete. $\square$

**Lemma 7.2.13 (GD fails to converge for a summable sequence of learning rates).** Let $\vartheta \in \mathbb{N}$, $\vartheta' \in \mathbb{R}^{\vartheta}$, $\xi \in \mathbb{R}^{\vartheta} \setminus \{\vartheta\}$, $\alpha \in (0, \infty)$, $(\gamma_n)_{n \in \mathbb{N}} \subseteq [0, \infty) \setminus \{1/\alpha\}$ *satisfy* $\sum_{n=1}^{\infty} \gamma_n < \infty$, let $\mathscr{L} : \mathbb{R}^{\vartheta} \to \mathbb{R}$ *satisfy for all* $\vartheta \in \mathbb{R}^{\vartheta}$ *that*

$\mathscr{L}(\vartheta) = \frac{\alpha}{2}\|\vartheta - \vartheta\|_2^2$, (7.70)

*and let* $\Theta : \mathbb{N}_0 \to \mathbb{R}^{\vartheta}$ *satisfy for all* $n \in \mathbb{N}$ *that* $\Theta_0 = \xi$ *and*

$\Theta_n = \Theta_{n-1} - \gamma_n (\nabla \mathscr{L})(\Theta_{n-1})$. (7.71)

*Then*

+   (i) *it holds for all* $n \in \mathbb{N}_0$ *that*

$\Theta_n - \vartheta = \left[ \prod_{k=1}^{n} (1 - \gamma_k \alpha) \right] (\xi - \vartheta)$, (7.72)

+   (ii) *it holds that*

$\liminf_{n \to \infty} \left[ \prod_{k=1}^{n} |1 - \gamma_k \alpha| \right] > 0$, (7.73)

*and*

+   (iii) *it holds that*

$\liminf_{n \to \infty} \| \Theta_n - \vartheta \|_2 > 0$. (7.74)