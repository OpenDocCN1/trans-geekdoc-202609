# # Bias-Variance Decomposition

Observations:

+   - We can not get better than the noise

Bias: $\mathbb{E}_x \left[\left(\hat{f}_*(oldsymbol{x}) - f(oldsymbol{x})ight)^2ight]$

+   - Difference of true function to the “best” estimate
- The best you can do with your model class
- Also called “structure error”

Variance: $\mathbb{E}_{D_n} \left[\mathbb{E}_x \left(\hat{f}_{D_n}(oldsymbol{x}) - \hat{f}_*(oldsymbol{x})ight)^2ightight]$

+   - Difference of the estimates to the “best” estimate
- Due to limited size of the data set
- Depends on number of data-points
- Also called “estimation error”

![](bbox=[0.573, 0.456, 0.936, 0.863])