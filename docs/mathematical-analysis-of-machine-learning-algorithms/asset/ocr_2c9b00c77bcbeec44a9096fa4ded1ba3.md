tion 8.3. Typically, the design of adaptive estimation methods also relies on data-dependent generalization analysis, similar to results developed in Section 8.3.

# Exercises

8.1 In Theorem 8.2, we may consider model selection with

$$r_m(q) = \frac{\ln(1/q)}{2\gamma n}$$

for a fixed $\gamma > 0$. Use multiplicative Chernoff bound to obtain oracle inequalities similar to those of Theorem 8.2 and Corollary 8.3.

8.2 We can derive an expected oracle inequality under conditions of Theorem 8.5. Find a $\beta$ dependent constant $C(\beta)$ such that the following expected oracle inequality holds:

$$\alpha\mathbb{E}_{\mathcal{S}_n}\phi(\hat{f},\mathcal{D}) \le \phi(f,\mathcal{D}) + \mathbb{E}_{\mathcal{S}_n}\bar{R}(\theta,f,\mathcal{S}_n) + C(\beta)\left(\frac{1}{\lambda n}\right)^{\beta}.$$

Note that the inequality does not depend on $\epsilon'$

8.3 Consider a function family $\mathcal{F}$, and for each $f \in \mathcal{F}$, we have a complexity measure $c(f) \ge 0$. Let $\mathcal{F}(\theta) = \{f \in \mathcal{F},c(f) \le \theta\}$ for $\theta > 0$. Assume that we have a bound

$$\bar{R}(\theta) \ge R_n(\mathcal{F}(\theta),\mathcal{D})$$

for any $\theta > 0$. Assume that $\phi(f,z) \in [0,1]$. Use Theorem 8.7 to obtain an oracle inequality for the following regularized ERM method:

$$\hat{f} = \arg\min_{f \in \mathcal{F}} \left[ \frac{1}{n}\sum_{i=1}^n \phi(f,Z_i) + 2\bar{R}(2c(f)) + \sqrt{\ln(2 + \log_2(2c(f)+1))/n} \right].$$

Hint: consider a sequence of function classes $\mathcal{F}(1), \mathcal{F}(2)\setminus\mathcal{F}(1),\mathcal{F}(4)\setminus\mathcal{F}(2),\dots$

8.4 Prove Theorem 8.11.

8.5 Consider the conditional density estimation problem

$$\phi(f,z) = -\ln p(y|f(x)).$$

Let $p_0(f)$ be a prior on $\mathcal{F}$, and assume that the true model is $p(y|f(x))$ is drawn according to the prior $p_0(f)$, and the corresponding data distribution $\mathcal{D}=\mathcal{D}_{f_*}$ has density $p_{f_*}(x,y)=p_*(x)p(y|f_*(x))$ for some unknown function $f_*(x)$. Show that for a given set of training data $\mathcal{S}_n$, the optimal Bayes estimator $\hat{f}_{\mathcal{S}_n}$ in terms of minimizing the expected loss

$$\mathbb{E}_{f_*\sim p_0}\mathbb{E}_{\mathcal{S}_n\sim\mathcal{D}_{f_*}^n}\mathbb{E}_{Z\sim\mathcal{D}_{f_*}} \phi(\hat{f}(Z))$$

is given by Bayesian model averaging over $p(y|f(x))$. Moreover, the Bayesian optimal model selection method is given by $\arg\max_\theta \Gamma(\theta|\mathcal{S}_n)$.

8.6 Show that the following example satisfies Proposition 8.12. Consider a one-dimensional problem with $x \sim \text{Uniform}(-1,1)$. Assume that we choose $f_*(x)$ randomly from a two-function family $\{f_*^k(x) : k = 1,2\}$, each with probability 0.5, where $f_*^1(x) = 1/\sqrt{n}$, and $f_*^2(x) = -1/\sqrt{n}$. Define two misspecified single-function model families $\{f_\theta(x)\}$ for $\theta = 1,2$ as $f_\theta(x) = 0.5$ for $\theta = 1$ and $f_\theta(x) = -0.5$ for $\theta = 2$.