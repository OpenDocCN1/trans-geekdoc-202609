# **Theorem 7.2.8** (Sudakov-Fernique inequality). Let \((X_t)_{t\in T}\) and \((Y_t)_{t\in T}\) be two *mean-zero Gaussian processes*. Assume that for all \(t,s\in T\), we have

$$\mathbb{E}(X_t-X_s)^2 \leq \mathbb{E}(Y_t-Y_s)^2.$$

*Then*

$$\mathbb{E}\sup_{t\in T}X_t \leq \mathbb{E}\sup_{t\in T}Y_t.$$

*Proof.* It is enough to prove this theorem for Gaussian random vectors \(X\) and \(Y\) in \(\mathbb{R}^n\), just like we did for Slepian inequality in Theorem [7.2.7](#). We again deduce the result from Gaussian Interpolation Lemma [7.2.5](#). But this time, instead of choosing \(f(x)\) that approximates the indicator function of \(\{\max_i x_i<\tau\}\), we want \(f(x)\) to approximate \(\max_i x_i\).

To this end, let \(\beta>0\) be a parameter and define the function⁴

$$f(x):=\frac{1}{\beta}\log\sum_{i=1}^{n}e^{\beta x_i}.$$

A quick check shows that

$$f(x)\to\max_{i\leq n}x_i\quad\text{as }\beta\to\infty.$$

(Do this!) Substituting \(f(x)\) into the Gaussian interpolation formula ([7.9](#)) and simplifying the expression shows that

$$\frac{d}{du}\,\mathbb{E}\,f(Z(u))\leq 0\quad\text{for all }u\in[0,1].$$

(Work through this step carefully in Exercise [7.7](#)!) Then we can finish the proof just like in Slepian inequality.

Some applications call for *min-max* bounds on random processes. For example, by ([4.14](#)), the smallest singular value of an \(m\times n\) Gaussian matrix \(A\) with all \(N(0,1)\) i.i.d. entries can be written as

$$s_n(A)=\min_{u\in S^{m-1}}\|Au\|_2=\min_{u\in S^{m-1}}\max_{v\in S^{n-1}}X_{uv},$$

where \(X_{uv}=\langle Au,v\rangle\) are normal random variables. A handy tool for this kind of problems is Gordon inequality, which extends Slepian and Sudakov-Fernique to the min-max setting:

# **Theorem 7.2.9** (Gordon inequality). Let \((X_{ut})_{u\in U,t\in T}\) and \(Y=(Y_{ut})_{u\in U,t\in T}\) be two *mean-zero Gaussian processes* indexed by pairs of points \((u,t)\) in a product set \(U\times T\). Assume that

$$\mathbb{E}(X_{ut}-X_{vs})^2\leq\mathbb{E}(Y_{ut}-Y_{vs})^2\quad\text{for all }u,t,s;$$
$$\mathbb{E}(X_{ut}-X_{vs})^2\geq\mathbb{E}(Y_{ut}-Y_{vs})^2\quad\text{for all }u\neq v\text{ and all }t,s.$$

⁴ The motivation for considering this form of \(f(x)\) comes from statistical mechanics, where the right side of ([7.12](#)) can be interpreted as a *log-partition function* and \(\beta\) as the *inverse temperature*.