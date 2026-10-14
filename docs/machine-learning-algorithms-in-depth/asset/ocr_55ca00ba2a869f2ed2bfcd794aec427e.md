Using the result derived in equation 3.12, we state that $q(x_i;\mu_i)$, which minimizes the KL divergence, is given by the following.

$$q_i(x_i)=\frac{1}{Z_i}\exp\left[E_{-q_i}\{\log p(x)\}\right]$$  
(3.17)

Here, $E_{-q_i}$ denotes the expectation over every $q_j$ except for $j=i$. To compute $q_i(x_i)$, we only care about the terms that involve $x_i$ (i.e., we can isolate them as shown in equation 3.18).

$$E_{-q_i}\{\log p(x)\}=E_{-q_i}\left\{x_i\sum_{j\in N(i)}w_{ij}x_j+\log N(x_i,\sigma^2)+\mathrm{const}\right\}$$
$$\qquad=x_i\sum_{j\in N(i)}w_{ij}\mu_j+\log N(x_i,\sigma^2)+\mathrm{const}$$  
(3.18)

Here, $N(i)$ denotes the neighbors of node $i$ and $\mu_j$ is the mean of a binary random variable.

$$\mu_j=E_{q_j}[x_j]=q_j(x_j=+1)\times(+1)+q_j(x_j=-1)\times(-1)$$  
(3.19)

Figure 3.4 shows the parametric form of our mean-field approximation for the Ising model.

![](bbox=[0.259, 0.556, 0.876, 0.765])

**Figure 3.4**  Ising model and its approximating distribution $q(x)$

To compute this mean, we need to know the values of $q_i(x_j=+1)$ and $q_i(x_j=-1)$. Let $m_i=\sum_{j\in N(i)}w_{ij}\mu_j$ be the mean value of neighbors and let $L_i^+=N(x_i=+1,\sigma^2)$ and $L_i^-=N(x_i=-1,\sigma^2)$; then, we can compute the mean as follows.