m \in \{1, 2, \ldots, M\}, be functions, assume for all $x \in E$ that $(X_{x,m}, Y_m)$, $m \in \{1, 2, \ldots, M\}$, are i.i.d. random variables, let $L, b \in (0, \infty)$ satisfy for all $x, y \in E$, $m \in \{1, 2, \ldots, M\}$ that

```
$$\begin{align*} |X_{x,m} - Y_m| \leq b \quad \text{ and } \quad |X_{x,m} - X_{y,m}| \leq L \delta(x,y), \tag{13.38} \end{align*}$$
```

and let $\mathbf{R}: E \to [0, \infty)$ and $\mathfrak{R}: E \times \Omega \to [0, \infty)$ satisfy for all $x \in E$, $\omega \in \Omega$ that

```
$$\begin{align*} \mathbf{R}(x) = \mathbb{E}\left[\mathbb{E}\left[X_{x,1} - Y_1|^2\right]\right] \quad \text{ and } \quad \mathfrak{R}(x, \omega) = \frac{1}{M} \left[\sum_{m=1}^M |X_{x,m}(\omega) - Y_m(\omega)|^2\right]. \tag{13.39} \end{align*}$$
```

Then

+   - it holds that $\Omega \ni \omega \mapsto \sup_{x \in E}|\mathfrak{R}(x, \omega) - \mathbf{R}(x)| \in [0, \infty)$ is $\mathcal{F}/\mathcal{B}([0, \infty))$-measurable and
- it holds for all $p \in [2, \infty)$, $c \in (0, \infty)$ that

```
$$\begin{align*} \left(\mathbb{E}\left[\sup_{x \in E}|\mathfrak{R}(x) - \mathbf{R}(x)|^p\right]\right)^{1/p} \leq \left(c^{(E, \delta, \frac{cb\sqrt{p-1}}{2L\sqrt{M}})}\right)^{1/p} \left[\frac{2(c+1)b^2\sqrt{p-1}}{\sqrt{M}}\right]. \tag{13.40} \end{align*}$$
```

(cf. Definition 4.3.2).

Proof of Lemma 13.3.1. Throughout this proof, for every $x \in E$, $m \in \{1, 2, \ldots, M\}$ let $\mathcal{Y}_{x,m}: \Omega \to \mathbb{R}$ satisfy $\mathcal{Y}_{x,m} = |X_{x,m} - Y_m|^2$. Observe that the assumption that for all $x \in E$ it holds that $(X_{x,m}, Y_m)$, $m \in \{1, 2, \ldots, M\}$, are i.i.d. random variables implies that for all $x \in E$ it holds that

```
$$\begin{align*} \mathbb{E}[\mathfrak{R}(x)] = \frac{1}{M} \left[\sum_{m=1}^M \mathbb{E}\left[|X_{x,m} - Y_m|^2\right]\right] = \frac{M \mathbb{E}\left[|X_{x,1} - Y_1|^2\right]}{M} = \mathbf{R}(x). \tag{13.41} \end{align*}$$
```

Furthermore, note that the assumption that for all $x \in E$, $m \in \{1, 2, \ldots, M\}$ it holds that $|X_{x,m} - Y_m| \leq b$ shows that for all $x \in E$, $m \in \{1, 2, \ldots, M\}$ it holds that

```
$$\begin{align*} \mathbb{E}\left[|\mathcal{Y}_{x,m}|\right] &= \mathbb{E}\left[|X_{x,m} - Y_m|^2\right] \leq b^2 < \infty, \tag{13.42} \\ \mathcal{Y}_{x,m} - \mathbb{E}[\mathcal{Y}_{x,m}] &= |X_{x,m} - Y_m|^2 - \mathbb{E}\left[|X_{x,m} - Y_m|^2\right] \leq |X_{x,m} - Y_m|^2 \leq b^2, \tag{13.43} \end{align*}$$
```

and

```
$$\begin{align*} \mathbb{E}[\mathcal{Y}_{x,m}] - \mathcal{Y}_{x,m} &= \mathbb{E}\left[|X_{x,m} - Y_m|^2\right] - |X_{x,m} - Y_m|^2 \leq \mathbb{E}\left[|X_{x,m} - Y_m|^2\right] \leq b^2. \tag{13.44} \end{align*}$$
```

Observe that (13.42), (13.43), and (13.44) ensure for all $x \in E$, $m \in \{1, 2, \ldots, M\}$, $p \in (0, \infty)$ that

```
$$\begin{align*} \left(\mathbb{E}\left[|\mathcal{Y}_{x,m} - \mathbb{E}[\mathcal{Y}_{x,m}]|^p\right]\right)^{1/p} \leq \left(\mathbb{E}\left[b^{2p}\right]\right)^{1/p} = b^2. \tag{13.45} \end{align*}$$
```