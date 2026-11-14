
SGD converges to the optimal solution at a rate of:

\[
\mathbb{E}[f(\mathbf{x}_k) - f(\mathbf{x}^*)] \le \frac{C}{k},\quad (681)
\]

where \(C\) is a constant depending on the step size \(\eta\), the variance of the stochastic gradients, and the strong convexity constant \(m\). This slower convergence rate is due to the inherent noise in the gradient estimates. Variance reduction techniques such as **mini-batch SGD** (using multiple data points per iteration) or **Momentum** (accumulating past gradients) are often employed to improve convergence speed and stability.

### 13.3.3 Second-Order Methods

Second-order methods make use of not just the gradient \(\nabla f(\mathbf{x})\), but also the **Hessian matrix** \(\mathbf{H}(\mathbf{x}) = \nabla^2 f(\mathbf{x})\), which is the matrix of second-order partial derivatives of the objective function. The update rule for second-order methods is:

\[
\mathbf{x}_{k+1} = \mathbf{x}_k - \eta \mathbf{H}^{-1}(\mathbf{x}_k) \nabla f(\mathbf{x}_k),\quad (682)
\]

where \(\mathbf{H}^{-1}(\mathbf{x}_k)\) is the inverse of the Hessian matrix.

Second-order methods typically have faster convergence rates compared to gradient descent, particularly when the function \(f\) has well-conditioned curvature. However, computing the Hessian is computationally expensive, which limits the scalability of these methods. Newton's method is a widely used second-order optimization technique that uses both the gradient and the Hessian. The update rule is given by:

\[
\mathbf{x}_{k+1} = \mathbf{x}_k - \eta \mathbf{H}^{-1}(\mathbf{x}_k) \nabla f(\mathbf{x}_k).\quad (683)
\]

Newton's method converges quadratically near the optimal point under the assumption that the objective function is twice continuously differentiable and the Hessian is positive definite. More formally, if \(\mathbf{x}_k\) is sufficiently close to the optimal point \(\mathbf{x}^*\), then the error \(\|\mathbf{x}_k - \mathbf{x}^*\|\) decreases quadratically:

\[
\|\mathbf{x}_{k+1} - \mathbf{x}^*\| \le C \|\mathbf{x}_k - \mathbf{x}^*\|^2,\quad (684)
\]

where \(C\) is a constant depending on the condition number of the Hessian.

Since directly computing the Hessian is expensive, quasi-Newton methods aim to approximate the inverse Hessian at each iteration. One of the most popular quasi-Newton methods is the **Broyden–Fletcher–Goldfarb–Shanno (BFGS)** method, which maintains an approximation to the inverse Hessian, updating it at each iteration. The Summary of what we discussed above are as follows:

- **Gradient Descent (GD)**: An optimization algorithm that updates the parameter vector in the direction opposite to the gradient of the objective function. Convergence is guaranteed under convexity assumptions with an appropriately chosen step size.
- **Stochastic Gradient Descent (SGD)**: A variant of GD that uses a random subset of the data to estimate the gradient at each iteration. While faster and less computationally intensive, its convergence is slower and more noisy, requiring variance reduction techniques for efficient training.
- **Second-Order Methods**: These methods use the Hessian (second derivatives of the objective function) to accelerate convergence, often exhibiting quadratic convergence near the optimum. However, the computational cost of calculating the Hessian restricts their practical use. Quasi-Newton methods, such as BFGS, approximate the Hessian to improve efficiency.

Each of these methods has its advantages and trade-offs, with gradient-based methods being widely used due to their simplicity and efficiency, and second-order methods providing faster convergence but at higher computational costs.

## 13.4 Matrix Calculus

### 13.4.1 Matrix Differentiation

Consider a matrix A of size m × n, where A = [a_ij]. For the purposes of differentiation, we will focus on functions f(A) that map matrices to scalars or other matrices. We aim to compute the derivative of f(A) with respect to A. Let f(A) be a scalar function of the matrix A. The derivative of this scalar function with respect to A is defined as:

\[
\frac{\partial f(\mathbf{A})}{\partial \mathbf{A}} = \left[ \frac{\partial f(\mathbf{A})}{\partial a_{ij}} \right] \quad (685)
\]

This is a matrix where the (i,j)-th entry is the partial derivative of the scalar function with respect to the element a_ij. Let us take an example of Differentiating the Frobenius Norm. Consider the Frobenius norm of a matrix A, defined as:

\[
\|\mathbf{A}\|_F = \sqrt{\sum_{i=1}^m \sum_{j=1}^n a_{ij}^2} \quad (686)
\]

To compute the derivative of \(\|\mathbf{A}\|_F\) with respect to A, we first apply the chain rule:

\[
\frac{\partial \|\mathbf{A}\|_F}{\partial a_{ij}} = \frac{2a_{ij}}{2\|\mathbf{A}\|_F} = \frac{a_{ij}}{\|\mathbf{A}\|_F} \quad (687)
\]

Thus, the gradient of the Frobenius norm is the matrix \(\frac{\mathbf{A}}{\|\mathbf{A}\|_F}\). The Matrix Derivatives of Common Functions are as follows:

- **Matrix trace**: For a matrix A, the derivative of the trace Tr(A) with respect to A is the identity matrix:

\[
\frac{\partial \text{Tr}(\mathbf{A})}{\partial \mathbf{A}} = \mathbf{I} \quad (688)
\]

- **Matrix product**: Let A and B be matrices, and consider the product f(A) = AB. The derivative of this product with respect to A is:

\[
\frac{\partial (\mathbf{AB})}{\partial \mathbf{A}} = \mathbf{B}^T \quad (689)
\]

