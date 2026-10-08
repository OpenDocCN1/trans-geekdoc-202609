Hence, we obtain that for all $j = (j_n)_{n \in \{0,1,\ldots,L\}} : \{0,1,\ldots,L\} \rightarrow \{1,2\}$ and all $k \in \{1,2,\ldots,L\}$ it holds that

```
$\begin{align*} \mathfrak{c}_k \leq \sum_{n=0}^{k-1} \bigg[ \bigg( \prod_{m=n+1}^{k-1} (l_m \| \theta_{3-jm} \|_\infty) \bigg) \mathbf{m}_{j,n} (l_{n+1}) \| \theta_1 - \theta_2 \|_\infty \bigg] \\ = \| \theta_1 - \theta_2 \|_\infty \sum_{n=0}^{k-1} \bigg[ \bigg( \prod_{m=n+1}^{k-1} (l_m \| \theta_{3-jm} \|_\infty) \bigg) \mathbf{m}_{j,n} (l_n + 1) \bigg]. \tag{11.93} \end{align*}$
```

Moreover, note that Lemma **11.3.5** ensures that for all $j \in \{1,2\}$, $k \in \{1,2,\ldots,L\} \cap (1,\infty)$, $x \in D$ it holds that

```
$\begin{align*} \| (\boldsymbol{\mathcal{R}}_\mathrm{e}^{\mathbf{N}} (\phi_{j,k})) (x) \|_\infty \\ = \bigg\| W_{j,k} \bigg( \mathfrak{D}_{l_{k-1}}^{\mathbf{N}} \bigg( (\boldsymbol{\mathcal{R}}_\mathrm{e}^{\mathbf{N}} (\phi_{j,k-1})) (x) \bigg) + B_{j,k} \bigg\|_\infty \\ \leq \bigg[ \sup_{v \in \mathbb{R}^{l_{k-1} \times \{0\}}} \frac{\| W_{j,k}^{l_v} \|_\infty}{\| v \|_\infty} \bigg] \| \mathfrak{D}_{l_{k-1}}^{\mathbf{N}} ( (\boldsymbol{\mathcal{R}}_\mathrm{e}^{\mathbf{N}} (\phi_{j,k-1})) (x) ) \|_\infty + \| B_{j,k} \|_\infty \\ \leq l_{k-1} \| \theta_j \|_\infty \| \mathfrak{D}_{l_{k-1}}^{\mathbf{N}} ( (\boldsymbol{\mathcal{R}}_\mathrm{e}^{\mathbf{N}} (\phi_{j,k-1})) (x) ) \|_\infty + \| \theta_j \|_\infty \\ \leq l_{k-1} \| \theta_j \|_\infty \| (\boldsymbol{\mathcal{R}}_\mathrm{e}^{\mathbf{N}} (\phi_{j,k-1})) (x) \|_\infty + \| \theta_j \|_\infty \\ = (l_{k-1} \| (\boldsymbol{\mathcal{R}}_\mathrm{e}^{\mathbf{N}} (\phi_{j,k-1})) (x) \|_\infty + 1) \| \theta_j \|_\infty \\ \leq (l_{k-1} \mathbf{m}_{j,k-1} + 1) \| \theta_j \|_\infty \leq \mathbf{m}_{j,k-1} (l_{k-1} + 1) \| \theta_j \|_\infty. \tag{11.94} \end{align*}$
```

Therefore, we obtain for all $j \in \{1,2\}$, $k \in \{1,2,\ldots,L\} \cap (1,\infty)$ that

```
$\mathbf{m}_{j,k} \leq \max \{1, \mathbf{m}_{j,k-1} (l_{k-1} + 1) \| \theta_j \|_\infty \}. \tag{11.95}$
```

In addition, observe that Lemma **11.3.5** proves that for all $j \in \{1,2\}$, $x \in D$ it holds that

```
$\begin{align*} \| (\boldsymbol{\mathcal{R}}_\mathrm{e}^{\mathbf{N}} (\phi_{j,1})) (x) \|_\infty = \| W_{j,1} x + B_{j,1} \|_\infty \\ \leq \big[ \sup_{v \in \mathbb{R}^{l_0 \times \{0\}}} \frac{\| W_{j,1}^{l_v} \|_\infty}{\| v \|_\infty} \big] \| x \|_\infty + \| B_{j,1} \|_\infty \tag{11.96} \\ \leq l_0 \| \theta_j \|_\infty \| x \|_\infty + \| \theta_j \|_\infty \leq l_0 \| \theta_j \|_\infty \max \{\| a \|, \| b \|\} + \| \theta_j \|_\infty \\ = (l_0 \max \{\| a \|, \| b \|\} + 1) \| \theta_j \|_\infty \leq \mathbf{m}_{j,0} (l_0 + 1) \| \theta_j \|_\infty. \end{align*}$
```

Hence, we obtain that for all $j \in \{1,2\}$ it holds that

```
$\mathbf{m}_{j,1} \leq \max \{1, \mathbf{m}_{j,0} (l_0 + 1) \| \theta_j \|_\infty \}. \tag{11.97}$
```

Combining this with (11.95) establishes that for all $j \in \{1,2\}$, $k \in \{1,2,\ldots,L\}$ it holds that

```
$\mathbf{m}_{j,k} \leq \max \{1, \mathbf{m}_{j,k-1} (l_{k-1} + 1) \| \theta_j \|_\infty \}. \tag{11.98}$
```