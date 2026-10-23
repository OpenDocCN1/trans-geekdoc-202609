
This can make it difficult to use such methods on large scale data. Fortunately, we can approximate the feature map for many (shift invariant) kernels using a randomly chosen finite set of M basis functions, thus reducing the cost to O(NM + M³). We briefly discuss this idea below. For more details, see e.g., [Liu+20].

### 17.4.3.1 Random features for RBF kernel

We will focus on the case of the Gaussian RBF kernel. One can show that

K(x, x') ≈ φ(x)ᵀ φ(x') (17.95)

where the (real-valued) feature vector is given by

φ(x) ≜ 1/√T [(sin(ω₁ᵀx),..., sin(ω_Tᵀx), cos(ω₁ᵀx),..., cos(ω_Tᵀx))] (17.96) = 1/√T [sin(Ωx), cos(Ωx)] (17.97)

where T = M/2, and Ω ∈ ℝ^{T×D} is a random Gaussian matrix, where the entries are sampled iid from N(0,1/σ²), where σ is the kernel bandwidth. The bias of the approximation decreases as we increase M. In practice, we use a finite M, and compute a single sample Monte Carlo approximation to the expectation by drawing a single random matrix. The representation in Eq. (17.97) is called random Fourier features (RFF) [RR08] or “weighted sums of random kitchen sinks” [RR09].

We can also use positive random features, rather than trigonometric random features, which can be preferable in some applications, such as attention Sec. 15.6.4. In particular, we can use