- **Matrix inverse**: The derivative of the inverse of A with respect to A is:

\[
\frac{\partial (\mathbf{A}^{-1})}{\partial \mathbf{A}} = -\mathbf{A}^{-1} \left( \frac{\partial \mathbf{A}}{\partial \mathbf{A}} \right) \mathbf{A}^{-1} \quad (690)
\]

### 13.4.2 Tensor Differentiation

A tensor is a multi-dimensional array of components that transform according to certain rules under a change of basis. For simplicity, let’s focus on second-order tensors (which are matrices in m × n form), but the results can extend to higher-order tensors.

Let T be a tensor, represented by the array of components \(T_{i_1, i_2, ..., i_k}\), where the indices \(i_1, i_2, ..., i_k\) are the dimensions of the tensor. Let f(T) be a scalar-valued function that depends on the tensor T. The derivative of this function with respect to the tensor components \(T_{i_1, ..., i_k}\) is given by:

\[
\frac{\partial f(\mathbf{T})}{\partial T_{i_1, ..., i_k}} = \text{Jacobian of } f(\mathbf{T}) \text{ with respect to } T_{i_1, ..., i_k} \quad (691)
\]

For example, consider a function of a second-order tensor, $f(\mathbf{T})$, where $\mathbf{T}$ is a matrix. The differentiation rule follows similar principles as matrix differentiation. The Jacobian is computed for each tensor component in the same fashion, based on the partial derivatives with respect to the individual tensor components.

Consider a second-order tensor $\mathbf{T}$, and let's compute the derivative of the Frobenius norm of $\mathbf{T}$:

\[
\|\mathbf{T}\|_F = \sqrt{\sum_{i_1, i_2, \dots, i_k} T_{i_1, \dots, i_k}^2} \quad (692)
\]

Differentiating with respect to $T_{i_1, \dots, i_k}$, we get:

\[
\frac{\partial \|\mathbf{T}\|_F}{\partial T_{i_1, \dots, i_k}} = \frac{2 T_{i_1, \dots, i_k}}{2 \|\mathbf{T}\|_F} = \frac{T_{i_1, \dots, i_k}}{\|\mathbf{T}\|_F} \quad (693)
\]

This is the gradient of the Frobenius norm, where each component $T_{i_1, \dots, i_k}$ is normalized by the Frobenius norm. For higher-order tensors, differentiation follows the same principles but extends to multi-indexed components. If $\mathbf{T}$ is a third-order tensor, say $T_{i_1, i_2, i_3}$, the differentiation of $f(\mathbf{T})$ with respect to any component is given by:

\[
\frac{\partial f(\mathbf{T})}{\partial T_{i_1, i_2, i_3}} = \text{Jacobian of } f(\mathbf{T}) \text{ with respect to the multi-index components.} \quad (694)
\]

For the tensor product of two tensors $\mathbf{T}_1$ and $\mathbf{T}_2$, say of orders $p$ and $q$, respectively, the product is another tensor of order $p + q$. Differentiation of the tensor product $\mathbf{T}_1 \otimes \mathbf{T}_2$ follows the product rule:

\[
\frac{\partial (\mathbf{T}_1 \otimes \mathbf{T}_2)}{\partial \mathbf{T}_1} = \mathbf{T}_2, \quad \frac{\partial (\mathbf{T}_1 \otimes \mathbf{T}_2)}{\partial \mathbf{T}_2} = \mathbf{T}_1 \quad (695)
\]

This tensor product rule applies for higher-order tensors, where differentiation follows tensor contraction rules. The process of differentiating matrices and tensors extends the rules of differentiation to multi-dimensional data structures, with careful application of chain rules, product rules, and understanding the Jacobian of the functions. For matrices, the derivative is a matrix of partial derivatives, while for tensors, the derivative is typically expressed as a tensor with respect to multi-index components. In higher-order tensor differentiation, we apply these principles recursively, accounting for multi-index notation, and respecting the tensor contraction rules that define how the components interact.

We start with the Differentiation of Scalar-Valued Functions with Matrix Arguments. Let $f : \mathbb{R}^{m \times n} \to \mathbb{R}$ be a scalar function of a matrix $\mathbf{X}$. The differential $df$ of $f$ is defined by:

\[
df = \lim_{\|\mathbf{H}\| \to 0} \frac{f(\mathbf{X} + \mathbf{H}) - f(\mathbf{X})}{\|\mathbf{H}\|} \quad (696)
\]

where $\mathbf{H}$ is an infinitesimal perturbation. The total derivative of $f$ is given by:

\[
df = \text{tr} \left( \left( \frac{\partial f}{\partial \mathbf{X}} \right)^T d\mathbf{X} \right). \quad (697)
\]

Definition of the Matrix Gradient: The gradient $\mathbf{D_X}f$ (or Jacobian) is the unique matrix satisfying:

\[
df = \text{tr} \left( \mathbf{D_X}^T d\mathbf{X} \right) . \quad (698)
\]

This ensures that differentiation is dual to the Frobenius inner product $\langle \mathbf{A}, \mathbf{B} \rangle = \text{tr}(\mathbf{A}^T \mathbf{B})$, giving a **Hilbert space structure**. Let's start with the example of Quadratic Form Differentiation. Let $f(\mathbf{X}) = \text{tr}(\mathbf{X}^T \mathbf{A} \mathbf{X})$. Expanding in a small perturbation $\mathbf{H}$:

\[
f(\mathbf{X} + \mathbf{H}) = \text{tr}((\mathbf{X} + \mathbf{H})^T \mathbf{A} (\mathbf{X} + \mathbf{H})). \quad (699)
\]
