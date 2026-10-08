*Proof of Corollary 5.6.3.* Note that Proposition 5.6.2 and (5.106) establish (5.107). The proof of Corollary 5.6.3 is thus complete. $\square$

# **5.6.3 On Lyapunov-type functions and coercivity-type conditions**

**Lemma 5.6.4** *(Derivate of the standard norm).* Let $\mathfrak{d} \in \mathbb{N}$, $\vartheta \in \mathbb{R}^{\mathfrak{d}}$ and let $V: \mathbb{R}^{\mathfrak{d}} \to \mathbb{R}$ satisfy for all $\theta \in \mathbb{R}^{\mathfrak{d}}$ that

$V(\theta) = \lVert \theta - \vartheta \rVert_{2}^{2}$ (5.108)

*(cf. Definition 3.3.4).* Then it holds for all $\theta \in \mathbb{R}^{\mathfrak{d}}$ that $V \in C^{\infty}(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})$ and

$(\nabla V)(\theta) = 2(\theta - \vartheta)$. (5.109)

*Proof of Lemma 5.6.4.* Throughout this proof, let $\vartheta_{1}, \vartheta_{2}, \ldots, \vartheta_{\mathfrak{d}} \in \mathbb{R}$ satisfy $\vartheta = (\vartheta_{1}, \vartheta_{2}, \ldots, \vartheta_{\mathfrak{d}})$. Note that the fact that for all $\theta = (\theta_{1}, \theta_{2}, \ldots, \theta_{\mathfrak{d}}) \in \mathbb{R}^{\mathfrak{d}}$ it holds that

$V(\theta) = \sum_{i=1}^{\mathfrak{d}}(\theta_{i} - \vartheta_{i})^{2}$ (5.110)

implies that for all $\theta = (\theta_{1}, \theta_{2}, \ldots, \theta_{\mathfrak{d}}) \in \mathbb{R}^{\mathfrak{d}}$ it holds that $V \in C^{\infty}(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})$ and

$(\nabla V)(\theta) = \begin{pmatrix} \frac{\partial V}{\partial \theta_{1}}(\theta) \\ \vdots \\ \frac{\partial V}{\partial \theta_{\mathfrak{d}}}(\theta) \end{pmatrix} = \begin{pmatrix} 2(\theta_{1} - \vartheta_{1}) \\ \vdots \\ 2(\theta_{\mathfrak{d}} - \vartheta_{\mathfrak{d}}) \end{pmatrix} = 2(\theta - \vartheta).$ (5.111)

The proof of Lemma 5.6.4 is thus complete. $\square$

**Corollary 5.6.5** *(On quadratic Lyapunov-type functions and coercivity-type conditions).* Let $\mathfrak{d} \in \mathbb{N}$, $c \in \mathbb{R}$, $T \in (0, \infty)$, $\vartheta \in \mathbb{R}^{\mathfrak{d}}$, let $O \subseteq \mathbb{R}^{\mathfrak{d}}$ be open, let $\mathcal{L}: C^{1}(O, \mathbb{R})$ satisfy for all $\theta \in O$ that

$\langle \theta - \vartheta, (\nabla \mathcal{L})(\theta) \rangle \geq c \lVert \theta - \vartheta \rVert_{2}^{2}$, (5.112)

and let $\Theta \in C([0, T], O)$ satisfy for all $t \in [0, T]$ that $\Theta_{t} = \Theta_{0} - \int_{0}^{t}(\nabla \mathcal{L})(\Theta_{s}) \, \mathrm{d}s$ *(cf. Definitions 1.4.7 and 3.3.4).* Then it holds for all $t \in [0, T]$ that

$\lVert \Theta_{t} - \vartheta \rVert_{2} \leq e^{-ct} \lVert \Theta_{0} - \vartheta \rVert_{2}$. (5.113)

*Proof of Corollary 5.6.5.* Throughout this proof, let $\mathcal{F}: O \to \mathbb{R}^{\mathfrak{d}}$ satisfy for all $\theta \in O$ that

$\mathcal{F}(\theta) = -(\nabla \mathcal{L})(\theta)$ (5.114)

and let $V: O \to \mathbb{R}$ satisfy for all $\theta \in O$ that

$V(\theta) = \lVert \theta - \vartheta \rVert_{2}^{2}$, (5.115)