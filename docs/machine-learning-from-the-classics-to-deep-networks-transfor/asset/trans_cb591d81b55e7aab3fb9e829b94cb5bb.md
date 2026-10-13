
$$
\pi_{n_k} = P_{k}^{(j)}\exp\left( \frac{1}{2}\mathbb{E}_{q_{Q}^{(j)}}\left\lbrack \ln|Q_{k}| \right\rbrack - \frac{1}{2}\text{trace}\left\{ \mathbb{E}_{q_{Q}^{(j)}}\lbrack Q_{k}\rbrack\left( \mathbf{x}_{n}\mathbf{x}_{n}^{T} - \mathbf{x}_{n}\mathbb{E}_{q_{\mathbf{\mu}}^{(j)}}\lbrack\mathbf{\mu}_{k}^{T}\rbrack - \mathbb{E}_{q_{\mathbf{\mu}}^{(j)}}\lbrack\mathbf{\mu}_{k}\rbrack\mathbf{x}_{n}^{T} + \mathbb{E}_{q_{\mathbf{\mu}}^{(j)}}\lbrack\mathbf{\mu}_{k}\mathbf{\mu}_{k}^{T}\rbrack \right) \right\} \right),
$$

$$
\rho_{n_k} = \frac{\pi_{n_k}}{\sum_{k = 1}^{K}\pi_{n_k}},
$$

$$
q_{\mathcal{Z}}^{(j + 1)}(\mathcal{Z}) = \prod\limits_{n = 1}^{N}\prod\limits_{k = 1}^{K}\rho_{n_k}^{z_{n_k}}.
$$
