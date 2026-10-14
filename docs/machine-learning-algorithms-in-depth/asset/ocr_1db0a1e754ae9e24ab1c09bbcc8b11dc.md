# *appendix B*
*Answers to exercises*

# 2.1 Derive full conditionals $p(x_A|x_B)$ for multivariate Gaussian distribution, where $A$ and $B$ are subsets of $x_1$, $x_2$, ..., $x_n$ of jointly Gaussian random variables.

Let’s partition our vector $x$ into two subsets, $x_A$ and $x_B$, and then we can write down the mean and covariance matrices in block form:

$$\mu = \begin{pmatrix} \mu_A \\ \mu_B \end{pmatrix}$$

$$\Sigma = \begin{pmatrix} \Sigma_{AA} & \Sigma_{AB} \\ \Sigma_{BA} & \Sigma_{BB} \end{pmatrix}$$

To compute the conditional distributions, we get the following result:

$p(x_A|x_B) = N\left(x_A|\mu_A + \Sigma_{AB}\Sigma_{BB}^{-1}(x_B - \mu_B), \Sigma_{AA} - \Sigma_{AB}\Sigma_{BB}^{-1}\Sigma_{BA}\right)$

$p(x_B|x_A) = N\left(x_B|\mu_B + \Sigma_{BA}\Sigma_{AA}^{-1}(x_A - \mu_A), \Sigma_{BB} - \Sigma_{BA}\Sigma_{AA}^{-1}\Sigma_{AB}\right)$

# 2.2 Derive marginals $p(x_A)$ and $p(x_B)$ for multivariate Gaussian distribution, where $A$ and $B$ are subsets of $x_1$, $x_2$, ..., $x_n$ of jointly Gaussian random variables.

Let’s partition our vector $x$ into two subsets, $x_A$ and $x_B$, and then we can write down the mean and covariance matrices in block form:

$$\mu = \begin{pmatrix} \mu_A \\ \mu_B \end{pmatrix}$$

$$\Sigma = \begin{pmatrix} \Sigma_{AA} & \Sigma_{AB} \\ \Sigma_{BA} & \Sigma_{BB} \end{pmatrix}$$