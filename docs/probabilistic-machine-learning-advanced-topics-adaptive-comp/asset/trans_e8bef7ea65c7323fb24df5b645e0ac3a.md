
where the terms in the exponent have been decomposed into the partitioned structure in Equation (2.104) as in Equation (2.106). Next, collecting all the terms involving \(\boldsymbol{x}_1\),
\[
p(\boldsymbol{x}_2) \propto \exp \left\{ -\frac{1}{2}\boldsymbol{x}_2^\top \boldsymbol{\Lambda}_{22} \boldsymbol{x}_2 + \boldsymbol{x}_2^\top \boldsymbol{\eta}_2 \right\} \int \exp \left\{ -\frac{1}{2} \boldsymbol{x}_1^\top \boldsymbol{\Lambda}_{11} \boldsymbol{x}_1 + \boldsymbol{x}_1^\top (\boldsymbol{\eta}_1 - \boldsymbol{\Lambda}_{12} \boldsymbol{x}_2) \right\} d\boldsymbol{x}_1, \tag{2.112}
\]
we can recognize the integrand as an exponential quadratic form. Therefore the integral is equal to the normalizing constant of a Gaussian with precision, \(\boldsymbol{\Lambda}_{11}\), and precision weighted mean, \(\boldsymbol{\eta}_1 - \boldsymbol{\Lambda}_{12} \boldsymbol{x}_2\), which is given by the reciprocal of Equation (2.83). Substituting this into our equation we have,
\[
p(\boldsymbol{x}_2) \propto \exp \left\{ -\frac{1}{2} \boldsymbol{x}_2^\top \boldsymbol{\Lambda}_{22} \boldsymbol{x}_2 + \boldsymbol{x}_2^\top \boldsymbol{\eta}_2 \right\} \exp \left\{ \frac{1}{2} (\boldsymbol{\eta}_1 - \boldsymbol{\Lambda}_{12} \boldsymbol{x}_2)^\top \boldsymbol{\Lambda}_{11}^{-1} (\boldsymbol{\eta}_1 - \boldsymbol{\Lambda}_{12} \boldsymbol{x}_2) \right\} \tag{2.113}
\]
\[
\propto \exp \left\{ -\frac{1}{2} \boldsymbol{x}_2^\top \boldsymbol{\Lambda}_{22} \boldsymbol{x}_2 + \boldsymbol{x}_2^\top \boldsymbol{\eta}_2 + \frac{1}{2} \boldsymbol{x}_2^\top \boldsymbol{\Lambda}_{21} \boldsymbol{\Lambda}_{11}^{-1} \boldsymbol{\Lambda}_{12} \boldsymbol{x}_2 - \boldsymbol{x}_2^\top \boldsymbol{\Lambda}_{21} \boldsymbol{\Lambda}_{11}^{-1} \boldsymbol{\eta}_1 \right\} \tag{2.114}
\]
\[
= \exp \left\{ -\frac{1}{2} \boldsymbol{x}_2^\top (\boldsymbol{\Lambda}_{22} - \boldsymbol{\Lambda}_{21} \boldsymbol{\Lambda}_{11}^{-1} \boldsymbol{\Lambda}_{12}) \boldsymbol{x}_2 + \boldsymbol{x}_2^\top (\boldsymbol{\eta}_2 - \boldsymbol{\Lambda}_{21} \boldsymbol{\Lambda}_{11}^{-1} \boldsymbol{\eta}_1) \right\}, \tag{2.115}
\]

which we now recognise as an exponential quadratic form in \(\boldsymbol{x}_2\). Extract the quadratic terms to get the marginal precision,
\[
\boldsymbol{\Lambda}_{22}^m = \boldsymbol{\Lambda}_{22} - \boldsymbol{\Lambda}_{21} \boldsymbol{\Lambda}_{11}^{-1} \boldsymbol{\Lambda}_{12}, \tag{2.116}
\]
and the linear terms to get the marginal precision-weighted mean,
\[
\boldsymbol{\eta}_2^m = \boldsymbol{\eta}_2 - \boldsymbol{\Lambda}_{21} \boldsymbol{\Lambda}_{11}^{-1} \boldsymbol{\eta}_1. \tag{2.117}
\]

