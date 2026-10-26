
## Exercises

10.1 In Example 10.9, assume that the vectors \([\psi(X) : X \in S_n]\) are orthogonal for \(\psi \in \Psi\). Derive a lower bound for the Rademacher complexity of \(F_{A,L_2}(\Psi)\) via direct calculation.

10.2 Let \(w_* = e_1 \in \mathbb{R}^d\). Consider \(\psi(x) = [\psi_1(x),\dots,\psi_d(x)] \in \mathbb{R}^d\) such that for observations \(\{(X_1,Y_1),\dots,(X_n,Y_n)\}\), \(n^{-1/2}[\psi_j(X_1),\dots,\psi_j(X_n)]\) are \(d\) orthonormal vectors in \(\mathbb{R}^n\) \((j=1,\dots,d)\), and \(Y_i = w_*^T \psi(X_i) + \varepsilon_i\), where \(\varepsilon_i \sim N(0,\sigma^2)\) \((i=1,\dots,n)\) are zero-mean noises. Consider ridge regression:

\[
\hat{w}(\lambda) = \arg\min_w \left[ \frac{1}{n} \sum_{i=1}^n (w^T \psi(X_i) - Y_i)^2 + \lambda \|w\|_2^2 \right].
\]

Find the optimal \(\lambda\) so that

\[
\mathbb{E}_\varepsilon \|\hat{w}(\lambda) - w_*\|_2^2
\]

is minimized. Compute the minimum value.

10.3 In the previous example, consider the Lasso regression:

\[
\hat{w}(\lambda) = \arg\min_w \left[ \frac{1}{n} \sum_{i=1}^n (w^T \psi(X_i) - Y_i)^2 + \lambda \|w\|_1 \right].
\]

For \(\lambda > 0\), find an upper bound of

\[
\mathbb{E}_\varepsilon \|\hat{w}(\lambda) - w_*\|_2^2.
\]

Find \(\lambda\) to approximately minimize the upper bound with logarithmic dependence on \(d\), and compare to that of the ridge regression.

10.4 Consider the uniform convergence bound in Theorem 10.4. Let \(\{1,\dots,m\} = J_1 \cup \dots \cup J_g\) be a nonoverlapping partition of \(\{1,\dots,m\}\) into \(g\) groups of size \(m/g\) each (we assume \(m/g\) is an integer). Let \(H\) contain the subsets of \(\{1,\dots,m\}\) that can be expressed as the union of one or more groups \(J_\ell\). That is, if \(J \in H\), then for all \(\ell = 1,\dots,g\), either \(J_\ell \subset J\) or \(J_\ell \cap J = \emptyset\).

In group sparsity, we consider only the sparse models indexed by \(F \in H\).

- Derive a uniform convergence bound for group sparsity, where we consider a uniform bound that holds for all \(w\) and \(F\) with \(\operatorname{supp}(w) \subset F\).
- Compare this bound to the sparse learning bound of Theorem 10.4, and derive an estimation method in (10.5) with \(r(F)\) obtained using this bound. Explain when group sparsity performs better.

10.5 Use the Rademacher complexity of constrained entropy regularization in Corollary 10.17, and the same techniques in the proof of Corollary 10.14 for the following.

- Derive a data-dependent bound that holds uniformly for all \(A > 0\).
- Use the bound to derive an oracle inequality for the soft regularization version of the Gibbs algorithm, and compare the result to Theorem 10.18.

10.6 Prove Proposition 10.39.

10.7 Consider Theorem 10.37. Assume that \(\sqrt{n} X\) is an \(n \times p\) random matrix with iid standard Gaussian entries, and \(\bar{F}\) is independent of \(X\). Show that there exists an absolute constant \(c_0 > 0\) so that if

\[
n \ge c_0 |\bar{F}| \ln(p),
\]

the irrepresentable condition \(\mu < 1\) holds with probability at least 0.5.

10.8 Consider Theorem 10.37 with columns of \(X\) normalized: \(\|X_i\|_2 = 1\) for all \(i \in [p]\).

- Show that if the mutual incoherence condition \(\sup_{i \ne j} |X_i^T X_j| < 1/(2s-1)\) holds for some integer \(s \ge 1\), then the irrepresentable condition holds for all \(\bar{w}\) such that \(\|\bar{w}\|_0 \le s\).
- Show that if the columns \(X_i\) are normalized from \(X'\), where \(X'\) is an \(n \times p\) random matrix with iid standard Gaussian entries, then the mutual incoherence condition holds with \(n = \Omega(s^2 \ln p)\).

## Analysis of Neural Networks

The idea of neural networks (NNs) can be dated back to the 1960s, and the key computational procedures for neural networks using stochastic gradient descent were developed in the 1980s. However, the training of neural networks was quite costly, and large-scale training of neural networks has only become practical with the advance of GPU computing in the 2010s.

A major difficulty in analyzing neural networks is their nonconvexity, and many of their empirically observed properties have not been fully explained by theory. This chapter presents some known theoretical results for neural networks, including some theoretical analysis that has been developed recently. While a general theory of neural networks is still under development, we will cover some existing results, including function approximation results and generalization analysis. In particular, we show that neural networks can be analyzed both using the kernel analysis of Chapter 9, and the \(L_1\) regularization-based analysis of Chapter 10.

### 11.1 Introduction to Neural Networks

The simplest neural networks are two-layer neural networks that are closely related to additive models. With real-valued output, and \(d\)-dimensional input vector \(x \in \mathbb{R}^d\), such two-layer neural networks can be written as follows as an additive model in (10.1):

