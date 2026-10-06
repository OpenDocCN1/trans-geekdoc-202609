# EM for Gaussian Mixture Models

**Weighted Maximum Likelihood** updates:

+   - Update coefficients: $\pi = \arg \max_{\pi} \sum_{i} \sum_{k} q_{ik} \log \pi_k$
- Result: $\pi_k = \frac{\sum_{i} q_{ik}}{\sum_{k} \sum_{i} q_{ik}} = \frac{\sum_{i} q_{ik}}{N}$

+   - Update components: $oldsymbol{\mu}_k, oldsymbol{\Sigma}_k = \arg \max_{oldsymbol{\mu}_k, oldsymbol{\Sigma}_k} \sum_{i} q_{ik} \log \mathcal{N}(oldsymbol{x}_i | oldsymbol{\mu}_k, oldsymbol{\Sigma}_k)$
- Mean: $oldsymbol{\mu}_k = \frac{\sum_{i} q_{ik} oldsymbol{x}_i}{\sum_{i} q_{ik}}$
- Covariance: $oldsymbol{\Sigma}_k = \frac{\sum_{i} q_{ik}(oldsymbol{x}_i - oldsymbol{\mu}_k)(oldsymbol{x}_i - oldsymbol{\mu}_k)^T}{\sum_{i} q_{ik}}$

**Same equations as before, but now we derived them!**