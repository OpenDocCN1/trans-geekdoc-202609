# Corollary 9.12.5. *Let* $\mathfrak{d} \in \mathbb{N}$, $\mathfrak{c} \in [0, 1]$,
$\varepsilon, L, \mathfrak{C} \in (0, \infty)$, $\alpha \in (0, 1)$, $\gamma \in (0, L^{-1}]$,
$\vartheta \in \mathbb{R}^{\mathfrak{d}}$, *let* $\mathbb{B} \subseteq \mathbb{R}^{\mathfrak{d}}$ *satisfy*
$\mathbb{B} = \{\theta \in \mathbb{R}^{\mathfrak{d}} : \|\theta - \vartheta\|_2 \leq \varepsilon\}$, *let*
$\mathcal{L} \in C^{1}(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})$ *satisfy*
$\mathcal{L}\|_{\mathbb{B}} \in \mathcal{C}^{1}(\mathbb{B}, \mathbb{R})$, *let*
$\mathcal{G}: \mathbb{R}^{\mathfrak{d}} \to \mathbb{R}^{\mathfrak{d}}$ *satisfy for all*
$\theta \in \mathbb{B}$ *that* $\mathcal{G}(\theta) = (\nabla \mathcal{L})(\theta)$, *assume for all*
$\theta_1, \theta_2 \in \mathbb{B}$ *that*

$$\|\mathcal{G}(\theta_1) - \mathcal{G}(\theta_2)\|_2 \leq L \|\theta_1 - \theta_2\|_2,$$ (9.249)

*let* $\Theta = (\Theta_n)_{n \in \mathbb{N}_0}$, $\mathbb{N}_0 \to \mathbb{R}^{\mathfrak{d}}$ *satisfy for all*
$n \in \mathbb{N}_0$ *that*

$$\Theta_{n+1} = \Theta_n - \gamma \mathcal{G}(\Theta_n),$$ (9.250)

*and assume for all* $\theta \in \mathbb{B}$ *that*

$$\begin{aligned}
& \left[\mathcal{L}(\theta) - \mathcal{L}(\vartheta)\right]^\alpha \leq \mathfrak{C}\|\mathcal{G}(\theta)\|_2, 
\ \ \mathfrak{c} = \left|\mathcal{L}(\Theta_0) - \mathcal{L}(\vartheta)\right|,
\ \ 2\mathfrak{C}(1-\alpha)^{-1} \mathfrak{c}^{1-\alpha} + \|\Theta_0 - \vartheta\|_2 
\leq \frac{\varepsilon}{\gamma L^{+1}},
\end{aligned}$$ (9.251)

*and* $\mathcal{L}(\theta) \geq \mathcal{L}(\vartheta)$. *Then there exists*
$\psi \in \mathcal{L}^{-1}(\{\mathcal{L}(\vartheta)\}) \cap \mathcal{G}^{-1}(\{0\})$ *such that for all*
$n \in \mathbb{N}_0$ *it holds that* $\Theta_n \in \mathbb{B}$, *0* $\leq$ *L(Theta-n)*
*minus* *L(psi)* $\leq (2+\mathfrak{C}^{-2}\gamma n)^{-1}$, *and*

$$\|\Theta_n - \psi\|_2 \leq \sum_{k=n}^{\infty} \|\Theta_{k+1} - \Theta_k\|_2 
\leq 2^{\alpha} \mathfrak{C}(1-\alpha)^{-1}(2+\mathfrak{C}^{-2}\gamma n)^{\alpha-1}.$$ (9.252)

*Proof of Corollary 9.12.5.* *Observe that the fact that*
$\mathcal{L}(\vartheta) = \inf_{\theta \in \mathbb{B}} \mathcal{L}(\theta)$ *ensures that*
$\mathcal{G}(\vartheta) = (\nabla \mathcal{L})(\vartheta) = 0$ *and*
$\inf_{n \in \{m \in \mathbb{N}_0: \ \forall k \in \mathbb{N}_0 \cap [0,m]:
\ \Theta_k \in \mathbb{B}\}} \mathcal{L}(\Theta_n) \geq \mathcal{L}(\vartheta)$. *Combining this
with Proposition 9.12.4 ensures that there exists*
$\psi \in \mathcal{L}^{-1}(\{\mathcal{L}(\vartheta)\}) \cap \mathcal{G}^{-1}(\{0\})$ *such that*

+   (I) *it holds for all* $n \in \mathbb{N}_0$ *that* $\Theta_n \in \mathbb{B}$,
(II) *it holds for all* $n \in \mathbb{N}_0$ *that* $0 \leq \mathcal{L}(\Theta_n) - \mathcal{L}(\psi) \leq \frac{2\mathfrak{C}^2 \mathfrak{c}^2}{\mathbb{I}_{\{0\}}(\mathfrak{c})+\mathfrak{c}^{2\alpha}n\gamma+2\mathfrak{C}^2\mathfrak{c}}$, *and*
(III) *it holds for all* $n \in \mathbb{N}_0$ *that*

$$\begin{aligned}
& \|\Theta_n - \psi\|_2 \leq \sum_{k=n}^{\infty} \|\Theta_{k+1} - \Theta_k\|_2
\leq \frac{2\mathfrak{C}|\mathcal{L}(\Theta_n) - \mathcal{L}(\psi)|^{1-\alpha}}{1-\alpha}\\
& \quad \leq \frac{2^{2-\alpha}\mathfrak{C}^{3-2\alpha}\mathfrak{c}^{2-2\alpha}}{(1-\alpha)(\mathbb{I}_{\{0\}}(\mathfrak{c})+\mathfrak{c}^{2\alpha}n\gamma+2\mathfrak{C}^2\mathfrak{c})^{1-\alpha}}.
\end{aligned}$$ (9.253)

*Note that item (II) and the assumption that* $\mathfrak{c} \leq 1$ *establish for all*
$n \in \mathbb{N}_0$ *that*

$$0 \leq \mathcal{L}(\Theta_n) - \mathcal{L}(\psi) \leq
2\mathfrak{C}^2(\mathfrak{C}^2\mathbb{I}_{\{0\}}(\mathfrak{c})+
\mathfrak{c}^{-2}\mathfrak{C}^{2\alpha}n\gamma+2\mathfrak{c})^{-1} \leq
(2+\mathfrak{C}^{-2}\gamma n)^{-1}.$$ (9.254)

*This and item (III) demonstrate for all* $n \in \mathbb{N}_0$ *that*

$$\|\Theta_n - \psi\|_2 \leq \sum_{k=n}^{\infty} \|\Theta_{k+1} - \Theta_k\|_2
\leq \frac{2\mathfrak{C}|\mathcal{L}(\Theta_n) - \mathcal{L}(\psi)|^{1-\alpha}}{1-\alpha}
\leq \left[\frac{2^{2-\alpha}\mathfrak{C}}{1-\alpha}\right]
(2+\mathfrak{C}^{-2}\gamma n)^{\alpha-1}.$$ (9.255)

*The proof of Corollary 9.12.5 is thus complete.*

384