
### Example 9.23

For binary classification problem with $y \in \{\pm1\}$, we may consider a classifier induced by a real-valued function $f(x)$ such that we predict $y=1$ if $f(x)\geq 0$ and $y=-1$ otherwise. If $f(x)$ is taken from an RKHS, then we have the following margin bound. With probability $1-\delta$, for all $f\in\mathcal H$ with $\|f\|_{\mathcal H}\leq A$,

$$\mathbb E_D\mathbb 1(f(X)Y\leq 0)\leq \frac{1}{n}\sum_{i=1}^{n}\mathbb 1(f(X_i)Y_i\leq\gamma)+\frac{2A}{\gamma}\sqrt{\frac{\mathbb E_D k(X,X)}{n}}+\sqrt{\frac{\ln(1/\delta)}{2n}}.$$

It says that if we can find a classifier with a small margin error, then we can achieve a good test classification error. Unlike the VC analysis in Chapter 4, the bound does not depend on the dimensionality of the feature vector $\psi(x)$, but rather on the classifier’s RKHS norm $A$, and margin condition.

The bound can be obtained as a direct consequence of Corollary 9.22, using a loss function $L(p,y)=\min(1,\max(0,1-py/\gamma))$, which is $\gamma^{-1}$ Lipschitz. In this case, $\mathbb 1(f(x)y\leq 0)\leq L(f(x),y)\leq\mathbb 1(f(x)y\leq\gamma)$.

We note that the Rademacher complexity analysis only leads to a convergence rate of $O(1/\sqrt n)$. However, similar to the VC analysis, it is possible to obtain a margin bound of $O(\ln n/n)$ when the margin error is zero. This requires a different analysis stated in Theorem 4.21, together with the empirical $L_\infty$ covering number of Theorem 5.20. We leave it to Exercise 9.5.

### Example 9.24

For SVM loss, $\gamma=1$. With hard regularization, we can take $M=(1+AB)$, where we assume that $k(x,x)\leq B^2$. Consider $\hat f$ that solves (9.9) up to an accuracy of $\epsilon' > 0$. From Corollary 9.22, we obtain with probability at least $1-\delta$,

$$\mathbb E_D L(\hat f(X),Y)\leq \inf_{\|f\|_{\mathcal H}\leq A}\mathbb E_D L(f(X),Y)+\epsilon'+\frac{2AB}{\sqrt n}+(1+AB)\sqrt{\frac{2\ln(2/\delta)}{n}}.$$

Given an arbitrary competitor $f\in\mathcal H$, the optimal value of $A$ would be $A=\|f\|_{\mathcal H}$. However, this requires us to know the value of $\|f\|_{\mathcal H}$, which is not feasible. In practice, it is more convenient to use the soft-regularized version (9.10), where the choice of $\lambda$ is less sensitive than $A$, and it can be set independently of $\|f\|_{\mathcal H}$. The following result is a direct consequence of Corollary 9.21 and Theorem 6.14.

### Corollary 9.25
If $L(p,y)$ is $\gamma$-Lipschitz with respect to $p$, then we have the following expected oracle inequality for (9.10):

$$\mathbb E_{S_n}L(\hat f,\mathcal D)\leq\inf_{f\in\mathcal H}\left[L(f,\mathcal D)+\frac{\lambda}{2}\|f\|_{\mathcal H}^{2}\right]+\frac{2\gamma^{2}\mathbb E_D k(X,X)}{\lambda n}.$$

Observe that in Corollary 9.25, the expected oracle inequality does not rely on the boundedness of $L(\cdot,\cdot)$. One may also obtain high probability inequalities by employing the technique of Chapter 8 and a union bound over a properly defined sequence of nested function classes.

### Corollary 9.26
Assume that L(p, y) ≥ 0 is γ Lipschitz in p, and sup_y L(0, y) ≤ M₀. Let B² = sup_x k(x, x), then with probability at least 1 − δ, for all f ∈ H,

