
## 3 Low-Rank Matrix Estimation

### 3.1 An AMP Algorithm for Estimating a Symmetric Rank-One Matrix

In this section, we will motivate and analyse an AMP algorithm for reconstructing a symmetric rank-one matrix based on an observation

$$A \equiv A(n) = \frac{\lambda}{n} v v^\top + W \in \mathbb{R}^{n \times n}$$ (3.1)

for some \( n \in \mathbb{N} \), where \( \lambda > 0 \) is a deterministic scalar, \( v \equiv v(n) \in \mathbb{R}^n \) is the signal (or “spike”) that we wish to estimate, and \( W \equiv W(n) \sim \text{GOE}(n) \) is a noise matrix. The asymptotic setting of interest to us here is one where \( \|v\|_n \equiv n^{-1/2}\|v\| \) converges to 1 as \( n \to \infty \); see (3.4) below.

A natural estimator of \( v \) is a principal eigenvector \( \hat{\varphi} \equiv \varphi^1(A) \in \mathbb{R}^n \) (with \( \|\hat{\varphi}\|_n = 1 \)) corresponding to the largest eigenvalue \( \lambda_1(A) \) of the observation matrix \( A \). A cornerstone of the spectral theory of such “deformed” GOE matrices is the so-called “BBP” phase transition. This was first established in the seminal paper of Baik et al. (2005) and later explored in greater generality by Baik and Silverstein (2006), Féral and Péché (2007), Capitaine et al. (2009) and Benaych-Georges and Nadakuditi (2011), among many others. See Johnstone and Paul (2018) for an accessible summary of this line of work, which reveals that in the limiting regime where $\|v\|_n$ converges to 1, the eigenstructure of $A \equiv A(n)$ for large $n$ exhibits two different types of qualitative behaviour depending on whether $\lambda \le 1$ or $\lambda > 1$. In particular, when $n \to \infty$, it follows from the concentration results in Knowles and Yin (2013, Theorems 2.7 and 6.3) that

$$
\lambda_1(A) \xrightarrow{c} \begin{cases} \lambda + \lambda^{-1} > 2 & \text{if } \lambda > 1 \\ 2 & \text{if } \lambda \in (0, 1], \end{cases}
\\
\frac{|\langle \hat{\varphi}, v \rangle|}{\|\hat{\varphi}\| \|v\|} \xrightarrow{c} \begin{cases} \sqrt{1 - \lambda^{-2}} & \text{if } \lambda > 1 \\ 0 & \text{if } \lambda \in (0, 1]; \end{cases}
$$
(3.2)

see also Peng (2012, Theorem 3.1) for the former and Corollary 3.4 below for the latter.

In the "supercritical" phase when $\lambda > 1$, the effect of the spike $v$ can be seen in the limiting expressions above: with high probability, $\hat{\varphi}$ is at least partially aligned with $v$ (although it does not estimate $v$ consistently) and $\lambda_1(A)$ is an outlier that is separated from the "bulk" of the spectrum of $A$. Indeed, the remaining eigenvalues of $A$ are asymptotically distributed according to the Wigner semicircle law on $[-2, 2]$, and it can be shown that the second-largest eigenvalue $\lambda_2(A)$ of $A \equiv A(n)$ satisfies $\lambda_2(A) \xrightarrow{c} 2$ as $n \to \infty$, so the limiting spectral gap $\lambda_1(A) - \lambda_2(A)$ is strictly positive.

On the other hand, in the "subcritical" phase when $\lambda \le 1$, the noise matrix $W$ obscures the signal in (3.1) to such an extent that $\hat{\varphi}$ is asymptotically uninformative as an estimator of $v$, as evidenced by the asymptotic orthogonality in (3.2), and $\lambda_1(A)$ remains attached to the bulk of the eigenvalues of $A$. In this low signal-to-noise regime, the limits for $\lambda_1(A)$ and $\hat{\varphi}$ in (3.2) are the same as for the leading eigenvalue and eigenvector of $W$ respectively.

A further limitation of the classical spectral estimator $\hat{\varphi}$ is that it is unable to exploit any additional information about the structure of $v$ that may be relevant for inference. For example, in some matrix estimation problems such as hidden clique detection and non-negative or sparse principal component analysis, there are natural constraints that force $v$ to be non-negative or sparse, or to lie in some finite set such as $\{0,1\}^n$ (Alon *et al.*, 1998; Deshpande and Montanari, 2015; Montanari and Richard, 2016; Vu and Lei, 2013; Zou *et al.*, 2006). A Bayesian approach to modelling a structured signal $v$ is to assume that its components are drawn from some suitable prior distribution that is fully or partially known. However, for general priors, a practical issue is the lack of efficient (i.e., polynomial-time) algorithms for computing or accurately approximating the Bayes estimator of $v$ with respect to quadratic loss, namely the posterior mean E($v$|$A$).

We will now present a generic (and computationally feasible) AMP procedure (3.3) for estimating $v$ (cf. Deshpande and Montanari, 2014; Deshpande *et al.*, 2016; Montanari and Venkataramanan, 2021), and obtain an exact characterisation of its asymptotic performance in terms of a state evolution recursion (Theorem 3.1 and Corollary 3.2). Guided by these theoretical guarantees, we will explain in Sections 3.2 and 3.3 how the inputs to the algorithm can be specialised further to take advantage of different types of prior information, and thereby produce estimators that outperform \(\hat{\varphi}\) in terms of asymptotic mean squared error.

