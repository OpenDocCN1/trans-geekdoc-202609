# Exercises

**Exercise 3.1.** Verify that for the transition matrix given in Equation 3.5, there is an absorbing state, if any two of $\alpha, \beta$ and $\gamma$ are both zero, but the Markov chain itself is not absorbing.

**Exercise 3.2.** The following state diagram is given with $\alpha, \beta \in [0, 1]$. What happens if $\alpha = 0$ or $eta = 0$ or both? Find a stationary distribution.

![](bbox=[0.403, 0.311, 0.596, 0.383])

**Exercise 3.3.** The following describes a system where the states are positive integers. States can only transition to the next integer up or down or remain stationary, apart from 1 which can only transition to 2 or stay. The transition probability of up is $\alpha$, while the transition probability for down is $\beta$. The stationary probability is $1-\eta$, apart from 1, where the stationary probability is $1-\\alpha$. The conditions $0 < \alpha < \beta$ and $\\alpha + \beta < 1$ hold. Draw the state diagram and show that $\mathbf{p} = (p_1, p_2, p_3, \dots)$

```
$p_k = \left( \frac{1-\eta}{\alpha+\beta} \right) \left( \frac{\alpha}{\alpha+\beta} \right)^{k-1}$
```

is a probability distribution and is the stationary distribution.

**Exercise 3.4.** Gibbs sampling for a bivariate normal target distribution.

# Bibliography

Devroye, L. (1986), *Non-Uniform Random Variate Generation*, 1 edn, Springer.

Montgomery, D. (2020), *Introduction to Statistical Quality Control*, 8 edn, John Wiley & Sons.

Norris, J. (1998), *Markov Chains*, Cambridge University Press.