
This establishes item (ii). The proof of Proposition 6.3.11 is thus completed. $\square$

## 6.3.3.3 Comparison of the convergence speeds of GD optimization with and without momentum

In this subsection we provide in Corollary 6.3.13 below a comparison between the convergence speeds of the plain-vanilla **GD** optimization method and the momentum **GD** optimization method. Our proof of Corollary 6.3.13 employs the auxiliary and elementary estimate in Lemma 6.3.12 below, the refined error analysis for the plain-vanilla **GD** optimization method in Section 6.3.3.1 above (see Lemma 6.3.7 and Lemma 6.3.8 in Section 6.3.3.1), as well as the error analysis for the momentum **GD** optimization method in Section 6.3.3.2 above (see Proposition 6.3.11 in Section 6.3.3.2).

**Lemma 6.3.12** (Comparison of the convergence rates of the **GD** optimization method and the momentum **GD** optimization method). *Let* $\mathcal{K}, \kappa \in (0, \infty)$ *satisfy* $\kappa < \mathcal{K}$. *Then*

$$\frac{\sqrt{\mathcal{K}}-\sqrt{\kappa}}{\sqrt{\mathcal{K}}+\sqrt{\kappa}}<\frac{\mathcal{K}-\kappa}{\mathcal{K}+\kappa}. \qquad \qquad \qquad \qquad \qquad \qquad \qquad (6.294)$$

*Proof of Lemma 6.3.12.* *Note that the fact that* $\mathcal{K}-\kappa>0<2\sqrt{\mathcal{K}\kappa}$ *ensures that*

$$\frac{\sqrt{\mathcal{K}}-\sqrt{\kappa}}{\sqrt{\mathcal{K}}+\sqrt{\kappa}}=\frac{(\sqrt{\mathcal{K}}-\sqrt{\kappa})(\sqrt{\mathcal{K}}+\sqrt{\kappa})}{(\sqrt{\mathcal{K}}+\sqrt{\kappa})^{2}}=\frac{\mathcal{K}-\kappa}{\mathcal{K}+2\sqrt{\mathcal{K}\kappa}+\kappa}<\frac{\mathcal{K}-\kappa}{\mathcal{K}+\kappa}. \qquad (6.295)$$

*The proof of Lemma 6.3.12 is thus completed.* $\square$

**Corollary 6.3.13** (Convergence speed comparisons between the **GD** optimization method and the momentum **GD** optimization method). *Let* $\mathbf{d} \in \mathbb{N}$, $\kappa, \mathcal{K}, \lambda_{1}, \lambda_{2}, \ldots, \lambda_{\mathbf{d}} \in (0, \infty)$, $\boldsymbol{\xi}=\left(\xi_{1}, \ldots, \xi_{\mathbf{d}}\right)$, $\vartheta=\left(\vartheta_{1}, \ldots, \vartheta_{\mathbf{d}}\right) \in \mathbb{R}^{\mathbf{d}}$ *satisfy* $\kappa=\min \left\{\lambda_{1}, \lambda_{2}, \ldots, \lambda_{\mathbf{d}}\right\}<\max \left\{\lambda_{1}, \lambda_{2}, \ldots, \lambda_{\mathbf{d}}\right\}=\mathcal{K}$, *let* $\mathscr{L}: \mathbb{R}^{\mathbf{d}} \rightarrow \mathbb{R}$ *satisfy for all* $\boldsymbol{\theta}=\left(\theta_{1}, \ldots, \theta_{\mathbf{d}}\right) \in \mathbb{R}^{\mathbf{d}}$ *that*

$$\mathscr{L}(\boldsymbol{\theta})=\frac{1}{2}\left[\sum_{i=1}^{\mathbf{d}} \lambda_{i}\left|\theta_{i}-\vartheta_{i}\right|^{2}\right], \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad (6.296)$$

*for every* $\gamma \in (0, \infty)$ *let* $\Theta^{\gamma}: \mathbb{N}_{0} \rightarrow \mathbb{R}^{\mathbf{d}}$ *satisfy for all* $n \in \mathbb{N}$ *that*

$$\Theta_{0}^{\gamma}=\boldsymbol{\xi} \quad \quad \text { and } \quad \quad \Theta_{n}^{\gamma}=\Theta_{n-1}^{\gamma}-\gamma\left(\nabla \mathscr{L}\right)\left(\Theta_{n-1}^{\gamma}\right), \qquad \qquad \qquad (6.297)$$

*and let* $\mathcal{M}: \mathbb{N}_{0} \cup\{-1\} \rightarrow \mathbb{R}^{\mathbf{d}}$ *satisfy for all* $n \in \mathbb{N}$ *that* $\mathcal{M}_{-1}=\mathcal{M}_{0}=\boldsymbol{\xi}$ *and*

