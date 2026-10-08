**Exercise 6.2.** Soft clustering is used to cluster five univariate data samples iteratively until K = 2 clusters. We assume normal distributions for the clusters $N(\mu_k, \sigma_k), k=1,2$. Suppose that at some point the responsibilities for the five data points are as follows:

| $v_k$ | 10 | 15 | 20 | 35 | 45 |
| $p(z_1|v_k)$ | 0.2 | 0.2 | 0.8 | 0.9 | |
| $p(z_2|v_k)$ | 0.8 | 0.8 | 0.2 | 0.1 | |

With responsibilities, calculate the expected number of samples $N_k$ in each cluster and update the coefficients $\mu_k$ and $\sigma_k$, for $k=1,2$. State the density function $p(v)$ of a point $v$ belonging to cluster $k$ and the overall density function $p(v)$. Thus update the responsibilities.

**Exercise 6.3.** The Dirichlet Process method is used to cluster the three data samples $
u_1=2.1,
u_2=3.0$ and $
u_3=4.5$ using the normal-inverse-Wishart distribution. The location m is initialized to the mean of the data. The inverse scale $\Psi$ is set to the data variance. The mean fraction $\lambda$ and degrees of freedom $
u$ are chosen most uninformative. Give values for $m, \Psi, \lambda$ and $
u$. For each of the data samples, they are the first to be considered in initialization. Calculate the parameters of the posterior normal-inverse-Wishart distribution $m_1, \Psi_1, \lambda_1$ and $
u_1$. Suppose $\mu_1$ and $\Sigma_1$ are not drawn from the posterior distribution, but set to $\mu_1=m_1$ and $\Sigma_1=\Psi_1$. For which value of concentration $\alpha$ does a new cluster favoured?

# Bibliography

+   Ghosh, J. & Ramamorthi, R. (2003), *Bayesian Nonparametrics*, Springer Series in Statistics, Springer.
Gonzales, R. & Woods, R. (2018), *Digital Image Processing*, 4 edn, Pearson.
McLlan, G. & Krishnan, T. (2007), *The EM Algorithm and Extensions*, Wiley Series in Probability and Statistics, 2 edn, Wiley.