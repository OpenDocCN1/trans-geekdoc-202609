For the two types of classification problems, we can directly obtain (assuming that $S_w$ is reversible):

```
$v = \left( \sum_{i=1}^{2} \sum_{j=1}^{n_i} \log (\mu_i^{-1} M_{ij}) \log(\mu_i^{-1} M_{ij})^T \right)^{-1} \log(\mu_1^{-1} \mu_2)$ . (9.42)
```

In summary, we obtain the new Lie–Fisher algorithm:

**Algorithm 9.5: Find Lie–Fisher projection geodesic**

**Input**: $\{M_{ij}\}_{i=1,j=1}^{i=2,n_i} \in G$, $M_{ij}$ represents the $j$-th sample of the $i$-th category, $n_i$ represents the number of training samples in the $i$-th category, and there are $c$ categories in total.

**Output**: the Lie algebra $v$ corresponding to Lie–Fisher projection geodesic $H_v$.

**Procedure:**

(1) Using Algorithm 9.4, calculate the inner mean $\mu$ of all Lie group samples $M_{ij}$ and the inner mean value $\mu_i$, $i=1, \dots, c$ of each category.

(2) Calculate $S_b$ and $S_w$:

$S_b = \sum_{i=1}^{c} n_i \log (\mu^{-1} \mu_i) \log (\mu^{-1} \mu_i)^T \ , \quad S_w = \sum_{i=1}^{c} \sum_{j=1}^{n_i} \log (\mu_i^{-1} M_{ij}) \log (\mu_i^{-1} M_{ij})^T$ .

(3) Find $S_w v = \Lambda S_b v$. Then, we can obtain $v$, which can generate the Lie–Fisher geodesic $H_v$ according to $\exp(tv)$, $t \in R$.

For testing the Lie group samples $T$, the category discriminant formula is as follows:

$i^* = \arg \min_{i=1, \dots, c} \|\log \left( (\exp(v^T \log(T)))^{-1} \exp(T^T \log(\mu_i)) \right)\| \ . \quad (9.43)$

Considering the computational problem, it is clear that (9.43) can also be approximated by the first-order BCH formula, so that the discriminant formula can be obtained:

$i^* = \arg \min_{i=1, \dots, c} \|v^T (\log (\mu_i - \log(T)))\| \ . \quad (9.44)$

# ### 9.4.3.3 The difference between the two forms of the Lie–Fisher algorithm

From the derivation of the two Lie–Fisher forms, regardless of the distribution characteristics of the Lie group samples, Algorithm 9.4 first maps all of them by logarithm mapping, which maps the Lie group samples to the Lie algebra linear space, and then uses the linearity of the Lie algebra space to calculate the mean and the direction of the projection. The main difference between Algorithm 9.5 and Algorithm 9.4 is that the calculation of the mean is not done in the Lie algebra space, but in the nonlinear space of the Lie group.

We can see that Algorithm 9.4 has the following advantages by direct analysis.

(1) It is computationally efficient. Map the sample to Lie algebra space only in the first step, which requires one logarithm mappings for all the samples, so that the overhead is slightly larger, but the subsequent steps are performed in the linear space and are more efficient.