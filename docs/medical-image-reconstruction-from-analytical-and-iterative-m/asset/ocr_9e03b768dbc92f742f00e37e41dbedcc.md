# ## 6.9.6 MAP (Green's one-step-late algorithm)

MAP stands for maximum a posteriori. The ML-EM algorithm can be changed into a MAP (i.e., Bayesian) algorithm by adding a penalty term in the denominator:

$$x_j^{\text{next}} = \frac{x_j^{\text{current}}}{\sum_i a_{ij} + \beta \frac{\partial U(x^{\text{current}})}{\partial x_j^{\text{current}}}} \sum_i a_{ij} \frac{p_i}{\sum_j a_{ij} x_j^{\text{current}}},$$ (6.80)

where $U(X)$ is the energy function defined in Section 6.8, and $\beta$ is the control parameter. This is not a true MAP algorithm because the energy function $U$ is supposed to be evaluated using the next estimate $X^{\text{next}}$, which is not yet available, hence, the term “one step late.”

This one-step-late MAP algorithm (6.80) can be modified for many applications. In emission tomography, if the projection matrix models the attenuation effects, the regularization in eq. (6.80) varies with the attenuation effects and is not uniform throughout the reconstructed image. Stronger regularization is found in one region, and weaker regularization is found in a different region. To overcome this drawback, we can replace $\sum_i a_{ij} + V$ by $(1 + V) \sum_i a_{ij}$, where

$$V = \beta \frac{\partial U(x^{\text{current}})}{\partial x_j^{\text{current}}}.$$ (6.81)

The modified version of eq. (6.80) is given as

$$x_j^{\text{next}} = \frac{1}{1 + V} \frac{x_j^{\text{current}}}{\sum_i a_{ij}} \sum_i \frac{\sum_i a_{ij} p_i}{\sum_j a_{ij} x_j^{\text{current}}},$$ (6.82)

which is simply the ML-EM algorithm (6.61) divided by $(1 + V)$. As $V \to 0$, the modified Green's one-step-late algorithm reduces to the ML-EM algorithm.

There is an alternative version of eq. (6.82) by using the approximation

$$\frac{1}{1 + V} \approx 1 - V, \text{ when } |V| \ll 1.$$ (6.83)

Then an alternative version of (6.82) is

$$x_j^{\text{next}} = (1 - V) \frac{x_j^{\text{current}}}{\sum_i a_{ij}} \sum_i \frac{\sum_i a_{ij} p_i}{\sum_j a_{ij} x_j^{\text{current}}},$$ (6.84)

If we are creative, we can develop many alternative versions of eq. (6.82). For example, to enforce $|V| < 1$, we can replace $V$ by $\frac{V}{\sqrt{1 + v^2}}$ in (6.82) and (6.84) if we want, obtaining eqs. (6.85) and (6.86), respectively.