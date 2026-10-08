
The assumption that $\bigcup_{k=1}^{\infty} \Theta_{k,0}(\Omega) \subseteq [-B, B]^d$ and the assumption that $0 \in \mathbf{T}$ therefore prove that
$$
\begin{aligned}
\int_D |\mathcal{N}_{u,v}^{\Theta_k \mathbf{1}}(x) - \mathcal{E}(x)|^2 \, \mathbb{P}_{\mathbf{X}_1}(dx) & \le \big[ \sup_{x \in D} |\mathcal{N}_{u,v}^{\theta_\mathbf{1}}(x) - \mathcal{E}(x)|^2 \big] + 2 \big[ \sup_{\theta \in [-B, B]^d} | \mathcal{R}(\theta) - \mathbf{R}(\theta) | \big] \\
& + \min_{k \in \{1, \dots, K\}} | \mathcal{R}(\Theta_{k,0}) - \mathcal{R}(\vartheta) | \\
& = \big[ \sup_{x \in D} |\mathcal{N}_{u,v}^{\theta_\mathbf{1}}(x) - \mathcal{E}(x)|^2 \big] + 2 \big[ \sup_{\theta \in [-B, B]^d} | \mathcal{R}(\theta) - \mathbf{R}(\theta) | \big] \\
& + \min_{k \in \{1, \dots, K\}} | \mathcal{R}(\Theta_{k,0}) - \mathcal{R}(\vartheta) | .
\end{aligned}
$$

Minkowski's inequality hence demonstrates that for all $p \in [1, \infty)$, $\vartheta \in [-c, c]^d \subseteq [-B, B]^d$ it holds that
$$
\begin{aligned}
\left( \mathbb{E} \left[ \left( \int_D |\mathcal{N}_{u,v}^{\Theta_k \mathbf{1}}(x) - \mathcal{E}(x)|^2 \, \mathbb{P}_{\mathbf{X}_1}(dx) \right)^p \right] \right)^{1/p} & \\
& \le \left( \mathbb{E} \left[ \sup_{x \in D} |\mathcal{N}_{u,v}^{\theta_\mathbf{1}}(x) - \mathcal{E}(x)|^{2p} \right] \right)^{1/p} + 2 \left( \mathbb{E} \left[ \sup_{\theta \in [-B, B]^d} | \mathcal{R}(\theta) - \mathbf{R}(\theta) |^p \right] \right)^{1/p} \\
& + \left( \mathbb{E} \left[ \min_{k \in \{1, \dots, K\}} | \mathcal{R}(\Theta_{k,0}) - \mathcal{R}(\vartheta) |^p \right] \right)^{1/p} \\
& \le \left[ \sup_{x \in D} |\mathcal{N}_{u,v}^{\theta_\mathbf{1}}(x) - \mathcal{E}(x)|^2 \right] + 2 \left( \mathbb{E} \left[ \sup_{\theta \in [-B, B]^d} | \mathcal{R}(\theta) - \mathbf{R}(\theta) |^p \right] \right)^{1/p} \\
& + \sup_{\theta \in [-c, c]^d} \left( \mathbb{E} \left[ \min_{k \in \{1, \dots, K\}} | \mathcal{R}(\Theta_{k,0}) - \mathcal{R}(\vartheta) |^p \right] \right)^{1/p}
\end{aligned}
$$

(cf. item **(i)** in Corollary **13.3.3** and item **(i)** in Corollary **11.3.9**). Furthermore, observe that Corollary **13.3.3** (applied with $v \doteq \max\{u+1, v\}$, $\mathbf{R} \doteq \mathbf{R}|_{[-B, B]^d}$, $\mathcal{R} \doteq \mathcal{R}|_{[-B, B]^d \times \Omega}$ in the notation of Corollary **13.3.3**) implies that for all $p \in (0, \infty)$ it holds that
$$
\begin{aligned}
\left( \mathbb{E} \left[ \sup_{\theta \in [-B, B]^d} | \mathcal{R}(\theta) - \mathbf{R}(\theta) |^p \right] \right)^{1/p} & \\
& \le \frac{9 ( \max\{u+1, v\} - u)^2 \mathbb{L} ( \|\mathbf{\|} \|_\infty + 1)^2 \max\{p, \ln(3MBb)\}}{\sqrt{M}} \\
& = \frac{9 \max\{1, (v-u)^2\} \mathbb{L} ( \|\mathbf{\|} \|_\infty + 1)^2 \max\{p, \ln(3MBb)\}}{\sqrt{M}} .
\end{aligned}
$$