| E_D L(f(X), Y) − (1/n) ∑ᵢ₌₁ⁿ L(f(Xᵢ), Yᵢ) | ≤ (1/√n)(4M₀ + 4γB‖f‖_H) + (3M₀ + 2γB‖f‖_H) √[ ln(2(2 + log₂(1 + γB‖f‖_H/M₀))²/δ) / (2n) ].

Proof Let Aθ = 2^{θ} A₀ for A₀ > 0 to be determined later, with q(θ) = 1/(θ + 1)² for θ = 1, 2, …. Consider Bθ = {f ∈ H: ‖f‖_H ≤ Aθ}. We know that L(p, y) ≤ L(0, y) + γ|p| ≤ M₀ + γAθB. Let Mθ = M₀ + γAθB. Then Corollary 9.22 implies that with probability at least 1 − q(θ)δ, for all f ∈ H with ‖f‖_H ≤ Aθ,

| E_D L(f(X), Y) − (1/n) ∑ᵢ₌₁ⁿ L(f(Xᵢ), Yᵢ) | ≤ 2γAθB/√n + Mθ √[ ln(2/(q(θ)δ)) / (2n) ].

Taking the union bound, we have with probability 1 − δ, for all f ∈ H and all θ ≥ 1 such that ‖f‖_H ≤ Aθ,

| E_D L(f(X), Y) − (1/n) ∑ᵢ₌₁ⁿ L(f(Xᵢ), Yᵢ) | ≤ 2γAθB/√n + Mθ √[ ln(2/(q(θ)δ)) / (2n) ].

We let θ(f) ≥ 1 be the smallest index such that ‖f‖_H ≤ Aθ. Then Aθ(f) ≤ 2(A₀ + ‖f‖_H), and thus θ(f) ≤ log₂(2 + 2‖f‖_H/A₀). We can take A₀ = M₀/(γB). This implies the desired bound. □

We can also obtain an oracle inequality as follows.

### Corollary 9.27
Assume that L(p, y) ≥ 0 is γ-Lipschitz in p, sup_y L(0, y) ∈ [0, M₀], and sup_x k(X, X) ≤ B². Then with probability 1 − δ, we have the following oracle inequality for (9.10):

L(f̂, D) ≤ inf_{f∈H} [ L(f, D) + (λ/2)‖f‖²_H + ε_B‖f‖_H ] + 2ε_M + ε_B²/(2λ),

where θ₀ = 1 + log₂(1 + γB √(2/(λM₀))), and

ε_M = 4M₀/√n + 3M₀ √[ ln(2(1 + θ₀)²/δ) / (2n) ],

ε_B = 4γB/√n + 2γB √[ ln(2(1 + θ₀)²/δ) / (2n) ].

Proof We note that ‖f‖²_H ≤ 2M₀/λ. Therefore Corollary 9.26 implies that with probability at least 1 − δ, for all f ∈ H,

| E_D L(f(X), Y) − (1/n) ∑ᵢ₌₁ⁿ L(f(Xᵢ), Yᵢ) | ≤ ε_M + ε_B‖f‖_H.  (9.13)

This implies that

L(\hat{f}, \mathcal{D}) \le \frac{1}{n} \sum_{i=1}^{n} L(\hat{f}(X_i), Y_i) + \frac{\lambda}{2} \|\hat{f}\|_{\mathcal{H}}^{2} \underbrace{-\frac{\lambda}{2} \|\hat{f}\|_{\mathcal{H}}^{2} + \epsilon_M + \epsilon_B \|\hat{f}\|_{\mathcal{H}}}_{V}
\le \frac{1}{n} \sum_{i=1}^{n} L(\hat{f}(X_i), Y_i) + \frac{\lambda}{2} \|\hat{f}\|_{\mathcal{H}}^{2} + \epsilon_M + \frac{\epsilon_B^{2}}{2\lambda}
\le \frac{1}{n} \sum_{i=1}^{n} L(f(X_i), Y_i) + \frac{\lambda}{2} \|f\|_{\mathcal{H}}^{2} + \epsilon_M + \frac{\epsilon_B^{2}}{2\lambda}
\le L(f, \mathcal{D}) + \frac{\lambda}{2} \|f\|_{\mathcal{H}}^{2} + \epsilon_B \|f\|_{\mathcal{H}} + 2\epsilon_M + \frac{\epsilon_B^{2}}{2\lambda}.

