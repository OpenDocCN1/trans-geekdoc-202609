
This matches the lower bound of Corollary 12.20.

For \(q > 2\), the generalization bound for the empirical risk minimization method is

\[
\mathbb{E}_{S_n \sim \mathcal{D}^n} \mathbb{E}_{X \sim \mathcal{D}_X} (\hat f_{\mathrm{erm}}(X) - f_{\mathcal{D}}(X))^2 = O(n^{-1/q}),
\]

and since \(1/q < 2/(q + 2)\), the rate is inferior to the minimax rate. In general, this rate cannot be improved without additional assumptions (Birgé and Massart, 1993). Therefore when the nonparametric family has a large entropy, ERM can be suboptimal.

It is possible to achieve the optimal rate of \(O(n^{-2/(q+2)})\) even when \(q > 2\). One of the optimal methods is least squares on sieves, and a related method is the Gibbs algorithm with an appropriate prior. A third method is the exponential model aggregation method, studied in Section 15.3.

In the following, we consider the sieve method (Grenander, 1981; Geman and Hwang, 1982; Birgé and Massart, 1998), which, in our setting, is simply least squares regression on discrete \(\epsilon\)-net.

Given a function class \(\mathcal{F}\), instead of running least squares on \(\mathcal{F}\) with

\[
\hat f = \arg\min_{f \in \mathcal{F}} \sum_{i=1}^{n} (f(X_i) - Y_i)^2,
\]

the sieve method considers a subset \(\mathcal{F}_n \subset \mathcal{F}\), and then performs least squares regression restricted to this subset:

\[
\hat f_{\mathcal{F}_n} = \arg\min_{f \in \mathcal{F}_n} \sum_{i=1}^{n} (f(X_i) - Y_i)^2.
\]

The following result shows that with appropriate \(\mathcal{F}_n\), we may achieve the minimax risk of Corollary 12.20.

### Proposition 12.21

Assume that the distribution of \(X\) is \(\mathcal{D}_X\). Let \(\mathcal{F}_n\) be an \(\epsilon\) packing subset of \(\mathcal{F}\) in the \(L_2(\mathcal{D}_X)\) metric with \(M(\epsilon, \mathcal{F}, L_2(\mathcal{D}_X))\) members. Assume there exists \(b > 0\) such that \(|f(X) - f'(X)| \le 2b\) for all \(f, f' \in \mathcal{F}\). Assume that \(f_{\mathcal{D}} \in \mathcal{F}\) and \(Y\) is sub-Gaussian:

\[
\ln \mathbb{E}_{Y|X} \exp(\lambda(Y - f_{\mathcal{D}}(X))) \le \frac{\lambda^2 b^2}{2}.
\]

Then

\[
\mathbb{E}_{S_n \sim \mathcal{D}^n} \mathbb{E}_{X \sim \mathcal{D}_X} (\hat f_{\mathcal{F}_n}(X) - f_{\mathcal{D}}(X))^2 \le \left[ 4\epsilon^2 + \frac{14 b^2}{n} \ln M(\epsilon, \mathcal{F}, L_2(\mathcal{D}_X)) \right].
\]

*Proof* Let \(\phi(f, Z) = (f(X)-Y)^2 - (f_{\mathcal{D}}(X)-Y)^2\) with \(Z = (X, Y)\). Let \(\rho = b^{-2}/4\). Then we have

\[
\begin{aligned}
\Lambda(\rho,f)
&= -\frac{1}{\rho}\ln \mathbb{E}_Z e^{-\rho\phi(f,Z)}
   \quad(\text{definition of } \Lambda \text{ in Theorem 10.18})\\
&= -\frac{1}{\rho}\ln \mathbb{E}_X\mathbb{E}_{Y|X} e^{-\rho(f(X)-f_{\mathcal{D}}(X))^2 + 2\rho(f(X)-f_{\mathcal{D}}(X))(Y-f_{\mathcal{D}}(X))}
   \quad(\text{definition of } \phi)\\
&\ge -\frac{1}{\rho}\ln \mathbb{E}_X e^{(-\rho + 2\rho^2 b^2)(f(X)-f_{\mathcal{D}}(X))^2}
   \quad(\text{sub-Gaussian noise assumption})\\
&\ge \frac{1}{\rho}\left[1 - \mathbb{E}_X e^{-0.5\rho(f(X)-f_{\mathcal{D}}(X))^2}\right]
   \quad(-\ln z \ge 1-z)\\
&\ge \frac{1}{\rho}\mathbb{E}_X e^{-2\rho b^2} \cdot 0.5\rho(f(X)-f_{\mathcal{D}}(X))^2
   \quad(1-e^{-z} \ge e^{-az}z \text{ for } z\in[0,a])\\
&\ge 0.3\,\mathbb{E}_X(f(X)-f_{\mathcal{D}}(X))^2.
   \quad(2\rho b^2=0.5)
\end{aligned}
\]

It follows from Theorem 10.18 by setting \(1/(\lambda n)=\rho=b^{-2}/4\) (which implies that \(\lambda=4b^2/n\)) that for any random estimator \(\hat q\) on \(\mathcal{F}_n\),