Moreover, note that Corollary **11.3.9** (applied with $\Theta \doteq \sum_{i=1}^{\mathbf{d}} \mathbf{L}_i(\mathbf{l}_{i-1}+1)$, $B \doteq c$, $(\Theta_k)_{k \in \{1, \dots, K\}} \doteq ( \Omega \ni \omega \mapsto \mathbb{I}_{\{ \Theta_{k,0} \in [-c, c]^d \}}(\omega) \Theta_{k,0}(\omega) \in [-c, c]^d)_{k \in \{1, \dots, K\}}$, $\mathcal{R} \doteq \mathcal{R}|_{[-c, c]^d \times \Omega}$ in the notation of Corollary **11.3.9**) ensures that for all $p \in (0, \infty)$ it holds that
$$
\begin{aligned}
\sup_{\theta \in [-c, c]^d} \left( \mathbb{E} \left[ \min_{k \in \{1, \dots, K\}} | \mathcal{R}(\Theta_{k,0}) - \mathcal{R}(\theta) |^p \right] \right)^{1/p} & \\
& = \sup_{\theta \in [-c, c]^d} \left( \mathbb{E} \left[ \min_{k \in \{1, \dots, K\}} | \mathcal{R}(\mathbb{I}_{\{ \Theta_{k,0} \in [-c, c]^d \}} \Theta_{k,0}) - \mathcal{R}(\theta) |^p \right] \right)^{1/p} \\
& \le \frac{4(v-u) b \mathbb{L} ( \|\mathbf{\|} \|_\infty + 1) \mathbb{L} c^p \max\{1, p\}}{K \mathbb{L} \tau^{-2}( \|\mathbf{\|} \|_\infty + 1)^{-2}} .
\end{aligned}
$$

Combining this and (15.20) with (15.19) establishes that for all $ p \in [1, \infty) $ it holds that
$$
\left(\mathbb{E} \left[ \left( \int_D |\mathcal{H}^{\Theta_{u, v}^{\mathbf{k}, 1}}(x) - \mathcal{E}(x)|^2 \, \mathbb{P}_{X_1}(\mathrm{d}x) \right)^p \right] \right)^{1/p} \leq \left[ \inf_{\theta \in [-c, c]^d} \sup_{x \in D} |\mathcal{H}^{\Theta_{u, v}^{\mathbf{k}, 1}}(x) - \mathcal{E}(x)|^2 \right] + \frac{4(v - u)b\mathbf{L}(\|\mathbf{1}\|_{\infty} + 1)^r c^\mathbf{L} \max \{ 1, p \}}{K^{[L - 1](\|\mathbf{1}\|_{\infty} + 1) - 2}} \quad (15.22) \\
+ \frac{18 \max \{ 1, (v - u)^2 \} \mathbf{L}(\|\mathbf{1}\|_{\infty} + 1)^2 \max \{ p, \ln(3Mb) \}}{\sqrt{M}} .
$$

In addition, observe that Jensen's inequality shows that for all $ p \in (0, \infty) $ it holds that
$$
\left(\mathbb{E} \left[ \left( \int_D |\mathcal{H}^{\Theta_{u, v}^{\mathbf{k}, 1}}(x) - \mathcal{E}(x)|^2 \, \mathbb{P}_{X_1}(\mathrm{d}x) \right)^p \right] \right)^{1/p} \leq \left( \mathbb{E} \left[ \left( \int_D |\mathcal{H}^{\Theta_{u, v}^{\mathbf{k}, 1}}(x) - \mathcal{E}(x)|^2 \, \mathbb{P}_{X_1}(\mathrm{d}x) \right)^{\max \{ 1, p \}} \right] \right)^{\frac{1}{\max \{ 1, p \}}} \quad (15.23)
$$

