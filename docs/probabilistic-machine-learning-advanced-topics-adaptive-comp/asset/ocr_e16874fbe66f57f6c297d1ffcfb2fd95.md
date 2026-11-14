![](bbox=[0.26, 0.09, 0.39, 0.34])

![](bbox=[0.57, 0.09, 0.79, 0.34])

Figure 12.6: (a) A mixture model represented as an “unrolled” DPGM. (b) After integrating out the continuous latent parameters.

where \(\boldsymbol{\beta} = (\mathbf{m}_0, \mathbf{V}_0, \mathbf{S}_0, \nu_0)\) are the hyper-parameters for the class-conditional densities. We now discuss how to compute these terms.

Suppose we use a symmetric prior of the form \(\boldsymbol{\pi} \sim \text{Dir}(\boldsymbol{\alpha})\), where \(\alpha_k = \alpha/K\), for the mixing weights. Then we can obtain the first term in Equation (12.53), from Equation (3.96), where

\(p(z_1, \dots, z_N | \alpha) = \frac{\Gamma(\alpha)}{\Gamma(N + \alpha)} \prod_{k=1}^K \frac{\Gamma(N_k + \alpha/K)}{\Gamma(\alpha/K)}\) (12.54)

Hence

\(p(z_i = k | \mathbf{z}_{-i}, \alpha) = \frac{p(\mathbf{z}_{1:N} | \alpha)}{p(\mathbf{z}_{-i} | \alpha)} = \frac{1}{\frac{\Gamma(N+1+\alpha)}{\Gamma(N+\alpha-1)}} \times \frac{\Gamma(N_k + \alpha/K)}{\Gamma(N_{k,-i} + \alpha/K)}\) (12.55)

\(= \frac{\Gamma(N + \alpha - 1)}{\Gamma(N + \alpha)} \frac{\Gamma(N_{k,-i} + 1 + \alpha/K)}{\Gamma(N_{k,-i} + \alpha/K)} = \frac{N_{k,-i} + \alpha}{N + \alpha - 1}\) (12.56)

where \(N_{k, -i} \triangleq \sum_{n \neq i} \mathbb{I}(z_n = k) = N_k - 1\), and where we exploited the fact that \(\Gamma(x+1) = x\Gamma(x)\).

To obtain the second term in Equation (12.53), which is the posterior predictive distribution for \(\mathbf{x}_i\) given all the other data and all the assignments, we use the fact that

\(p(\mathbf{x}_i | \mathbf{x}_{-i}, \mathbf{z}_{-i}, z_i = k, \boldsymbol{\beta}) = p(\mathbf{x}_i | \mathcal{D}_{-i,k}, \boldsymbol{\beta})\) (12.57)

where \(\mathcal{D}_{-i,k} = \{\mathbf{x}_j : z_j = k, j \neq i\}\) is all the data assigned to cluster \(k\) except for \(\mathbf{x}_i\). If we use a conjugate prior for \(\boldsymbol{\theta}_k\), we can compute \(p(\mathbf{x}_i | \mathcal{D}_{-i,k}, \boldsymbol{\beta})\) in closed form. Furthermore, we can efficiently update these predictive likelihoods by caching the sufficient statistics for each cluster. To compute the above expression, we remove \(\mathbf{x}_i\)'s statistics from its current cluster (namely \(z_i\)), and then evaluate \(\mathbf{x}_i\) under each cluster's posterior predictive distribution. Once we have picked a new cluster, we add \(\mathbf{x}_i\)'s statistics to this new cluster.