\[
0.3\mathbb{E}_{S_n}\mathbb{E}_{f\sim \hat q(\cdot|S_n)}\mathbb{E}_X(f(X)-f_{\mathcal{D}}(X))^2
\le
\mathbb{E}_{S_n}\mathbb{E}_{f\sim \hat q(\cdot|S_n)}\frac{1}{n}\sum_{i=1}^{n}\phi(f,Z_i)
+\frac{4b^2}{n}\mathbb{E}_{S_n}\operatorname{KL}(\hat q\|q_0).
\tag{12.1}
\]

Let \(\hat q\) correspond to the deterministic estimator \(\hat f_{\mathcal{F}_n}\), and let \(q_0\) be the uniform distribution on \(\mathcal{F}_n\). Then \(\operatorname{KL}(\hat q\|q_0) \le \ln|\mathcal{F}_n|\). Therefore we obtain

\[
\begin{aligned}
0.3\mathbb{E}_{S_n} Q_{\mathrm{LS}}(\hat f_{\mathcal{F}_n},\mathcal{D})
&\le \mathbb{E}_{S_n}\frac{1}{n}\sum_{i=1}^{n}\phi(\hat f_{\mathcal{F}_n},Z_i)+\frac{4b^2}{n}\ln|\mathcal{F}_n|\\
&\le \inf_{f\in\mathcal{F}_n}\mathbb{E}_{S_n}\frac{1}{n}\sum_{i=1}^{n}\phi(f,Z_i)+\frac{4b^2}{n}\ln|\mathcal{F}_n|\\
&\le \inf_{f\in\mathcal{F}_n}Q_{\mathrm{LS}}(f,\mathcal{D})+\frac{4b^2}{n}\ln|\mathcal{F}_n|
\le \epsilon^2+\frac{4b^2}{n}\ln|\mathcal{F}_n|.
\end{aligned}
\]

\((\hat f_{\mathcal{F}_n}\) is the empirical risk minimizer on \(\mathcal{F}_n\).)

The last inequality used the fact that \(\mathcal{F}_n\) is an \(\epsilon\) packing of \(\mathcal{F}\) and \(f_{\mathcal{D}}\in\mathcal{F}\). This implies the desired bound.

### Example 12.22

Consider the covering number condition of Corollary 12.20.

We note that

\[
\inf_{\epsilon>0} O\left(\epsilon^2+\frac{1}{n}\ln M(\epsilon,\mathcal{F},L_2(\mathcal{D}_X))\right)=O(n^{-2/(2+q)}).
\]

Therefore the upper bound of Proposition 12.21 matches the lower bound of Corollary 12.20.

The method of sieves can be regarded as a regularization method for ERM. The optimality of using a sieve versus ERM on the original function class implies that ERM can overfit if not used properly, which leads to suboptimality. It is suitable only for certain function classes but not others.

Another method that is closely related to the Gibbs algorithm is model aggregation, studied in Section 15.3. The generalization bound there implies that using model aggregation on a sieve \(\mathcal{F}_n = \{f_1,\dots,f_N\}\), with \(N = M(\epsilon,\mathcal{F},L_2(\mathcal{D}_X))\), we have

\[
\mathbb{E}_{S_n} Q_{\mathrm{LS}}(\hat f,\mathcal{D}) = O\Big(\inf_j Q_{\mathrm{LS}}(f_j,\mathcal{D}) + n^{-1}\ln M(\epsilon,\mathcal{F},L_2(\mathcal{D}_X))\Big).
\]

This achieves the same rate as that of Proposition 12.21. It follows that the exponential aggregation algorithm is also an optimal algorithm for least squares regression.

## 12.5 Minimax Analysis for Density Estimation

Assume that we are given a family of conditional distributions \(\mathcal{F} = \{p(Y|X) : p \in \mathcal{F}\}\) and the true conditional distribution \(p_{\mathcal{D}} \in \mathcal{F}\). Similar to Section 12.4, we assume that all conditional densities share a marginal distribution \(\mathcal{D}_X\) on \(X\) (which the learning algorithm does not need to know). The joint distribution is \(\mathcal{P} = \{p(X,Y)=p_{\mathcal{D}_X}(X)p(Y|X) : p \in \mathcal{F}\}\).

Given any \(p \in \mathcal{F}\), we are interested in minimizing its squared Hellinger distance to the true distribution

\[
Q_H(p,\mathcal{D}) = H_{\mathcal{D}_X}(p\|p_{\mathcal{D}})^2 = \mathbb{E}_{X\sim\mathcal{D}_X} H(p(\cdot|X)\|p_{\mathcal{D}}(\cdot|X))^2.
\]

Here \(H_{\mathcal{D}_X}\) is the Hellinger distance between the joint probability distributions \(p_{\mathcal{D}_X}(X)p(Y|X)\) and \(p_{\mathcal{D}_X}(X)p_{\mathcal{D}}(Y|X)\) in \(\mathcal{P}\).

