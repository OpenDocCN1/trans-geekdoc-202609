
## 17.7.1 Functional analysis

In this section, we introduce some basic concepts from the area of **functional analysis**. This extends ideas from Sec. C.1.2 to the case of *vector spaces of functions.*

Every element of a (real-valued) function space \(\mathcal{F}\) is a function of the form \(f : \mathcal{X} \to \mathbb{R}\), and elements (functions) can be added and scalar multiplied as if they were vectors. That is, if \(f \in \mathcal{F}\) and \(g \in \mathcal{F}\), then \(\alpha f + \beta g \in \mathcal{F}\) for \(\alpha,\beta \in \mathbb{R}\).

We can also define an **inner product** for \(\mathcal{F}\), which is a mapping \(\langle f,g\rangle \in \mathbb{R}\) which satisfies the following:

$$
\langle \alpha f_1 + \beta f_2, g \rangle = \alpha \langle f_1,g\rangle + \beta \langle f_2,g\rangle \tag{17.156}
$$
$$
\langle f,g\rangle = \langle g,f\rangle \tag{17.157}
$$
$$
\langle f,f\rangle \ge 0 \tag{17.158}
$$
$$
\langle f,f\rangle = 0 \text{ iff } f(\mathbf{x}) = 0 \text{ for all } \mathbf{x} \in \mathcal{X} \tag{17.159}
$$

We define the norm of a function using

$$
\|f\| \triangleq \sqrt{\langle f,f\rangle} \tag{17.160}
$$

We say that \(f,g \in \mathcal{F}\) are orthogonal to each other if \(\langle f,g\rangle = 0\). We say that a set of functions \(\{f_i, i \in \mathcal{I}\}\) is an orthonormal system if the norm of every \(f_i\) is 1, and the \(\{f_i\}\) are orthogonal. Hence the \(\{f_i\}\) are linearly independent. An orthonormal system is called an **orthonormal basis** if there is no other (non-zero) \(f \in \mathcal{F}\) that is orthogonal to all the \(\{f_i\}\).

## 17.7.2 Hilbert space

A function space \(\mathcal{H}\) with an inner product operator is called a **Hilbert space**. (We also require that the function space be complete, which means that every Cauchy sequence of functions \(f_i \in \mathcal{H}\) has a limit that is also in \(\mathcal{H}\).)

The most common Hilbert space is the space known as \(L^2\). To define this, we need to specify a **measure** \(\mu\) on the input space \(\mathcal{X}\); this is a function that assigns any (suitable) subset \(A\) of \(\mathcal{X}\) to a positive number, such as its volume. This can be defined in terms of the density function \(w : \mathcal{X} \to \mathbb{R}\), as follows:

$$
\mu(A) = \int_A w(x)dx \tag{17.161}
$$

Thus we have \(\mu(dx) = w(x)dx\). We can now define \(L^2(\mathcal{X},\mu)\) to be the space of functions \(f : \mathcal{X} \to \mathbb{R}\) that satisfy

$$
\int_{\mathcal{X}} f(x)^2 w(x)dx < \infty \tag{17.162}
$$

This is known as the set of **square-integrable functions**. This space has an inner product defined by

$$
\langle f,g\rangle = \int_{\mathcal{X}} f(x)g(x)w(x)dx \tag{17.163}
$$

A Hilbert space with an orthonormal basis \(\{f_i\}\) is similar to a Euclidean vector space. In particular, any element \(f \in \mathcal{H}\) can be written as a unique linear combination of basis vectors:

$$
f = \sum_i \langle f, f_i \rangle f_i
$$

## 17.7.3 Reproducing Kernel Hilbert Space

Let \(\mathcal{H}\) be the space \(L^2(\mathcal{X})\) of functions \(\mathcal{X} \to \mathbb{R}\). For each \(x \in \mathcal{X}\), let \(\delta_x : \mathcal{H} \to \mathbb{R}\) be the evaluation functional that takes as input a function \(f \in \mathcal{H}\) and evaluates it at \(x\), i.e., \(\delta_x(f) = f(x)\). We say that a Hilbert space \(\mathcal{H}\) is a Reproducing Kernel Hilbert Space or RKHS if for each \(\delta_x\) there is a unique element \(K_x \in \mathcal{H}\) such that for every \(f \in \mathcal{H}\)

$$
\delta_x(f) = f(x) = \langle f, K_x \rangle
$$

Now consider the function \(f = K_y \in \mathcal{H}\) evaluated at \(x\). We have

$$
\delta_x(K_y) = K_y(x) = \langle K_y, K_x \rangle \triangleq K(x,y)
$$

This is called the reproducing property and \(K(x,y)\) is called the RKHS kernel. Clearly the kernel function is symmetric. One can also show that it is positive semidefinite, in the sense that we can represent it as

$$
K(x,y) = \sum_{j \geq 1} \lambda_j \psi_j(x) \psi_j(y)
$$

where \(\{\lambda_j\}\) is a countable sequence of non-negative numbers decreasing to 0, and the \(\psi_j\) are orthonormal functions in \(L^2(\mathcal{X})\). This result is known as Mercer's theorem.

Mercer’s theorem tells us that every RKHS has a corresponding positive definite kernel function. The converse of this is known as the Moore-Aronszajn theorem. More precisely, this says that for every psd kernel function \(K : \mathcal{X} \times \mathcal{X} \to \mathbb{R}\), there exists a unique RKHS of functions \(f : \mathcal{X} \to \mathbb{R}\) with reproducing kernel \(K\).

## 17.7.4 Representer theorem