## 2.3.2 Linear Gaussian systems

Consider two random vectors \(\boldsymbol{y} \in \mathbb{R}^D\) and \(\boldsymbol{z} \in \mathbb{R}^L\), which are jointly Gaussian with the following joint distribution:
\[
p(\boldsymbol{z}) = \mathcal{N}(\boldsymbol{z} | \tilde{\boldsymbol{\mu}}, \tilde{\boldsymbol{\Sigma}}) \tag{2.118}
\]
\[
p(\boldsymbol{y} | \boldsymbol{z}) = \mathcal{N}(\boldsymbol{y} | \mathbf{W}\boldsymbol{z} + \boldsymbol{b}, \boldsymbol{\Omega}) \tag{2.119}
\]
where \(\mathbf{W}\) is a matrix of size \(D \times L\). This is an example of a **linear Gaussian system**.

### 2.3.2.1 Joint distribution

The corresponding joint distribution, \(p(\boldsymbol{z}, \boldsymbol{y}) = p(\boldsymbol{z})p(\boldsymbol{y} | \boldsymbol{z})\), is itself a \(D + L\) dimensional Gaussian, with mean and covariance given by the following (this result can be obtained by moment matching):
\[
p(\boldsymbol{z}, \boldsymbol{y}) = \mathcal{N}(\boldsymbol{z}, \boldsymbol{y} | \tilde{\boldsymbol{\mu}}, \tilde{\boldsymbol{\Sigma}}) \tag{2.120a}
\]
\[
\tilde{\boldsymbol{\mu}} \triangleq \left( \begin{array}{c} \tilde{\boldsymbol{\mu}} \\ \boldsymbol{m} \end{array} \right) \triangleq \left( \begin{array}{c} \tilde{\boldsymbol{\mu}} \\ \mathbf{W} \tilde{\boldsymbol{\mu}} + \boldsymbol{b} \end{array} \right) \tag{2.120b}
\]
\[
\tilde{\boldsymbol{\Sigma}} \triangleq \left( \begin{array}{c c } \tilde{\boldsymbol{\Sigma}} & \mathbf{C}^\top \\ \mathbf{C} & \mathbf{S} \end{array} \right) \triangleq \left( \begin{array}{c c } \tilde{\boldsymbol{\Sigma}} & \tilde{\boldsymbol{\Sigma}} \mathbf{W}^\top \\ \mathbf{W} \tilde{\boldsymbol{\Sigma}} & \mathbf{W} \tilde{\boldsymbol{\Sigma}} \mathbf{W}^\top + \boldsymbol{\Omega} \end{array} \right) \tag{2.120c}
\]

See Algorithm 8.1 on page 363 for some pseudocode to compute this joint distribution.

### 2.3.2.2 Posterior distribution (Bayes' rule for Gaussians)

Now we consider computing the posterior \( p(\boldsymbol{z}|\boldsymbol{y}) \) from a linear Gaussian system. Using Equation (2.78) for conditioning a joint Gaussian, we find that the posterior is given by

\[
p(\boldsymbol{z}|\boldsymbol{y}) = \mathcal{N}(\boldsymbol{z} | \hat{\boldsymbol{\mu}}, \hat{\boldsymbol{\Sigma}})
\]
\[
\hat{\boldsymbol{\mu}} = \tilde{\boldsymbol{\mu}} + \tilde{\boldsymbol{\Sigma}} \mathbf{W}^T (\boldsymbol{\Omega} + \mathbf{W} \tilde{\boldsymbol{\Sigma}} \mathbf{W}^T)^{-1} (\boldsymbol{y} - (\mathbf{W} \tilde{\boldsymbol{\mu}} + \boldsymbol{b}))
\]
\[
\hat{\boldsymbol{\Sigma}} = \tilde{\boldsymbol{\Sigma}} - \tilde{\boldsymbol{\Sigma}} \mathbf{W}^T (\boldsymbol{\Omega} + \mathbf{W} \tilde{\boldsymbol{\Sigma}} \mathbf{W}^T)^{-1} \mathbf{W} \tilde{\boldsymbol{\Sigma}}
\]

