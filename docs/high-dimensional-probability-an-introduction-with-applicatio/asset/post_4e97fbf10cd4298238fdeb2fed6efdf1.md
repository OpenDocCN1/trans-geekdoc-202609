
Substitute this into (7.11) to get

$$
\sum_{i=1}^{n} \frac{1}{\sqrt{u}}\,\mathbb{E}\,X_i\,\frac{\partial f}{\partial x_i}(Z(u)) = \sum_{i,j=1}^{n} \Sigma_{ij}^{X}\,\mathbb{E}\,\frac{\partial^2 f}{\partial x_i\,\partial x_j}(Z(u)).
$$

Taking expectation of both sides with respect to \(Y\), we lift the conditioning on \(Y\).

We can similarly evaluate the other sum in (7.10), the one containing the terms \(Y_i\). Combining the two sums we complete the proof.

## 7.2.2 Proof of Slepian inequality

We are ready to establish a preliminary, functional form of Slepian inequality.

**Lemma 7.2.6 (Slepian inequality, functional form).** *Consider two mean-zero Gaussian random vectors \(X\) and \(Y\) in \(\mathbb{R}^n\). Assume that for all \(i,j=1,\ldots,n\), we have*

$$
\mathbb{E}X_i^2 = \mathbb{E}Y_i^2 \quad\text{and}\quad \mathbb{E}(X_i-X_j)^2 \leq \mathbb{E}(Y_i-Y_j)^2.
$$

*Consider a twice-differentiable function \(f:\mathbb{R}^n\to\mathbb{R}\) such that*

$$
\frac{\partial^2 f}{\partial x_i\,\partial x_j} \geq 0 \quad\text{for all } i\ne j.
$$

*Then*

$$
\mathbb{E}f(X) \geq \mathbb{E}f(Y),
$$

*assuming both expectations exist and are finite.*

*Proof.* The assumptions imply that the entries of the covariance matrices \(\Sigma^X\) and \(\Sigma^Y\) of \(X\) and \(Y\) satisfy

$$
\Sigma_{ii}^{X}=\Sigma_{ii}^{Y} \quad\text{and}\quad \Sigma_{ij}^{X}\geq\Sigma_{ij}^{Y}
$$

for all \(i,j=1,\ldots,n\). We can assume that \(X\) and \(Y\) are independent. (Why?) Applying Lemma 7.2.5 and using our assumptions, we conclude that

$$
\frac{d}{du}\,\mathbb{E}f(Z(u)) \geq 0,
$$

so \(\mathbb{E}f(Z(u))\) increases in \(u\). Then \(\mathbb{E}f(Z(1))=\mathbb{E}f(X)\) is at least as large as \(\mathbb{E}f(Z(0))=\mathbb{E}f(Y)\). This completes the proof.

Now we are ready to prove Slepian inequality, Theorem 7.2.2. Let us state and prove it in the equivalent form for Gaussian random vectors.

**Theorem 7.2.7 (Slepian inequality).** *Let \(X\) and \(Y\) be Gaussian random vectors as in Lemma 7.2.6. Then for every \(\tau\geq 0\) we have*

$$
\mathbb{P}\{\max_{i\leq n}X_i\geq\tau\}\leq\mathbb{P}\{\max_{i\leq n}Y_i\geq\tau\}.
$$

Consequently,

$$
\mathbb{E}\max_{i\le n} X_i \le \mathbb{E}\max_{i\le n} Y_i.
$$

*Proof.* Let \(h:\mathbb{R}\to[0,1]\) be a twice-differentiable, non-increasing approximation to the indicator function of the interval \((-\infty,\tau)\):

$$
h(x)\approx \mathbf{1}_{(-\infty,\tau)},
$$

like in Figure 7.2. Define the function \(f:\mathbb{R}^n\to\mathbb{R}\) by

![](img/b122213aed28c1888de83a894123323e_208_0.png)

**Figure 7.2** The function \(h(x)\) is a smooth, non-increasing approximation to the indicator function \(\mathbf{1}_{(-\infty,\tau)}\).

$$
f(x)=h(x_1)\cdots h(x_n).
$$

