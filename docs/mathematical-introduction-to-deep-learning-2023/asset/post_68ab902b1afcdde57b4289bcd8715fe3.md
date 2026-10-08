
# **12.1.4.2 Probability to fall below a barrier**

*Proof of Proposition 12.1.9.* Note that Lemma 12.1.1 ensures that for all $\lambda \in [0,\infty)$ it holds that

$$
\mathbb{P}(X \geq \varepsilon) \leq \mathbb{P}(\lambda X \geq \lambda\varepsilon) = \mathbb{P}(\exp(\lambda X) \geq \exp(\lambda\varepsilon)) \leq \frac{\mathbb{E}[\exp(\lambda X)]}{\exp(\lambda\varepsilon)} = e^{-\lambda\varepsilon}\mathbb{E}[e^{\lambda X}].
$$
(12.19)

The proof of Proposition 12.1.9 is thus complete.

**Corollary 12.1.10.** Let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $X: \Omega \rightarrow \mathbb{R}$ be a random variable, and let $c, \varepsilon \in \mathbb{R}$. Then

$$
\mathbb{P}(X \geq c + \varepsilon) \leq \inf_{\lambda \in [0,\infty)} (e^{-\lambda\varepsilon}\mathbb{M}_{X-c}(\lambda)).
$$
(12.20)

*Proof of Corollary 12.1.10.* Throughout this proof, let $Y: \Omega \rightarrow \mathbb{R}$ satisfy

$$
Y = X - c.
$$
(12.21)

Observe that Proposition 12.1.9 and (12.21) ensure that

$$
\mathbb{P}(X - c \geq \varepsilon) = \mathbb{P}(Y \geq \varepsilon) \leq \inf_{\lambda \in [0,\infty)} (e^{-\lambda\varepsilon}\mathbb{M}_{Y}(\lambda)) = \inf_{\lambda \in [0,\infty)} (e^{-\lambda\varepsilon}\mathbb{M}_{X-c}(\lambda)).
$$
(12.22)

The proof of Corollary 12.1.10 is thus complete.

**Corollary 12.1.11.** Let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $X: \Omega \rightarrow \mathbb{R}$ be a random variable with $\mathbb{E}[|X|] < \infty$, and let $\varepsilon \in \mathbb{R}$. Then

$$
\mathbb{P}(X \geq \mathbb{E}[X] + \varepsilon) \leq \inf_{\lambda \in [0,\infty)} (e^{-\lambda\varepsilon}\mathbb{M}_{X-\mathbb{E}[X]}(\lambda)).
$$
(12.23)

*Proof of Corollary 12.1.11.* Observe that Corollary 12.1.10 (applied with $c \triangleq \mathbb{E}[X]$ in the notation of Corollary 12.1.10) establishes (12.23). The proof of Corollary 12.1.11 is thus complete.

# **12.1.4.2 Probability to fall below a barrier**

**Corollary 12.1.12.** Let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $X: \Omega \rightarrow \mathbb{R}$ be a random variable, and let $c, \varepsilon \in \mathbb{R}$. Then

$$
\mathbb{P}(X \leq c - \varepsilon) \leq \inf_{\lambda \in [0,\infty)} (e^{-\lambda\varepsilon}\mathbb{M}_{c-X}(\lambda)).
$$
(12.24)

*Proof of Corollary 12.1.12.* Throughout this proof, let $\mathfrak{c} \in \mathbb{R}$ satisfy $\mathfrak{c} = -c$ and let $\mathfrak{X}: \Omega \rightarrow \mathbb{R}$ satisfy

$$
\mathfrak{X} = -X.
$$
(12.25)

Observe that Corollary 12.1.10 and (12.25) ensure that

$$
\begin{aligned}
\mathbb{P}(X \leq c - \varepsilon) &= \mathbb{P}(-X \geq -c + \varepsilon) = \mathbb{P}(\mathfrak{X} \geq \mathfrak{c} + \varepsilon) \\
&\leq \inf_{\lambda \in [0,\infty)} (e^{-\lambda\varepsilon}\mathbb{M}_{\mathfrak{X}-\mathfrak{c}}(\lambda)) \\
&= \inf_{\lambda \in [0,\infty)} (e^{-\lambda\varepsilon}\mathbb{M}_{\mathfrak{c}-X}(\lambda)).
\end{aligned}
$$
(12.26)

The proof of Corollary 12.1.12 is thus complete.

# 12.1.4.3 Sums of independent random variables

**Corollary 12.1.13.** *Let* $(\Omega, \mathcal{F}, \mathbb{P})$ *be a probability space, let* $\varepsilon \in \mathbb{R}$, $N \in \mathbb{N}$, *and let* $X_n \colon \Omega \rightarrow \mathbb{R}$, $n \in \{1, 2, \dots, N\}$, *be independent random variables with* $\max_{n \in \{1,2,\dots,N\}} \mathbb{E}[|X_n|] < \infty$. *Then*