This is known as Bayes' rule for Gaussians. We see that if the prior \( p(\boldsymbol{z}) \) is Gaussian, and the likelihood \( p(\boldsymbol{y}|\boldsymbol{z}) \) is Gaussian, then the posterior \( p(\boldsymbol{z}|\boldsymbol{y}) \) is also Gaussian. We therefore say that the Gaussian prior is a conjugate prior for the Gaussian likelihood, since the posterior distribution has the same type as the prior. (In other words, Gaussians are closed under Bayesian updating.)

We can simplify these equations by defining \( \mathbf{S} = \mathbf{W} \tilde{\boldsymbol{\Sigma}} \mathbf{W}^T + \boldsymbol{\Omega} \), \( \mathbf{C} = \tilde{\boldsymbol{\Sigma}} \mathbf{W}^T \), and \( \mathbf{m} = \mathbf{W} \tilde{\boldsymbol{\mu}} + \boldsymbol{b} \), as in Equation (2.120). We also define the Kalman gain matrix:\(^8\)

\[
\mathbf{K} = \mathbf{C} \mathbf{S}^{-1}
\]

From this, we get the posterior

\[
\hat{\boldsymbol{\mu}} = \tilde{\boldsymbol{\mu}} + \mathbf{K} (\boldsymbol{y} - \mathbf{m})
\]
\[
\hat{\boldsymbol{\Sigma}} = \tilde{\boldsymbol{\Sigma}} - \mathbf{K} \mathbf{C}^T
\]

Note that

\[
\mathbf{K} \mathbf{S} \mathbf{K}^T = \mathbf{C} \mathbf{S}^{-1} \mathbf{S} \mathbf{S}^{-T} \mathbf{C}^T = \mathbf{C} \mathbf{S}^{-1} \mathbf{C}^T = \mathbf{K} \mathbf{C}^T
\]

and hence we can also write the posterior covariance as

\[
\hat{\boldsymbol{\Sigma}} = \tilde{\boldsymbol{\Sigma}} - \mathbf{K} \mathbf{S} \mathbf{K}^T
\]

Using the matrix inversion lemma from Equation (2.93), we can also rewrite the posterior in the following form [Bis06, p93], which takes \( O(L^3) \) time instead of \( O(D^3) \) time:

\[
\hat{\boldsymbol{\Sigma}} = (\tilde{\boldsymbol{\Sigma}}^{-1} + \mathbf{W}^T \boldsymbol{\Omega}^{-1} \mathbf{W})^{-1}
\]
\[
\hat{\boldsymbol{\mu}} = \hat{\boldsymbol{\Sigma}} [\mathbf{W}^T \boldsymbol{\Omega}^{-1} (\boldsymbol{y} - \boldsymbol{b}) + \tilde{\boldsymbol{\Sigma}}^{-1} \tilde{\boldsymbol{\mu}}]
\]

Finally, note that the corresponding normalization constant for the posterior is just the marginal on \( \boldsymbol{y} \) evaluated at the observed value:

\[
p(\boldsymbol{y}) = \int \mathcal{N}(\boldsymbol{z} | \tilde{\boldsymbol{\mu}}, \tilde{\boldsymbol{\Sigma}}) \mathcal{N}(\boldsymbol{y} | \mathbf{W} \boldsymbol{z} + \boldsymbol{b}, \boldsymbol{\Omega}) d\boldsymbol{z}
\]
\[
= \mathcal{N}(\boldsymbol{y} | \mathbf{W} \tilde{\boldsymbol{\mu}} + \boldsymbol{b}, \boldsymbol{\Omega} + \mathbf{W} \tilde{\boldsymbol{\Sigma}} \mathbf{W}^T) = \mathcal{N}(\boldsymbol{y} | \mathbf{m}, \mathbf{S})
\]

From this, we can easily compute the log marginal likelihood. We summarize all these equations in Algorithm 8.1.

![](img/ca72c1626f4850f058a9edc138c1ac73_61_0.png)

Figure 2.10: We observe \(\boldsymbol{x} = (0, -1)\) (red cross) and \(\boldsymbol{y} = (1, 0)\) (green cross) and estimate \(\mathbb{E}[\boldsymbol{z}|\boldsymbol{x}, \boldsymbol{y}, \boldsymbol{\theta}]\) (black cross). (a) Equally reliable sensors, so the posterior mean estimate is in between the two circles. (b) Sensor 2 is more reliable, so the estimate shifts more towards the green circle. (c) Sensor 1 is more reliable in the vertical direction, Sensor 2 is more reliable in the horizontal direction. The estimate is an appropriate combination of the two measurements. Generated by `sensor_fusion_2d.ipynb`.

