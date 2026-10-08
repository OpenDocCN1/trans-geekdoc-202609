
The next result, Corollary 6.1.17 below, combines Proposition 6.1.16 with Proposition 6.1.9 to obtain an error analysis which assumes the conditions in (6.119) and (6.120) in Proposition 6.1.16 above. A result similar to Corollary 6.1.17 can, for instance, be found in Nesterov [303, Theorem 1.2.4].

Corollary 6.1.17 (Error analysis for the GD optimization method under conditions on the Hessian of the objective function). Let \(\boldsymbol{\theta} \in \mathbb{N}\), let \(\| \cdot \|: \mathbb{R}^{d} \times \mathbb{R} \rightarrow \mathbb{R}\) satisfy for all \(A \in \mathbb{R}^{d \times d}\) that \(\|A\|=\sup _{v \in \mathbb{R}^{d}\{0\}} \frac{\|Av\|_{2}}{\|v\|_{2}}\), and let \(\lambda, \alpha \in(0, \infty)\), \(\beta \in[\alpha, \infty)\), \((\gamma_{n})_{n \in \mathbb{N}} \subseteq[0, \frac{4 \alpha}{9 \beta^{2}})\), \(\forall \xi \in \mathbb{R}^{d}\), \(\mathcal{L} \in C^{2}\left(\mathbb{R}^{d}, \mathbb{R}\right)\) satisfy for all \(v, w \in \mathbb{R}^{d}\) that

$$\nabla \mathcal{L}(\vartheta)=0, \quad(\text { Hess } \mathcal{L})(v) - (\text { Hess } \mathcal{L})(w) \leq \lambda \| v-w\|_{2} \quad(6.130) $$

$$\{\mu \in \mathbb{R}: \exists u \in \mathbb{R}^{d}\backslash\{0\} :[(\text { Hess } \mathcal{L})(\vartheta)] u=\mu u\} \subseteq[\alpha, \beta] \quad(6.131) $$

and \(\|\xi-\vartheta\|_{2} \leq \frac{\alpha}{\lambda}\), and let \(\Theta: \mathbb{N}_{0} \rightarrow \mathbb{R}^{d}\) satisfy for all \(n \in \mathbb{N}\) that

\(\Theta_{0}=\xi\) and \(\Theta_{n}=\Theta_{n-1}-\gamma_{n}(\nabla \mathcal{L})(\Theta_{n-1})\) (6.132)

(cf. Definition 3.3.4.) Then

(i) it holds that \(\{\theta \in \mathbb{B}: \mathcal{L}(\theta)=\inf _{w \in \mathbb{B}} \mathcal{L}(w)\}=\{\vartheta\}\),

(ii) it holds for all \(k \in \mathbb{N}\) that \(0 \leq 1-\alpha \gamma_{k}+\frac{9 \beta^{2}(\gamma_{k})^{2}}{4} \leq 1\),

(iii) it holds for all \(n \in \mathbb{N}_{0}\) that
$$\|\Theta_{n}-\vartheta\|_{2} \leq\left[\prod_{k=1}^{n}\left[1-\alpha \gamma_{k}+\frac{9 \beta^{2}(\gamma_{k})^{2}}{4}\right]^{1 / 2}\right]\|\xi-\vartheta\|_{2},$$ (6.133)

and

(iv) it holds for all \(n \in \mathbb{N}_{0}\) that
$$0 \leq \mathcal{L}\left(\Theta_{n}\right)-\mathcal{L}(\vartheta) \leq \frac{3 \beta}{4}\left[\prod_{k=1}^{n}\left[1-\alpha \gamma_{k}+\frac{9 \beta^{2}(\gamma_{k})^{2}}{4}\right]^{2}\right]\|\xi-\vartheta\|_{2}^{2} .$$ (6.134)

Proof of Corollary 6.1.17. Note that (6.130), (6.131), and Proposition 6.1.16 prove that for all \(\theta \in\{w \in \mathbb{R}^{d}:\|w-\vartheta\|_{2} \leq \frac{\alpha}{\lambda}\}\) it holds that

$(\theta-\vartheta, \nabla \mathcal{L}(\theta)) \geq \frac{\alpha}{2} \|\theta-\vartheta\|_{2}^{2} \quad \text{and} \quad \|\nabla \mathcal{L}(\theta)\|_{2} \leq \frac{3 \beta}{2} \|\theta-\vartheta\|_{2} \quad(6.135)$

(cf. Definition 1.4.7.) Combining this, the assumption that

\(\|\xi-\vartheta\|_{2} \leq \frac{\alpha}{\lambda},\) (6.136)

(6.132), and items (iv) and (v) in Proposition 6.1.9 (applied with \(c \sim \frac{\alpha}{2}\), \(L \sim \frac{3 \beta}{2}\), \(r \sim \frac{\alpha}{\lambda}\) in the notation of Proposition 6.1.9) establishes items (i), (ii), (iii), and (iv). The proof of Corollary 6.1.17 is thus complete.