φ(x) ≜ e^{-||x||²/2} 1/√M [(exp(ω₁ᵀx),..., exp(ω_Mᵀx)] (17.98)

where ω_m are sampled as before. For details, see [Cho+20b]. Regardless of whether we use trigonometric or positive features, we can obtain a lower variance estimate by ensuring that the rows of Z are random but orthogonal; these are called orthogonal random features. Such sampling can be conducted efficiently via Gram-Schmidt orthogonalization of the unstructured Gaussian matrices [Yu+16], or several approximations that are even faster (see [CRW17; Cho+19]).

### 17.4.3.2 Fastfood approximation

Unfortunately, storing the random matrix Ω takes O(DM) space, and computing Ωx takes O(DM) time, where D is the input dimensionality, and M is the number of random features. This can be prohibitive if M ≫ D, which it may need to be in order to get any benefits over using the original set of features. Fortunately, we can use the fast Hadamard transform to reduce the memory from O(MD) to O(M), and reduce the time from O(MD) to O(M log D). This approach has been called fastfood [LSS13], a reference to the original term “kitchen sinks”.

### 17.4.3.3 Extreme learning machines

We can use the random features approximation to the kernel to convert a GP into a linear model of the form

$$f(\mathbf{x}; \boldsymbol{\theta}) = \mathbf{W}\phi(\mathbf{x}) = \mathbf{W}h(\mathbf{Zx}) \tag{17.99}$$

where $h(a) = \sqrt{1/M}[\sin(a), \cos(a)]$ for RBF kernels. This is equivalent to a one-layer MLP with random (and fixed) input-to-hidden weights. When $M > N$, this corresponds to an over-parameterized model, which can perfectly interpolate the training data.

In [Cur+17], they apply this method to fit a logistic regression model of the form $f(\mathbf{x};\boldsymbol{\theta}) = \mathbf{W}^\top h(\mathbf{Zx}) + \mathbf{b}$ using SGD; they call the resulting method “McKernel”. We can also optimize $\mathbf{Z}$ as well as $\mathbf{W}$, as discussed in [Alb+17], although now the problem is no longer convex.

Alternatively, we can use $M < N$, but stack many such random nonlinear layers together, and just optimize the output weights. This has been called an **extreme learning machine** or **ELM** (see e.g., [Hua14]), although this work is controversial.²

## 17.5 Support vector machines (SVMs)

In this section, we discuss a form of (non-probabilistic) predictors for classification and regression problems which have the form

$$f(\mathbf{x}) = \sum_{i=1}^{N} \alpha_i \mathcal{K}(\mathbf{x}, \mathbf{x}_i) \tag{17.100}$$

By adding suitable constraints, we can ensure that many of the $\alpha_i$ coefficients are 0, so that predictions at test time only depend on a subset of the training points. The surviving points are called “**support vectors**”, and the resulting model is called a **support vector machine** or **SVM**. We give a brief summary below. More details can be found in e.g., [VGS97; SS01],

### 17.5.1 Large margin classifiers

Consider a binary classifier of the form $h(\mathbf{x}) = \operatorname{sign}(f(\mathbf{x}))$, where the decision boundary is given by the following linear function:

$$f(\mathbf{x}) = \mathbf{w}^\top \mathbf{x} + w_0 \tag{17.101}$$

(In the SVM literature, it is common to assume the class labels are $-1$ and $+1$, rather than 0 and 1. To avoid confusion, we denote such target labels by $\tilde{y}$ rather than $y$.) There may be many lines that separate the data. However, intuitively we would like to pick the one that has maximum **margin**, which is the distance of the closest point to the decision boundary, since this will give us the most robust solution. This idea is illustrated in Fig. 17.14: the solution on the left has larger margin than the one on the right, and intuitively it is better, since it will be less sensitive to perturbations of the data.

2. The controversy has arisen because the inventor Guang-Bin Huang has been accused of not citing related prior work, such as the equivalent approach based on random feature approximations to kernels. For details, see https://en.wikipedia.org/wiki/Extreme_learning_machine#Controversy.

## 17.5 Support vector machines (SVMs)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_573_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_573_1.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_574_0.png)

Figure 17.16: Illustration of the benefits of scaling the input features before computing a max margin classifier. Adapted from Figure 5.2 of [Gér19]. Generated by svm_classifier_feature_scaling.py.

How can we compute such a large margin classifier? First we need to derive an expression for the distance of a point to the decision boundary. Referring to Fig. 17.15(a), we see that

x = x_⊥ + r w / ||w||  (17.102)

where r is the distance of x from the decision boundary whose normal vector is w, and x_⊥ is the orthogonal projection of x onto this boundary.

We would like to maximize r, so we need to express it as a function of w. First, note that

f(x) = w^T x + w0 = (w^T x_⊥ + w0) + r w^T w / ||w|| = (w^T x_⊥ + w0) + r ||w||  (17.103)

Since 0 = f(x_⊥) = w^T x_⊥ + w0, we have f(x) = r ||w|| and hence r = f(x)/||w||.

Since we want to ensure each point is on the correct side of the boundary, we also require f(x_n) ỹ_n > 0. We want to maximize the distance of the closest point, so our final objective becomes max_{w,w0} 1/||w|| min_{n=1}^N [ ỹ_n (w^T x_n + w0) ]  (17.104)

### 17.5.2 The dual problem

The objective in Eq. (17.105) is a standard quadratic programming problem (Sec. 5.5.4), since we have a quadratic objective subject to linear constraints. This has $N + D + 1$ variables subject to $N$ constraints, and is known as a **primal problem**.

In convex optimization, for every primal problem we can derive a **dual problem**. Let $\boldsymbol{\alpha} \in \mathbb{R}^N$ be the dual variables, corresponding to Lagrange multipliers that enforce the $N$ inequality constraints. The generalized Lagrangian is given below (see Sec. 5.5.2 for relevant background information on constrained optimization):

$\mathcal{L}(\mathbf{w}, w_0, \boldsymbol{\alpha}) = \frac{1}{2} \mathbf{w}^\top \mathbf{w} - \sum_{n=1}^{N} \alpha_n (\tilde{y}_n (\mathbf{w}^\top \mathbf{x}_n + w_0) - 1) \tag{17.106}$

To optimize this, we must find a stationary point that satisfies

$(\hat{\mathbf{w}}, \hat{w}_0, \hat{\boldsymbol{\alpha}}) = \min_{\mathbf{w}, w_0} \max_{\boldsymbol{\alpha}} \mathcal{L}(\mathbf{w}, w_0, \boldsymbol{\alpha}) \tag{17.107}$

We can do this by computing the partial derivatives wrt $\mathbf{w}$ and $w_0$ and setting to zero. We have

$\nabla_{\mathbf{w}} \mathcal{L}(\mathbf{w}, w_0, \boldsymbol{\alpha}) = \mathbf{w} - \sum_{n=1}^{N} \alpha_n \tilde{y}_n \mathbf{x}_n \tag{17.108}$

$\frac{\partial}{\partial w_0} \mathcal{L}(\mathbf{w}, w_0, \boldsymbol{\alpha}) = - \sum_{n=1}^{N} \alpha_n \tilde{y}_n \tag{17.109}$

and hence

$\hat{\mathbf{w}} = \sum_{n=1}^{N} \hat{\alpha}_n \tilde{y}_n \mathbf{x}_n \tag{17.110}$

$0 = \sum_{n=1}^{N} \hat{\alpha}_n \tilde{y}_n \tag{17.111}$

Plugging these into the Lagrangian yields the following

$\mathcal{L}(\hat{\mathbf{w}}, \hat{w}_0, \boldsymbol{\alpha}) = \frac{1}{2} \hat{\mathbf{w}}^\top \hat{\mathbf{w}} - \sum_{n=1}^{N} \alpha_n \tilde{y}_n \hat{\mathbf{w}}^\top \mathbf{x}_n - \sum_{n=1}^{N} \alpha_n \tilde{y}_n w_0 + \sum_{n=1}^{N} \alpha_n \tag{17.112}$

$= \frac{1}{2} \hat{\mathbf{w}}^\top \hat{\mathbf{w}} - \hat{\mathbf{w}}^\top \hat{\mathbf{w}} - 0 + \sum_{n=1}^{N} \alpha_n \tag{17.113}$

$= -\frac{1}{2} \sum_{i=1}^{N} \sum_{j=1}^{N} \alpha_i \alpha_j \tilde{y}_i \tilde{y}_j \mathbf{x}_i^\top \mathbf{x}_j + \sum_{n=1}^{N} \alpha_n \tag{17.114}$

This is called the **dual form** of the objective. We want to maximize this wrt $\boldsymbol{\alpha}$ subject to the constraints that $\sum_{n=1}^{N} \alpha_n \tilde{y}_n = 0$ and $0 \le \alpha_n$ for $n = 1 : N$.
