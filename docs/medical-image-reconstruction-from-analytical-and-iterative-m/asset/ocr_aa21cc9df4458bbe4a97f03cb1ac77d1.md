![](bbox=[0.102, 0.092, 0.562, 0.188])

Fig. 6.8: The negative gradient direction may not be the most efficient way to find the function's minimum.

![](bbox=[0.102, 0.271, 0.562, 0.352])

Fig. 6.9: The conjugate gradient direction is more effective than the gradient direction.

# 6.4 ML-EM algorithms

We do not have to use a least-squares objective function. There are many different ways to set up an objective function. If we use the Poisson noise model or simply use the nonnegativity constraint, we will get a special objective function. By minimizing that special objective function, a multiplicative updating algorithm known as the ML-EM algorithm is derived and can be symbolically expressed as

```
\(\bar{x}^{\text{next}} = \bar{x}^{\text{current}} \frac{\text{Backproject}\left\{ \text{Measurement} / \text{Project}\left(\bar{x}^{\text{current}}\right) \right\}}{\text{Backproject}\left\{ \bar{1} \right\}}, \quad (6.29)\)
```

where \(\{\bar{1}\}\) is a vector with elements of 1s. The size of the vector is that of the projection data vector. In this algorithm, the data discrepancy is calculated as a ratio instead of a difference. The distinguishing feature of this algorithm is its nonnegativity. If the initial image \(\bar{x}^0\) does not contain any negative pixels or voxels, the image values will never become negative.

Now let us explain the name of this algorithm: ML-EM. The objective function of this algorithm can be a likelihood function, which is the joint probability density function of Poisson random variables. We are looking for a solution (i.e., the reconstructed image) that can maximize this likelihood function. Therefore, this is a maximum likelihood algorithm.

When we try to maximize or minimize a function (e.g., an objective function or a likelihood function), we usually take the partial derivatives with respect to all of its