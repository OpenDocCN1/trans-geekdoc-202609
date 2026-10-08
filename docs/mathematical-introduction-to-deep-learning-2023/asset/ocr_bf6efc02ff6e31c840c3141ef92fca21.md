# 4.4. Refined ANN approximations results for multi-dimensional functions

Proof of Lemma 4.4.8. Throughout this proof, let $\eta_1, \eta_2, \dots, \eta_d \in \mathbb{R}$ satisfy

$$\pmb{\theta} = (\eta_1, \eta_2, \dots, \eta_d) \tag{4.173}$$

and let $\pmb{\Phi} \in \big(\bigtimes_{i=1}^{L} \mathbb{R}^{l_i \times l_{i-1}} \times \mathbb{R}^{l_L}\big)$ satisfy

$$\boldsymbol{\mathcal{T}}(\pmb{\Phi}) = \big(\eta_1, \eta_2, \dots, \eta_{\mathcal{P}(\Phi)}\big) \tag{4.174}$$

(cf. Definitions 1.3.1 and 1.3.5). Note that Lemma 4.4.7 establishes that there exists $\Psi \in \mathbf{N}$ which satisfies

$$\mathcal{D}(\Psi) = (\mathfrak{l}_0, \mathfrak{l}_1, \dots, \mathfrak{l}_{\ulcorner}), \; \big\| \boldsymbol{\mathcal{T}}(\Psi) \big\|_{\infty} \leq \max \big\{ 1, \big\| \boldsymbol{\mathcal{T}}(\pmb{\Phi}) \big\|_{\infty} \big\}, \; \text{and} \; \mathcal{R}^{\mathbf{N}}_{\mathfrak{T}}(\Psi) = \mathcal{R}^{\mathbf{N}}_{\mathfrak{T}}(\pmb{\Phi}) \tag{4.175}$$

(cf. Definitions 1.2.4, 1.3.4, and 3.3.4). Next let $\vartheta = (\vartheta_1, \vartheta_2, \dots, \vartheta_{\mathfrak{l}}) \in \mathbb{R}^{\mathfrak{l}}$ satisfy

$$\big(\vartheta_1, \vartheta_2, \dots, \vartheta_{\mathcal{P}(\Psi)}\big) = \boldsymbol{\mathcal{T}}(\Psi) \quad \text{and} \quad \forall \, i \in \mathbb{N} \cap \big( \mathcal{P}(\Psi), \pmb{0} + 1 \big): \vartheta_i = 0. \tag{4.176}$$

Observe that (4.173), (4.174), (4.175), and (4.176) show that

$$\big\| \vartheta \big\|_{\infty} = \big\| \boldsymbol{\mathcal{T}}(\Psi) \big\|_{\infty} \leq \max \big\{ 1, \big\| \boldsymbol{\mathcal{T}}(\pmb{\Phi}) \big\|_{\infty} \big\} \leq \max \big\{ 1, \big\| \pmb{\theta} \big\|_{\infty} \big\}. \tag{4.177}$$

Furthermore, note that Lemma 4.4.2 and (4.174) ensure that for all $x \in \mathbb{R}^{l_0}$ it holds that

$$\big( \mathcal{L}^{\theta, (l_0, l_1, \dots, l_L)}_{\infty, \infty} \big)(x) = \big( \mathcal{L}^{\boldsymbol{\mathcal{T}}(\Psi), \mathcal{D}(\Psi)}_{\infty, \infty} \big)(x) = \big( \mathcal{R}^{\mathbf{N}}_{\mathfrak{T}}(\pmb{\Phi}) \big)(x) \tag{4.178}$$

(cf. Definition 4.4.1). Moreover, observe that Lemma 4.4.2, (4.175), and (4.176) imply that for all $x \in \mathbb{R}^{l_0}$ it holds that

$$\big( \mathcal{L}^{\vartheta, (l_0, l_1, \dots, l_{\ulcorner})}_{\infty, \infty} \big)(x) = \big( \mathcal{L}^{\boldsymbol{\mathcal{T}}(\Psi), \mathcal{D}(\Psi)}_{\infty, \infty} \big)(x) = \big( \mathcal{R}^{\mathbf{N}}_{\mathfrak{T}}(\Psi) \big)(x). \tag{4.179}$$

Combining this and (4.178) with (4.175) and the assumption that $\mathfrak{l}_0 = l_0$ and $\mathfrak{l}_{\ulcorner} = l_L$ demonstrates that

$$\mathcal{L}^{\theta, (l_0, l_1, \dots, l_L)}_{\infty, \infty} = \mathcal{L}^{\vartheta, (l_0, l_1, \dots, l_{\ulcorner})}_{\infty, \infty}. \tag{4.180}$$

Therefore, we obtain that

$$\mathcal{L}^{\theta, (l_0, l_1, \dots, l_L)}_{u, v} = \mathcal{C}_{u, v, l_L} \circ \mathcal{L}^{\theta, (l_0, l_1, \dots, l_L)}_{\infty, \infty} = \mathcal{C}_{u, v, l_{\ulcorner}} \circ \mathcal{L}^{\vartheta, (l_0, l_1, \dots, l_{\ulcorner})}_{\infty, \infty} = \mathcal{L}^{\vartheta, (l_0, l_1, \dots, l_{\ulcorner})}_{u, v} \tag{4.181}$$

(cf. Definition 1.2.10). This and (4.177) prove (4.172). The proof of Lemma 4.4.8 is thus complete.

□

159