This, (15.22), and the fact that $\ln(3Mb) \geq 1$ prove that for all $ p \in (0, \infty) $ it holds that
$$
\left(\mathbb{E} \left[ \left( \int_D |\mathcal{H}^{\Theta_{u, v}^{\mathbf{k}, 1}}(x) - \mathcal{E}(x)|^2 \, \mathbb{P}_{X_1}(\mathrm{d}x) \right)^p \right] \right)^{1/p} \leq \left[ \inf_{\theta \in [-c, c]^d} \sup_{x \in D} |\mathcal{H}^{\Theta_{u, v}^{\mathbf{k}, 1}}(x) - \mathcal{E}(x)|^2 \right] + \frac{4(v - u)b\mathbf{L}(\|\mathbf{1}\|_{\infty} + 1)^r c^\mathbf{L} \max \{ 1, p \}}{K^{[L - 1](\|\mathbf{1}\|_{\infty} + 1) - 2}} \quad (15.24) \\
+ \frac{18 \max \{ 1, (v - u)^2 \} \mathbf{L}(\|\mathbf{1}\|_{\infty} + 1)^2 \max \{ p, \ln(3Mb) \}}{\sqrt{M}} .
$$

The proof of Proposition 15.1.2 is thus complete.

$\square$

Lemma 15.1.3. Let $ a, x, p \in (0, \infty) $. Then $ ax^p \leq \exp( \frac{a^{1/p} p x}{e} ) $.

Proof of Lemma 15.1.3. Note that the fact that for all $ y \in \mathbb{R} $ it holds that $ y + 1 \leq e^y $ demonstrates that
$$
ax^p = (a^{1/p} x)^p = [ e( \frac{a^{1/p} p x}{e} - 1 + 1 ) ]^p \leq [ e \exp(\frac{a^{1/p} p x}{e} - 1) ]^p = \exp( \frac{a^{1/p} p x}{e} ) . \quad (15.25)
$$

The proof of Lemma 15.1.3 is thus complete.

$\square$

Lemma 15.1.4. Let $ M, c \in [1, \infty) $, $ B \in [c, \infty) $. Then $\ln(3MBc) \leq \frac{23B}{18}\ln(eM) $.

Proof of Lemma 15.1.4. Observe that Lemma 15.1.3 and the fact that $ 2\sqrt[3]{c} \leq \frac{23}{18} $ imply that
$$
3B^2 \leq \exp(\frac{2\sqrt{3}B}{e}) \leq \exp( \frac{23B}{18} ) . \quad (15.26)
$$

The fact that $ B \geq c \geq 1 $ and $ M \geq 1 $ therefore ensures that
$$
\ln(3MBc) \leq \ln(3B^2M) \leq \ln(eM)^{23B/18} = \frac{23B}{18}\ln(eM) . \quad (15.27)
$$

The proof of Lemma 15.1.4 is thus complete.

$\square$

## Chapter 15: Composéd error estimates

**Theorem 15.1.5.** Let $(\Omega,\mathcal{F},\mathbb{P})$ be a probability space, let $M, d \in \mathbb{N}$, $a, u \in \mathbb{R}$, $b \in (a, \infty)$, $v \in (u, \infty)$, for every $j \in \mathbb{N}$ let $X_j\colon \Omega \to [a, b]^d$ and $Y_j\colon \Omega \to [u, v]$ be random variables, assume that $(X_j, Y_j)$, $j \in \{1, 2, \ldots, M\}$, are i.i.d., let $A \in (0, \infty)$, $\mathbf{L} \in \mathbb{N}$ satisfy $\mathbf{L} \ge A \lfloor a^d(\infty)(A)/(2d)+1\rfloor$, let $\mathbf{l}= (\mathbf{l}_0, \mathbf{l}_1, \ldots, \mathbf{l}_{\mathbf{L}}) \in \mathbb{N}^{\mathbf{L}+1}$ satisfy for all $i \in \{2, 3, 4, \ldots\} \cap [0, \mathbf{L}]$ that

$\mathbf{l}_0=d, \quad \mathbf{l}_1 \ge A \lfloor a^d(\infty)(A) \rfloor, \quad \mathbf{l}_i \ge \lfloor a^d(\infty)(A) \max \{4/d - 2i + 3, 2\} \rfloor, \quad and \quad \mathbf{l}_{\mathbf{L}} = 1,\quad (15.28)$

