(i) it holds for all $x \in E$ that $\mathbb{E}[|Z_x|] < \infty$,
(ii) it holds that $\Omega \supseteq \omega \to \sup_{x \in E}[Z_x(\omega) - \mathbb{E}[Z_x]] \in [0, \infty)$ is $\mathcal{F}/\mathcal{B}([0, \infty))$-measurable, and
(iii) it holds for all $p \in [2, \infty)$, $r \in (0, \infty)$ that

\[
\begin{gather*}
\left( \mathbb{E}\left[ \sup_{x \in E} |Z_x - \mathbb{E}[Z_x]|^p \right] \right)^{1/p} \\
\leq 2 \big(\mathcal{C}^{(E, \delta, r)}\big)^{1/p} \left[ Lr + \frac{\sqrt{p - 1}}{\sqrt{M}} \left( \sup_{x \in E} \max_{n \in \{1, \dots, M\}} \left( \mathbb{E}\left[ |Y_{x, m} - \mathbb{E}[Y_{x, m}]|^p \right] \right)^{1/p} \right) \right] 
\end{gather*} \tag{13.29}

(cf. Definition 4.3.2).

Proof of Lemma 13.2.4. Observe that the assumption that for all $x \in E$, $m \in \{1, 2, \dots, M\}$ it holds that $\mathbb{E}[|Y_{x, m}]| < \infty$ proves that for all $x \in E$ it holds that

\[
\mathbb{E}[|Z_x|] = \mathbb{E}\left[\frac{1}{M}\sum_{m = 1}^{M}Y_{x, m}\right] \leq \frac{1}{M}\sum_{m = 1}^{M}\mathbb{E}[|Y_{x, m}]| \leq \max_{m \in \{1, 2, \dots, M\}}\mathbb{E}[|Y_{x, m}]| < \infty. \tag{13.30}

This establishes item (i). Note that (13.27) demonstrates that for all $x$, $y \in E$ it holds that

\[
|Z_x - Z_y| = \frac{1}{M}\left|\left[\sum_{m = 1}^{M}Y_{x, m}\right] - \left[\sum_{m = 1}^{M}Y_{y, m}\right]\right| \leq \frac{1}{M}\left[\sum_{m = 1}^{M}|Y_{x, m} - Y_{y, m}|\right] \leq L \delta(x, y). \tag{13.31}

Item (i) and Lemma 12.3.5 therefore prove item (ii). It thus remains to show item (iii). For this observe that item (i), (13.31), and Lemma 13.2.3 imply that for all $p \in [1, \infty)$, $r \in (0, \infty)$ it holds that

\[
\left( \mathbb{E}\left[ \sup_{x \in E}|Z_x - \mathbb{E}[Z_x]|^p \right] \right)^{1/p} \leq \big(\mathcal{C}^{(E, \delta, r)}\big)^{1/p}\left[ 2Lr + \sup_{x \in E}\left( \mathbb{E}\left[ |Z_x - \mathbb{E}[Z_x]|^p \right] \right)^{1/p} \right] \tag{13.32}

(cf. Definition 4.3.2). Furthermore, note that (13.30) and Corollary 13.1.6 (applied to $(d \frown 1, (X_m)_{m \in \{1, \dots, M\}}) \frown (Y_{x, m})_{m \in \{1, \dots, M\}}$ for $x \in E$ in the notation of Corollary 13.1.6) ensure that for all $x \in E$, $p \in [2, \infty)$, $r \in (0, \infty)$ it holds that

\[
\begin{gather*}
\left( \mathbb{E}\left[ |Z_x - \mathbb{E}[Z_x]|^p \right] \right)^{1/p} = \left( \mathbb{E}\left[\left|\frac{1}{M}\sum_{m = 1}^{M}Y_{x, m} - \mathbb{E}\left[\frac{1}{M}\sum_{m = 1}^{M}Y_{x, m}\right]\right|^p\right]\right)^{1/p} \\
\leq \frac{2\sqrt{p - 1}}{\sqrt{M}}\left[ \max_{m \in \{1, \dots, M\}}\left( \mathbb{E}\left[ |Y_{x, m} - \mathbb{E}[Y_{x, m}]|^p \right] \right)^{1/p} \right]^{1/p}. \tag{13.33}
\end{gather*}

Combining this with (13.32) shows that for all $p \in [2, \infty)$, $r \in (0, \infty)$ it holds that

\[
\begin{gather*}
\left( \mathbb{E}\left[ \sup_{x \in E}|Z_x - \mathbb{E}[Z_x]|^p \right] \right)^{1/p} \\
\leq \big(\mathcal{C}^{(E, \delta, r)}\big)^{1/p}\left[ 2Lr + \frac{2\sqrt{p - 1}}{\sqrt{M}}\left( \sup_{x \in E}\max_{m \in \{1, \dots, M\}}\left( \mathbb{E}\left[ |Y_{x, m} - \mathbb{E}[Y_{x, m}]|^p \right] \right)^{1/p} \right) \right] \\
= 2\big(\mathcal{C}^{(E, \delta, r)}\big)^{1/p}\left[ Lr + \frac{\sqrt{p - 1}}{\sqrt{M}}\left( \sup_{x \in E}\max_{m \in \{1, \dots, M\}}\left( \mathbb{E}\left[ |Y_{x, m} - \mathbb{E}[Y_{x, m}]|^p \right] \right)^{1/p} \right) \right]. \tag{13.34}
\end{gather*}

The proof of Lemma 13.2.4 is thus complete. \square