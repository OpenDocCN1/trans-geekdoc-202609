
finite, in which case $\alpha_i$ is updated to this value. Note that when the optimal $\alpha_i$ is infinite and $d_i(x)$ is already excluded from the model, no action is necessary. In all cases, $\Sigma$ and its inverse $C$ have to be updated, since $A$ has changed.

The matrices $\mathbf{D}$ and $\Sigma$ change during the run of the algorithm. However, they stay comparatively small compared to the number $M$ of basis functions in the dictionary and the sample number $N$. The matrix $\mathbf{C}$ is subject to rank 1 updates as basis functions are added, deleted or their hyperparameters re-estimated. These rank 1 updates are the addition or subtraction of the outer product of the basis function evaluated at the sample points with itself, derived from the hyperparameter updates. However, in practice $C$ and its inverse are not calculated.

It should be noted here that the dictionary of basis functions does not need to be static; a new basis function can be created, evaluated, and possibly added to the model at any point.

In the update formula, where the logarithm of the marginal likelihood $\mathcal{L}$ is denoted by $\Delta\mathcal{L}$ and updated quantities are denoted by a:

**Addition:** In this case,

$$\Delta\mathcal{L} = \frac{Q_i^2}{S_i} + \log \frac{S_i}{Q_i^2}$$

$$\hat{\Sigma} = \left( \Sigma + \sigma^{-2}\Sigma_{ii}\mathbf{D}_i^T\mathbf{D}_i - \sigma^{-2}\Sigma_{ii}\mathbf{D}_i^T\mathbf{\Sigma} / \Sigma_{ii} \right)$$

$$\hat{\mu} = \left( \mu_i - \sigma^{-2}\mu_i\mathbf{\Sigma}^T\mathbf{D}_i / \Sigma_{ii} \right)$$

where $\Sigma_{ii} = (\alpha_i + S_i)^{-1}$ and $\mu_i = \Sigma_{ii}Q_i$.

**Deletion:** The index $j$ denotes the column of $\mathbf{D}$ which is to be removed, when $d_j$ is removed from the current model. $\Sigma_j$ is the $j^{th}$ element of $\Sigma$ and $\Sigma_{ij}$ is the $j^{th}$ element of $\mu$ is $\mu_j$.

$$\Delta\mathcal{L} = \frac{Q_j^2}{S_j} - \log \left(1 - \frac{S_j}{\alpha_j} \right)$$

$$\hat{\Sigma} = \Sigma - \frac{1}{\Sigma_{jj}}\Sigma_j\mathbf{\Sigma}_T^T$$

$$\hat{\mu} = \mu - \frac{\mu_j}{\Sigma_{jj}}\mathbf{\Sigma}_j$$

After these updates the $j^{th}$ row and column needs to be removed from $\Sigma$ and the $j^{th}$ element from $\mu$.

**Re-estimation:** Defining

$$\kappa_j = (\Sigma_{jj} + (\tilde{\alpha}_i - \alpha_i)^{-1})^{-1}$$

with $\Sigma_{jj}$ and $\Sigma_j$ as in the case of deletion, we have

$$2\Delta\mathcal{L} = \frac{Q_i^2}{S_i + (\tilde{\alpha}_i^{-1} - \alpha_i^{-1})} - \log(1 + S_i(\tilde{\alpha}_i^{-1} - \alpha_i^{-1}))$$
$$\tilde{\Sigma} = \Sigma - \kappa_j\Sigma_j^T$$
$$\hat{\mu} = \mu - \kappa\mu\Sigma_j$$

We noted that a new candidate basis function can be created and evaluated for inclusion in the model at any point in time. The model can also adapt, when a new data sample arrives. Thus, this technique is also suitable for online learning. We can calculate the logarithm of the marginal likelihood for the current model when a data sample $(\mathbf{t}_s, \mathbf{x}_s)$ is added. This means adding a row to the data matrix $\mathbf{D}$ yielding

$$\mathbf{D}_s = \begin{pmatrix} \mathbf{D} \\ d(\mathbf{x}_s)^T \end{pmatrix}$$

We have

$$\mathbf{C}_* = \sigma^2\mathbf{I} + (d(\mathbf{x}_s)^T \mathbf{A}^{-1}) (\mathbf{D}^T \mathbf{d}(\mathbf{x}_s)) = \begin{pmatrix} \mathbf{C} & \mathbf{v} \\ \mathbf{v}^T & \mathbf{v} \end{pmatrix}$$

where $\mathbf{v} = \mathbf{DA}^{-1}d(\mathbf{x}_s)$ and $v = d(\mathbf{x}_s)^T\mathbf{A}^{-1}d(\mathbf{x}_s) + \sigma^2$. Note that $\mathbf{C}_*$ is symmetric.

Using the formula for block matrices we have

$$\mathbf{C}_* = |\mathbf{C}||v - \mathbf{v}^T\mathbf{C}^{-1}\mathbf{v}|$$

