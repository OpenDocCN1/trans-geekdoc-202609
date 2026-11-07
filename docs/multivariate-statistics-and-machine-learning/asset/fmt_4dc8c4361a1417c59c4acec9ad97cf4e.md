
Note that the only difference between the two quantities that are minimized is in (6.6), we have added the trailing term $\\lambda{\\sum\\limits\_{j = 1}^{p}\\beta\_{j}^{2}}$, where `β[j]²` is simply the square of `β[j]` which we are already familiar. However, this quantity is “weighted” by `λ`, which is a *tuning parameter* that is imposed on the sum of the squared regression weights (i.e., $\\sum\\limits\_{j = 1}^{p}\\beta\_{j}^{2}$). Taken together, the trailing term $\\lambda{\\sum\\limits\_{j = 1}^{p}\\beta\_{j}^{2}}$ is known as a *shrinkage penalty*. But why add this penalty term to the original residual sums of squares? What is the theoretical consequence of doing so? We explore that motivation now.269

### 6.2.2 Consequence of Ridge Estimator

We first note that the residual sums of squares for ridge regression reduces to ordinary least-squares regression when the value for the tuning parameter is equal to 0, since

$$\\begin{array}{l} {RSS = {\\sum\\limits\_{i = 1}^{n}\\left( {y\_{i} - \\beta\_{0} - {\\sum\\limits\_{j = 1}^{p}{\\beta\_{j}x\_{ij}}}} \\right)^{2}} + \\lambda{\\sum\\limits\_{j = 1}^{p}\\beta\_{j}^{2}}} \\\\ {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, = {\\sum\\limits\_{i = 1}^{n}\\left( {y\_{i} - \\beta\_{0} - {\\sum\\limits\_{j = 1}^{p}{\\beta\_{j}x\_{ij}}}} \\right)^{2}} + 0{\\sum\\limits\_{j = 1}^{p}\\beta\_{j}^{2}}} \\\\ {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, = {\\sum\\limits\_{i = 1}^{n}\\left( {y\_{i} - \\beta\_{0} - {\\sum\\limits\_{j = 1}^{p}{\\beta\_{j}x\_{ij}}}} \\right)^{2}}} \\\\ \\end{array}$$

For values of `λ` greater than 0, we see that it has the effect of increasing the value of the residual sums of squares, since we are then adding on at least *some* of $\\sum\\limits\_{j = 1}^{p}\\beta\_{j}^{2}$ to the least-squares residual.

Hence, ridge regression has the *apparent* effect of *increasing the residual sums of squares over what it would have been had we simply used least-squares regression*. This effect can seem contradictory to the purpose of conducting regression in the first place, as up to now, the goal in regression analysis has always been to *minimize* the objective function, which for classical least-squares has typically been the sum of squared errors. But now, with ridge regression, we are purposely adding on a “penalty” term that would seem to have the effect of *increasing* the sums of squared errors.

Why would we want to do this? We should have a good reason for doing so. It turns out that we do, and that is because we are *no longer using the best unbiased estimator.* Instead, ridge regression uses a *biased estimator*. Ridge regression has an explicit analytic solution, and so numerical methods are not required. Numerical methods will be required when we encounter a related technique called the *lasso*, as a closed-form solution for the lasso does not exist.

To understand why using a biased estimator may be advantageous over employing an unbiased one, we need to revisit the bias-variance tradeoff discussed earlier in the book.

### 6.2.3 Revisiting the Bias-Variance Tradeoff: Why Ridge Is Useful

To appreciate why ridge regression is effective and why using a biased estimator has an advantage over an unbiased one, we need to recall the bias-variance tradeoff concept:

`E(y[0]−f̂(x[0]))²` = `Var(f̂(x[0]))` + `[Bias[f̂(x[0])]]²` + `Var(ε)`

(6.7)

