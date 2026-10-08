The posterior probability that $v_n$ belongs to cluster $k$ given the sample in $\mathcal{D} \setminus \{v_n\}$ and $v_n$'s cluster assignments is

$p(z_{n,k}=1|\mathcal{D} \setminus \{v_n\\}, \alpha, \mathbf{m}, \boldsymbol{\lambda}, \boldsymbol{\Psi}, \boldsymbol{
u}) =$
np(z_{n,k}=1|\mathcal{D} \setminus \{v_n\}, \alpha)p(|\mathcal{D} \setminus \{v_n\}, z_{n,k}=1, \mathbf{m}, \boldsymbol{\lambda}, \boldsymbol{\Psi}, \boldsymbol{
u})$

In this case, we have

$p(z_{n,k}=1|\{v_n\}, \alpha) = \frac{N_k}{N-1+\alpha}$

while $p(|\mathcal{D} \setminus \{v_n\}, z_{n,k}=1, \mathbf{m}, \boldsymbol{\lambda}, \boldsymbol{
u})$ is as in Equation(6.14).
The possibility that $v_n$ belongs to an empty cluster is

$p(z_{n,K+1}=1|\{v_n\}, \alpha, \mathbf{m}, \boldsymbol{\lambda}, \boldsymbol{
u}) =$\nnp(z_{n,K+1}=1|\{v_n\}, \alpha)p(|\mathcal{D} \setminus \{v_n\}, z_{n,k}=1, \mathbf{m}, \boldsymbol{\lambda}, \boldsymbol{
u})$\n$ (Wait, the original text says $z_{n,K+1}=1, \mathbf{m}, \boldsymbol{\lambda}, \boldsymbol{
u}$ in the second part)

where

$\alpha = \frac{\alpha}{N-1+\alpha}$

and $p(|\mathcal{D} \setminus \{v_n\}, z_{n,k}=1, \mathbf{m}, \boldsymbol{\lambda}, \boldsymbol{
u})$ is as in Equation(6.14).
The sample $v_n$ is assigned to either one of the existing clusters or an empty cluster. In either case, the posterior, normal, inverse, Wishart distribution needs to be calculated and new samples for the covariance matrix and mean drawn for cluster. Listing 6.7a implements this algorithm. Figures 6.12 and 6.13 are two runs on the same data. While they start out differently, both arrive at clusters with the proportions being approximately 0.5 and 0.4 which agrees with the choice when the dataset was generated.

Recall that, when $K$ was fixed, the data generation was described as

$v_n \sim \mathcal{N}(\mu_k, \boldsymbol{\Sigma}_k)\n\pi \sim \text{Dir}(\alpha)\n\mu_k, \boldsymbol{\Sigma}_k \sim \Gamma$

where $G$ was a distribution which is zero everywhere apart from $K$ pairs $(\boldsymbol{\Sigma}_k)$, which were generated from the base distribution $G_0 = \text{NIW}(\mathbf{m}, \boldsymbol{\lambda}, \boldsymbol{
u})$ and the probability mass for these $K$ pairs followed a Dirichlet-process distribution with parameter $\alpha$.
A *Dirichlet process* extends the concept to an unknown variable number of clusters $K$. The notation is

$v_n \sim \mathcal{N}(\mu_k, \boldsymbol{\Sigma}_k)\n\mu_k, \boldsymbol{\Sigma}_k \sim \Gamma\nG \sim DP($\alpha, G_0)$