The first inequality used (9.13). The second inequality can be obtained by maximizing V over \|\hat{f}\|_{\mathcal{H}}. The third inequality used the fact that \hat{f} is the solution of (9.10). The last inequality used (9.13) again.

### Example 9.28
Consider the soft-regularized SVM in (9.10). We can let γ = 1 and M₀ = 1/B. It follows that if we take λ = O(1/√n), then we get an oracle inequality from Corollary 9.27 with a convergence rate of O(√(ln ln n / n)).

## 9.4 Vector-Valued Functions

We now consider vector-valued functions using kernels. In this case, we have f(x): 𝒳 → ℝ^q for some q > 1. Let f(x) = [f₁(x),...,f_q(x)]. If we consider the feature space representation, then there are two possibilities. One is to treat these functions as sharing the same feature vector, but with different w:

f_ℓ(x) = ⟨w_ℓ, ψ(x)⟩      (ℓ = 1,...,q).

Another view is to consider the same w, but with different features for different dimension:

f_ℓ(x) = ⟨w, ψ(x,ℓ)⟩. (9.14)

The second view is more general because we may write the first view as follows. We concatenate the feature representation by letting w = [w₁,...,w_q] and ψ(x,ℓ) = [0,...,0,ψ(x),0,...,0] with only the ℓth concatenating component to be ψ(x), and the other components as zeros. With this representation, ⟨w, ψ(x,ℓ)⟩ = ⟨w_ℓ, ψ(x)⟩. In the following discussions, we focus on (9.14).

Similar to (9.2), we have the following formulation in feature representation:

ĥw = arg min_{w∈ℋ} [ 1/n ∑_{i=1}^{n} L(⟨w, ψ(X_i,·)⟩, Y_i) + λ/2 ‖w‖² ], (9.15)

### Theorem 9.29

Consider q-dimensional vector-valued function f(x). Let \hat f(x)= \langle \hat w, \psi(x,\cdot)\rangle with \hat w being the solution of (9.15). Then

$$\hat f(x)=\sum_{i=1}^{n}\mathbf{k}(x,X_i)\hat\alpha_i,$$

with

$$\langle \hat w, \hat w\rangle = \sum_{i=1}^{n}\sum_{j=1}^{n}\hat\alpha_i^{\top}\mathbf{k}(X_i,X_j)\hat\alpha_j,$$

where each \hat\alpha_i \in \mathbb{R}^q, and

$$\mathbf{k}(x,x')=\begin{bmatrix}k_{1,1}(x,x') & \cdots & k_{1,q}(x,x')\\ \vdots & & \vdots\\ k_{q,1}(x,x') & \cdots & k_{q,q}(x,x')\end{bmatrix},$$

and

$$k_{i,j}(x,x')=\langle\psi(x,i),\psi(x',j)\rangle \qquad (i,j=1,\dots,q).$$

Therefore the solution of (9.15) is equivalent to

$$\hat\alpha=\arg\min_{\alpha\in\mathbb{R}^{q\times n}}\left[\frac{1}{n}\sum_{i=1}^{n}L\left(\sum_{j=1}^{n}\mathbf{k}(X_i,X_j)\alpha_j,Y_i\right) +\frac{\lambda}{2}\sum_{i=1}^{n}\sum_{j=1}^{n}\alpha_i^{\top}\mathbf{k}(X_i,X_j)\alpha_j\right].\tag{9.16}$$

Proof The proof is similar to that of Theorem 9.2, and we define the objective in (9.15) as Q1(w). The objective in (9.16) is denoted by Q2(α). The solution of (9.15) satisfies the following first-order optimality condition:
