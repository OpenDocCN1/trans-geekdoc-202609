# 11.5.9.1 Coordinate descent

Sometimes it is hard to optimize all the variables simultaneously, but it easy to optimize them one by one. In particular, we can solve for the j’th coefficient with all the others held fixed as follows:

$$w_j^* = \arg\min_{\eta} \mathcal{L}(\mathbf{w} + \eta \mathbf{e}_j) \tag{11.119}$$

where $\mathbf{e}_j$ is the j’th unit vector. This is called **coordinate descent**. We can either cycle through the coordinates in a deterministic fashion, or we can sample them at random, or we can choose to update the coordinate for which the gradient is steepest.

This method is particularly appealing if each one-dimensional optimization problem can be solved analytically, as is the case for lasso (see Eq. (11.104)). This is known as the **shooting** algorithm [Fu98; WL08]. (The term “shooting” is a reference to cowboy theme inspired by the term “lasso”.) See Algorithm 4 for details.

This coordinate descent method has been generalized to the GLM case in [FHT10], and is the basis of the popular **glmnet** software library.

**Algorithm 4:** Coordinate descent for lasso (aka shooting algorithm)

1 Initialize **w** = (**X**ᵀ**X** + λ**I**)⁻¹**X**ᵀ**y**;
2 **repeat**
3   **for** d = 1, …, D **do**
4     a_d = Σ_{n=1}^N x_{nd}²;
5     c_d = Σ_{n=1}^N x_{nd}(y_n - **w**ᵀ**x**_n + w_d x_{nd});
6     w_d = SoftThreshold(c_d / a_d, λ / a_d);
7 **until** converged;

# 11.5.9.2 Projected gradient descent

In this section, we convert the non-differentiable ℓ₁ penalty into a smooth regularizer. To do this, we first use the **split variable trick** to define **w** = **w**⁺ − **w**⁻, where **w**⁺ = max{**w**,0} and **w**⁻ = −min{**w**,0}. Now we can replace ‖**w**‖₁ with Σ_d (w_d⁺ + w_d⁻). We also have to replace NLL(**w**) with NLL(**w**⁺ + **w**⁻). Thus we get the following smooth, but constrained, optimization problem:

$$\min_{\mathbf{w}^+ \ge 0, \mathbf{w}^- \ge 0} \text{NLL}(\mathbf{w}^+ - \mathbf{w}^-) + \lambda \sum_{d=1}^D (w_d^+ + w_d^-) \tag{11.120}$$

We can use projected gradient descent (Sec. 5.6.1) to solve this problem. Specifically, we can enforce the constraint by projecting onto the positive orthant, which we can do using w_d = max(w_d,0); this operation is denoted by P₊. Thus the projected gradient update takes the following form:

$$\begin{pmatrix} \mathbf{w}_{t+1}^+ \\ \mathbf{w}_{t+1}^- \end{pmatrix} = P_+ \left( \begin{bmatrix} \mathbf{w}_t^+ - \eta_t \nabla \text{NLL}(\mathbf{w}_t^+ - \mathbf{w}_t^-) - \eta_t \lambda \mathbf{e} \\ \mathbf{w}_t^- + \eta_t \nabla \text{NLL}(\mathbf{w}_t^+ - \mathbf{w}_t^-) - \eta_t \lambda \mathbf{e} \end{bmatrix} \right) \tag{11.121}$$

where e is the unit vector of all ones.