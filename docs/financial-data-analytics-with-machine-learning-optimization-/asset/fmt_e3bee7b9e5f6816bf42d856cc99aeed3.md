
10. For a Shapiro–Wilk diagnostic test on fitted residuals, say $\hat{\epsilon}_i$'s for notational simplicity, the test statistic becomes

$$W = \frac{\left(\sum_{i=1}^{n} a_i \hat{\epsilon}_{(i)}\right)^2}{\sum_{i=1}^{n} \left(\bar{\hat{\epsilon}} - \hat{\epsilon}_i\right)^2}$$

Since $\hat{\epsilon}_i = \epsilon_i + O_p\left(\frac{1}{\sqrt{n}}\right)$, where $\epsilon_i$'s are iid true random noises, and recalling that $\mathbf{a}$ is a unit vector, the numerator equals

$$\left(\sum_{i=1}^{n} a_i \epsilon_{(i)}\right)^2 + 2 \sum_{i \neq j} a_i a_j \epsilon_{(i)} O_p\left(\frac{1}{\sqrt{n}}\right) + \text{higher order terms}$$

whose first term $\left(\sum_{i=1}^{n} a_i \epsilon_{(i)}\right)^2 \approx \sum_{i=1}^{n} a_i^2 \cdot \sum_{i=1}^{n} \epsilon_i^2 = \sum_{i=1}^{n} \epsilon_i^2 \approx O_p(n)$; while by applying the Cauchy–Schwarz inequality on the square of the second cross-term,

$$\left(\sum_{i,j; i \neq j} a_i a_j \epsilon_{(i)} O_p\left(\frac{1}{\sqrt{n}}\right)\right)^2 \leq \left(\sum_{j=1}^{n} a_j \sum_{i \neq j} a_i O_p\left(\frac{1}{\sqrt{n}}\right)\right)^2 \leq \sum_{j=1}^{n} a_j^2 \cdot \left(\sum_{i \neq j} a_i O_p\left(\frac{1}{\sqrt{n}}\right)\right)^2 \leq \sum_{j=1}^{n} a_j^2 \cdot \sum_{i=1}^{n} a_i^2 \cdot \sum_{i=1}^{n} O_p\left(\frac{1}{n}\right) = O_p(1)$$

hence the first term $\left(\sum_{i=1}^{n} a_i \epsilon_{(i)}\right)^2$ is the dominating one in the numerator. Likewise, the denominator $\sum_{i=1}^{n} \left(\bar{\hat{\epsilon}} - \hat{\epsilon}_i\right)^2$ is dominated by the term $\sum_{i=1}^{n} \left(\bar{\epsilon} - \epsilon_i\right)^2$ involving true random noises only. As a result, the direct plug-in of the original test statistic is justifiable.
