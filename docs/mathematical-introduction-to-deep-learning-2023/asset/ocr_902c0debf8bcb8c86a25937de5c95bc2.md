*is $\mathcal{F}/\mathcal{B}([0, \infty])$-measurable*

*(cf. Definition 4.4.1).*

*Proof of Lemma 15.1.1*. Throughout this proof let $\Xi: \Omega \to \mathbb{R}^\mathbf{d}$ satisfy for all $\omega \in \Omega$ that

```
$$
\Xi(\omega) = \Theta_{\mathbf{k}(\omega)}(\omega).
$$
```

Observe that the assumption that $\Theta_{k,n}: \Omega \to \mathbb{R}^\mathbf{d}$, $k, n \in \mathbb{N}_0$, and $\mathbf{k}: \Omega \to (\mathbb{N}_0)^2$ are random variables implies that for all $U \in \mathcal{B}(\mathbb{R}^\mathbf{d})$ it holds that

```
$$
\begin{aligned}
&\Xi^{-1}(U) = \{\omega \in \Omega: \Xi(\omega) \in U\} = \{\omega \in \Omega: \Theta_{\mathbf{k}(\omega)}(\omega) \in U\} \\
&\quad= \{\omega \in \Omega: [\exists k, n \in \mathbb{N}_0: (\Theta_{k,n}(\omega) \in U \wedge \mathbf{k}(\omega) = (k, n))]\} \\
&\quad= \bigcup_{k=0}^\infty \bigcup_{n=0}^\infty \{\omega \in \Omega: \Theta_{k,n}(\omega) \in U\} \cap \{\omega \in \Omega: \mathbf{k}(\omega) = (k, n)\} \\
&\quad= \bigcup_{k=0}^\infty \bigcup_{n=0}^\infty ([ (\Theta_{k,n})^{-1}(U)] \cap [\mathbf{k}^{-1}(\{(k, n)\})]) \in \mathcal{F}.
\end{aligned}
$$
```

This proves that

```
$$
\Omega \ni \omega \mapsto \Theta_{\mathbf{k}(\omega)}(\omega) \in \mathbb{R}^\mathbf{d}
$$
```

is $\mathcal{F}/\mathcal{B}(\mathbb{R}^\mathbf{d})$-measurable. Furthermore, note that that Corollary 11.3.7 (applied with $a \curvearrowleft \|x\|_\infty$, $b \curvearrowleft \|x\|_\infty$, $u \curvearrowleft u$, $v \curvearrowleft v$, $d \curvearrowleft \mathbf{d}$, $L \curvearrowleft \mathbf{L}$, $l \curvearrowleft 1$ for $x \in \mathbb{R}^\mathbf{d}$ in the notation of Corollary 11.3.7) ensures that for all $\theta, \vartheta \in \mathbb{R}^\mathbf{d}$, $x \in \mathbb{R}^\mathbf{d}$ it holds that

```
$$
\begin{aligned}
&|\mathcal{N}_{u,v}^{\theta,1}(x) - \mathcal{N}_{u,v}^{\vartheta,1}(x)| \le \sup_{y \in [-\|x\|_\infty, \|x\|_\infty]} |0| |\mathcal{N}_{u,v}^{\theta,1}(y) - \mathcal{N}_{u,v}^{\vartheta,1}(y)| \\
&\le \mathbf{L}\max\{1, \|x\|_\infty\} (\|\|\|_\infty + 1)\mathbf{L}\left(\max\{1, \|\theta\|_\infty, \|\vartheta\|_\infty\} \mathbf{L}^{-1}\|\theta - \vartheta\|_\infty\right)
\end{aligned}
$$
```

(cf. Definitions 3.3.4 and 4.4.1). This shows for all $x \in \mathbb{R}^\mathbf{d}$ that

```
$$
\mathbb{R}^\mathbf{d} \ni \theta \mapsto \mathcal{N}_{u,v}^{\theta,1}(x) \in \mathbb{R}
$$
```

is continuous. Moreover, observe that the fact that for all $\theta \in \mathbb{R}^\mathbf{d}$ it holds that $\mathcal{N}_{u,v}^{\theta,1} \in C(\mathbb{R}^\mathbf{d}, \mathbb{R})$ establishes that for all $\theta \in \mathbb{R}^\mathbf{d}$ it holds that $\mathcal{N}_{u,v}^{\theta,1}(x) \in \mathcal{B}(\mathbb{R}^\mathbf{d})/\mathcal{B}(\mathbb{R})$-measurable. This, (15.7), the fact that $(\mathbb{R}^\mathbf{d}, \|\cdot\|_\infty|_{\mathbb{R}^\mathbf{d}})$ is a separable normed $\mathbb{R}$-vector space, and Lemma 11.2.6 prove item (i). Note that item (i) and (15.5) demonstrate that

```
$$
\Omega \times \mathbb{R}^\mathbf{d} \ni (\omega, x) \mapsto \mathcal{N}_{u,v}^{\Theta_{\mathbf{k}(\omega)}(\omega),1}(x) \in \mathbb{R}
$$
```

is $(\mathcal{F} \otimes \mathcal{B}(\mathbb{R}^\mathbf{d}))/\mathcal{B}(\mathbb{R})$-measurable. This implies item (ii). Observe that item (ii) and the assumption that $\mathcal{E}: D \to \mathbb{R}$ is $\mathcal{B}(D)/\mathcal{B}(\mathbb{R})$-measurable ensure that for all $p \in [0, \infty)$ it holds that

```
$$
\Omega \times D \ni (\omega, x) \mapsto (\mathcal{N}_{u,v}^{\Theta_{\mathbf{k}(\omega)}(\omega),1}(x) - \mathcal{E}(x))^p \in [0, \infty)
$$
```

is $(\mathcal{F} \otimes \mathcal{B}(D))/\mathcal{B}([0, \infty))$-measurable. Tonelli's theorem hence establishes item (iii). The proof of Lemma 15.1.1 is thus complete. \qquad \qquad \qquad \square