# 8 Nonlinear input transformations and kernels

All training data is used during training (that is, solving (8.19b)) but when making predictions (using (8.19a)) only the support vectors contribute. This can significantly reduce the computational burden. The larger $\epsilon$ chosen by the user, the fewer support vectors and fewer computations needed when making predictions. It can therefore be said that $\alpha$ has a regularizing effect, in the sense that the more/fewer support vectors that are used the more/less complicated model. We summarize support vector regression in Method 8.2.

# Learn support vector regression

**Data:** Training data $\mathcal{T} = \{x_i, y_i\}_{i=1}^n$
**Result:** Learned parameters $\hat{\alpha}$

+   1 Compute $\hat{\alpha}$ by numerically solving (8.19b-8.19c)

# Predict with kernel ridge regression

**Data:** Learned parameters $\hat{\alpha}$ and test input $\mathbf{x}_*$
**Result:** Prediction $\hat{y}(\mathbf{x}_*)$ (8.19a).

+   1 Compute $\hat{y}(\mathbf{x}_*)$ as (8.19a).

# Method 8.2: Support vector regression and kernel ridge regression

We consider again the car stopping distance problem from Example 8.2 in Figure 8. With $\lambda=0.01$ and $\epsilon=15$, we apply support vector regression to the data (red line). As a reference we also show the corresponding kernel ridge regression (blue line).

![](bbox=[0.205, 0.503, 0.794, 0.733])

**Fig. 8.4**

In Figure 8.4 we have enclosed (in red) the $\epsilon$-tube all data points where $\alpha_i 
eq 0$, the so-called support vectors. We have included all support vectors located outside the $\epsilon$-tube. This is a direct effect of using the $\epsilon$-insensitive loss, which explicitly encodes the loss function for data points. If choosing a smaller $\epsilon$, we would have more support vectors, and vice versa. Another consequence of the sparsity of $\alpha$ is that when computing a prediction (8.19a) with support vector regression, it is sufficient to do the computation (in this case) only five data points. For kernel ridge regression, which does not have a sparse $\alpha$, the prediction (8.14a) depends on all 62 data points.

Draft (April 30, 2021) of Machine Learning – A First Course for Engineers and Scientists. http://mlbook.org
Andreas Lindholm, Nils Wahlström, Fredrik Lindström, and Thomas B. Schön. 2021.