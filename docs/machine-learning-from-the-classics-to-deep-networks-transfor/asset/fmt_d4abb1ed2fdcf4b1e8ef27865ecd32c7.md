
## EM Algorithm Steps

1.  **Expectation (E-step):** At the $(j+1)$-th iteration, compute $p(\mathcal{X}^{(l)}|\mathcal{X}, \boldsymbol{\xi}^{(j)})$ and
    $$Q(\boldsymbol{\xi}, \boldsymbol{\xi}^{(j)}) = \mathbb{E}[\ln p(\mathcal{X}, \mathcal{X}^{(l)}; \boldsymbol{\xi})] \tag{12.40}$$
    where the expectation is taken with respect to $p(\mathcal{X}^{(l)}|\mathcal{X}; \boldsymbol{\xi}^{(j)})$.

2.  **Maximization (M-step):** Determine $\boldsymbol{\xi}^{(j+1)}$ so that
    $$Q(\boldsymbol{\xi}^{(j+1)}, \boldsymbol{\xi}^{(j)}) \ge Q(\boldsymbol{\xi}, \boldsymbol{\xi}^{(j)}) \tag{12.41}$$

3.  **Check for convergence** according to a criterion. If it is not satisfied, go back to step 1.

A possible convergence criterion is to check whether $\|\boldsymbol{\xi}^{(j+1)} - \boldsymbol{\xi}^{(j)}\| < \epsilon$, for some user-defined constant $\epsilon$. The use of the EM algorithm presupposes that working with the joint PDF $p(\mathcal{X}, \mathcal{X}^{(l)}; \boldsymbol{\xi})$ is computationally tractable. This is, for example, the case when working within the exponential family of PDFs, where the E-step may require only the computation of a few statistics of the latent variables. The exponential family of distributions is a computationally convenient one and it is treated in more detail in Section [12.8](#Chp012_583-634_B9780443292385000184.xhtml#s0075).

### Remarks 12.3

*   The EM algorithm was proposed and given its name in the seminal 1977 paper by Arthur Dempster, Nan Laird, and Donald Rubin [12]. The paper generalized previously published results, as for example [2,38], and had a significant impact as a powerful tool in statistics. The complete convergence proof was given in [47]. See, for example, [29] for a related discussion.

*   It can be shown that the EM algorithm converges to an (in general, local) maximum of $p(\mathcal{X}; \boldsymbol{\xi})$, which was our original goal. The likelihood never decreases. The convergence is slower than the quadratic convergence of Newton-type searching techniques, although near an optimal point a speedup may be possible. However, the convergence of the algorithm is smooth and its complexity more attractive than Newton-type schemes, with no matrix inversions involved. The keen reader may obtain more information in, for example, [14,30,33,43].

*   The EM algorithm can be modified to obtain the MAP estimate. To this end, the M-step is changed to (Problem [12.4](#Chp012_583-634_B9780443292385000184.xhtml#o0095))
    $$
    \boldsymbol{\xi}^{(j + 1)} = \arg\max_{\boldsymbol{\xi}}\left\{ \mathcal{Q}(\boldsymbol{\xi},\boldsymbol{\xi}^{(j)}) + \ln p(\boldsymbol{\xi}) \right\}, \tag{12.42}
    $$
    where $p(\boldsymbol{\xi})$ is the prior PDF associated with $\boldsymbol{\xi}$, if it is considered to be a random vector.

*   The EM algorithm can be sensitive to the choice of the initial point $\boldsymbol{\xi}^{(0)}$. In practice, one can run the algorithm a number of times, starting from different initial points, and keep the best of the results. Other initialization procedures have also been used, depending on the application.