Then \(f(x)\) is an approximation to the indicator function

$$
f(x)\approx \mathbf{1}_{\{\max_i x_i<\tau\}}.
$$

We are looking to apply the functional form of Slepian inequality, Lemma 7.2.6, for \(f(x)\). To check the assumptions of this result, note that for \(i\ne j\) we have

$$
\frac{\partial^2 f}{\partial x_i\,\partial x_j}=h'(x_i)h'(x_j)\cdot\prod_{k\notin\{i,j\}}h(x_k).
$$

The first two factors are non-positive and the others are nonnegative by the assumption. Thus the second derivative is nonnegative, as required.

It follows that

$$
\mathbb{E}f(X)\ge\mathbb{E}f(Y).
$$

By approximation, this implies

$$
\mathbb{P}\left\{\max_{i\le n}X_i<\tau\right\}\ge\mathbb{P}\left\{\max_{i\le n}Y_i<\tau\right\}.
$$

This proves the first part of the conclusion. The second part follows by using the integrated tail formula in Exercise 1.15(b) (check!)

## 7.2.3 Sudakov–Fernique and Gordon inequalities

Slepian inequality has two assumptions on the processes \((X_t)\) and \((Y_t)\) in (7.3): the equality of variances and the dominance of increments. We now remove the assumption on the equality of variances, and are still able to obtain (7.5).

**Theorem 7.2.8 (Sudakov-Fernique inequality).** Let \((X_t)_{t\in T}\) and \((Y_t)_{t\in T}\) be two *mean-zero Gaussian processes*. Assume that for all \(t,s\in T\), we have

$$
\mathbb{E}(X_t-X_s)^2 \leq \mathbb{E}(Y_t-Y_s)^2.
$$

*Then*

$$
\mathbb{E}\sup_{t\in T}X_t \leq \mathbb{E}\sup_{t\in T}Y_t.
$$

*Proof.* It is enough to prove this theorem for Gaussian random vectors \(X\) and \(Y\) in \(\mathbb{R}^n\), just like we did for Slepian inequality in Theorem 7.2.7. We again deduce the result from Gaussian Interpolation Lemma 7.2.5. But this time, instead of choosing \(f(x)\) that approximates the indicator function of \(\{\max_i x_i<\tau\}\), we want \(f(x)\) to approximate \(\max_i x_i\).

To this end, let \(\beta>0\) be a parameter and define the function⁴

$$
f(x):=\frac{1}{\beta}\log\sum_{i=1}^{n}e^{\beta x_i}.
$$

A quick check shows that

$$
f(x)\to\max_{i\leq n}x_i\quad\text{as }\beta\to\infty.
$$

(Do this!) Substituting \(f(x)\) into the Gaussian interpolation formula (7.9) and simplifying the expression shows that

$$
\frac{d}{du}\,\mathbb{E}\,f(Z(u))\leq 0\quad\text{for all }u\in[0,1].
$$

(Work through this step carefully in Exercise 7.7!) Then we can finish the proof just like in Slepian inequality.

Some applications call for *min-max* bounds on random processes. For example, by (4.14), the smallest singular value of an \(m\times n\) Gaussian matrix \(A\) with all \(N(0,1)\) i.i.d. entries can be written as

$$
s_n(A)=\min_{u\in S^{n-1}}\|Au\|_2=\min_{u\in S^{n-1}}\max_{v\in S^{m-1}}X_{uv},
$$

where \(X_{uv}=\langle Au,v\rangle\) are normal random variables. A handy tool for this kind of problems is Gordon inequality, which extends Slepian and Sudakov-Fernique to the min-max setting:

**Theorem 7.2.9 (Gordon inequality).** Let \((X_{ut})_{u\in U,t\in T}\) and \((Y_{ut})_{u\in U,t\in T}\) be two *mean-zero Gaussian processes* indexed by pairs of points \((u,t)\) in a product set \(U\times T\). Assume that

$$
\mathbb{E}(X_{ut}-X_{vs})^2\leq\mathbb{E}(Y_{ut}-Y_{vs})^2\quad\text{for all }u,v,t,s;
$$

