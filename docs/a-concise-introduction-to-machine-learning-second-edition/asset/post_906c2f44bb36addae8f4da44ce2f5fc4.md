
This way of generating data is known as the *Chinese Restaurant Process* (CRP). Many Chinese restaurants feature round tables with a centre that can be turned. The various dishes are placed there, and the diners can share by turning the centre. Data generation is likened to a hypothetical Chinese restaurant with an infinite variety of tables and each table can seat as many diners as necessary. The first customer sits at the first table and orders a variety of food. This determines the distribution. What they eat fancy corresponds to a sample data. The second customer might choose to sit at the same table. They will eat from the same selection of food, but not exactly as the first customer. They sample a distinct set of food. On the other hand, they might choose to sit at a new table and order a different set of dishes which constitutes the distribution of the second process. As new customers arrive, they either sit at an available open table or open a new one.

Since the final number of customers $V$ is finite, so is the number of tables $K$. The final configuration reached it is unique up to the relabeling of tables. This means there are $K!$ equivalent ways this configuration could have been reached. In this turn the order in which the customers arrive is of no importance. If a different ordering the first customer sits at a different table which becomes the first table, we relabel this table to 1 and change all labels.

## 6.7 Dirichlet Process

Having considered the process of how the dataset is generated, we need to change our viewpoint and deduce the number of clusters and which samples belong to which data. As before with Bayesian mixtures, we choose a concentration parameter $\alpha$ and prior probability distributions, and deduce posterior probabilities from the data using Gibbs sampling. However, now $K$ is the current number of clusters and is variable. The normal, inverse Wishart distribution with parameters $m$, $\Psi$ and $\nu$ are used as prior to illustrate.

At initialization stage the samples are considered in a random order. Let $\mathbf{v}_1$ be first considered. It also constitutes the first cluster. The posterior normal, inverse Wishart distribution of this cluster is calculated from the prior as

$$ \begin{aligned} \mathbf{m}_1 &= \frac{\mathbf{v}_1}{\lambda + 1} \\ \lambda_1 &= \lambda \\ \nu_1 &= \nu + 1 \\ \Psi_1 &= \Psi + \frac{\lambda}{\lambda + 1}(\mathbf{v}_1 - \mathbf{m})(\mathbf{v}_1 - \mathbf{m})^T \end{aligned} $$

A covariance matrix $\mathbf{\Sigma}_1$ and mean $\boldsymbol{\mu}_1$ are drawn from this distribution for this cluster.

![](img/c6c76bf52016db7e78a5e30d4766ef81_213_0.png)
![](img/c6c76bf52016db7e78a5e30d4766ef81_213_1.png)
![](img/c6c76bf52016db7e78a5e30d4766ef81_213_2.png)

(a) Initial cluster assignment.
(b) Cluster assignment after 10 iterations.
(c) Cluster assignment after 20 iterations.
6.12: Dirichlet process method example.

$v_n$ is the $n^{th}$ sample considered and $\mathcal{D}_n = \{v_1, \dots, v_{n-1}\}$. That is $\mathcal{D}_n$ is the set of all samples considered so far and their cluster assignments.
For $k=1, \dots, K$, where $K$ is the current number of clusters, we calculate the probabilities that $v_n$ belongs to cluster $k$ given the samples in $\mathcal{D}_n$ and their cluster assignments,

$$p(z_{n,k}=1|\mathcal{D}_n, \alpha, \boldsymbol{m}, \boldsymbol{\lambda}, \mathbf{\Psi}, \nu) = p(z_{n,k}=1|\mathcal{D}_n, \alpha)p(v_n|\mathcal{D}_n, z_{n,k}=1, \boldsymbol{m}, \boldsymbol{\lambda}, \mathbf{\Psi}, \nu)$$

following the product rule. Now, following the Chinese Restaurant Process,

$$p(z_{n,k}=1|\mathcal{D}_n, \alpha) = \frac{n_k}{n-1+\alpha}$$

where $n_k$ is the number of samples assigned to cluster $k$. On the other hand,

$$p(v_n|\mathcal{D}_n, z_{n,k}=1, \boldsymbol{m}, \mathbf{\Psi}, \nu) \approx \frac{1}{\sqrt{|2\pi\Sigma_k|}} \exp (-\frac{1}{2}(v_n-\mu_k)^T\Sigma_k^{-1}(v_n-\mu_k)) \quad (6.14)$$

So the data $\mathcal{D}_n$, and the current cluster assignments are not used directly, but indirectly via the current $\boldsymbol{\mu}_k$ and $\boldsymbol{\Sigma}_k$.

We also calculate the probability that $v_n$ belongs to a, so far unseen, empty cluster. It is

$$p(z_{n,K+1}=1|\mathcal{D}_n, \alpha, \boldsymbol{m}, \boldsymbol{\lambda}, \mathbf{\Psi}, \nu) =$$

The first factor is

$$p(z_{n,K+1}=1|\mathcal{D}_n, \alpha) = \frac{\alpha}{n-1+\alpha}$$

![](img/c6c76bf52016db7e78a5e30d4766ef81_214_0.png)

(a) Initial cluster assignment.
(b) Cluster assignment after 10 iterations.
(c) Cluster assignment after 20 iterations.
Figure 6.13: Dirichlet process method example.

according to the Chinese Restaurant Process. The dataset $\mathcal{D}_n$ only influences this factor by its current size $n-1$. The other factor is the probability of $\mathbf{v}_n$ belonging to an empty cluster. Since this cluster is still empty, its distribution is completely determined by the prior.

$$p(\mathbf{v}_n, \tilde{z}_n, K+1 = 1, \mathbf{m}, \boldsymbol{\lambda}, \boldsymbol{\nu}) = \frac{1}{\sqrt{2\pi}} \exp\left(-\frac{1}{2}(\mathbf{v}_n - \mathbf{m})^T \boldsymbol{\nu}^{-1}(\mathbf{v}_n - \mathbf{m})\right)$$

Having calculated these $K+1$ probabilities, they are used to sample which cluster $v_n$ belongs to, either of the existing clusters or the empty cluster. If the former, the posterior normal, inverse Wishart distribution of that cluster needs to be updated and a new covariance matrix mean to be drawn from it. If the latter, this cluster may be empty and the parameters $\mathbf{m}_{k_n}, \boldsymbol{\lambda}_{k_n},$ and $\boldsymbol{\nu}_{k_n}$ of the posterior, normal, inverse Wishart distribution need to be calculated. Both are updated according to $K+1$. The prior gets updated to the posterior by one sample $\mathbf{v}_n$. A covariance matrix $\boldsymbol{\Sigma}_{K+1}$ and mean $\boldsymbol{\mu}_{K+1}$ are drawn from this distribution.

Once samples have been considered, the initialization is complete. While Figures 6.12 and 6.13 show different results, they both arrive at clusters with proportions approximately 0.5 and 0.4, which agrees with the choice when the data was generated.
