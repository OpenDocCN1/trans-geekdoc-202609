
The above objective is a quadratic problem in $N$ variables. Standard QP solvers take $O(N^3)$ time. However, specialized algorithms, which avoid the use of generic QP solvers, have been developed for this problem, such as the sequential **minimal optimization** or SMO algorithm [Pl98], which takes $O(N)$ to $O(N^2)$ time.

Since this is a convex objective, the solution must satisfy the KKT conditions (Sec. 5.5.2), which tell us that the following properties hold:

$$
\begin{aligned}
\alpha_n &\ge 0 &&\tag{17.115}\\
\tilde y_n f(x_n)-1 &\ge 0 &&\tag{17.116}\\
\alpha_n\bigl(\tilde y_n f(x_n)-1\bigr) &= 0 &&\tag{17.117}
\end{aligned}
$$

Hence either $\alpha_n=0$ (in which case example $n$ is ignored when computing $\hat{\mathbf w}$) or the constraint $\tilde y_n(\hat{\mathbf w}^{\mathsf T}\mathbf x_n+\hat w_0)=1$ is active. This latter condition means that example $n$ lies on the margin boundary; these points are known as the **support vectors**, as shown in Fig. 17.15(b). We denote the set of support vectors by $\mathcal S$.

To perform prediction, we use

$$f(\mathbf{x};\hat{\mathbf w},\hat w_0)=\hat{\mathbf w}^{\mathsf T}\mathbf x+\hat w_0=\sum_{n\in\mathcal S}\alpha_n\tilde y_n\mathbf x_n^{\mathsf T}\mathbf x+\hat w_0 \tag{17.118}$$

To solve for $\hat w_0$ we can use the fact that for any support vector, we have $\tilde y_n f(\mathbf x;\hat{\mathbf w},\hat w_0)=1$. Multiplying both sides by $\tilde y_n$, and exploiting the fact that $\tilde y_n^2=1$, we get $\hat w_0=\tilde y_n-\hat{\mathbf w}^{\mathsf T}\mathbf x_n$. In practice we get better results by averaging over all the support vectors to get

$$\hat w_0=\frac{1}{|\mathcal S|}\sum_{n\in\mathcal S}(\tilde y_n-\hat{\mathbf w}^{\mathsf T}\mathbf x_n)=\frac{1}{|\mathcal S|}\sum_{n\in\mathcal S}\left(\tilde y_n-\sum_{m\in\mathcal S}\alpha_m\tilde y_m\mathbf x_m^{\mathsf T}\mathbf x_n\right) \tag{17.119}$$

## 17.5.3 Soft margin classifiers

If the data is not linearly separable, there will be no feasible solution in which $\tilde y_n f_n\ge 1$ for all $n$. We therefore introduce **slack variables** $\xi_n\ge 0$ and replace the hard constraints that $\tilde y_n f_n\ge 1$ with the **soft margin constraints** that $\tilde y_n f_n\ge 1-\xi_n$. The new objective becomes

$$\min_{\mathbf w,w_0,\boldsymbol\xi}\ \frac{1}{2}\|\mathbf w\|^2+C\sum_{n=1}^{N}\xi_n\quad \text{s.t.}\quad \xi_n\ge 0,\quad \tilde y_n(\mathbf x_n^{\mathsf T}\mathbf w+w_0)\ge 1-\xi_n \tag{17.120}$$

where $C\ge 0$ is a hyperparameter controlling how many points we allow to violate the margin constraint. (If $C=\infty$, we recover the unregularized, hard-margin classifier.)

The corresponding Lagrangian for the soft margin classifier becomes

$$\mathcal L(\mathbf w,w_0,\boldsymbol\alpha,\boldsymbol\xi,\boldsymbol\mu)=\frac{1}{2}\mathbf w^{\mathsf T}\mathbf w+C\sum_{n=1}^{N}\xi_n-\sum_{n=1}^{N}\alpha_n\bigl(\tilde y_n(\mathbf w^{\mathsf T}\mathbf x_n+w_0)-1+\xi_n\bigr)-\sum_{n=1}^{N}\mu_n\xi_n \tag{17.121}$$

where $\alpha_n\ge 0$ and $\mu_n\ge 0$ are the Lagrange multipliers. Optimizing out $\mathbf w$, $w_0$ and $\boldsymbol\xi$ gives the dual form

$$\mathcal L(\boldsymbol\alpha)=\sum_{i=1}^{N}\alpha_i-\frac{1}{2}\sum_{i=1}^{N}\sum_{j=1}^{N}\alpha_i\alpha_j\tilde y_i\tilde y_j\mathbf x_i^{\mathsf T}\mathbf x_j \tag{17.122}$$

This is identical to the hard margin case; however, the constraints are different. In particular, the KKT conditions imply

$$0 \le \alpha_n \le C \tag{17.123}$$

$$\sum_{n=1}^N \alpha_n \tilde{y}_n = 0 \tag{17.124}$$

If $\alpha_n = 0$, the point is ignored. If $0 < \alpha_n < C$ then $\xi_n = 0$, so the point lies on the margin. If $\alpha_n = C$, the point can lie inside the margin, and can either be correctly classified if $\xi_n \le 1$, or misclassified if $\xi_n > 1$. See Fig. 17.15(b) for an illustration. Hence $\sum_n \xi_n$ is an upper bound on the number of misclassified points.

