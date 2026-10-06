# 2.5 Directional Derivative

So, we conclude for some $\alpha \ge 0$

> $$\max_{t \in[0,1]} (	ilde{y}(t) + \lambda h(t)) \le \lambda \alpha \text{ for all } \lambda > 0,$

and with the equality (2.7), we get

> $$\lim_{\lambda\to0_+} \tilde{y}(t_{\lambda}) + \lambda h(t_{\lambda}) = \lim_{\lambda\to0_+} \tilde{y}(t).$

Then there is a sequence $(\lambda_k)_{k\in\mathbb{N}}$ of positive real numbers converging to 0 with $\lim_{k\to\infty} t_{\lambda_k} = \hat{t} \in [0,1]$, and it is evident that $\hat{t} \in M(Y)$. Here, we conclude

> $$\psi'(\hat{t})(h) = \lim_{k\to\infty} \frac{1}{\lambda_k} (\max (\tilde{y}(t) + \lambda_k h(t)) - \tilde{y}(t))$
\= \tilde{y}'(t_{\lambda_k}) + \lambda_k h'(t_{\lambda_k}) \ge \tilde{y}'(t_{\lambda_k})$$
\le \lim_{k\to\infty} \frac{1}{\lambda_k} (\tilde{y}'(t_{\lambda_k}) + \lambda_k h'(t_{\lambda_k}) - \tilde{y}'(t_{\lambda_k}))$
\= \lim_{k\to\infty} h'(t_{\lambda_k})$$
\= h'(\hat{t})$$
\le \max_{t\inM(Y)} h(t). \quad (2.8)$

The inequalities (2.6) and (2.8) lead to the assertion.

Next, we turn our attention to the Hilbert space of symmetric (n, n) matrices.

**Proposition 2.13 ([63, 275]) for the assertion in part (a) and [73], Proposition-4.1, (d)] for part (b)** Let $Y := S^n$ (with $n \in \mathbb{N}$) denote the real Hilbert space of symmetric metric (n, n) matrices.

(a) The Löwner cone

> $C := S^n_+ = \{A \in S^n \| \text{ positive semidefinite}\}$

be chosen. The $-S^n_-$ representing functional $\psi : S^n \to \mathbb{R}$ with

> $$\Psi(A) := \max_{\|x\_2=1} x^T Ax = (\text{maximal eigenvalue of } A) \text{ for all } A \in S^n$

($|\cdot\|_2$ denotes the Euclidean norm in $\mathbb{R}^n$) has the directional derivative at arbitrary $\bar{A} \in S^n$ given by

> $$\psi'(\bar{A})(H) = \max_{x\inX(\bar{A})} x^T Hx \text{ for all } H \in S^n$