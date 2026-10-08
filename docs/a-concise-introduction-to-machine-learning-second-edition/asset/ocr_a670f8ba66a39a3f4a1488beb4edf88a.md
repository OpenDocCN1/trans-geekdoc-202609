the scaled sample covariance matrix. The posterior then has parameters

```
$$\begin{aligned} \mathbf{m}^{	ext{post}} &= \lambda\mathbf{m} + N\mathbf{v} \ \lambda^{	ext{post}} &= \lambda + N, \ \nu^{	ext{post}} &= \nu + N, \ \Psi^{	ext{post}} &= \Psi + S + \frac{\lambda N}{\lambda + N}(\mathbf{v} - \mathbf{m})^T \end{aligned}$
```

In particular, if $N=1$, we have one single data point $\mathbf{v} = \mathbf{s}$ and $S=0$. With this,

```
$$\begin{aligned} \mathbf{m}^{	ext{post}} &= \lambda\mathbf{v} \ \lambda^{	ext{post}} &= \lambda + 1, \ \nu^{	ext{post}} &= \nu + 1, \ \Psi^{	ext{post}} &= \Psi + \frac{\lambda}{\lambda+1}(\mathbf{v} - \mathbf{m})^T \end{aligned}$ (6.12)
```

Thus the data are considered one at a time and the posterior is calculated sequentially.

However, above does not consider the probabilities of a sampling belonging to a cluster governed by a Dirichlet prior distribution with parameter $\alpha = (\alpha/K, \dots, \alpha/K)$. We start with a random assignment of the indicator variables $z_1, \dots, z_n$. For each cluster $k$, let $N_k$ be the number of samples in $k$ with this assignment. We calculate the parameters $\mathbf{m}_k, \mathbf{v}_k, \nu_k$ of the posterior, normal, inverse Wishart distribution for each cluster and $\mu_k, \\mathbf{\Sigma}_k$ from this distribution. Gibbs sampling is used to select and reassign samples to clusters in a random order. To end this, a random sample $v_n$ is its current cluster assignment. Let it be the dataset without this sample, $D \setminus \{v_n\}$. It needs to be removed from cluster $l$ by returning to the $l^{th}$ parameters of the normal, inverse Wishart distribution for the $l^{th}$ cluster. Using (6.12) with the scalar parameters $\lambda$ and $\nu$, we get

```
$$\begin{aligned} \mathbf{m}_l^{	ext{prior}} &= \lambda\mathbf{m}_l + v_n \ \lambda_l^{	ext{prior}} &= \lambda + 1, \ \nu_l^{	ext{prior}} &= \nu + 1, \ \Psi_l^{	ext{prior}} &= \Psi + \frac{\lambda}{\lambda+1}(v_n - \mathbf{m}_l)(v_n - \mathbf{m}_l)^T \end{aligned}$
```

Note that this is independent of the order, in which samples were assigned clusters. A new mean $\mu_l$ and covariance matrix $\mathbf{\Sigma}_l$ are drawn from this distribution, and $N_l$ is replaced by $N_l-1$.

We calculate for $k=1, \dots, K$ the probabilities that $\mathbf{v}_n$ belongs to cluster $k$ given all the other data samples and their assignments,

```
$p(z_{n,k}=1|D \setminus \{v_n\}, \alpha, \mathbf{m}, \lambda, \Psi, \nu) = \n$nn$ $p(z_{n,k}=1|D \setminus \{v_n\}, \alpha)p(v_n|D \setminus \{v_n\}, k=1, \lambda, \Psi, \nu)$ (6.13)
```