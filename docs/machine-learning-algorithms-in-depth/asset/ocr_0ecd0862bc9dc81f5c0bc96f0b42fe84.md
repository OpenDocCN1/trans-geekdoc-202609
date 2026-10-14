This implies the following equation.

$$\sum_i r_{ik}(x_i - \mu_k) = 0 \implies \mu_k = \frac{\sum_i r_{ik}x_i}{\sum_i r_{ik}} \tag{8.16}$$

To compute optimum $\Sigma_k$, we can use the trace identity.

$$x^T A x = \operatorname{tr}\left(x^T A x\right) = \operatorname{tr}\left(x x^T A\right) = \operatorname{tr}\left(A x x^T\right) \tag{8.17}$$

Using $\hat{\lambda}=\Sigma^{-1}$ notation, we have the following.

$$l(\Lambda) \propto -\frac{1}{2}\sum_i r_{ik}\log|\Lambda| - \frac{1}{2}\sum_i r_{ik}\operatorname{tr}\left[(x_i - \mu)(x_i - \mu)^T \Lambda\right]$$
$$= -\frac{1}{2}\sum_i r_{ik}\log|\Lambda| - \frac{1}{2}\operatorname{tr}(S_\mu \Lambda) \tag{8.18}$$

Taking the matrix derivative, we get the following equation.

$$\frac{\partial l(\Lambda)}{\partial \Lambda} = -\frac{1}{2}\sum_i r_{ik}\Lambda^{-T} - \frac{1}{2}S_\mu^T = 0$$
$$\Lambda^{-1}\sum_i r_{ik} = S_\mu^T \implies \Sigma = \frac{S_\mu^T}{\sum_i r_{ik}}$$
$$\Sigma = \frac{\sum_i r_{ik}(x_i - \mu_k)(x_i - \mu_k)^T}{\sum_i r_{ik}} = \frac{\sum_i r_{ik}x_i x_i^T}{\sum_i r_{ik}} - \mu_k \mu_k^T \tag{8.19}$$

These equations make intuitive sense; the mean of cluster $k$ is weighted by $r_{ik}$ average of all points assigned to cluster $k$, while the covariance is the weighted empirical scatter matrix. We are now ready to implement the EM algorithm for GMM from scratch! Let’s start by looking at the pseudo-code in figure 8.3.

The GMM class consists of three main functions: gmm_em, estep, and mstep. In gmm_em, we initialize the means using the K-means algorithm and initialize covariances as identity matrices. Next, we iterate between the estep that computes responsibilities (aka soft assignments) of data point $i$ to each of the $k$ clusters and the mstep that takes the responsibilities as input and computes model parameters: mean, covariance, and mixture proportions for each cluster in the Gaussian mixture model (GMM). The code in the estep and mstep functions follows the derivations in the text. In the following code