$$\mathbf{C}_*^{-1} = \begin{pmatrix} \mathbf{C}^{-1} - \frac{\mathbf{C}^{-1}\mathbf{v}\mathbf{v}^T\mathbf{C}^{-1}}{1+\mathbf{v}^T\mathbf{C}^{-1}\mathbf{v}} & -\frac{\mathbf{C}^{-1}\mathbf{v}}{1+\mathbf{v}^T\mathbf{C}^{-1}\mathbf{v}} \\ -\frac{\mathbf{v}^T\mathbf{C}^{-1}}{1+\mathbf{v}^T\mathbf{C}^{-1}\mathbf{v}} & \frac{1}{1+\mathbf{v}^T\mathbf{C}^{-1}\mathbf{v}} \end{pmatrix}$$

Let $\mathbf{t}_s^T = (t_{1,s}, \dots, t_{N,s})$, we calculate

$$\mathbf{t}_s^T\mathbf{C}_*^{-1}\mathbf{t}_s = \mathbf{t}_s^T\mathbf{C}^{-1}\mathbf{t}_s - \frac{(\mathbf{t}_s^T\mathbf{C}^{-1}\mathbf{v})^2}{1+\mathbf{v}^T\mathbf{C}^{-1}\mathbf{v}}$$

Thus the logarithm of the marginal likelihood $\mathcal{L}(\mathbf{t}_s, \sigma^2)$ is $\log \mathcal{L}(\mathbf{t}, \sigma^2) + \Delta\mathcal{L}$,

$$\Delta\mathcal{L} = -\frac{1}{2} [\log 2\pi + \log |v - \mathbf{v}^T\mathbf{C}^{-1}\mathbf{v}| + \frac{1}{1+\mathbf{v}^T\mathbf{C}^{-1}\mathbf{v}}(\mathbf{t}_s^T\mathbf{C}^{-1}\mathbf{v})^2]$$

This change can be interpreted probabilistically. Using the Woodbury identity, $\Sigma$ is related to $C^{-1}$ by

$$\Sigma = A^{-1} - A^{-1}DD^T A^{-1}$$

The predictive distribution for $t_*$ has variance and mean

$$\sigma_*^2 = \sigma^2 + \mathbf{d}(\mathbf{x}_*)^T\mathbf{d}(\mathbf{x}_*)$$
$$m_* = \mathbf{d}(\mathbf{x}_*)^T\mu$$

where we used the fact that $DA^{-1}D^T = C$ in the calculation of the model. Thus $(t_* - m_*)^2/\sigma_*^2$ is the square of the difference of the sample measurement and its prediction by the current model. Thus, the change in log evidence

$$\Delta\mathcal{L} = -\frac{1}{2}[\log 2\pi + \log\sigma_*^2 + \frac{(m_* - t_*)^2}{\sigma_*^2}]$$

Hence the change is the likelihood of the new data value $t_*$ at $\mathbf{x}_*$, given the predictive distribution $\mathcal{N}(m_*,\sigma_*^2)$. Since $\sigma_* \ge \sigma$, the change lies from $-\infty$ to $\log(2\pi\sigma^2)^{-1/2}$. It can be positive. In this case, the new sample samples the model. If the likelihood of the data is small, the marginal likelihood is reduced, indicating that the model could be improved. To do so, all quantities must be updated with the new data included.

**New data sample:** In this case,

$$\Delta\mathcal{L} = \log\frac{1}{\sqrt{2\pi}\sigma_*} \exp\left(-\frac{(m_* - t_*)^2}{2\sigma_*^2}\right)$$
$$\mathbf{\Sigma} = \Sigma - \frac{1}{\sigma_*^2}\mathbf{d}(\mathbf{x}_*)\mathbf{d}(\mathbf{x}_*)^T$$
$$\hat{\mu} = \mu - \frac{1}{\sigma_*^2}\mathbf{d}(\mathbf{x}_*)$$

The algorithm can continue improving the model by considering the basis functions in turn. $\mathcal{N}(m_*,\sigma_*^2)$ Sparse Bayesian infers a predictive distribution for $t_*$ with mean and variance as given in (8.11). This predictive distribution is heavily dependent on the model, since it depends on $\mathbf{d}(\mathbf{x}_*)$ which are the basis functions included in the model evaluated at $\mathbf{x}_*$. It is customary to choose basis functions for the dictionary which decay quickly moving away from the center, or basis functions with finite, compact support. Therefore, the degenerate case is possible where $\mathbf{d}(\mathbf{x}_*)$ is close to, or equal to zero, and in this case the predictive probability distribution becomes $\mathcal{N}(0,\sigma)$ which is meaningless. The confidence we place in the predictions should only be informed by the data, and be independent of the dictionary of basis functions.

Let $\mathcal{S}$ be a subset of the samples. This could be all samples or a suitable set of neighbourhoods of $\mathbf{x}$. We estimate the probability distribution of $t_*$ to be normal with mean and variance

$$\begin{aligned} \hat{m} &= \text{mean}\{t_i\}, \ \mathbf{x}_i \in \mathcal{S} \\ \hat{\sigma}^2 &= \text{var}\{t_i\}, \ \mathbf{x}_i \in \mathcal{S} \end{aligned}$$

With this estimate, the expected change, when considering $x_*$, in the log

$$\mathbb{E}[\Delta L] = \int_{-\infty}^{\infty} \log \left( \frac{1}{\sqrt{2\pi\sigma_*^2}} \right) \exp\left(-\frac{(t_*-m_*)^2}{2\sigma_*^2}\right) dt_* = \frac{\sigma_*^2 + (m-t_*)^2}{2\sigma^2}$$