$$\mathcal{M}_{n}=\mathcal{M}_{n-1}-\frac{4}{\left(\sqrt{\mathcal{K}}+\sqrt{\kappa}\right)^{2}}\left(\nabla \mathscr{L}\right)\left(\mathcal{M}_{n-1}\right)+\left[\frac{\sqrt{\mathcal{K}}-\sqrt{\kappa}}{\sqrt{\mathcal{K}}+\sqrt{\kappa}}\right]^{2}\left(\mathcal{M}_{n-1}-\mathcal{M}_{n-2}\right). \qquad (6.298)$$

*Then*

- (i) there exist $\gamma, C \in (0,\infty)$ such that for all $n \in \mathbb{N}_{0}$ it holds that $\|\Theta_n^\gamma - \vartheta\|_2 \le C\big[\frac{\mathcal{K}-\sqrt{\mathcal{K}\kappa}}{\mathcal{K}+\sqrt{\mathcal{K}\kappa}}\big]^n,$ (6.299)
- (ii) it holds for all $\gamma \in (0,\infty), n \in \mathbb{N}_{0}$ that $\|\Theta_n^\gamma - \vartheta\|_2 \ge \min\{[|\xi_1-\vartheta_1|, \dots, |\xi_d-\vartheta_d|]\big[\frac{\kappa}{\mathcal{K}}\big]^{n/2}\}$, (6.300)
- (iii) for every $\varepsilon \in (0,\infty)$ there exists $C \in (0,\infty)$ such that for all $n \in \mathbb{N}_{0}$ it holds that $\|\mathcal{M}_n - \vartheta\|_2 \le C \big[\frac{\sqrt{\mathcal{K}}-\sqrt{\kappa}}{\sqrt{\mathcal{K}}+\sqrt{\kappa}} + \varepsilon\big]^n,$ (6.301)
- (iv) it holds that $\frac{\sqrt{\mathcal{K}}-\sqrt{\kappa}}{\sqrt{\mathcal{K}}+\sqrt{\kappa}} < \frac{\mathcal{K}-\kappa}{\mathcal{K}+\kappa}$ (cf. Definition 3.3.4).

*Proof of Corollary 6.3.13.* First, note that Lemma 6.3.7 proves item (i). Next observe that Lemma 6.3.8 establishes item (ii). In addition, note that Proposition 6.3.11 proves item (iii). Finally, observe that Lemma 6.3.12 establishes item (iv). The proof of Corollary 6.3.13 is thus complete. $\square$

Corollary 6.3.13 above, roughly speaking, shows in the case of the considered class of quadratic objective functions that the momentum GD optimization method in (6.298) outperforms the classical plain-vanilla GD optimization method (and, in particular, the classical plain-vanilla GD optimization method in (6.224) in Lemma 6.3.7 above) provided that the parameters $\lambda_{1}, \lambda_{2}, \ldots, \lambda_{d} \in (0,\infty)$ in the objective function in (6.296) satisfy the assumption that

$$\min\{\lambda_1, \dots, \lambda_d\} < \max\{\lambda_1, \dots, \lambda_d\}. \qquad (6.302)$$

The next elementary result, Lemma 6.3.14 below, demonstrates that the momentum GD optimization method in (6.298) and the plain-vanilla GD optimization method in (6.224) in Lemma 6.3.7 above coincide in the case where $\min\{\lambda_1, \dots, \lambda_d\} = \max\{\lambda_1, \dots, \lambda_d\}$.

**Lemma 6.3.14** (Concurrence of the GD optimization method and the momentum GD optimization method). Let $\vartheta \in \mathbb{R}^{d}$, $\xi \in \mathbb{R}^{d}$, $\alpha \in (0, \infty)$, let $\mathscr{L}: \mathbb{R}^{d} \rightarrow \mathbb{R}$ satisfy for all $\theta \in \mathbb{R}^{d}$ that

$$\mathscr{L}(\theta) = \frac{\alpha}{2}\|\theta - \vartheta\|^2_2, \qquad (6.303)$$

let $\Theta: \mathbb{N}_0 \rightarrow \mathbb{R}^{d}$ satisfy for all $n \in \mathbb{N}$ that

$$\Theta_0 = \xi \quad \text{and} \quad \Theta_n = \Theta_{n-1} - \frac{2}{(\alpha+\alpha)}\nabla \mathscr{L})(\Theta_{n-1}), \qquad (6.304)$$

and let $\boldsymbol{M} : \mathbb{N}_0 \cup \{-1\} \to \mathbb{R}^{d}$ satisfy for all $n \in \mathbb{N}$ that $\boldsymbol{M}_{-1} = \boldsymbol{M}_0 = \boldsymbol{\xi}$ and