where `E(y[0]−f̂(x[0]))²` is the expected test mean squared error (i.e., `MSE`) at a given value of `x`, that of `x[0]`. The goal is to get `E(y[0]−f̂(x[0]))²` down or reduced. All else equal in the equality, we see that an increase in `[Bias[f̂(x[0])]]²` will have the effect of increasing `E(y[0]−f̂(x[0]))²`, not decreasing it, again, *all else equal*. But here’s the key to understanding ridge regression: *not all else is equal*! For an increase in bias, the hope is that the variance of the function, that of `Var(f̂(x[0]))`, will decrease, which overall, for a constant `Var(ε)` implies that `E(y[0]−f̂(x[0]))²` will decrease overall, not *increase*. Cutting right to the chase, *ridge regression works by purposely introducing bias into the estimator to offset a reduction in variance*, which we can summarize succinctly below:270

$$\\begin{array}{l} \\left. E\\left( {y\_{0} - \\hat{f}\\left( x\_{0} \\right)} \\right)^{2} = \\,\\downarrow Var\\left( {\\hat{f}\\left( x\_{0} \\right)} \\right) + \\uparrow\\left\\lbrack {Bias\\left\\lbrack {\\hat{f}\\left( x\_{0} \\right)} \\right\\rbrack} \\right\\rbrack^{2} + Var\\left( \\varepsilon \\right) \\right. \\\\ \\left. \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, = \\downarrow E\\left( {y\_{0} - \\hat{f}\\left( x\_{0} \\right)} \\right)^{2} \\right. \\\\ \\end{array}$$

(6.8)

That is, the net effect of using a ridge estimator is desirable because it typically results in a smaller `MSE` on test data. This last point is important. *The smaller MSE is expected (and desired) on test data, not necessarily training data*.

When performing ridge regression, it is common to recommend standardization of input variables prior to carrying out the procedure, despite the recommendation not being accepted by everyone ([Izenman, 2008](#ref.xhtml#re_CIT000167); [Thisted, 1976](#ref.xhtml#re_CIT000356)).

### 6.2.4 A Visual Look at Ridge Regression

Ridge regression can be understood visually and is often referred to as *penalized* least-squares regression. The original motivation for the ridge estimator, as discussed, was the observation made by [Hoerl and Kennard (1970)](#ref.xhtml#re_CIT000154) that potential instability in the `OLS` estimator could be tracked by adding a small constant `k` to the diagonal entries of `X^T X` before taking its inverse. This is what results in the *ridge estimator*, or sometimes called the *ridge rule*. This has the effect of regularizing ordinary least-squares by shrinking toward a multiple of the identity matrix ([Friedman, 1989](#ref.xhtml#re_CIT000114)).

But what is the significance of adding this small constant `k`? To understand this, consider the depiction in [Figure 6.2](#c6.xhtml#f6.2) (left) featuring that of concentric ovals or ellipses for `OLS`, along with the search space for ridge estimators. We can see that the ridge estimate lies on the outer oval of the `OLS` ellipse, for both `β[1]` and `β[2]` (note that `β[1]` and `β[2]` are on the `x` and `y` axes, respectively).271

![Figure 6.2 Concentric RSS ellipses for OLS. The ridge estimate is a shrunken version of the OLS estimate moving coefficients toward 0 as a function of a tuning parameter (left). For a constant concentric ellipse, the ridge estimates for \\beta\_{1} and \\beta\_{2} lie as indicated in the plot where both coefficients \\beta\_{1} and \\beta\_{2} have been shrunken toward, but not to, 0. That is, where the ellipse “touches” the circle (it is a circle or “disk” and not another shape as a consequence of the ridge constraint region) is at a point on the circle unequal to 0. In contrast, the lasso solution (right) generates a shape of a diamond constraint region with sharp edges, and hence the lasso solution for \\beta\_{1} and \\beta\_{2} is more likely to have a given coefficient equal to 0.Return to text.⏎](images/fig6.2.jpg)