Let \((g_k)_{k=0}^\infty\) be a sequence of Lipschitz functions on R with corresponding weak derivatives \(g'_k\). Given \(\hat{v}^{-1} \equiv \hat{v}^{-1}(n) := 0 \in \mathbb{R}^n\) and an initialiser \(v^0 \equiv v^0(n) \in \mathbb{R}^n\) for some \(n \in \mathbb{N}\), we recursively define \(\hat{v}^k \equiv \hat{v}^k(n) \in \mathbb{R}^n\), \(b_k \equiv b_k(n) \in \mathbb{R}\) and \(\hat{v}^{k+1} \equiv \hat{v}^{k+1}(n) \in \mathbb{R}^n\) by

\(\hat{v}^k := g_k(v^k), \quad b_k := \langle g'_k(v^k) \rangle_n = \frac{1}{n} \sum_{i=1}^n g'_k(v_i^k), \quad v^{k+1} := A\hat{v}^k - b_k\hat{v}^{k-1}\)

for \(k \in \mathbb{N}_0\). This has a very similar form to the abstract recursion (2.1) that we studied in Section 2.1, the main difference being that (3.3) is a valid algorithm with the data matrix \(A \equiv A(n)\) in place of the unobserved noise matrix \(W \equiv W(n)\).

As mentioned in the Introduction, we can view (3.3) as a generalised power iteration, in which the additional Onsager correction term \(-b_k\hat{v}^{k-1}\) is crucial for ensuring that the iterates $v^k$ have the desired asymptotic distributional properties. In fact, we will see in Section 3.3 that for a specific choice of linear functions $g_k$ given by (3.27), the corresponding recursion (3.3) is asymptotically equivalent to a standard power iteration that converges to the principal eigenvector \(\hat{\phi}\) of \(A\).

To set up our asymptotic framework, consider a sequence of recursions (3.3) indexed by \(n \in \mathbb{N}\), for which the following conditions hold:

- (M0) The noise matrix \(W \equiv W(n) \sim \text{GOE}(n)\) in (3.1) is independent of \((\delta^0, v) \equiv (\delta^0(n), v(n))\) for each \(n\).

- (M1) There exist \(\mu_0, \sigma_0 \in \mathbb{R}\) and independent random variables \(U, V\) with \(\mathbb{E}(U^2) = \mathbb{E}(V^2) = 1\), such that

\[
\sup_{v \in \text{PL}_2(2,1)} \left| \frac{1}{n} \sum_{i=1}^n v \langle v_i^0, v_i \rangle - \mathbb{E}\{v \langle \mu_0 V + \sigma_0 U, V \rangle \} \right| \xrightarrow{\mathfrak{L}} 0.
\]

In other words, writing \(\bar{\mu}^0\) for the distribution of \(\langle \mu_0 V + \sigma_0 U, V \rangle\), and \(\nu_n(v^0, v)\) for the joint empirical distribution of the components of \(v^0, v \in \mathbb{R}^n\) for \(n \in \mathbb{N}\), we have

\[
\hat{d}_2(\nu_n(v^0, v), \bar{\mu}^0) \xrightarrow{\mathfrak{L}} 0 \quad \text{or equivalently} \quad d_2(\nu_n(v^0, v), \bar{\mu}^0) \xrightarrow{\mathfrak{L}} 0.
\]

- (M2) For each \(k \in \mathbb{N}\), the function \(g_k^e: \mathbb{R} \to \mathbb{R}\) is continuous Lebesgue almost everywhere, i.e., the set of discontinuities of \(g_k^e\) has Lebesgue measure 0.

Henceforth, we will write \(\pi\) for the distribution of \(V\), which can be viewed as the “limiting prior distribution” of the components of the signal \(v \equiv v(n)\). Note that while \(v\) is only identifiable up to sign in the original spiked model (3.1), knowledge of \(\pi\) may help us to distinguish \(v\) from \(-v\) in the limit \(n \to \infty\), for example if \(\pi\) has non-zero mean. By considering the \(\text{PL}_2(2)\) functions \(\langle x, y \rangle \mapsto y^2\), \(\langle x, y \rangle \mapsto xy\) and \(\langle x, y \rangle \mapsto x^2\), we deduce from (M1) that

\[
\|v\|_n^2 = \frac{1}{n} \sum_{i=1}^n v_i^2 \xrightarrow{\mathfrak{L}} \mathbb{E}(V^2) = 1,\quad (3.4)
\]

\(\begin{aligned} \lambda \langle v^0, v \rangle_n \xrightarrow{\mathfrak{L}} \lambda \mathbb{E}(v g_0(\mu_0 V + \sigma_0 U)) =: \mu_1 \quad \text{and} \\ \|v^0\|_n^2 \xrightarrow{\mathfrak{L}} \mathbb{E}(g_0(\mu_0 V + \sigma_0 U)^2) =: \sigma_1^2. \end{aligned}\quad (3.5)\)
