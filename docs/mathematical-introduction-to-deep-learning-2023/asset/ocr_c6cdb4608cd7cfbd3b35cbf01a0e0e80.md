# **5.7.4**  **Approximation error with respect to the objective function**

**Corollary 5.7.5** (Approximation error with respect to the objective function). Let $\mathfrak{d} \in \mathbb{N}$, $c, L \in (0, \infty)$, $r \in (0, \infty]$, $\vartheta \in \mathbb{R}^{\mathfrak{d}}$, $\mathbb{B} = \{w \in \mathbb{R}^{\mathfrak{d}} : \|w - \vartheta\|_2 \leq r\}$, $\xi \in \mathbb{B}$, $\mathcal{L} \in C^2(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})$ satisfy for all $\theta \in \mathbb{B}$ that

$$(\theta - \vartheta, (\nabla\mathcal{L})(\theta)) \geq c\|\theta - \vartheta\|_2^2 \qquad \text{and} \qquad \|(\nabla\mathcal{L})(\theta)\|_2 \leq L\|\theta - \vartheta\|_2 \tag{5.189}$$
(c.f. Definitions 1.4.7 and 3.3.4). Then

+   (i) there exists a unique continuous function $\Theta : [0, \infty) \to \mathbb{R}^{\mathfrak{d}}$ such that for all $t \in [0, \infty)$ it holds that

$$\Theta_t = \xi - \int_0^t (\nabla\mathcal{L})(\Theta_s) \, \mathrm{d}s, \tag{5.190}$$

+   (ii) it holds that $\{\theta \in \mathbb{B} : \mathcal{L}(\theta) = \inf_{w \in \mathbb{B}} \mathcal{L}(w)\} = \{\vartheta\}$,
(iii) it holds for all $t \in [0, \infty)$ that $\|\Theta_t - \vartheta\|_2 \leq e^{-ct}\|\xi - \vartheta\|_2$, and
(iv) it holds for all $t \in [0, \infty)$ that

$$0 \leq \tfrac{\xi}{2}\|\Theta_t - \vartheta\|_2^2 \leq \mathcal{L}(\Theta_t) - \mathcal{L}(\vartheta) \leq \tfrac{L}{2}\|\Theta_t - \vartheta\|_2^2 \leq \tfrac{L}{2} e^{-2ct}\|\xi - \vartheta\|_2^2. \tag{5.191}$$

*Proof of Corollary 5.7.5.* Theorem 5.7.4 and Lemma 5.6.9 establish items (i), (ii), (iii), and (iv). The proof of Corollary 5.7.5 is thus complete. \qquad $\square$