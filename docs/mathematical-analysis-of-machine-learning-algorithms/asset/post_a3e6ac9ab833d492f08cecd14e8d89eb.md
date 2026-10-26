
We know from Theorem 2.1 that for all $j$ and $z \ge 0$,

$$\Pr\left(g'_j \le \frac{\epsilon z}{\sqrt{2n}}\right) \le 1 - 0.5e^{-(z+1)^2/2},$$
$$\Pr\left(g'_j \le -\frac{\epsilon z}{\sqrt{2n}}\right) \le 0.5e^{-z^2/2},$$

and thus

$$\Pr\left(\sup_j g'_j \le \frac{\epsilon z}{\sqrt{2n}}\right) \le \left(1 - 0.5e^{-(z+1)^2/2}\right)^M,$$
$$\Pr\left(\sup_j g'_j \le -\frac{\epsilon z}{\sqrt{2n}}\right) \le 0.5^M e^{-M z^2/2}.$$

We note that the desired inequality is trivial for $M \le 2$. For $M \ge 3$,

$$\mathbb{E}\sup_j \frac{\sqrt{2n}g'_j}{\epsilon} = -\int_{-\infty}^0 \Pr\left(\sup_j g'_j \le \frac{\epsilon z}{\sqrt{2n}}\right) dz + \int_0^{\infty} \Pr\left(\sup_j g'_j \ge \frac{\epsilon z}{\sqrt{2n}}\right) dz$$
$$\ge \int_0^{\infty} \left(1 - \left(1 - 0.5e^{-(z+1)^2/2}\right)^M\right) dz - \int_{-\infty}^0 0.5^M e^{-M z^2/2} dz$$
$$\ge \int_0^{\sqrt{2\ln M}-1} \left(1 - 0.5\left(1 - 0.5/M\right)^M\right) dz - \int_{-\infty}^0 0.5^M e^{-M z^2/2} dz$$
$$\ge \int_0^{\sqrt{2\ln M}-1} \left(1 - 0.5/\sqrt{e}\right) dz - 0.5^{M+1} M^{-1/2} \int_{-\infty}^{\infty} e^{-z^2/2} dz$$
$$= \left(1 - 0.5/\sqrt{e}\right)\left(\sqrt{2\ln M} - 1\right) - 0.5^{M+1} M^{-1/2} \sqrt{2\pi}$$
$$\ge 0.98\sqrt{\ln M} - 0.9.$$

This implies the desired bound.

A more precise characterization of Gaussian complexity, due to Talagrand (1996a), is to consider a generalization of covering numbers (*majorizing measures*), with a generalization of the chaining technique referred to as *generic chaining*. We consider any measure $\mu$ on $\mathcal{F}$, and let

$$\mu(f, \epsilon, L_2(\mathcal{S}_n)) = \mu\left(\{f' \in \mathcal{F} : \|f' - f\|_{L_2(\mathcal{S}_n)} \le \epsilon\}\right).$$

Then $-\ln \mu(f, \epsilon, L_2(\mathcal{S}_n))$ may be regarded as a generalization of the entropy number of $\mathcal{F}$ localized around $f$. If we define

$$\gamma_2(\mathcal{F}, \mathcal{S}_n) = \inf_{\mu} \sup_{f \in \mathcal{F}} \int_0^{\infty} \sqrt{\frac{-\ln \mu(f, \epsilon, L_2(\mathcal{S}_n))}{n}} \, d\epsilon,$$
then the following result shows the equivalence of Gaussian complexity and the corresponding entropy integral in terms of majorizing measure (Talagrand, 1996a).

## Theorem 12.5 (The Majorizing Measure Theorem)

There exists an absolute constant $C > 0$ so that

$C^{-1}\gamma_2(\mathcal{F},\mathcal{S}_n) \le G(\mathcal{F},\mathcal{S}_n) \le C\gamma_2(\mathcal{F},\mathcal{S}_n)$.

The result shows that the entropy integral bound for empirical processes is generally tight, although one may need to replace covering numbers by majorizing measures in certain situations. In other cases, the difference between covering number and majorizing measure is not significant.

## 12.2 Minimax Analysis for Statistical Estimation

We consider the general statistical estimation problem, where we want to estimate a certain quantity $\theta \in \Theta$ based on a sample $Z$ from a distribution $\mathcal{D}$ on $\mathcal{Z}$. A learning algorithm (estimator) $\mathcal{A}$ is a (possibly random) map $\mathcal{Z} \to \Theta$. The quality of the estimated distribution dependent quantity $\theta \in \Theta$ can be measured by a general loss function

$Q(\theta,\mathcal{D})$

and the goal is to find an estimator $\mathcal{A}$ that achieves the smallest loss $Q(\mathcal{A}(Z),\mathcal{D})$ when $Z \sim \mathcal{D}$.

Note that this definition can handle the general setting of supervised learning, where we observe $n$ iid training examples $\mathcal{S}_n = \{Z_1,\dots,Z_n\}$ from an unknown underlying distribution $\mathcal{D}$. In this case, we may simply take $Z = \mathcal{S}_n$ that is generated according to the product distribution $\mathcal{D}^n$. The model parameter space $\Theta$ can be regarded as the set of prediction functions, and we may denote $\theta$ by $f$, so that the learning algorithm $\mathcal{A}$ learns a function $\hat f = \mathcal{A}(\mathcal{S}_n)$.

### Example 12.6

For a least squares problem, $f(x)$ is a real-valued regression function. Let $f_{\mathcal{D}}(x)=\mathbb{E}_{\mathcal{D}}[Y|X=x]$. We may define $Q(f,\mathcal{D}) = \mathbb{E}_{X\sim\mathcal{D}}\big(f(X)-f_{\mathcal{D}}(X)\big)^2.$

### Example 12.7

For conditional density estimation with $K$ classes $y \in \{1,\dots,K\}$, we may consider $\Theta$ as the class of vector-valued density functions $f(x) = [p(y=1|x),\dots,p(y=K|x)]$. For density estimation, the estimation quality can be measured by the KL-divergence $Q(f,\mathcal{D}) = \mathbb{E}_{X\sim\mathcal{D}}\mathbb{E}_{Y\sim p_{\mathcal{D}}(Y|X)} \ln \frac{p_{\mathcal{D}}(Y|X)}{p(Y|X)}$, or by squared Hellinger distance: $Q(f,\mathcal{D}) = 2 - 2\mathbb{E}_{X\sim\mathcal{D}}\mathbb{E}_{Y\sim p_{\mathcal{D}}(Y|X)} \left(\frac{p(Y|X)}{p_{\mathcal{D}}(Y|X)}\right)^{1/2}$.

### Example 12.8

For $K$-class classification problems, if we are interested in classification accuracy, then we may use the excess classification error over the Bayes classification error as quality measure. Here,

$$f_D(x)=\arg\max_{\ell} p_D(Y=\ell\mid X=x)$$

is the optimal Bayes classifier. Let $f(x)\in\{1,\ldots,K\}$ be any classifier, then we can define

$$Q(f,\mathcal{D})=\mathbb{E}_{X\sim\mathcal{D}}\left[\Pr(Y=f_D(X)\mid X)-\Pr(Y=f(X)\mid X)\right].$$

In statistical estimation, we do not know the true distribution $\mathcal{D}$, but can only observe a sample $S_n$ from $\mathcal{D}^n$. In this case, we may consider a family of distributions $\mathcal{P}$ that contains $\mathcal{D}$. For each $\mathcal{D}\in\mathcal{P}$, a learning algorithm learns a quantity $\theta$ that depends on $\mathcal{D}$ from a sample $S_n\sim\mathcal{D}^n$. We are interested in the worst-case expected risk of a learning algorithm $\mathcal{A}$ to measure the ability of the algorithm to learn the quantity $\theta$ with respect to a family of distributions $\mathcal{P}$.

### Definition 12.9

Consider a distribution family $\mathcal{P}$ on sample space $\mathcal{Z}$, a parameter space $\Theta$. A learning algorithm $\mathcal{A}:\mathcal{Z}^n\to\Theta$, a loss function $Q:\Theta\times\mathcal{P}\to\mathbb{R}$. Then the worst-case expected risk of a learning algorithm (i.e. a statistical estimator) $\mathcal{A}$ with respect to $\mathcal{P}$ is given by

$$r_n(\mathcal{A},\mathcal{P},Q)=\sup_{\mathcal{D}\in\mathcal{P}}\mathbb{E}_{S_n\sim\mathcal{D}^n}\mathbb{E}_{\mathcal{A}}\,Q(\mathcal{A}(S_n),\mathcal{D}),$$

where $\mathbb{E}_{\mathcal{A}}$ is the expectation over any internal randomization of $\mathcal{A}$. Moreover, the minimax risk is defined as

$$r_n(\mathcal{P},Q)=\inf_{\mathcal{A}}r_n(\mathcal{A},\mathcal{P},Q).$$

The standard statistical framework for optimality is to find an algorithm with the smallest worse-case risk $r_n(\mathcal{A},\mathcal{P},Q)$. This type of analysis is referred to as *minimax analysis*. The minimax risk $r_n(\mathcal{P},Q)$ depends only on sample size $n$, distribution family $\mathcal{P}$, and loss function $Q$. In nonparametric statistics, it is difficult to find the exact expression of minimax risk. Therefore we often consider rate optimal algorithms $\mathcal{A}$, which achieve the optimal minimax risk $r_n(\mathcal{P},Q)$ up to a constant factor as $n\to\infty$.

In minimax analysis, we are interested in estimating the minimax risk (up to a constant factor). To establish an upper bound of $r_n(\mathcal{P},Q)$, we consider specific learning algorithms and analyze their convergence rates. For example, if we consider the ERM method $\mathcal{A}_{\mathrm{erm}}$ for the least squares regression problem, then we may obtain an upper bound of

$$r_n(\mathcal{P},Q)\le r_n(\mathcal{A}_{\mathrm{erm}},\mathcal{P},Q)=O(n^{-r})$$

for some $r>0$, based on the analysis of Example 6.49.

On the other hand, if we can show a lower bound $r_n(\mathcal{P},Q)\ge cn^{-r}$ for some constant $c$ that may depend on $\mathcal{P}$ but independent of $n$, then we know that the

ERM method achieves the optimal minimax lower bound. That is, no statistical estimator can perform much better than ERM up to a constant factor for this distribution family. If the lower bound is $O(n^{-r'})$ for $r' > r$, then ERM may not be optimal. As we will see, both situations can happen, depending on the entropy of the function class 𝓕 to be estimated.

## 12.3 Lower Bounds Using Fano’s Inequality

In this section, we will describe a general method to derive lower bounds for statistical estimation based on Fano’s inequality, which is stated as follows.

**Theorem 12.10** *(Fano’s Inequality)*  Consider a finite family of distributions $\mathcal{P} = \{\mathcal{D}_1, \dots, \mathcal{D}_N\}$. Assume that $j$ is a random variable that is uniformly distributed in $\{1, \dots, N\}$, and conditioned on $j$, $Z \sim \mathcal{D}_j$. Let $f(Z) \in \{1, \dots, N\}$ be an estimate of the index $j$. Then

$$\frac{1}{N}\sum_{j=1}^{N}\Pr_{Z\sim\mathcal{D}_j}(f(Z)\ne j) \ge 1-\frac{I(j,Z)+\ln 2}{\ln(N)}.$$

where

$$I(j,Z)=\mathbb{E}_{(j,Z)\sim p(j,Z)}\ln\frac{p(j,Z)}{p(j)p(Z)}$$

is the mutual information between random variables $j$ and $Z$ (see Appendix B).

In the following, we prove a generalization of the Fano’s inequality, which is more convenient to apply for our purpose.

**Theorem 12.11**  *Consider a finite family of distributions* $\mathcal{P} = \{\mathcal{D}_1, \dots, \mathcal{D}_N\}$. Given a loss function $Q$ on $\Theta \times \mathcal{P}$, let

$$m=\sup_{\theta\in\Theta}\left|\left\{k:Q(\theta,\mathcal{D}_k)<\epsilon\right\}\right|.$$

Assume that $j$ is a random variable that is uniformly distributed in $\{1, \dots, N\}$, and conditioned on $j$, $Z \sim \mathcal{D}_j$. Given any (possibly random) estimator $\mathcal{A}(Z)$,

$$\frac{1}{N}\sum_{j=1}^{N}\Pr_{Z\sim\mathcal{D}_j}(Q(\mathcal{A}(Z),\mathcal{D}_j)<\epsilon)\le\max\left(\frac{m}{N},\frac{I(j,Z)+\ln 2}{\ln(N/m)}\right).$$

where $I(j,Z)$ is the mutual information of $j$ and $Z$. The probability includes possible randomization in $\mathcal{A}$.

*Proof*  Let $p_j$ be the density function of $Z$ for $\mathcal{D}_j$. Then the joint distribution of $(j, Z)$ is given by

$$p(j,Z)=\frac{1}{N}p_j(Z).$$