### 2.3.2.3 Example: Sensor fusion with known measurement noise

Suppose we have an unknown quantity of interest, \(\boldsymbol{z} \sim \mathcal{N}(\boldsymbol{\mu}_z, \boldsymbol{\Sigma}_z)\), from which we get two noisy measurements, \(\boldsymbol{x} \sim \mathcal{N}(\boldsymbol{z}, \boldsymbol{\Sigma}_x)\) and \(\boldsymbol{y} \sim \mathcal{N}(\boldsymbol{z}, \boldsymbol{\Sigma}_y)\). Pictorially, we can represent this example as \(\boldsymbol{x} \leftarrow \boldsymbol{z} \rightarrow \boldsymbol{y}\). This is an example of a linear Gaussian system. Our goal is to combine the evidence together, to compute \(p(\boldsymbol{z}|\boldsymbol{x}, \boldsymbol{y}; \boldsymbol{\theta})\). This is known as **sensor fusion**. (In this section, we assume \(\boldsymbol{\theta} = (\boldsymbol{\Sigma}_x, \boldsymbol{\Sigma}_y)\) is known. See Supplementary Section 2.1.2 for the general case.)

We can combine \(\boldsymbol{x}\) and \(\boldsymbol{y}\) into a single vector \(\boldsymbol{v}\), so the model can be represented as \(\boldsymbol{z} \rightarrow \boldsymbol{v}\), where \(p(\boldsymbol{v}|\boldsymbol{z}) = \mathcal{N}(\boldsymbol{v}|\mathbf{W}\boldsymbol{z}, \boldsymbol{\Sigma}_v)\), where \(\mathbf{W} = [\mathbf{I}; \mathbf{I}]\) and \(\boldsymbol{\Sigma}_v = [\boldsymbol{\Sigma}_x, \mathbf{0}; \mathbf{0}, \boldsymbol{\Sigma}_y]\) are block-structured matrices. We can then apply Bayes' rule for Gaussians (Section 2.3.2.2) to compute \(p(\boldsymbol{z}|\boldsymbol{v})\).

Figure 2.10(a) gives a 2d example, where we set \(\boldsymbol{\Sigma}_x = \boldsymbol{\Sigma}_y = 0.01\mathbf{I}_2\), so both sensors are equally reliable. In this case, the posterior mean is halfway between the two observations, \(\boldsymbol{x}\) and \(\boldsymbol{y}\). In Figure 2.10(b), we set \(\boldsymbol{\Sigma}_x = 0.05\mathbf{I}_2\) and \(\boldsymbol{\Sigma}_y = 0.01\mathbf{I}_2\), so sensor 2 is more reliable than sensor 1. In this case, the posterior mean is closer to \(\boldsymbol{y}\). In Figure 2.10(c), we set

\[
\boldsymbol{\Sigma}_x = 0.01 \begin{pmatrix} 10 & 1 \\ 1 & 1 \end{pmatrix}, \quad \boldsymbol{\Sigma}_y = 0.01 \begin{pmatrix} 1 & 1 \\ 1 & 10 \end{pmatrix} \tag{2.130}
\]

so sensor 1 is more reliable in the second component (vertical direction), and sensor 2 is more reliable in the first component (horizontal direction). In this case, the posterior mean is vertically closer to \(\boldsymbol{x}\) and horizontally closer to \(\boldsymbol{y}\).

### 2.3.3 A general calculus for linear Gaussian systems

In this section, we discuss a general method for performing inference in linear Gaussian systems. The key is to define joint distributions over the relevant variables in terms of a **potential function**, represented in information form. We can then easily derive rules for marginalizing potentials, multiplying and dividing potentials, and conditioning them on observations. Once we have defined these operations, we can use them inside of the belief propagation algorithm (Section 9.3) or junction tree algorithm (Supplementary Section 9.2) to compute quantities of interest. We give the details on how to perform these operations below; our presentation is based on [Lau92; Mur02].