let $\mathbf{d} \in \mathbb{N}$ satisfy $\mathbf{d} \ge \sum_{i=1}^{\mathbf{L}} \mathbf{l}_i (\mathbf{l}_{i-1} + 1)$, let $\mathcal{R}\colon \mathbb{R}^{\mathbf{d}} \times \Omega \to [0, \infty)$ satisfy for all $\theta \in \mathbb{R}^{\mathbf{d}}$ that

$\mathcal{R}(\theta)= \frac{1}{M} \Big[ \sum_{j=1}^{M} [\mathcal{N}^{d, 1}_{u,v} (X_j) - Y_j]^2 \ Big],\quad (15.29)$

let $\mathcal{E}\colon [a, b]^d \to [u, v]$ satisfy $\mathbb{P}$-a.s. that

$\mathcal{E}(X_1) = \mathbb{E}[Y_1|X_1],\quad (15.30)$

let $L \in \mathbb{R}$ satisfy for all $x, y \in [a, b]^d$ that $|\mathcal{E}(x) - \mathcal{E}(y)| \le L \| x - y \|_1$, let $K \in \mathbb{N}$, $c \in [\max \{1, L, |a|, |b|, 2|u|, 2|v| \}, \infty)$, $B \in [c, \infty)$, for every $k, n \in \mathbb{N}_0$ let $\Theta_{k,n}\colon \Omega \to \mathbb{R}^{\mathbf{d}}$ be a random variable, assume $\bigcup_{k=1}^{\infty} \Theta_{k,0}(\Omega) \subseteq [-B, B]^d$, assume that $\Theta_{k,0}$, $k \in \{1, 2, \ldots, K\}$, are i.i.d., assume that $\Theta_{1,0}$ is continuously uniformly distributed on $[-c, c]^{\mathbf{d}}$, let $N \in \mathbb{N}$, $\mathbf{T} \subseteq \{0, 1, \ldots, N\}$ satisfy $0 \in \mathbf{T}$, let $\mathbf{k}\colon \Omega \to (\mathbb{N}_0)^2$ be a random variable, and assume for all $\omega \in \Omega$ that

$\mathbf{k}(\omega) \in \{ (k, n) \in \{1, 2, \ldots, K\} \times \mathbf{T}\colon \| \Theta_{k,n}(\omega) \|_\infty \le B\}\quad (15.31)$

and

$\mathcal{R}(\Theta_{\mathbf{k}(\omega)}(\omega)) = \min \{ (k, n) \in \{1, 2, \ldots, K\} \times \mathbf{T}\colon \| \Theta_{k,n}(\omega) \|_\infty \le B \ \mathcal{R}(\Theta_{k,n}(\omega))\}\quad (15.32)$

(cf. Definitions 3.3.4 and 4.4.1). Then it holds for all $p \in (0, \infty)$ that

$\begin{align*} & \Big( \mathbb{E} \Big[ \Big( \int_{[a, b]^d} |\mathcal{N}^{\Theta_{\mathbf{k}, 1}}_{u, v} (x) - \mathcal{E}(x)|^2 \, \mathbb{P}_{X_1} (\mathrm{d}x) \Big)^p \Big] \Big)^{1/p} \\ & \le \frac{36d^2c^4}{A^{\beta/d}} + \frac{4 \mathbf{L} (\| \mathbf{l} \|_\infty + 1)^{\mathbf{L}} \mathcal{L}^{L+2} \max \{1, p\}}{K^{\lceil \mathbf{L} \rceil \left( \| \mathbf{L} \|_\infty + 1 \right)^{-2}}} \\ & \quad + \frac{23B^3 \mathbf{L} (\| \mathbf{l} \|_\infty + 1)^2 \max \{p, \ln (eM)\}}{\sqrt{M}}\quad (15.33) \end{align*}$

(cf. Lemma 15.1.1).

**Proof of Theorem 15.1.5.** Note that the assumption that for all $x, y \in [a, b]^d$ it holds that $|\mathcal{E}(x) - \mathcal{E}(y)| \le L \| x - y \|_1$ establishes that $\mathcal{E}\colon [a, b]^d \to [u, v]$ is $\mathcal{B} ([a, b]^d) / \mathcal{B} ([u, v])$-measurable. Proposition 15.1.2 (applied with $b \hookrightarrow \max \{1, |a|, |b| \}$, $D \hookrightarrow [a, b]^d$ in the