$$\boldsymbol{M}_{n} = \boldsymbol{M}_{n-1} - \frac{4}{(\sqrt{\alpha} + \sqrt{\alpha})^2}(\nabla\mathcal{L})(\boldsymbol{M}_{n-1}) + \left[\frac{\sqrt{\alpha} - \sqrt{\alpha}}{\sqrt{\alpha} + \sqrt{\alpha}}\right]^2 (\boldsymbol{M}_{n-1} - \boldsymbol{M}_{n-2}) \qquad (6.305)$$

(cf. Definition 3.3.4). Then

- (i) it holds that $\boldsymbol{M}|_{\mathbb{N}_0} : \mathbb{N}_0 \to \mathbb{R}^{d}$ is the momentum GD process for the objective function $\mathcal{L}$ with learning rates $\mathbb{N} \ni n \mapsto 1/\alpha \in [0, \infty)$, momentum decay factors $\mathbb{N} \ni n \mapsto 0 \in [0, 1]$, and initial value $\boldsymbol{\xi}$,
- (ii) it holds for all $n \in \mathbb{N}_0$ that $\boldsymbol{M}_n = \boldsymbol{\Theta}_n$, and
- (iii) it holds for all $n \in \mathbb{N}$ that $\boldsymbol{\Theta}_n = \boldsymbol{\vartheta} = \boldsymbol{M}_n$

(cf. Definition 6.3.1).

Proof of Lemma 6.3.14. First, note that (6.305) implies that for all $n \in \mathbb{N}$ it holds that

$$\boldsymbol{M}_n = \boldsymbol{M}_{n-1} - \frac{4}{(2\sqrt{\alpha})^2}(\nabla\mathcal{L})(\boldsymbol{M}_{n-1}) = \boldsymbol{M}_{n-1} - \frac{1}{\alpha}(\nabla\mathcal{L})(\boldsymbol{M}_{n-1}). \qquad (6.306)$$

Combining this with the assumption that $\boldsymbol{M}_0 = \boldsymbol{\xi}$ establishes item (i). Next note that (6.304) ensures that for all $n \in \mathbb{N}$ it holds that

$$\boldsymbol{\Theta}_n = \boldsymbol{\Theta}_{n-1} - \frac{1}{\alpha}(\nabla\mathcal{L})(\boldsymbol{\Theta}_{n-1}). \qquad (6.307)$$

Combining this with (6.306) and the assumption that $\boldsymbol{\Theta}_0 = \boldsymbol{\xi} = \boldsymbol{M}_0$ proves item (ii). Furthermore, observe that Lemma 5.6.4 assures that for all $\boldsymbol{\theta} \in \mathbb{R}^{d}$ it holds that

$$(\nabla\mathcal{L})(\boldsymbol{\theta}) = \frac{\alpha}{2}(2(\boldsymbol{\theta} - \boldsymbol{\vartheta})) = \alpha(\boldsymbol{\theta} - \boldsymbol{\vartheta}). \qquad (6.308)$$

Next we claim that for all $n \in \mathbb{N}$ it holds that

$$\boldsymbol{\Theta}_n = \boldsymbol{\vartheta}. \qquad (6.309)$$

We now prove (6.309) by induction on $n \in \mathbb{N}$. For the base case $n = 1$ note that (6.307) and (6.308) imply that

$$\boldsymbol{\Theta}_1 = \boldsymbol{\Theta}_0 - \frac{1}{\alpha}(\nabla\mathcal{L})(\boldsymbol{\Theta}_0) = \boldsymbol{\xi} - \frac{1}{\alpha}(\alpha(\boldsymbol{\xi} - \boldsymbol{\vartheta})) = \boldsymbol{\xi} - (\boldsymbol{\xi} - \boldsymbol{\vartheta}) = \boldsymbol{\vartheta}. \qquad (6.310)$$

This establishes (6.309) in the base case $n = 1$. For the induction step observe that (6.307) and (6.308) assure that for all $n \in \mathbb{N}$ with $\boldsymbol{\Theta}_n = \boldsymbol{\vartheta}$ it holds that

$$\boldsymbol{\Theta}_{n+1} = \boldsymbol{\Theta}_n - \frac{1}{\alpha}(\nabla\mathcal{L})(\boldsymbol{\Theta}_n) = \boldsymbol{\vartheta} - \frac{1}{\alpha}(\alpha(\boldsymbol{\vartheta} - \boldsymbol{\vartheta})) = \boldsymbol{\vartheta}. \qquad (6.311)$$

Induction thus proves (6.309). Combining (6.309) and item (ii) establishes item (iii). The proof of Lemma 6.3.14 is thus complete. $\square$
