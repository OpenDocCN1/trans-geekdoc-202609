# # Mathematical Formulation

Observation:

+   - $w^T x + b = 0$ and $c(w^T x + b) = 0$ define the same hyper-plane

+   - Scaling $c$ can be chosen freely

Choose scaling such that

+   - For positive support vectors $w^T x_+ + b = +1$

+   - For negative support vectors $w^T x_- + b = -1$

Margin is then given by

$$\frac{w^T x_+ + b - w^T x_- + b}{\||w||} = \frac{2}{\|w||}$}$

![](bbox=[0.438, 0.245, 0.978, 0.811])