\[
f_m(w,x) = \sum_{j=1}^{m} u_j h(\theta_j^{\top} x + b_j), \tag{11.1}
\]

where \(x \in \mathbb{R}^d\), \(\theta_j \in \mathbb{R}^d\), \(b_j \in \mathbb{R}\), \(u_j \in \mathbb{R}\), and \(w = \{[u_j, \theta_j, b_j] : j = 1, \dots, m\}\). The function \(h(\cdot)\) is referred to as an activation function, and some popular choices include rectified linear unit (ReLU) \(h(z) = \max(0, z)\) and sigmoid \(h(z) = 1/(1 + e^{-z})\) as shown in Figure 11.1.

![](img/49407831b69246276f2b471882509fb2_233_0.png)

(a) ReLU

![](img/49407831b69246276f2b471882509fb2_233_1.png)

(b) sigmoid

**Figure 11.1** Neural network activation functions

In practice, the model parameters \(w\) are often trained using stochastic gradient descent (SGD). Since a two-layer neural network can be regarded as an additive model, we may apply the generalization analysis in Chapter 10 directly. Similar to kernel methods, it is known that two-layer neural networks are universal function approximators (see Section 11.2).

More generally, we may define a \(K\)-layer fully connected deep neural network with real-valued output as follows. Let \(m^{(0)} = d\) and \(m^{(K)} = 1\); we recursively define

\[
\begin{aligned}
x_j^{(0)} &= x_j \quad (j = 1, \dots, m^{(0)}),\\
x_j^{(k)} &= h\left(\sum_{j'=1}^{m^{(k-1)}} \theta_{j,j'}^{(k)} x_{j'}^{(k-1)} + b_j^{(k)}\right) \quad (j = 1, \dots, m^{(k)}), \quad k = 1,2,\dots,K-1,\\
f(x) &= x_1^{(K)} = \sum_{j=1}^{m^{(K-1)}} u_j x_j^{(K-1)},
\end{aligned}
\]

where the model parameters can be represented by \(w = \{[u_j, \theta_{j,j'}^{(k)}, b_j^{(k)}] : j,j',k\}\), with \(m^{(k)}\) being the number of hidden units at layer \(k\). Figure 11.2 illustrates a \(K = 4\) layer neural network with \(m^{(0)} = 3\), \(m^{(1)} = m^{(2)} = 5\), \(m^{(3)} = 4\), and \(m^{(4)} = 1\).

![](img/49407831b69246276f2b471882509fb2_233_2.png)

**Figure 11.2** Four-layer fully connected neural network

### 11.2 Function Approximation

It is known that neural networks are universal function approximators. In fact, it is known that a two-layer neural network (11.1) is universal if \(h(\cdot)\) is not a polynomial (Leshno et al., 1993).

**Theorem 11.1** (Leshno et al., 1993)  If \(h\) is a *nonpolynomial continuous function*, then the function class in (11.1) is dense in \(C^0(K)\) for all compact subsets \(K\) of \(\mathbb{R}^d\), where \(C^0(K)\) denotes the set of continuous functions on \(K\).

A more refined result was obtained in Barron (1993), which considered functions with a certain smoothness property in Fourier representation.

**Definition 11.2**  Consider a real-valued function \(f(x): \mathbb{R}^d \to \mathbb{R}\). Assume that \(f \in L_1(\mathbb{R}^d)\) has the following Fourier representation:

\[
f(x)=\int_{\mathbb{R}^d} e^{i\omega^T x}\,\tilde f(\omega)\,d\omega,
\]

where \(\tilde f(\omega)\) is the Fourier transform of \(f(x)\) that may be a complex function. Define

\[
C(f)=\int_{\mathbb{R}^d}\|\omega\|_2\,|\tilde f(\omega)|\,d\omega.
\]

**Theorem 11.3** (Barron, 1993)  Let \(h(z)\) be a *bounded measurable function* on the real line for which \(\lim_{z\to-\infty}h(z)=0\) and \(\lim_{z\to\infty}h(z)=1\). Consider \(B_r=\{x\in\mathbb{R}^d:\|x\|_2\le r\}\), and let \(f\) be a real-valued function defined on \(B_r\) such that \(C(f)<\infty\). Then there exists a neural network (11.1) such that

\[
\int (f(x)-f(0)-f_m(w,x))^2\,d\mu(x)\le \frac{(2rC(f))^2}{m},
\]

where \(\mu\) is an arbitrary probability measure on \(B_r\).

**Proof**  A key property of the complexity measure \(C(f)\), shown in Barron (1993), is that \(f(x)-f(0)\) belongs to the convex closure of functions

\[
\{u h(\theta^T x+b): |u|\le 2rC(f)\},
\]

where the closure is taken with respect to \(\mu\). This result, together with Theorem 10.7, implies Theorem 11.3.

Note that we can take any \(b\) so that \(h(b)\ne 0\), and

\[
f(0)=\bigl(f(0)/h(b)\bigr)h(0^T x+b).
\]

It follows that if \(f(x)-f(0)\) can be represented by a two-layer neural network (11.1) with \(m\) neurons, then \(f(x)\) can be represented by a two-layer neural network (11.1) with \(m+1\) neurons. Therefore Theorem 11.3 implies that any \(f\) with finite \(C(f)\) can be approximated by a two-layer neural network. It can be shown that the function class \(\{f:C(f)<\infty\}\) is dense on any compact set of \(\mathbb{R}^d\). This implies the desired universal approximation result.
