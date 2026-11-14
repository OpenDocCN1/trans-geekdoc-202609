![](bbox=[0.102, 0.098, 0.552, 0.403])

Fig. 6.6: For a degenerated system, the iterative algorithm solution depends on the initial value.

at the early iterations, the images only contain low-frequency components; at higher iterations, high-frequency components are recovered and noise comes into effect, too.

# 6.3.2 The Landweber algorithm

The Landweber algorithm is a simplified gradient descent algorithm, in which the step size is a fixed value determined by the user. Unlike the gradient decent algorithm, the Landweber algorithm does not necessarily reach the minimum in the decent direction at each iteration. However, the algorithm can converge if the step size is chosen small enough. How small is small enough? The step size \(\alpha\) should satisfy

```
\(0 < \alpha < \frac{2}{\sigma_1^2},\) (6.28)
```

where \(\sigma_1\) is the largest singular value of matrix \(A\). Sometimes, it is advantageous to make the step size \(\alpha\) variable, as a function of, for example, iteration number, noise weighting, and/or regions of interest.