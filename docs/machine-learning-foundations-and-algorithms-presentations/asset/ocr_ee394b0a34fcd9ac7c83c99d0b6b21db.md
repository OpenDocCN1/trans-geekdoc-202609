# KL for Gaussian Distributions

We can also compute the KL for Gaussian densities in closed form:

```
$KL(\\mathcal{N}_0|\mathcal{N}_1) = \frac{1}{2} \left\{ \text{tr}(\mathbf{\Sigma}_1^{-1} \mathbf{\Sigma}_0) + \log \frac{|\mathbf{\Sigma}_1|}{\mathbf{\Sigma}_0|} + (\mathbf{\mu}_1 - \mathbf{\mu}_0)^T \mathbf{\Sigma}_1^{-1} (\mathbf{\mu}_1 - \mathbf{\mu}_0) - k \right\}$
```

![](bbox=[0.548, 0.315, 0.994, 0.715])

+   - **1st term**: compares "shape/rotation" of distributions
- **2nd term**: compares entropies of distribution
- **3rd term**: compares means of distributions
  - Measured in metric space defined by $\mathbf{\Sigma}_1^{-1}$
  - Higher dissimilarity if there is less variance of $\mathcal{N}_1$ in the update direction of the means