Remark 6.1.18. In Corollary 6.1.17 we establish convergence of the considered GD process under, amongst other things, the assumption that all eigenvalues of the Hessian of \(\mathcal{L}: \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}\) at the local minimum point \(\vartheta\) are strictly positive (see (6.131)). In the situation where \(\mathcal{L}\) is the cost function (integrated loss function) associated to a supervised learning problem in the training of ANNs, this assumption is basically not satisfied. Nonetheless, the convergence analysis for Corollary 6.1.17 can, roughly speaking, also be performed under the essentially (up to the smoothness conditions) more general assumption that there exists \(k \in \mathbb{N}_{0}\) such that the set of local minimum points is locally a smooth \(k\)-dimensional submanifold of \(\mathbb{R}^{\mathfrak{d}}\) and that the rank of the Hessian of \(\mathcal{L}\) on this set of local minimum points locally (at least) \(\mathfrak{d}-k\) (cf. Fehrman et al. [132] for details). In certain situations this essentially generalized assumption has also been shown to be satisfied in the training of ANNs in suitable supervised learning problems (see Jentzen & Riekert [223]).

### 6.1.4.6 Equivalent conditions on the objective function

Lemma 6.1.19. Let \(\mathfrak{d} \in \mathbb{N}\), let \(\langle \cdot, \cdot \rangle: \mathbb{R}^{\mathfrak{d}} \times \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}\) be a scalar product, let \(\| \cdot \|: \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}\) satisfy for all \(v \in \mathbb{R}^{\mathfrak{d}}\) that \(\| v \|=\sqrt{\langle v, v \rangle}\), let \(\gamma \in(0, \infty)\), \(\varepsilon \in(0,1)\), \(r \in(0, \infty)\), \(\vartheta \in \mathbb{R}^{\mathfrak{d}}\), \(\mathbb{B}=\{w \in \mathbb{R}^{\mathfrak{d}}: \| w-\vartheta \| \leq r\}\), and let \(\mathscr{G}: \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}^{\mathfrak{d}}\) satisfy for all \(\theta \in \mathbb{B}\) that

\(\| \theta-\gamma \mathscr{G}(\theta)-\vartheta \| \leq \varepsilon\| \theta-\vartheta \|\). (6.137)

Then it holds for all \(\theta \in \mathbb{B}\) that

$$\begin{gathered}\langle\theta-\vartheta, \mathscr{G}(\theta)\rangle \geq \max \left\{\left\lfloor \frac{1-\varepsilon^{2}}{2 \gamma} \right\rfloor \|\theta-\vartheta\|^{2}, \frac{\gamma}{2}\|\mathscr{G}(\theta)\|^{2}\right\}\\ \geq \min \left\{\frac{1-\varepsilon^{2}}{2 \gamma}, \frac{\gamma}{2}\right\} \max \left\{\|\theta-\vartheta\|^{2},\|\mathscr{G}(\theta)\|^{2}\right\} .\end{gathered}$$ (6.138)

Proof of Lemma 6.1.19. First, note that (6.137) ensures that for all \(\theta \in \mathbb{B}\) it holds that

$$\begin{gathered}\varepsilon^{2}\|\theta-\vartheta\|^{2} \geq\|\theta-\gamma \mathscr{G}(\theta)-\vartheta\|^{2}=\|\left(\theta-\vartheta\right)-\gamma \mathscr{G}(\theta)\|^{2}\\ =\|\theta-\vartheta\|^{2}-2 \gamma\langle\theta-\vartheta, \mathscr{G}(\theta)\rangle+\gamma^{2}\|\mathscr{G}(\theta)\|^{2} .\end{gathered}$$ (6.139)

Hence, we obtain for all \(\theta \in \mathbb{B}\) that

$$\begin{gathered}2 \gamma\langle\theta-\vartheta, \mathscr{G}(\theta)\rangle \geq\left(1-\varepsilon^{2}\right)\|\theta-\vartheta\|^{2}+\gamma^{2}\|\mathscr{G}(\theta)\|^{2}\\ \geq \max \left\{\left(1-\varepsilon^{2}\right)\|\theta-\vartheta\|^{2}, \gamma^{2}\|\mathscr{G}(\theta)\|^{2}\right\} \geq 0 .\end{gathered}$$ (6.140)

This demonstrates that for all \(\theta \in \mathbb{B}\) it holds that

$$\begin{gathered}\langle\theta-\vartheta, \mathscr{G}(\theta)\rangle \geq \frac{1}{2 \gamma} \max \left\{\left(1-\varepsilon^{2}\right)\|\theta-\vartheta\|^{2}, \gamma^{2}\|\mathscr{G}(\theta)\|^{2}\right\}\\ =\max \left\{\left\lfloor \frac{1-\varepsilon^{2}}{2 \gamma} \right\rfloor \|\theta-\vartheta\|^{2}, \frac{\gamma}{2}\|\mathscr{G}(\theta)\|^{2}\right\}\\ \geq \min \left\{\frac{1-\varepsilon^{2}}{2 \gamma}, \frac{\gamma}{2}\right\} \max \left\{\|\theta-\vartheta\|^{2},\|\mathscr{G}(\theta)\|^{2}\right\} .\end{gathered}$$ (6.141)

