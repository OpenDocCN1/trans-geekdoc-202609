Then E_{Zg}(S_n; Z) = 0 and g(S_n; z) is 2ε uniformly stable. Theorem 7.24 implies that with probability at least 1 − δ/2,

$\bar{g}(S_{n+1}) \le 2[\log_2 n]\,\epsilon(1+2.5\ln(2/\delta)), \tag{7.2}$

where

$\bar{g}(S_{n+1}) = \frac{1}{n}\sum_{i=1}^{n}\left[\left(\mathbb{E}_{\mathcal A}\phi(\mathcal A(S_{n+1}^{(i)}),\mathcal D)-\mathbb{E}_{\mathcal A}\phi(\mathcal A(S_{n+1}^{(i)}),Z_i)\right) - \underbrace{\left(\mathbb{E}_{S_{n+1}^{(i)}}\mathbb{E}_{\mathcal A}\phi(\mathcal A(S_{n+1}^{(i)}),\mathcal D)-\mathbb{E}_{S_{n+1}^{(i)}}\mathbb{E}_{\mathcal A}\phi(\mathcal A(S_{n+1}^{(i)}),Z_i)\right)}_{\Delta_n}\right].$

Here S_{n+1} = S_n ∪ {Z_{n+1}} with Z_{n+1} ∼ 𝒟 independent of S_n. Moreover, as in Theorem 7.24, we use the notation S_{n+1}^{(i)} = {Z_1, …, Z_{i−1}, Z_{n+1}, Z_{i+1}, …, Z_n}.

In (7.1), we observe that E_{S_n} E_𝒜 φ(𝒜(S_n), 𝒟) is a number that depends on 𝒟, and E_{S_n} E_𝒜 φ(𝒜(S_n), Z_i) depends only on Z_i. Therefore by changing S_n to S_{n+1}^{(i)} and Z_i′ to Z_i, we obtain the following equivalent form of (7.1). With probability at least 1 − δ/2,

$\begin{aligned}
\Delta_n &= \frac{1}{n}\sum_{i=1}^{n}\left[\mathbb{E}_{S_{n+1}^{(i)}}\mathbb{E}_{\mathcal A}\phi(\mathcal A(S_{n+1}^{(i)}),\mathcal D)-\mathbb{E}_{S_{n+1}^{(i)}}\mathbb{E}_{\mathcal A}\phi(\mathcal A(S_{n+1}^{(i)}),Z_i)\right] \\
&\le (1-\alpha)\mathbb{E}_{S_n}\mathbb{E}_{\mathcal A}\phi(\mathcal A(S_n),\mathcal D)+\epsilon_n(\delta/2) \\
&\le (1-\alpha)\mathbb{E}_{S_n}\mathbb{E}_{\mathcal A}\phi(\mathcal A(S_n),S_n)+\epsilon_n(\delta/2)+(1-\alpha)\epsilon. \tag{7.3}
\end{aligned}$

The first inequality is equivalent to (7.1). The second inequality used Theorem 7.2. It follows from the union bound that with probability 1 − δ, both (7.2) and (7.3) hold. This implies that

$\begin{aligned}
\mathbb{E}_{\mathcal A}\phi(\mathcal A(S_n),\mathcal D)
&\le \frac{1}{n}\sum_{i=1}^{n}\left[\mathbb{E}_{\mathcal A}\phi(\mathcal A(S_{n+1}^{(i)}),\mathcal D)\right]+\epsilon \\
&= \frac{1}{n}\sum_{i=1}^{n}\left[\mathbb{E}_{\mathcal A}\phi(\mathcal A(S_{n+1}^{(i)}),Z_i)\right]+\bar{g}(S_{n+1})+\Delta_n+\epsilon \\
&\le \frac{1}{n}\sum_{i=1}^{n}\left[\mathbb{E}_{\mathcal A}\phi(\mathcal A(S_{n+1}^{(i)}),Z_i)\right]+2[\log_2 n]\epsilon(1+2.5\ln(2/\delta)) \\
&\quad +(1-\alpha)\mathbb{E}_{S_n}\mathbb{E}_{\mathcal A}\phi(\mathcal A(S_n),S_n)+\epsilon_n(\delta/2)+(2-\alpha)\epsilon \\
&\le \frac{1}{n}\sum_{i=1}^{n}\left[\mathbb{E}_{\mathcal A}\phi(\mathcal A(S_n),Z_i)\right]+2[\log_2 n]\epsilon(1+2.5\ln(2/\delta)) \\
&\quad +(1-\alpha)\mathbb{E}_{S_n}\mathbb{E}_{\mathcal A}\phi(\mathcal A(S_n),S_n)+\epsilon_n(\delta/2)+(3-\alpha)\epsilon.
\end{aligned}$

In the proof, the first inequality used uniform stability of 𝒜. The second inequality used (7.2) and (7.3). The third inequality used the uniform stability of 𝒜. □