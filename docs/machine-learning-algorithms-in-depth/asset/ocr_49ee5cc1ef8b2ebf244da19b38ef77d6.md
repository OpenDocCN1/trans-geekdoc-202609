We can now compute the gradient with respect to our parameters.

$$\nabla_{\theta} L(\theta, \theta_0; \alpha) = \theta - \sum_{i=1}^{n} \alpha_i y_i x_i = 0$$

$$\frac{d}{d\theta_0} L(\theta, \theta_0; \alpha) = - \sum_{i=1}^{n} \alpha_i y_i = 0 \tag{5.11}$$

By substituting the expression for $\theta$ back into our Lagrangian, we get the following.

$$(\text{dual})\quad \max_{\alpha} \sum_{i=1}^{n} \alpha_i - \frac{1}{2} \sum_{i=1}^{n} \sum_{j=1}^{n} \alpha_i \alpha_j y_i y_j \left[ x_i^T x_j \right]$$

$$\text{subject to}\quad \alpha_i \ge 0, \sum_{i=1}^{n} \alpha_i y_i = 0 \tag{5.12}$$

The most notable change in the dual formulation is that d-dimensional data points $x_i$ and $x_j$ interact via the inner product. This has significant computational advantages over the primal formulation (in addition to simpler constraints in the dual).

The inner product measures the degree of similarity between two vectors and can be generalized via the kernels $K(x_i, x_j)$. Kernels measure a degree of similarity between objects, without explicitly representing them as feature vectors. This is particularly advantageous when we don’t have access to or choose not to look into the internals of our objects. Typically, a kernel function that compares two objects $x_i, x_j \in X$ is symmetric $K(x_i, x_j)=K(x_j, x_i)$ and nonnegative $K(x_i, x_j)\ge 0$. There is a wide variety of kernels, ranging from graph kernels that compute the similarity between graphs to string kernels and document kernels. One popular kernel example we will use in our SVM implementation is a radial basis function (RBF) kernel, shown in the following equation.

$$K(x_i, x_j) = \exp\left( - \frac{\|x_i - x_j\|^2}{2\sigma^2} \right) \tag{5.13}$$

We are now ready to implement a binary SVM classifier from scratch, using the CVXOPT optimization package. CVXOPT is a free software package for convex optimization based on Python programming language and can be downloaded at cvxopt.org.

The standard form of a quadratic program (QP) following CVXOPT notation is shown in the following equation.

$$\min_{x} \frac{1}{2} x^T P x + q^T x \quad \text{subject to}\quad Gx \le h,\ Ax = b \tag{5.14}$$

Note that this objective function is convex if and only if matrix $P$ is positive semidefinite. The CVXOPT QP expects the problem in the form of equation 5.14 parameterized by