let $\phi_{j,k} \in \mathbf{N}$, $k \in \{1, 2, \ldots, L\}$, $j \in \{1, 2\}$, satisfy for all $j \in \{1, 2\}$, $k \in \{1, 2, \ldots, L\}$ that

$$\phi_{j,k} = \left( (W_{1,1}, B_{1,1}), (W_{j,2}, B_{j,2}), \ldots, (W_{j,k}, B_{j,k}) \right) \in \left[\bigtimes_{i=1}^{k} \left(\mathbb{R}^{L_i \times L_{i-1}} \times \mathbb{R}^{L_i}\right)\right], \quad (11.83)$$

let $D = [a,b]^l o$, let $\mathbf{m}_{j,k} \in [0, \infty)$, $j \in \{1, 2\}$, $k \in \{0, 1, \ldots, L\}$, satisfy for all $j \in \{1, 2\}$, $k \in \{0, 1, \ldots, L\}$ that

$$\mathbf{m}_{j,k} = \begin{cases} \max\{1, |a|, |b|\} & : k = 0 \\ \max\big\{1, \sup_{x \in D} \left\| \left(\mathcal{R}_\tau^\mathbf{N} (\phi_{j,k}) (x) \right)\right\|_\infty \big\} & : k > 0, \end{cases} \quad (11.84)$$

and let $\mathbf{c}_k \in [0, \infty)$, $k \in \{0, 1, \ldots, L\}$, satisfy for all $k \in \{0, 1, \ldots, L\}$ that

$$\mathbf{c}_k = \begin{cases} 0 & : k = 0 \\ \sup_{x \in D} \left\| \left(\mathcal{R}_\tau^\mathbf{N} (\phi_{1,k}) (x) - (\mathcal{R}_\tau^\mathbf{N} (\phi_{2,k}) (x) \right) \right\|_\infty & : k > 0 \end{cases} \quad (11.85)$$

(cf. Definitions 1.2.4, 1.3.1, 1.3.4, 1.3.5, and 3.3.4). Note that Lemma 11.3.5 ensures that

$$\begin{align*} \mathbf{c}_1 &= \sup_{x \in D} \left\| \left(\mathcal{R}_\tau^\mathbf{N} (\phi_{1,1}) (x) - (\mathcal{R}_\tau^\mathbf{N} (\phi_{2,1}) (x) \right) \right\|_\infty \\ &= \sup_{x \in D} \left\| (W_{1,1} x + B_{1,1}) - (W_{2,1} x + B_{2,1}) \right\|_\infty \\ &\leq \left[\sup_{x \in D} \left\| (W_{1,1} - W_{2,1}) x \right\|_\infty\right] + \left\| B_{1,1} - B_{2,1} \right\|_\infty \\ &\leq \left[\sup_{v \in \overline{\theta}^0 / \{0\}} \left( \frac{\left\| (W_{1,1} - W_{2,1}) v \right\|_\infty}{\|v\|_\infty} \right)\right] \left[\sup_{x \in D} \|x\|_\infty\right] + \|B_{1,1} - B_{2,1}\|_\infty \\ &\leq l_0 \|\theta_1 - \theta_2\|_\infty \max\{|a|, |b|\} + \|B_{1,1} - B_{2,1}\|_\infty \\ &\leq l_0 \|\theta_1 - \theta_2\|_\infty \max\{|a|, |b|\} + \|\theta_1 - \theta_2\|_\infty \\ &= \|\theta_1 - \theta_2\|_\infty (l_0 \max\{|a|, |b|\} + 1) \leq \mathbf{m}_{1,0} \|\theta_1 - \theta_2\|_\infty (l_0 + 1). \end{align*} \quad (11.86)$$

Furthermore, observe that the triangle inequality proves that for all $k \in \{1, 2, \ldots, L\} \cap (1, \infty)$ it holds that

$$\begin{align*} \mathbf{c}_k &= \sup_{x \in D} \left\| \left(\mathcal{R}_\tau^\mathbf{N} (\phi_{1,k}) (x) - (\mathcal{R}_\tau^\mathbf{N} (\phi_{2,k}) (x) \right) \right\|_\infty \\ &= \sup_{x \in D} \left\| \left[ W_{1,k} \left( \mathfrak{A}_{k-1} \left(\mathcal{R}_\tau^\mathbf{N} (\phi_{1,k-1}) (x) \right) \right) + B_{1,k} \right] \right. \\ &\quad \quad \quad - \left[ W_{2,k} \left( \mathfrak{A}_{k-1} \left(\mathcal{R}_\tau^\mathbf{N} (\phi_{2,k-1}) (x) \right) \right) + B_{2,k} \right] \left\|_\infty \right. \end{align*} \quad (11.87)$$

$$\leq \left\| \sup_{x \in D} \left[ W_{1,k} \left( \mathfrak{A}_{k-1} \left(\mathcal{R}_\tau^\mathbf{N} (\phi_{1,k-1}) (x) \right) \right) - W_{2,k} \left( \mathfrak{A}_{k-1} \left(\mathcal{R}_\tau^\mathbf{N} (\phi_{2,k-1}) (x) \right) \right) \right] \right\|_\infty$$

$+ \|\theta_1 - \theta_2\|_\infty.$