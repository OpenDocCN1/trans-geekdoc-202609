obtained over all possible permutation mappings $[n] \to [n]$. Then, we have

$$\mathbb{E}_\tau\Big[\frac{1}{|\tilde S|}\sum_{i\in\tilde S}\|\mathbf{z}_i - \bar{\mathbf{v}}_S\|^2\Big] = \frac{1}{|P_{\tilde S}|}\sum_{\tilde S\in P_{\tilde S}}\mathbb{E}_\tau\Big[\frac{1}{|\tilde S|}\sum_{i\in\tilde S}\|\mathbf{z}_i - \bar{\mathbf{v}}_S\|^2 \Big| \tilde S\Big]$$

$$= \frac{1}{|P_{\tilde S}|}\sum_{\tilde S\in P_{\tilde S}}\Big(\frac{1}{|\tilde S|}\sum_{i\in\tilde S}\mathbb{E}_\tau\big[\|\mathbf{z}_i - \bar{\mathbf{v}}_S\|^2 \mid \tilde S\big]\Big).$$

Hence, it suffices to show that, for any $i \in [n/s]$, 

$$\mathbb{E}_\tau\big[\|\mathbf{z}_i - \bar{\mathbf{v}}_S\|^2 \cdot \mathbb{1}\{\mathcal{B}_i \subseteq S\}\big] \le \frac{1}{s}\cdot\frac{1}{|S|}\sum_{i\in S}\|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2.\tag{5.8}$$

Given the random set $\mathcal{B}_i$, by the triangle and the Jensen's inequalities, we have

$$\|\mathbf{z}_i - \bar{\mathbf{v}}_S\|^2 = \Big\|\frac{1}{|\mathcal{B}_i|}\sum_{k\in\mathcal{B}_i}(\mathbf{v}_k - \bar{\mathbf{v}}_S)\Big\|^2 \le \frac{1}{|\mathcal{B}_i|}\sum_{k\in\mathcal{B}_i}\|\mathbf{v}_k - \bar{\mathbf{v}}_S\|^2.$$

Recall that $n$ is assumed to be divisible by $s$; hence, all buckets are of size $s$, i.e., $|\mathcal{B}_i| = s$. We can write the above as

$$\|\mathbf{z}_i - \bar{\mathbf{v}}_S\|^2 \le \frac{1}{s}\sum_{k\in\mathcal{B}_i}\|\mathbf{v}_k - \bar{\mathbf{v}}_S\|^2 = \frac{1}{s}\mathbb{E}_{k\sim\mathcal{B}_i}\Big[\|\mathbf{v}_k - \bar{\mathbf{v}}_S\|^2\Big],$$

where $k \sim \mathcal{B}_i$ means that $k$ is uniformly distributed over the set $\mathcal{B}_i$. Taking the conditional expectation $\mathbb{E}_\tau[\cdot|\mathcal{B}_i]$ on both sides, we get

$$\mathbb{E}_\tau\big[\|\mathbf{z}_i - \bar{\mathbf{v}}_S\|^2 \mid \mathcal{B}_i\big] \le \frac{1}{s}\mathbb{E}_{k\sim\mathcal{B}_i}\big[\|\mathbf{v}_k - \bar{\mathbf{v}}_S\|^2 \mid \mathcal{B}_i\big].\tag{5.9}$$

Note that $\mathbb{E}_\tau\big[\|\mathbf{z}_i - \bar{\mathbf{v}}_S\|^2 \cdot \mathbb{1}\{\mathcal{B}_i \subseteq S\}\big] = \mathbb{E}_\tau\big[\|\mathbf{z}_i - \bar{\mathbf{v}}_S\|^2 \mid \mathcal{B}_i\big]\,\mathbb{P}_\tau\big[\mathcal{B}_i \subseteq S\big]$. Substituting from $(5.9)$, we obtain that

$$\mathbb{E}_\tau\big[\|\mathbf{z}_i - \bar{\mathbf{v}}_S\|^2 \cdot \mathbb{1}\{\mathcal{B}_i \subseteq S\}\big] \le \frac{1}{s}\mathbb{E}_{k\sim\mathcal{B}_i}\big[\|\mathbf{v}_k - \bar{\mathbf{v}}_S\|^2 \mid \mathcal{B}_i\big]\,\mathbb{P}_\tau\big[\mathcal{B}_i \subseteq S\big].\tag{5.10}$$