# 3
Low-Rank Matrix Estimation

# 3.1 An AMP Algorithm for Estimating a Symmetric Rank-One Matrix

In this section, we will motivate and analyse an AMP algorithm for reconstructing a symmetric rank-one matrix based on an observation

```
$$A \equiv A(n) = \frac{\lambda}{n} v v^\top + W \in \mathbb{R}^{n \times n}$$ (3.1)
```

for some \( n \in \mathbb{N} \), where \( \lambda > 0 \) is a deterministic scalar, \( v \equiv v(n) \in \mathbb{R}^n \) is the signal (or “spike”) that we wish to estimate, and \( W \equiv W(n) \sim \text{GOE}(n) \) is a noise matrix. The asymptotic setting of interest to us here is one where \( \|v\|_n \equiv n^{-1/2}\|v\| \) converges to 1 as \( n \to \infty \); see (3.4) below.

A natural estimator of \( v \) is a principal eigenvector \( \hat{\varphi} \equiv \varphi^1(A) \in \mathbb{R}^n \) (with \( \|\hat{\varphi}\|_n = 1 \)) corresponding to the largest eigenvalue \( \lambda_1(A) \) of the observation matrix \( A \). A cornerstone of the spectral theory of such “deformed” GOE matrices is the so-called “BBP” phase transition. This was first established in the seminal paper of Baik et al. (2005) and later explored in greater generality by Baik and Silverstein (2006), Féral and Péché (2007), Capitaine et al. (2009) and Benaych-Georges and Nadakuditi (2011), among many others. See Johnstone and Paul (2018)