In this section, we consider the application of RKHS to the problem of (regularized) empirical risk minimization. In particular, we state and prove the representer theorem [KW70; SHS01], which generalizes the result of Eq. (17.130).

**Theorem 17.7.1 (Representer theorem).** Consider the following regularized empirical risk minimization problem:

$$
f^* = \arg\min_{f \in \mathcal{H}_{\mathcal{K}}} \mathcal{L}(f)
$$

where

$$
\mathcal{L}(f) = \frac{1}{N} \sum_{n=1}^N \ell(y_n, f(x_n)) + R(\|f\|)
$$

where \(\mathcal{H}_{\mathcal{K}}\) is an RKHS with kernel \(\mathcal{K}\), \(\ell(y, \hat{y}) \in \mathbb{R}\) is a loss function, \(R(c) \in \mathbb{R}\) is a strictly monotonic penalty function, and

$$
\|f\|_{\mathcal{H}} = \sqrt{\langle f, f \rangle_{\mathcal{H}}} \tag{17.170}
$$

is the norm of the function. Then we have

$$
f^*(x) = \sum_{i=1}^{N} \alpha_i \mathcal{K}(x, x_i) \tag{17.171}
$$

where \(\alpha_i \in \mathbb{R}\) are some coefficients that depend on the training data \(\{(x_n, y_n)\}\).

*Proof.* Let us define the feature map \(\Phi(x) = \mathcal{K}(\cdot, x)\). Given any \(x_1, \dots, x_N\), we can use orthogonal projection to decompose any \(f \in \mathcal{H}_{\mathcal{K}}\) into a sum of two functions, one lying in the span of \(\{\Phi(x_1), \dots, \Phi(x_N)\}\), and the other lying in the orthogonal complement; let this latter function be denoted by \(v\). Thus

$$
f = \sum_{i=1}^{N} \alpha_i \Phi(x_i) + v \tag{17.172}
$$

where \(\langle v, \Phi(x_i) \rangle = 0\) for all \(i\). Using this result, together with the reproducing property, we have

$$
f(x_j) = \left\langle \sum_{i=1}^{N} \alpha_i \Phi(x_i) + v, \Phi(x_j) \right\rangle = \sum_{i=1}^{N} \alpha_i \langle \Phi(x_i), \Phi(x_j) \rangle \tag{17.173}
$$

Since \(f(x_j)\) is independent of \(v\), we see that the first term in \(\mathcal{L}(f)\) is independent of \(v\). Now let us consider the second (regularization) term in \(\mathcal{L}(f)\). Since \(v\) is orthogonal to \(\sum_{i=1}^{N} \alpha_i \Phi(x_i)\) and \(R\) is strictly monotonic, we have

$$
R(\|f\|) = R\left( \left\| \sum_{i=1}^{N} \alpha_i \Phi(x_i) + v \right\| \right) \tag{17.174}
$$

$$
= R\left( \sqrt{ \left\| \sum_{i=1}^{N} \alpha_i \Phi(x_i) \right\|^2 + \|v\|^2 } \right) \tag{17.175}
$$

$$
\ge R\left( \left\| \sum_{i=1}^{N} \alpha_i \Phi(x_i) \right\| \right) \tag{17.176}
$$

Thus we can minimize the second term of \(\mathcal{L}(f)\) by setting \(v = 0\). Hence we can minimize the overall regularized loss by using a solution of the form

$$
f^*(\cdot) = \sum_{i=1}^{N} \alpha_i \Phi(x_i) = \sum_{i=1}^{N} \alpha_i \mathcal{K}(\cdot, x_i) \tag{17.177}
$$

## 18 Trees, forests, bagging and boosting

### 18.1 Classification and regression trees (CART)

In this section, we discuss **classification and regression trees (CART)** [BFOS84], also called **decision trees** [Qui86; Qui93], which are widely used for tabular datasets. We introduced this model in Sec. 1.2.1.3. Here we go into more detail.

#### 18.1.1 Model definition

A CART model is a tree structure consisting of a set of nested decision rules. At each node \(i\), the feature dimension \(d_i\) of the input vector \(\mathbf{x}\) is compared to a threshold value \(t_i\), and the input is then passed down to the left or right branch, depending on whether it is above or below threshold. (For categorical values, we compare if \(x_{d_i}\) is equal to the target value \(t_i\) or not.) At the leaves of the tree, the model specifies a distribution over the output for points that are in that part of the input space.

Formally, a CART model can be defined by

$$
T(\mathbf{x};\theta)=\sum_{j=1}^{J} w_j\mathbb{I}(\mathbf{x}\in R_j) \tag{18.1}
$$

where \(R_j\) is the region specified by the \(j\)th leaf node, \(w_j\) is the predicted output for that node, and \(\theta=\{(R_j,w_j):j=1:J\}\). (For regression, the predicted output for each leaf \(w_j\) is a scalar; for classification, it can be the logits or class probabilities.)

For example, consider the regression tree in Fig. 18.1(a). The first node asks if \(x_1\) is less than some threshold \(t_1\). If yes, we then ask if \(x_2\) is less than some other threshold \(t_2\). If yes, we are in the bottom left quadrant of space, \(R_1\). If no, we ask if \(x_1\) is less than \(t_3\). And so on. The result of these axis-parallel splits is to partition 2D space into 5 regions, as shown in Figure 18.1(b). We can now associate a mean response with each of these regions, resulting in the piecewise constant surface shown in Figure 18.1(c).

For classification problems, we can proceed in a similar manner, except that the leaves contain a distribution over the class labels, rather than just the mean response. See Fig. 18.2a–Fig. 18.2b for an example.
