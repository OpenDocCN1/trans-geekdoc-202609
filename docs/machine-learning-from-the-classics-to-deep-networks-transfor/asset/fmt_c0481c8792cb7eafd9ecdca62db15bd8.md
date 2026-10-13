
$p(\mathbf{x}) = \sum\limits_{k = 1}^{K}P_{k}\mathcal{N}\left( \mathbf{x}|\mathbf{\mu}_{k},Q_{k}^{- 1} \right),\quad\mathbf{x} \in \mathbb{R}^{l}.$

![Equation](images/B9780443292385000196/si154.png)

The task is to estimate the unknown parameters (`P[k]`, `μ[k]`, `Q[k]`), $k = 1, 2, \dots, K$. We already know that this is a typical task with latent variables, and the complete set comprises (`x[n]`, `k[n]`), $n = 1, 2, \dots, N$, with `k[n]` being the index of the respective mixture, $k[n] = 1, 2, \dots, K$. In Section [12.6](#Chp012_583-634_B9780443292385000184.xhtml), the information about each of the latent variables, `k[n]`, entered into the problem via the posterior `P(k[n]|x[n])` for every time instant `n`, the summation over all possible values of `k[n]` was performed, and hence one could drop out the time index. However, in the current context, a different path has to be followed and we have to consider the latent variables together with their corresponding time index. To this end, and following [13], an auxiliary latent random vector is introduced, `z[n] ∈ ℝ^(K)`, for each observation, $n = 1, 2, \dots, N$. Its components take binary values, such as

$z_{n_{k}} \in \{ 0,1\}\quad{and}\quad\sum\limits_{k = 1}^{K}z_{n_{k}} = 1,$

![Equation](images/B9780443292385000196/si162.png)(13.49)

and they are used as indicators of the respective mixture from which the observation at time `n`, `x[n]`, was drawn; that is, if `z[n[k]] = 1` it indicates that `x[n]` was drawn from the `k`th distribution. Obviously,
