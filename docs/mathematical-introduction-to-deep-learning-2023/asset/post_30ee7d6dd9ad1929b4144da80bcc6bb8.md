
The fact that for all $c, p \in (0, \infty)$ with $\kappa_c \leq 1$ it holds that

$$\begin{gathered}\begin{split}\inf_{\varepsilon \in (0, \infty)} & \left[ \frac{2(c+1)b^{2} \max\{1, (\kappa_{c})^{\varepsilon}\} \sqrt{\max\{1, p, \tfrac{d}{\varepsilon}\}}}{\sqrt{M}} \\ = \inf_{\varepsilon \in (0, \infty)} & \left[ \frac{2(c+1)b^{2} \sqrt{\max\{1, p, \tfrac{d}{\varepsilon}\}}}{\sqrt{M}} \right] \leq \frac{2(c+1)b^{2} \sqrt{\max\{1, p\}}}{\sqrt{M}} \leq \frac{2(c+1)b^{2} \sqrt{\varepsilon} \max\{1, p, \mathbf{d} \ln( [ \kappa_c ]^{2})\}}{\sqrt{M}}.\end{split}\tag{13.63}\end{gathered}$$

and (13.60) therefore imply that for all $p \in (0, \infty)$ it holds that

$$\begin{gathered}\begin{aligned}\left( \mathbb{E} \left| \sup_{\theta \in [ \alpha, \beta ]^{d}} | \mathscr{R}(\theta) - \mathbf{R}(\theta) |^{p} \right)\right)^{\frac{1}{p}} & \\ \leq \inf_{c, \varepsilon \in (0, \infty)} & \left[ \frac{2(c+1)b^{2} \max\{1, (\kappa_{c})^{\varepsilon}\} \sqrt{\max\{1, p, \tfrac{d}{\varepsilon}\}}}{\sqrt{M}} \\ = \inf_{c, \varepsilon \in (0, \infty)} & \left[ \frac{2(c+1)b^{2} \max\{1, [2\sqrt{M}L(\beta-\alpha)(c b)^{-1}]^{\varepsilon}\} \sqrt{\max\{1, p, \tfrac{d}{\varepsilon}\}}}{\sqrt{M}} \right] \\ \leq \inf_{c \in (0, \infty)} & \left[ \frac{2(c+1)b^{2} \sqrt{\varepsilon} \max\{1, \mathbf{d} \ln( [ \kappa_c ]^{2})\}}{\sqrt{M}} \right] \leq \inf_{c \in (0, \infty)} & \left[ \frac{2(c+1)b^{2} \sqrt{\varepsilon} \max\{1, \mathbf{d} \ln(4ML^{2}(\beta-\alpha)^{2}(c b)^{-2})\}}{\sqrt{M}} \right].\end{aligned}\tag{13.64}\end{gathered}$$

This establishes item (ii). The proof of Proposition 13.3.2 is thus complete. $\square$

**Corollary 13.3.3.** *Let $d, M \in \mathbb{N}$, $b \in [1, \infty)$, $u \in \mathbb{R}$, $v \in [u + 1, \infty)$, $D \subseteq [ - b, b ]^{d}$, let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $\mathbb{X}_{m} = (X_{m}, Y_{m}) : \Omega \rightarrow (D \times [u, v])$, $m \in \{ 1, 2, \ldots, M \}$, be i.i.d. random variables, let $B \in [1, \infty)$, $\mathbf{L}, \mathbf{d} \in \mathbb{N}$, $\mathbf{1} = ( \mathbf{1}_{0}, \mathbf{1}_{1}, \ldots, \mathbf{1}_{\mathbf{L}} ) \in \mathbb{N}^{\mathbf{L}+1}$ satisfy $\mathbf{1}_{0} = d$, $\mathbf{1}_{\mathbf{L}} = 1$, and $\mathbf{d} \geq \sum_{i = 1}^{\mathbf{L}} \mathbf{1}_{i} (\mathbf{1}_{i - 1} + 1)$, let $\mathbf{R} : [ - B, B ]^{d} \to [0, \infty)$ and $\mathscr{R} : [ - B, B ]^{d} \times \Omega \to [0, \infty)$ satisfy for all $\theta \in [ - B, B ]^{d}$, $\omega \in \Omega$ that*

$$\mathbf{R}(\theta) = \mathbb{E} [ |\mathscr{A}_{u,v}^{\theta,1} (X_{1}) - Y_{1}|^{2} ] \quad \text{and} \quad \mathscr{R}(\theta, \omega) = \frac{1}{M} \left[ \sum_{m=1}^{M} |\mathscr{A}_{u,v}^{\theta,1} (X_{m}(\omega)) - Y_{m}(\omega) |^{2} \right]$$

*(cf. Definition 4.4.1). Then*

- (i) *it holds that $\Omega \ni \omega \mapsto \sup_{\theta \in [ - B, B ]^{d}} | \mathscr{R}(\theta, \omega) - \mathbf{R}(\theta) | \in [0, \infty]$ is $\mathcal{F}/\mathcal{B}([0, \infty])$-measurable and*
- (ii) *it holds for all* $p\in(0,\infty)$ *that*

$$\begin{aligned}\begin{aligned}\mathbb{E}\left[\sup_{\theta\in[-B,B]^{d}}\|\mathscr{E}(\theta)-\mathbf{R}(\theta)\|^{p}\right]^{1/p}\\&\leq\frac{9(v-u)^{2}\mathbf{L}(\|\mathbf{l}\|_{\infty}+1)\sqrt{\max\{p,\ln(4(Mb)^{\lceil L\rceil}/(\|\mathbf{l}\|_{\infty}+1)B)\}}}{\sqrt{M}}\\&\leq\frac{9(v-u)^{2}\mathbf{L}(\|\mathbf{l}\|_{\infty}+1)^{2}\max\{p,\ln(3Mbb)\}}{\sqrt{M}}\end{aligned}\tag{13.66}\end{aligned}$$

*(cf. Definition 3.3.4).*

*Proof of Corollary 13.3.9.* Throughout this proof, let $\mathbf{d}=\sum_{i=1}^{\mathbf{L}}\mathbf{l}_{i}(\mathbf{l}_{i-1}+1)\in\mathbb{N}$, let $L= b\mathbf{L}(\|\mathbf{l}\|_{\infty}+1)^{\mathbf{L}}B^{\mathbf{L}-1}\in(0,\infty)$, for every $\theta\in[-B,B]^{\mathfrak{d}}$ let $f_{\theta}\colon D\to\mathbb{R}$ satisfy for all $x\in D$ that

$$f_{\theta}(x)=\mathcal{N}_{u,v}^{\theta,1}(x),\tag{13.67}$$

let $\mathscr{E}\colon[-B,B]^{\mathfrak{d}}\to[0,\infty)$ satisfy for all $\theta\in[-B,B]^{\mathfrak{d}}$ that

$$\mathscr{E}(\theta)=\mathbb{E}\left[\left|f_{\theta}(X_{1})-Y_{1}\right|^{2}\right]=\mathbb{E}\left[\left|\mathcal{N}_{u,v}^{\theta,1}(X_{1})-Y_{1}\right|^{2}\right],\tag{13.68}$$

and let $R\colon[-B,B]^{\mathfrak{d}}\times\Omega\to[0,\infty)$ satisfy for all $\theta\in[-B,B]^{\mathfrak{d}}$, $\omega\in\Omega$ that

$$R(\theta,\omega)=\frac{1}{M}\left[\sum_{m=1}^{M}\left|f_{\theta}(X_{m}(\omega))-Y_{m}(\omega)\right|^{2}\right]=\frac{1}{M}\left[\sum_{m=1}^{M}\left|\mathcal{N}_{u,v}^{\theta,1}(X_{m}(\omega))-Y_{m}(\omega)\right|^{2}\right]\tag{13.69}$$

*(cf. Definition 3.3.4).* Note that the fact that for all $\theta\in\mathbb{R}^{\mathfrak{d}}$, $x\in\mathbb{R}^{d}$ it holds that $\mathcal{N}_{u,v}^{\theta,1}(x)\in[u,v]$ and the assumption that for all $m\in\{1,2,\dots,M\}$ it holds that $Y_{m}(\Omega)\subseteq[u,v]$ ensure for all $\theta\in[-B,B]^{\mathfrak{d}}$, $m\in\{1,2,\dots,M\}$ that

$$\left|f_{\theta}(X_{m})-Y_{m}\right|=\left|\mathcal{N}_{u,v}^{\theta,1}(X_{m})-Y_{m}\right|\leq\sup_{y_{1},y_{2}\in[u,v]}\left|y_{1}-y_{2}\right|=v-u.\tag{13.70}$$

Furthermore, observe that the assumption that $D\subseteq[-b,b]^{d}$, $\mathbf{l}_{0}=d$, and $\mathbf{l}_{\mathbf{L}}=1$, Corollary 11.3.7 (applied with $a\wedge-b$, $b\wedge b$, $u\wedge u$, $v\wedge v$, $d\wedge\mathfrak{d}$, $L\wedge\mathbf{L}$, $l\wedge\mathbf{l}$ in the notation of Corollary 11.3.7), and the assumption that $b\geq 1$ and $B\geq 1$ show that for all $\theta,\vartheta\in[-B,B]^{\mathfrak{d}}$, $x\in D$ it holds that

$$\begin{aligned}\begin{aligned}\left|f_{\theta}(x)-f_{\vartheta}(x)\right|&\leq\sup_{y\in[-b,b]^{d}}\left|\mathcal{N}_{u,v}^{\theta,1}(y)-\mathcal{N}_{u,v}^{\vartheta,1}(y)\right|\\&\leq\mathbf{L}\max\{1,b\}(\|\mathbf{l}\|_{\infty}+1)^{\mathbf{L}}(\max\{1,\|\theta\|_{\infty},\|\vartheta\|_{\infty}\}^{\mathbf{L}-1}\|\theta-\vartheta\|_{\infty}\\&\leq b\mathbf{L}(\|\mathbf{l}\|_{\infty}+1)^{\mathbf{L}}B^{\mathbf{L}-1}\|\theta-\vartheta\|_{\infty}=L\|\theta-\vartheta\|_{\infty}.\end{aligned}\tag{13.71}\end{aligned}$$

Moreover, note that the fact that $\mathbf{d}\geq\mathfrak{d}$ and the fact that for all $\theta=(\theta_{1},\theta_{2},\dots,\theta_{\mathfrak{d}})\in\mathbb{R}^{\mathfrak{d}}$ it holds that $\mathcal{N}_{u,v}^{\theta,1}=\mathcal{N}_{u,v}^{(\theta_{1},\theta_{2},\dots,\theta_{\mathfrak{d}}),1}$ demonstrates that for all $\omega\in\Omega$ it holds that

$$\sup_{\theta\in[-B,B]^{d}}\left|\mathscr{E}(\theta,\omega)-\mathbf{R}(\theta)\right|=\sup_{\theta\in[-B,B]^{\mathfrak{d}}}\left|R(\theta,\omega)-\mathscr{E}(\theta)\right|.\tag{13.72}$$

## 13.3. Strong convergence rates for the generalisation error

In addition, observe that (13.70), (13.71), Proposition 13.3.2 (applied with $\alpha \leadsto -B$, $\beta \leadsto B$, **d** $\leadsto$ **d**, $b \leadsto v - u$, **R** $\leadsto$ $\mathscr{R}$, $\mathscr{R} \leadsto R$ in the notation of Proposition 13.3.2 ), the fact that

$$v - u \geq (u + 1) - u = 1 \tag{13.73}$$

and the fact that

$$\mathbf{d} \leq \mathbf{L}\|\mathbf{I}\|_{\infty}(\|\mathbf{I}\|_{\infty} + 1) \leq \mathbf{L}(\|\mathbf{I}\|_{\infty} + 1)^2 \tag{13.74}$$

prove that for all $p \in (0, \infty)$ it holds that $\Omega \supseteq \omega \leadsto \sup_{\theta \in [-B, B] \setminus \{R(\theta, \omega) - \mathscr{R}(\theta) \mid [0, \infty]$ is $\mathcal{F} / \mathcal{B}([0, \infty])$-measurable and

$$\begin{align*}
\begin{gathered}
\left( \mathbb{E} \left[ \sup_{\theta \in [-B, B] \setminus \{R(\theta) - \mathscr{R}(\theta)\}} |p| \right] \right)^{1 / p} \\
\leq \inf_{C \in (0, \infty)} \frac{2(C + 1)(v - u)^2 \sqrt{e} \max \{1, \mathbf{p}, \ln(4ML^2(2B)^2(C(v - u)^2))\}}{\sqrt{M}} \\
\leq \inf_{C \in (0, \infty)} \frac{2(C + 1)(v - u)^2 \sqrt{e} \max \{1, p, \mathbf{L}\|\mathbf{I}\|_{\infty} + 1\}^2 \ln(2^4ML^2B^2C^{-2})}{\sqrt{M}} .
\end{gathered}
\tag{13.75}
\end{align*}$$

Combining this with (13.72) establishes item (i). Note that (13.72), (13.75), the fact that $2^{6}\mathbf{L}^{2} \leq 2^{6} \cdot 2^{4}(\mathbf{L} - 1) = 2^{4+2\mathbf{L}} \leq 2^{\mathbf{L}+2\mathbf{L}} = 2^{6\mathbf{L}}$, the fact that $3 \geq e$, and the assumption that $B \geq 1$, **L** $\geq 1$, $M \geq 1$, and $b \geq 1$ imply that for all $p \in (0, \infty)$ it holds that

$$\begin{align*}
\begin{gathered}
\left(\mathbb{E}\left[\sup_{\theta \in[-B, B]}\left|\mathscr{R}(\theta)-\mathbf{R}(\theta)\right|^{p}\right]\right)^{1 / p}=\left(\mathbb{E}\left[\sup_{\theta \in[-B, B]}\left|R(\theta)-\mathscr{R}(\theta)\right|^{p}\right]\right)^{1 / p} \\
\leq \frac{2^{\left(1 / 2+1\right)}(v-u)^{2} \sqrt{e} \max \left\{1, p, \mathbf{L}\left(\|\mathbf{I}\|_{\infty}+1\right)^{2} \ln\left(2^{4} M L^{2} B^{2} 2^{2}\right)\right\}}{\sqrt{M}} \\
=\frac{3(v-u)^{2} \sqrt{e} \max \left\{p, \mathbf{L}\left(\|\mathbf{I}\|_{\infty}+1\right)^{2} \ln\left(2^{6} M b^{2} \mathbf{L}^{2}\left(\|\mathbf{I}\|_{\infty}+1\right)^{2} \mathbf{L}^{B^{2} L}\right)\right\}}{\sqrt{M}} \\
\leq \frac{3(v-u)^{2} \sqrt{3} \max \left\{p, 3 \mathbf{L}^{2}\left(\|\mathbf{I}\|_{\infty}+1\right)^{2} \ln\left(2^{6} \mathbf{L} M b^{2}\left(\|\mathbf{I}\|_{\infty}+1\right)^{2} \mathbf{L}^{2 \mathbf{L}}\right)^{(3 \mathbf{L})}\right\}}{\sqrt{M}} \\
\leq \frac{3(v-u)^{2} \sqrt{3} \max \left\{p, 3 \mathbf{L}^{2}\left(\|\mathbf{I}\|_{\infty}+1\right)^{2} \ln\left(2^{6}(M b)^{2}\left(\|\mathbf{I}\|_{\infty}+1\right) B\right)\right\}}{\sqrt{M}} \\
\leq \frac{9(v-u)^{2} \mathbf{L}\left(\|\mathbf{I}\|_{\infty}+1\right) \sqrt{\max \left\{p, \ln \left(4(M b)^{3 \mathbf{L}}\left(\|\mathbf{I}\|_{\infty}+1\right) B\right)\right\}}}{\sqrt{M}} .
\end{gathered}
\tag{13.76}
\end{align*}$$

Next observe that the fact that for all $n \in \mathbb{N}$ it holds that $n \leq 2^{n-1}$ and the fact that $\|\mathbf{I}\|_{\infty} \geq 1$ ensure that

$$4(\|\mathbf{I}\|_{\infty} + 1) \leq 2^{2} \cdot 2^{(\|\mathbf{I}\|_{\infty}+1)-1} = 2^{3} \cdot 2^{(\|\mathbf{I}\|_{\infty}+1)-2} \leq 3^{2} \cdot 3^{(\|\mathbf{I}\|_{\infty}+1)-2} = 3^{\|\mathbf{I}\|_{\infty}+1}. \tag{13.77}$$
