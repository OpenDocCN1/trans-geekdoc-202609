enables the ML-centric methods to serve as a complementary alternative to any hydrologic simulation model. The conceptual formulations and mathematical concepts of each algorithm are briefly discussed in the following sections.

# Support Vector Machines

The SVM algorithm is proposed by Vapnik, (2013) as a binary classification method. This algorithm uses the concept of Vapnik Chervonenkis (VC) dimension (see Vapnik, 2013), which is a measure of capacity or complexity of a machine to minimize structural risk to optimization and obtain learning and generalization ability. Given by a set of N samples of {xₖ, yₖ}ₖ₌₁ᴺ, x ∈ Rᵐ, y ∈ R, where x is an input vector of size m, and y is the corresponding output value. An SVM estimator f on regression can be expressed as

$$f(x)=\omega\cdot\phi(x)+b,$$  (5.1)

where ω is a weight vector and b denotes bias. The ϕ represents a nonlinear transfer function that maps the input vectors into a high dimensional feature space (e.g., Vapnik, 2013). A convex optimization problem with an ε-insensitivity loss function is used in this model to obtain optimization (equation (5.2)):

$$\begin{aligned}
\min_{\omega,b,\xi,\xi^*}\;&\frac{1}{2}\|\omega\|^2+C\sum_{i=1}^{m}(\xi_i+\xi_i^*)\\
\text{s.t.}\;&\omega\cdot\phi(x_i)+b-y_i\le\varepsilon+\xi_i,\\
&y_i-\omega\cdot\phi(x_i)-b\le\varepsilon+\xi_i^*,\\
&\xi_i,\xi_i^*\ge0;\ i=1,2,\ldots,m.
\end{aligned}$$  (5.2)

where ξ and ξ* are slack variables, which include soft margin to deal with infeasible constraints; C is a positive constant to penalize training errors by the loss function over the error tolerance ε and prevent overfitting. In this algorithm, the overfitting problem is typically solved using Duality Theory and Lagrangian multipliers and imposing Karush-Kuhn-Tucker (KKT) optimality condition (see Shevade et al., 2000; Smola, 2002).

# Bayesian Lasso

In the classic linear regression setting, the original Lasso model, proposed by Tibshirani (1996), is an L1-penalized least squares estimate that