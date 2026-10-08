This establishes item $(\mathbf{v})$. In addition, observe that item $(\mathbf{V})$ and (4.96) establish item $(\mathbf{v})$. Next note that item $(\mathbf{III})$ ensures that for all $i \in \mathbb{N} \cap (1, \mathcal{H}(\mathbf{F}))$ it holds that

$\frac{K}{2^{i-1}} \ge \frac{K}{2^{\mathcal{H}(\mathbf{F})-1}} = \frac{K}{2^{[\log_{2} K]}} \ge \frac{K}{2^{[\log_{2} K]+1}} = \frac{K}{2K} = \frac{1}{2}.$ (4.99)

Item $(\mathbf{V})$ and (4.96) hence show that for all $i \in \mathbb{N} \cap (1, \mathcal{H}(\mathbf{F}))$ it holds that

$\mathbb{D}_{i}(\mathbf{F}) \le \frac{K}{2^{i-1}} \le \frac{3K}{2^{i-1}} \le \left( \frac{3d}{4^{r}} \right)^{d} \frac{3}{2^{i-2}}.$ (4.100)

Furthermore, note that the fact that for all $x \in [a, b]^{d}$ it holds that $\|x\|_{\infty} \le \max\{|a|, |b|\}$ and item $(\mathbf{VI})$ imply that

$\begin{aligned} \| \mathcal{T}(\mathbf{F}) \|_{\infty} \le & \max\{1, L, \max_{k \in \{1, \ldots, K\}} \|\mathbf{f}_{k}\|_{\infty}, 2[\max_{k \in \{1, \ldots, K\}} |f(\mathbf{f}_{k})|]\} \\ \le & \max\{1, L, |a|, |b|, 2[\sup_{x \in [a, b]^{d}} |f(x)|]\} . \end{aligned}$ (4.101)

This establishes item $(\mathbf{viii})$. Moreover, observe that the assumption that

$\sup_{x \in [a, b]^{d}} \left[ \min_{k \in \{1, \ldots, K\}} \delta(x, \mathbf{f}_{k}) \right] \le (b-a)r$ (4.102)

and item $(\mathbf{VII})$ demonstrate that

$\sup_{x \in [a, b]^{d}} (\mathcal{R}_{\epsilon}^{\mathbf{N}}(\mathbf{F}))(x) - f(x)| \le 2L \left[ \sup_{x \in [a, b]^{d}} \left( \min_{k \in \{1, \ldots, K\}} \delta(x, \mathbf{f}_{k}) \right) \right] \le 2L(b-a)r.$ (4.103)

This establishes item $(\mathbf{viii})$. It thus remains to prove item $(\mathbf{vi})$. For this note that items $(\mathbf{I})$ and $(\mathbf{II})$, (4.98), and (4.100) assure that

$\begin{aligned} \mathcal{P}(\mathbf{F}) &= \sum_{i=1}^{\mathcal{L}(\mathbf{F})} \mathbb{D}_{i}(\mathbf{F})(\mathbb{D}_{i-1}(\mathbf{F})+1) \\ &\le 2d \left( \frac{3d}{4^{r}} \right)^{d}(d+1) + \left( \frac{3d}{4^{r}} \right)^{d} 3 \left( 2d \left( \frac{3d}{4^{r}} \right)^{d}+1 \right) \\ &\quad + \left[ \sum_{i=3}^{\left[ \frac{\mathcal{L}(\mathbf{F})-1}{\mathcal{L}(\mathbf{F})-1} \right]} \left( \frac{3d}{4^{r}} \right)^{d} \frac{3}{2^{i-2}} \left( \left( \frac{3d}{4^{r}} \right)^{d} \frac{3}{2^{i-3}}+1 \right) + \left( \frac{3d}{4^{r}} \right)^{d} \frac{3}{2^{\mathcal{L}(\mathbf{F})-3}}+1 \right] . \end{aligned}$ (4.104)

Next note that the fact that $\frac{3d}{4^{r}} \ge 3$ ensures that

$\begin{aligned} & 2d \left( \frac{3d}{4^{r}} \right)^{d}(d+1) + \left( \frac{3d}{4^{r}} \right)^{d} 3 \left( 2d \left( \frac{3d}{4^{r}} \right)^{d}+1 \right) + \left( \frac{3d}{4^{r}} \right)^{d} \frac{3}{2^{\mathcal{L}(\mathbf{F})-3}}+1 \\ \le & \left( \frac{3d}{4^{r}} \right)^{2d} \left( 2d(d+1) + 3(2d+1) + \frac{3}{2^{\mathcal{L}(\mathbf{F})-3}}+1 \right) \\ \le & \left( \frac{3d}{4^{r}} \right)^{2d} d^{2}(4+9+12+1) = 26 \left( \frac{3d}{4^{r}} \right)^{2d} d^{2}. \end{aligned}$ (4.105)