$$
\mathbb{P}\left[\left|\sum_{n=1}^N (X_n - \mathbb{E}[X_n])\right| \geq \varepsilon\right] \leq \inf_{\lambda \in [0,\infty)}\left(e^{-\lambda \varepsilon} \prod_{n=1}^N \mathbb{M}_{X_n - \mathbb{E}[X_n]}(\lambda)\right).
$$
(12.27)

*Proof of Corollary 12.1.13.* *Throughout this proof, let* $Y_n \colon \Omega \rightarrow \mathbb{R}$, $n \in \{1,2,\dots,N\}$, *satisfy for all* $n \in \{1,2,\dots,N\}$ *that*

$$
Y_n = X_n - \mathbb{E}[X_n].
$$
(12.28)

Observe that Proposition 12.1.9, Lemma 12.1.8, and (12.28) ensure that

$$
\begin{align*}
\mathbb{P}\left(\left|\sum_{n=1}^N (X_n - \mathbb{E}[X_n])\right| \geq \varepsilon\right) &= \mathbb{P}\left(\left|\sum_{n=1}^N Y_n\right| \geq \varepsilon\right) \leq \inf_{\lambda \in [0,\infty)}\left(e^{-\lambda \varepsilon} \mathbb{M}_{\sum_{n=1}^N Y_n}(\lambda)\right) \\
&= \inf_{\lambda \in [0,\infty)}\left(e^{-\lambda \varepsilon} \prod_{n=1}^N \mathbb{M}_{Y_n}(\lambda)\right) = \inf_{\lambda \in [0,\infty)}\left(e^{-\lambda \varepsilon} \prod_{n=1}^N \mathbb{M}_{X_n - \mathbb{E}[X_n]}(\lambda)\right).
\end{align*}
$$
(12.29)

The proof of Corollary 12.1.13 is thus complete.

# 12.1.5 Hoeffding's inequality

# 12.1.5.1 On the moment-generating function for bounded random variables

**Lemma 12.1.14.** *Let* $(\Omega, \mathcal{F}, \mathbb{P})$ *be a probability space, let* $\lambda, a \in \mathbb{R}$, $b \in (a, \infty)$, $p \in [0,1]$ *satisfy* $p = \frac{a}{(b-a)}$, *let* $X \colon \Omega \rightarrow [a,b]$ *be a random variable with* $\mathbb{E}[X] = 0$, *and let* $\phi \colon \mathbb{R} \rightarrow \mathbb{R}$ *satisfy for all* $x \in \mathbb{R}$ *that* $\phi(x) = \ln(1 - p + pe^x) - px$. *Then*

$$
\mathbb{E}[e^{\lambda X}] \leq e^{\phi(\lambda(b-a))}.
$$
(12.30)

*Proof of Lemma 12.1.14.* *Observe that for all* $x \in \mathbb{R}$ *it holds that*

$$
\begin{align*}
x(b-a) &= bx - ax = [ab - ax] + [bx - ab] = [a(b-x) + b(x-a)] \\
&= a(b-x) + b[b - a - b + x] = a(b-x) + b[(b-a) - (b-x)].
\end{align*}
$$
(12.31)

Hence, we obtain that for all $x \in \mathbb{R}$ it holds that

$$
x = a\left(\frac{b-x}{b-a}\right) + b\left[1 - \left(\frac{b-x}{b-a}\right)\right].
$$
(12.32)

This implies that for all $x \in \mathbb{R}$ it holds that

$$
\lambda x = \left(\frac{b-x}{b-a}\right) \lambda a + \left[1-\left(\frac{b-x}{b-a}\right)\right] \lambda b.
$$
(12.33)

The fact that $\mathbb{R} \ni x \mapsto e^x \in \mathbb{R}$ is convex hence demonstrates that for all $x \in [a, b]$ it holds that

$$
e^{\lambda x} = \exp \left(\left(\frac{b-x}{b-a}\right) \lambda a + \left[1-\left(\frac{b-x}{b-a}\right)\right] \lambda b\right) \leq \left(\frac{b-x}{b-a}\right) e^{\lambda a} + \left[1-\left(\frac{b-x}{b-a}\right)\right] e^{\lambda b}.
$$
(12.34)

The assumption that $\mathbb{E}[X] = 0$ therefore assures that

$$
\mathbb{E}\left[e^{\lambda X}\right] \leq \left(\frac{b}{b-a}\right) e^{\lambda a} + \left[1-\left(\frac{b}{b-a}\right)\right] e^{\lambda b}.
$$
(12.35)

Combining this with the fact that

$$
\begin{align*}
\frac{b}{b-a} &= 1-\left[1-\left(\frac{b}{(b-a)}\right)\right] \\
&= 1-\left[\left(\frac{(b-a)}{(b-a)}\right)-\left(\frac{b}{(b-a)}\right)\right] \\
&= 1-\left[\frac{-a}{(b-a)}\right] = 1-p
\end{align*}
$$
(12.36)

demonstrates that