As before, the bias term can be computed using

$$\hat{w}_0 = \frac{1}{|\mathcal{M}|} \sum_{n \in \mathcal{M}} \left( \tilde{y}_n - \sum_{m \in \mathcal{S}} \alpha_m \tilde{y}_m \mathbf{x}_m^\top \mathbf{x}_n \right) \tag{17.125}$$

where $\mathcal{M}$ is the set of points having $0 < \alpha_n < C$.

There is an alternative formulation of the soft margin SVM known as the $\nu$-SVM classifier [Sch+00]. This involves maximizing

$$\mathcal{L}(\boldsymbol{\alpha}) = -\frac{1}{2} \sum_{i=1}^N \sum_{j=1}^N \alpha_i \alpha_j \tilde{y}_i \tilde{y}_j \mathbf{x}_i^\top \mathbf{x}_j \tag{17.126}$$

subject to the constraints that

$$0 \le \alpha_n \le 1/N \tag{17.127}$$

$$\sum_{n=1}^N \alpha_n \tilde{y}_n = 0 \tag{17.128}$$

$$\sum_{n=1}^N \alpha_n \ge \nu \tag{17.129}$$

This has the advantage that the parameter $\nu$, which replaces $C$, can be interpreted as an upper bound on the fraction of margin errors (points for which $\xi_n > 0$), as well as a lower bound on the number of support vectors.

## 17.5.4 The kernel trick

So far we have converted the large margin binary classification problem into a dual problem in $N$ unknowns $(\boldsymbol{\alpha})$ which (in general) takes $O(N^3)$ time to solve, which can be slow. However, the principal benefit of the dual problem is that we can replace all inner product operations $\mathbf{x}^\top \mathbf{x}'$ with a call to a positive definite (Mercer) kernel function, $\mathcal{K}(\mathbf{x}, \mathbf{x}')$. This is called the kernel trick.

In particular, we can rewrite the prediction function in Eq. (17.118) as follows:

$$f(\mathbf{x}) = \hat{\mathbf{w}}^\top \mathbf{x} + \hat{w}_0 = \sum_{n \in \mathcal{S}} \alpha_n \tilde{y}_n \mathbf{x}_n^\top \mathbf{x} + \hat{w}_0 = \sum_{n \in \mathcal{S}} \alpha_n \tilde{y}_n \mathcal{K}(\mathbf{x}_n, \mathbf{x}) + \hat{w}_0 \tag{17.130}$$

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_578_0.png)

Figure 17.17: Log-odds vs \(x\) for 3 different methods. Adapted from Figure 10 of [Tip01]. Used with kind permission of Mike Tipping.

We also need to kernelize the bias term. This can be done by kernelizing Eq. (17.119) as follows:

$$\hat{w}_0 = \frac{1}{|\mathcal{S}|} \sum_{i\in\mathcal{S}} \left( \tilde{y}_i - \left(\sum_{j\in\mathcal{S}} \hat{\alpha}_j \tilde{y}_j \mathbf{x}_j \right)^\top \mathbf{x}_i \right) = \frac{1}{|\mathcal{S}|} \sum_{i\in\mathcal{S}} \left( \tilde{y}_i - \left(\sum_{j\in\mathcal{S}} \hat{\alpha}_j \tilde{y}_j \mathcal{K}(\mathbf{x}_j, \mathbf{x}_i) \right) \right) \tag{17.131}$$

The kernel trick allows us to avoid having to deal with an explicit feature representation of our data, and allows us to easily apply classifiers to structured objects, such as strings and graphs.

## 17.5.5 Converting SVM outputs into probabilities

An SVM classifier produces a hard-labeling, $\hat{y}(\mathbf{x}) = \operatorname{sign}(f(\mathbf{x}))$. However, we often want a measure of confidence in our prediction. One heuristic approach is to interpret $f(\mathbf{x})$ as the log-odds ratio, $\log \frac{p(y=1|\mathbf{x})}{p(y=0|\mathbf{x})}$. We can then convert the output of an SVM to a probability using

$$p(y=1|\mathbf{x},\boldsymbol{\theta}) = \sigma\big(a f(\mathbf{x}) + b\big) \tag{17.132}$$

where $a$, $b$ can be estimated by maximum likelihood on a separate validation set. (Using the training set to estimate $a$ and $b$ leads to severe overfitting.) This technique was first proposed in [Pla00], and is known as Platt scaling.

However, the resulting probabilities are not particularly well calibrated, since there is nothing in the SVM training procedure that justifies interpreting $f(\mathbf{x})$ as a log-odds ratio. To illustrate this, consider an example from [Tip01]. Suppose we have 1d data where $p(x|y=0)=\text{Unif}(0,1)$ and $p(x|y=1)=\text{Unif}(0.5,1.5)$. Since the class-conditional distributions overlap in the $[0.5,1]$ range, the log-odds of class 1 over class 0 should be zero in this region, and infinite outside this region. We sampled 1000 points from the model, and then fit a probabilistic kernel classifier (an RVM, described in Sec. 17.6.1) and an SVM with a Gaussian kernel of width 0.1. Both models can perfectly capture the decision boundary, and achieve a generalization error of 25%, which is Bayes optimal in this problem. The probabilistic output from the RVM is a good approximation to the true log-odds, but this is not the case for the SVM, as shown in Fig. 17.17.