The proof of Lemma 6.1.19 is thus complete. $\square$

Lemma 6.1.20. Let \(\mathfrak{d} \in \mathbb{N}\), let \(\langle\cdot, \cdot\rangle: \mathbb{R}^{\mathfrak{d}} \times \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}\) be a scalar product, let \(\|\cdot\|: \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}\) satisfy for all \(v \in \mathbb{R}^{\mathfrak{d}}\) that \(\|v\| = \sqrt{\langle v, v\rangle}\), let \(c \in (0, \infty)\), \(r \in (0, \infty)\), \(\vartheta \in \mathbb{R}^{\mathfrak{d}}\), \(\mathbb{B} = \{w \in \mathbb{R}^{\mathfrak{d}} : \|w - \vartheta\| \leq r\}\), and let \(\mathscr{G}: \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}^{\mathfrak{d}}\) satisfy for all \(\theta \in \mathbb{B}\) that

$$\langle\theta - \vartheta, \mathscr{G}(\theta)\rangle \geq c \max \left\{\|\theta - \vartheta\|^2, \|\mathscr{G}(\theta)\|^2\right\} . \tag{6.142}$$

Then it holds for all \(\theta \in \mathbb{B}\) that

$$\langle\theta - \vartheta, \mathscr{G}(\theta)\rangle \geq c \|\theta - \vartheta\|^2 \quad \text { and } \quad \|\mathscr{G}(\theta)\| \leq \frac{1}{c} \|\theta - \vartheta\| . \tag{6.143}$$

*Proof of Lemma 6.1.20.* Observe that (6.142) and the Cauchy-Schwarz inequality assure that for all \(\theta \in \mathbb{B}\) it holds that

$$\|\mathscr{G}(\theta)\|^2 \leq \max \left\{\|\theta - \vartheta\|^2, \|\mathscr{G}(\theta)\|^2\right\} \leq \frac{1}{c}\langle\theta - \vartheta, \mathscr{G}(\theta)\rangle \leq \frac{1}{c}\|\theta - \vartheta\|\|\mathscr{G}(\theta)\| . \tag{6.144}$$

Therefore, we obtain for all \(\theta \in \mathbb{B}\) that

$$\|\mathscr{G}(\theta)\| \leq \frac{1}{c} \|\theta - \vartheta\| . \tag{6.145}$$

Combining this with (6.142) completes the proof of Lemma 6.1.20. \(\square\)

Lemma 6.1.21. Let \(\mathfrak{d} \in \mathbb{N}\), \(c \in (0, \infty)\), \(r \in (0, \infty)\), \(\vartheta \in \mathbb{R}^{\mathfrak{d}}\), \(\mathbb{B} = \{w \in \mathbb{R}^{\mathfrak{d}} : \|w - \vartheta\|_2 \leq r\}\), \(\mathscr{L} \in C^1(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})\) satisfy for all \(\theta \in \mathbb{B}\) that

$$(\theta - \vartheta)\langle\nabla \mathscr{L}\rangle(\theta)\rangle \geq c \|\theta - \vartheta\|_2^2 . \tag{6.146}$$

Then it holds for all \(v \in \mathbb{R}^{\mathfrak{d}}\), \(s, t \in [0, 1]\) with \(\|v\|_2 \leq r\) and \(s \leq t\) that

$$\mathscr{L}(\vartheta + t v) - \mathscr{L}(\vartheta + s v) \geq \frac{c}{2} (t^2 - s^2) \|v\|_2^2 . \tag{6.147}$$

*Proof of Lemma 6.1.21.* First of all, observe that (6.146) implies that for all \(v \in \mathbb{R}^{\mathfrak{d}}\) with \(\|v\|_2 \leq r\) it holds that

$$\langle(\nabla \mathscr{L})(\vartheta + v), v\rangle \geq c \|v\|_2^2, \tag{6.148}$$

The fundamental theorem of calculus hence ensures that for all \(v \in \mathbb{R}^{\mathfrak{d}}\), \(s, t \in [0, 1]\) with \(\|v\|_2 \leq r\) and \(s \leq t\) it holds that

$$\begin{aligned} \mathscr{L}(\vartheta+t v)-\mathscr{L}(\vartheta+s v) & =\left[\mathscr{L}(\vartheta+h v)\right]_{h=s}^{h=t} \\
& =\int_s^t \mathscr{L}^{\prime}(\vartheta+h v) v \, \mathrm{d} h \\
& =\int_s^t \frac{1}{h}\langle(\nabla \mathscr{L})(\vartheta+h v), h v\rangle \, \mathrm{d} h \\
& \geq \int_s^t \frac{c}{h}\|h v\|_2^2 \mathrm{d} h \\
& =c\left[\int_s^t h \, \mathrm{d} h\right]\|v\|_2^2=\frac{c}{2}(t^2-s^2) \|v\|_2^2 .\end{aligned} \tag{6.149}$$

The proof of Lemma 6.1.21 is thus complete. \(\square\)
