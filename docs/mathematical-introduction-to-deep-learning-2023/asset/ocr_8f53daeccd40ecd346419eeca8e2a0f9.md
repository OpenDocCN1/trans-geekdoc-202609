*(ii)* *it holds for all* $\varepsilon \in (0, \infty)$, $x \in (\mathbb{R}^d)^M$ *that*

$$\text{Batchmean}(\text{Batchnorm}_{\beta,\gamma,\varepsilon}(x)) = \beta,$$
\tag{10.9}

*and*

*(iii)* *it holds for all* $x = ((x_i^{(m)})_{i \in \{1,2,\dots,d\}})_{m \in \{1,2,\dots,M\}} \in (\mathbb{R}^d)^M$, $i \in \{1,2,\dots,d\}$ *with* $\#(\bigcup_{m=1}^{M}\{x_i^{(m)}\}) > 1$ *that*

$$\lim\limits_{\varepsilon\searrow0}\left|\text{Batchvar}_i(\text{Batchnorm}_{\beta,\gamma,\varepsilon}(x)) - (\gamma_i)^2\right| = 0$
\tag{10.10}

*(cf. Definitions 10.1.2, 10.1.3, and 10.1.6).*

*Proof of Lemma 10.1.7. Note that* (10.1), (10.3), (10.5), *and* (10.7) *establish item* (i). *In addition, note that item* (i) *ensures that for all* $\varepsilon \in (0, \infty)$, $x = ((x_i^{(m)})_{i \in \{1,2,\dots,d\}})_{m \in \{1,2,\dots,M\}} \in (\mathbb{R}^d)^M$, $i \in \{1,2,\dots,d\}$ *it holds that*

$\begin{align*}
&\text{Batchmean}_i(\text{Batchnorm}_{\beta,\gamma,\varepsilon}(x)) = \frac{1}{M}\sum_{m=1}^{M} \left[\gamma_i \left[\frac{x_i^{(m)} - \text{Batchmean}_i(x)}{\sqrt{\text{Batchvar}_i(x) + \varepsilon}}\right] + \beta_i\right] \\
&\hspace{2.5cm}= \gamma_i \left[\frac{\frac{1}{M}\sum_{m=1}^{M} x_i^{(m)} - \text{Batchmean}_i(x)}{\sqrt{\text{Batchvar}_i(x) + \varepsilon}}\right] + \beta_i \\
&\hspace{2.5cm}= \gamma_i \left[\frac{\text{Batchmean}_i(x) - \text{Batchmean}_i(x)}{\sqrt{\text{Batchvar}_i(x) + \varepsilon}}\right] + \beta_i = \beta_i
\end{align*}
\tag{10.11}

*(cf. Definitions 10.1.2, 10.1.3, and 10.1.6). This implies item* (ii). *Furthermore, observe that* (10.11) *and item* (i) *ensure that for all* $\varepsilon \in (0, \infty)$, $x = ((x_i^{(m)})_{i \in \{1,2,\dots,d\}})_{m \in \{1,2,\dots,M\}} \in (\mathbb{R}^d)^M$, $i \in \{1,2,\dots,d\}$ *it holds that*

$\begin{align*}
&\text{Batchvar}_i(\text{Batchnorm}_{\beta,\gamma,\varepsilon}(x)) \\
&= \frac{1}{M}\sum_{m=1}^{M} \left[\gamma_i \left[\frac{x_i^{(m)} - \text{Batchmean}_i(x)}{\sqrt{\text{Batchvar}_i(x) + \varepsilon}}\right] + \beta_i - \text{Batchmean}_i(\text{Batchnorm}_{\beta,\gamma,\varepsilon}(x))\right]^2 \\
&= \frac{1}{M}\sum_{m=1}^{M} (\gamma_i)^2 \left[\frac{x_i^{(m)} - \text{Batchmean}_i(x)}{\sqrt{\text{Batchvar}_i(x) + \varepsilon}}\right]^2 \\
&= (\gamma_i)^2 \left[\frac{\frac{1}{M}\sum_{m=1}^{M} (x_i^{(m)} - \text{Batchmean}_i(x))^2}{\text{Batchvar}_i(x) + \varepsilon}\right] = (\gamma_i)^2 \left[\frac{\text{Batchvar}_i(x)}{\text{Batchvar}_i(x) + \varepsilon}\right].
\end{align*}
\tag{10.12}

Combining this with the fact that for all $x = ((x_i^{(m)})_{i \in \{1,2,\dots,d\}})_{m \in \{1,2,\dots,M\}} \in (\mathbb{R}^d)^M$, $i \in \{1,2,\dots,d\}$ with $\#(\bigcup_{m=1}^{M}\{x_i^{(m)}\}) > 1$ it holds that

$$\text{Batchvar}_i(x) > 0$
\tag{10.13}

implies item (iii). The proof of Lemma 10.1.7 is thus complete. $\square$