$$
\begin{align*}
\mathbb{E}\left[e^{\lambda X}\right] &\leq \left(\frac{b}{b-a}\right) e^{\lambda a} + \left[1-\left(\frac{b}{b-a}\right)\right] e^{\lambda b} \\
&= (1-p) e^{\lambda a} + [1-(1-p)] e^{\lambda b} \\
&= (1-p) e^{\lambda a} + p e^{\lambda b} \\
&= \left[(1-p) + p e^{\lambda (b-a)}\right] e^{\lambda a}.
\end{align*}
$$
(12.37)

Moreover, note that the assumption that $p = \frac{-a}{(b-a)}$ shows that $p(b-a) = -a$. Hence, we obtain that $a = -p(b-a)$. This and (12.37) assure that

$$
\begin{align*}
\mathbb{E}\left[e^{\lambda X}\right] &\leq \left[(1-p) + p e^{\lambda (b-a)}\right] e^{-p\lambda (b-a)} = \exp \left(\ln \left(\left[\left(1-p\right) + p e^{\lambda (b-a)}\right] e^{-p\lambda (b-a)}\right)\right) \\
&= \exp \left(\ln \left(\left(1-p\right) + p e^{\lambda (b-a)}\right) - p\lambda (b-a)\right) = \exp \left(\phi(\lambda (b-a))\right).
\end{align*}
$$
(12.38)

The proof of Lemma 12.1.14 is thus complete. $\square$

# 12.1.5.2 Hoeffding’s lemma

**Lemma 12.1.15.** Let $p \in [0, 1]$ and let $\phi: \mathbb{R} \to \mathbb{R}$ satisfy for all $x \in \mathbb{R}$ that $\phi(x) = \ln(1 - p + p e^{x}) - px$. Then it holds for all $x \in \mathbb{R}$ that $\phi(x) \leq \frac{x^{2}}{8}$.

*Proof of Lemma 12.1.15.* Observe that the fundamental theorem of calculus ensures that for all $x \in \mathbb{R}$ it holds that

$$
\begin{align*}
\phi(x) &= \phi(0) + \int_{0}^{x} \phi^{\prime}(y) \mathrm{d} y \\
&= \phi(0) + \phi^{\prime}(0) x + \int_{0}^{x} \int_{0}^{y} \phi^{\prime \prime}(z) \mathrm{d} z \mathrm{d} y \\
&\leq \phi(0) + \phi^{\prime}(0) x + \frac{x^{2}}{2} \left[\sup _{z \in \mathbb{R}} \phi^{\prime \prime}(z)\right].
\end{align*}
$$
(12.39)

Moreover, note that for all $x \in \mathbb{R}$ it holds that

$$
\phi^{\prime}(x) = \left[\frac{p e^{x}}{1 - p + p e^{x}}\right] - p \quad \text { and } \quad \phi^{\prime \prime}(x) = \left[\frac{p e^{x}}{1 - p + p e^{x}}\right] - \left[\frac{p^{2} e^{2 x}}{\left(1 - p + p e^{x}\right)^{2}}\right].
$$
(12.40)

Hence, we obtain that

$$
\phi^{\prime}(0) = \left[\frac{p}{1 - p + p}\right] - p = 0.
$$
(12.41)

In the next step we combine (12.40) and the fact that for all $a \in \mathbb{R}$ it holds that

$$
a(1-a) = a - a^{2} = -\left[a^{2} - 2 a\left[\frac{1}{2}\right] + \left[\frac{1}{2}\right]^{2}\right] + \left[\frac{1}{2}\right]^{2} = \frac{1}{4} - \left[a - \frac{1}{2}\right]^{2} \leq \frac{1}{4}
$$
(12.42)

to obtain that for all $x \in \mathbb{R}$ it holds that $\phi^{\prime \prime}(x) \leq \frac{1}{4}$. This, (12.39), and (12.41) ensure that for all $x \in \mathbb{R}$ it holds that

$$
\phi(x) \leq \phi(0) + \phi^{\prime}(0) x + \frac{x^{2}}{2}\left[\sup _{z \in \mathbb{R}} \phi^{\prime \prime}(z)\right] = \phi(0) + \frac{x^{2}}{2}\left[\sup _{z \in \mathbb{R}} \phi^{\prime \prime}(z)\right] \leq \phi(0) + \frac{x^{2}}{8} = \frac{x^{2}}{8}.
$$
(12.43)

The proof of Lemma 12.1.15 is thus complete.

**Lemma 12.1.16.** Let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $a \in \mathbb{R}, b \in[a, \infty)$, $\lambda \in \mathbb{R}$, and let $X: \Omega \to [a, b]$ be a random variable with $\mathbb{E}[X]=0$. Then

$$
\mathbb{E}\left[\exp (\lambda X)\right] \leq \exp \left(\frac{\lambda^{2}(b - a)^{2}}{8}\right).
$$
(12.44)

![](img/dec290f673e6357c31893c67b579ffe1_439_0.png)