$$
\mathbb{E}(X_{ut}-X_{vs})^2\geq\mathbb{E}(Y_{ut}-Y_{vs})^2\quad\text{for all }u\neq v\text{ and all }t,s.
$$

⁴ The motivation for considering this form of \(f(x)\) comes from statistical mechanics, where the right side of (7.12) can be interpreted as a *log-partition function* and \(\beta\) as the *inverse temperature*.

where \(g\sim N(0,I_n)\) and \(h\sim N(0,I_m)\) are independent Gaussian vectors. The increments of this process are

$$
\begin{aligned}
\mathbb{E}(Y_{uv}-Y_{wz})^2
&=\mathbb{E}\left(\langle g,u-w\rangle+\langle h,v-z\rangle\right)^2\\
&=\mathbb{E}\langle g,u-w\rangle^2+\mathbb{E}\langle h,v-z\rangle^2\quad\text{(by independence, mean 0)}\\
&=\|u-w\|_2^2+\|v-z\|_2^2\quad\text{(since $g,h$ are standard normal).}
\end{aligned}
$$

Comparing the increments of the two processes, we see that

$$
\mathbb{E}(X_{uv}-X_{wz})^2\leq\mathbb{E}(Y_{uv}-Y_{wz})^2\quad\text{for all }(u,v),(w,z)\in T,
$$

as required in Sudakov-Fernique inequality. Applying Theorem 7.2.8, we obtain

$$
\begin{aligned}
\mathbb{E}\|A\|&=\mathbb{E}\sup_{(u,v)\in T}X_{uv}\leq\mathbb{E}\sup_{(u,v)\in T}Y_{uv}\\
&=\mathbb{E}\sup_{u\in S^{n-1}}\langle g,u\rangle+\mathbb{E}\sup_{v\in S^{m-1}}\langle h,v\rangle\\
&=\mathbb{E}\|g\|_2+\mathbb{E}\|h\|_2\\
&\leq\left(\mathbb{E}\|g\|_2^2\right)^{1/2}+\left(\mathbb{E}\|h\|_2^2\right)^{1/2}\quad\text{(recall Exercise 1.11)}\\
&=\sqrt n+\sqrt m\quad\text{(see Proposition 3.2.1(b)).}
\end{aligned}
$$

Theorem 7.3.1 only gives an expectation bound, but we can boost it to a high-probability bound using the concentration tools from Section 5.2:

**Corollary 7.3.2 (Norms of Gaussian random matrices: tails).**

*Let \(A\) be an \(m\times n\) matrix with independent \(N(0,1)\) entries. Then for every \(t\geq 0\), we have*

$$
\mathbb{P}\{\|A\|\geq\sqrt m+\sqrt n+t\}\leq 2\exp(-ct^2).
$$

**Proof.** Let's combine the expectation bound (Theorem 7.3.1) with Gaussian concentration (Theorem 5.2.3). Think of \(A\) as a long random vector in \(\mathbb{R}^{m\times n}\) by concatenating the rows. This makes \(A\) a standard normal random vector: \(A\sim N(0,I_{nm})\). Consider the function

$$
f(A):=\|A\|
$$

that maps the vectorized matrix to the matrix's operator norm. Since the operator norm is bounded by Frobenius norm, and the Frobenius norm is just the Euclidean norm on \(\mathbb{R}^{m\times n}\), \(f\) is a Lipschitz function on \(\mathbb{R}^{m\times n}\) with Lipschitz norm bounded by 1. (Why?) Then Theorem 5.2.3 yields

$$
\mathbb{P}\{\|A\|\geq\mathbb{E}\|A\|+t\}\leq 2\exp(-ct^2).
$$

The bound on \(\mathbb{E}\|A\|\) from Theorem 7.3.1 completes the proof.

Now try Exercise 7.11 to prove that a *symmetric Gaussian matrix* satisfies

$$
\mathbb{E}\|A\|\leq 2\sqrt n,
$$

and Exercise 7.13 to show that the *smallest singular value* of an \(m\times n\) Gaussian matrix \(A\) satisfies

$$
\mathbb{E}\,s_n(A)\geq\sqrt m-\sqrt n.
$$