We focus on the case that there exists \(c_{\mathcal{F}} > 0\) so that for all \(p,p' \in \mathcal{F}\)

\[
\mathbb{E}_{X\sim\mathcal{D}_X} \mathrm{KL}(p(\cdot|X)\|p'(\cdot|X)) \le c_{\mathcal{F}} H_{\mathcal{D}_X}(p\|p')^2. \tag{12.2}
\]

For example, this condition holds if \(\ln p(Y|X)\) is bounded.

The following result is a direct consequence of Theorem 12.15. The proof is similar to that of Theorem 12.17, and we leave it as an exercise.

### Theorem 12.24

*Consider the conditional density estimation problem with \(X \sim \mathcal{D}_X\), and assume that the true conditional probability is given by*

\[
p_{\mathcal{D}}(Y|X) \in \mathcal{F}.
\]

*Assume that (12.2) holds. If \(\mathcal{F}\) contains \(N\) conditional densities \(p_1,\dots,p_N\) such that*

\[
\ln N \ge \ln 4 + 2c_{\mathcal{F}} \sup_{j,k} H_{\mathcal{D}_X}(p_j\|p_k)^2,
\]

*then*

\[
r_n(\mathcal{P},Q_H) \ge 0.125 \inf_{j\neq k} H_{\mathcal{D}_X}(p_j\|p_k)^2.
\]

We have the following lower bound using metric entropy with respect to the Hellinger distance, which is analogous to Corollary 12.20.

### Corollary 12.25

*If for some \(C>0\) and \(\epsilon>0\),*

\[
C^{-1}\epsilon^{-q}\leq \ln M(\epsilon,\mathcal{F},H_{\mathcal{D}_X})\leq C\epsilon^{-q}.
\]

*Assume that (12.2) holds. Then we have*

\[
r_n(\mathcal{P},Q_H)\geq C'n^{-2/(2+q)}
\]

*for some \(C'>0\).*

We also have the following upper bound using the Gibbs algorithm on sieves.

### Proposition 12.26

*Assume that the distribution of \(X\) is \(\mathcal{D}_X\). Let \(\mathcal{F}_n\) be an \(\epsilon\) packing subset of \(\mathcal{F}\) under the \(H_{\mathcal{D}_X}\) metric with \(M(\epsilon,\mathcal{F},H_{\mathcal{D}_X})\) members. Assume that \(p_{\mathcal{D}}\in\mathcal{F}\) and (12.2) holds. Let \(\hat q\) be a Gibbs distribution on \(\mathcal{F}_n\) defined as*

\[
\hat q(p\mid S_n)\propto q_0(p)\exp\left(0.5\sum_{i=1}^{n}\ln p(Y_i\mid X_i)\right),
\]

*where \(q_0(p)\) is the uniform distribution on \(\mathcal{F}_n\). Then*

\[
\mathbb{E}_{S_n\sim \mathcal{D}^n}\mathbb{E}_{p\sim\hat q}Q_H(p,\mathcal{D})\leq c_{\mathcal{F}}\epsilon^2+\frac{2\ln M(\epsilon,\mathcal{F},H_{\mathcal{D}_X})}{n}.
\]

*Proof* Let \(\Delta(\mathcal{F}_n)\) denote the set of probability distributions on \(\mathcal{F}_n\). We obtain

\[
\begin{aligned}
\mathbb{E}_{S_n\sim \mathcal{D}^n}\mathbb{E}_{p\sim\hat q}Q_H(p,\mathcal{D})
&\leq \inf_{q\in\Delta(\mathcal{F}_n)}\left[\mathbb{E}_{p\sim q}\mathbb{E}_{X\sim \mathcal{D}_X}\mathrm{KL}(p_{\mathcal{D}}(\cdot\mid X)\Vert p(\cdot\mid X))+\frac{2\mathrm{KL}(q\Vert q_0)}{n}\right]\\
&\leq \inf_{q\in\Delta(\mathcal{F}_n)}\left[c_{\mathcal{F}}\mathbb{E}_{p\sim q}H_{\mathcal{D}_X}(p_{\mathcal{D}}\Vert p)^2+\frac{2\ln M(\epsilon,\mathcal{F},H_{\mathcal{D}_X})}{n}\right].
\end{aligned}
\]

The first inequality used Corollary 10.26 with \(\alpha=0.5\). The second inequality used (12.2) and \(\mathrm{KL}(q\Vert q_0)\leq\ln M(\epsilon,\mathcal{F},H_{\mathcal{D}_X})\). Since \(\mathcal{F}_n\) is also an \(\epsilon\)-cover of \(\mathcal{F}\) in \(H_{\mathcal{D}_X}\), we obtain the desired bound.

Under the condition of Corollary 12.25, we note that

\[
\inf_{\epsilon>0}O\left(\epsilon^2+\frac{1}{n}\ln M(\epsilon,\mathcal{F},H_{\mathcal{D}_X})\right)=O\left(n^{-2/(2+q)}\right).
\]

Therefore the upper bound of Proposition 12.26 matches the lower bound of Corollary 12.25.

## 12.6 Lower Bounds Using Assouad’s Lemma

While the minimax risk analysis using Fano’s inequality is applicable to a number of problems, the resulting bound employs KL-divergence, which can be infinity for
