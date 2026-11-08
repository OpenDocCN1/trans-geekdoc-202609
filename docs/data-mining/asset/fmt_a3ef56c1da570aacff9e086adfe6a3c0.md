
The foundation for statistical clustering is a statistical model called a finite mixture model. A mixture is a set of `k` probability distributions, representing `k` clusters, that govern the attribute values for members of that cluster. In other words, each distribution gives the probability that a particular instance would have a certain set of attribute values if it were known to be a member of that cluster. Each cluster has a different distribution. Any particular instance “really” belongs to one and only one of the clusters but it is not known which one. Finally, the clusters are not equally likely; there is some probability distribution that reflects their relative populations.

## The Expectation Maximization Algorithm for a Mixture of Gaussians

One of the simplest finite mixture situations is when there is only one numeric attribute, which has a Gaussian or normal distribution for each cluster, but with different means and variances. The clustering problem is to take a set of instances—in this case each instance is just a number—and a prespecified number of clusters and work out each cluster’s mean and variance and the population distribution between the clusters. The mixture model combines several normal distributions, and its probability density function looks like a mountain range with a peak for each component.

[Fig. 13.5](#Ch014_485-514_B9780443158889000145.xhtml#f0030) shows a simple example. There are two clusters A and B, and each has a normal distribution with means and standard deviations `μ[A]` and `σ[A]` for cluster A and `μ[B]` and `σ[B]` for cluster B. Samples are taken from these distributions using cluster A with probability `p[A]` and cluster B with probability `p[B]` (where `p[A] + p[B] = 1`). resulting in a data set like that shown. Now imagine being given the data set without the classes—just the numbers—and being asked to determine the five parameters that characterize the model: `μ[A]`, `σ[A]`, `μ[B]`, `σ[B]`, and `p[A]` (the parameter `p[B]` can be calculated directly from `p[A]`). That is the finite mixture problem.

![Fig. 13.5 A two-class mixture model.](images/F000145f13-05-9780443158889.jpg)

[Fig. 13.5](#Ch014_485-514_B9780443158889000145.xhtml#Bf0030) A two-class mixture model.

If you knew which of the two distributions each instance came from finding the five parameters would be easy—just estimate the mean and standard deviation for the cluster A samples and the cluster B samples separately, using the formulas

```
$\\begin{matrix} {\\mu = \\frac{x\_{1} + x\_{2} + \\cdots + x\_{n}}{n},} \\\\ {\\sigma^{2} = \\frac{\\left( x\_{1} - \\mu \\right)^{2} + \\left( x\_{2} - \\mu \\right)^{2} + \\cdots + \\left( x\_{n} - \\mu \\right)^{2}}{n - 1}.} \\\\ \\end{matrix}$
```

![Equation](images/F000145si58.png)

(The use of `n-1` rather than `n` as the denominator in the second formula ensures an unbiased estimate of the variance rather than the maximum likelihood estimate; it makes little difference in practice if `n` is used instead.) Here, `x[1]`, `x[2]`, …, `x[n]` are the samples from the distribution A or B. To estimate the fifth parameter `p[A]`, take the proportion of the instances that are in the A cluster.

If you knew the five parameters, finding the (posterior) probabilities that a given instance comes from each distribution would be easy. Given an instance `x[i]`, the probability that it belongs to cluster A is

```
$P(A \\mid x\_{i}) = \\frac{P(x\_{i} \\mid A) \\cdot P\\left( A \\right)}{P\\left( x\_{i} \\right)} = \\frac{N(x\_{i};\\mu\_{A},\\sigma\_{A})p\_{A}}{P(x\_{i})},$
```

![Equation](images/F000145si60.png)
