# # Full-Dataset Lower Bound

$$\mathcal{L}(\{q_i\}, p) = \frac{1}{N} \sum_{i} \int q_i(z) \log p(x_i|z)dz - KL(q_i(z)||p(z))$$

+   - Introduced individual variational distribution $q_i(z)$ for each data point
- **More directed sampling:**
  - Instead of sampling from the uninformed prior $p(z)$ ...
  - ... we can now sample from the variational distributions $q_i(z) \approx p(z|x_i)$
  - Each $q_i(z)$ will produce **samples with high** $p(x|z)$ **once optimized**!

+   - **Integral is outside the log:**
  - only one sample from $q_i(z)$ needed to obtain unbiased estimate of the lower bound
  - i.e. suitable for **stochastic gradient descent** while the marginal loglikelihood is not