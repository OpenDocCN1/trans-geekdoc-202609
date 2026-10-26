
## 8.3 Model Selection on Training Data Using Data Dependent Bounds

In the typical application of model selection, we can split a large labeled dataset into training and validation partitions, and employ the technique of Section 8.2 to do model selection on the validation data. However, the split effectively reduces the training data size, and it is difficult to nest model selection procedures (i.e., to select model selection algorithms). To address this issue, an alternative approach is to do model selection directly on the training data ($S_N = S_n$) without any training and validation partition. This is possible if we have a sample-dependent generalization bound, as we will demonstrate in this section.

In the following, we still consider a countable sequence of models, parameterized by function families $\{\mathcal{F}(\theta): \theta = 1, 2, \ldots\}$. Consider the following model selection algorithm, which simultaneously finds the model hyperparameter $\hat{\theta}$ and model function $\hat{f} \in \mathcal{F}(\hat{\theta})$ on the training data $S_n$:

$$Q(\hat{\theta}, \hat{f}, S_n) \leq \inf_{\theta, f \in \mathcal{F}(\theta)} Q(\theta, f, S_n) + \tilde{\epsilon}, \tag{8.3}$$

where for $f \in \mathcal{F}(\theta)$,

$$Q(\theta, f, S_n) = \phi(f, S_n) + \tilde{R}(\theta, f, S_n),$$

where $\tilde{R}$ is an appropriately chosen sample-dependent upper bound of the complexity for family $\mathcal{F}(\theta)$.

Sample-dependent uniform convergence bounds can be used to design $\tilde{R}$ in the model selection algorithm (8.3) on training data only, without splitting the training data into training versus validation partitions. The idea is similar to the model selection on validation data presented in Section 8.2, with a data-dependent uniform convergence bound replacing the Chernoff bound. The following generic result shows that for this model selection method, we can obtain an oracle inequality from any sample-dependent uniform convergence bound.

**Theorem 8.5** Let $\{q(\theta) \geq 0\}$ be a sequence of numbers that satisfy (8.1). Assume that for each model $\theta$, we have the following uniform convergence result. With probability at least $1-\delta$, for all $f \in \mathcal{F}(\theta)$,

$$\alpha\phi(f, \mathcal{D}) \leq \phi(f, S_n) + \hat{\epsilon}(\theta, f, S_n) + \left(\frac{\ln(c_0/\delta)}{\lambda n}\right)^\beta,$$

for some constants $\alpha, \lambda, \beta > 0$ and $c_0 \geq 1$. If we choose

$$\tilde{R}(\theta, f, S_n) \geq \hat{\epsilon}(\theta, f, S_n) + 2^{\max(0,\beta-1)}\left(\frac{\ln(c_0/q(\theta))}{\lambda n}\right)^\beta,$$

then the following uniform convergence result holds. With probability at least $1-\delta$, for all $\theta$ and $f \in \mathcal{F}(\theta)$,

$$\alpha\phi(f, \mathcal{D}) \leq \phi(f, S_n) + \tilde{R}(\theta, f, S_n) + 2^{\max(0,\beta-1)}\left(\frac{\ln(1/\delta)}{\lambda n}\right)^\beta.$$

If, moreover, we have for all $\theta$ and $f \in \mathcal{F}(\theta)$ the following concentration bound holds, with probability $1-\delta$:

$$\phi(f, S_n) + \widetilde{R}(\theta, f, S_n) \le \mathbb{E}_{S_n}\left[\alpha'\phi(f, S_n) + \alpha''\widetilde{R}(\theta, f, S_n)\right] + \epsilon'(\theta, f, \delta).$$

Then we have the following oracle inequality for (8.3). With probability at least $1-\delta$,

$$\alpha\phi(\hat{f}, \mathcal{D}) \le \inf_{\theta,f\in\mathcal{F}(\theta)}\left[\alpha'\phi(f, \mathcal{D}) + \alpha''\mathbb{E}_{S_n}\widetilde{R}(\theta, f, S_n) + \epsilon'(\theta, f, \delta/2)\right] + \widetilde{\epsilon} + 2^{\max(0,\beta-1)}\left(\frac{\ln(2/\delta)}{\lambda n}\right)^\beta.$$

**Proof** Taking the union bound over $\theta$, each with probability $1 - 0.5q(\theta)\delta$, we obtain that with probability at least $1-\delta/2$, for all $\theta$ and $f \in \mathcal{F}(\theta)$,

$$\alpha\phi(f, \mathcal{D}) \le \phi(f, S_n) + \hat{\epsilon}(\theta, f, S_n) + \left(\frac{\ln(c_0/q(\theta))}{\lambda n} + \frac{\ln(2/\delta)}{\lambda n}\right)^\beta$$

$$\le \phi(f, S_n) + \hat{\epsilon}(\theta, f, S_n) + 2^{\max(0,\beta-1)}\left(\frac{\ln(c_0/q(\theta))}{\lambda n}\right)^\beta + 2^{\max(0,\beta-1)}\left(\frac{\ln(2/\delta)}{\lambda n}\right)^\beta$$

$$\le \phi(f, S_n) + \widetilde{R}(\theta, f, S_n) + 2^{\max(0,\beta-1)}\left(\frac{\ln(2/\delta)}{\lambda n}\right)^\beta.$$

The first inequality used the union bound over all $\theta$. The second inequality used Jensen’s inequality. The third inequality used the assumption on $\widetilde{R}$. This proves the desired uniform convergence result.

Now since $\hat{f}$ is the solution of (8.3), it follows that for all $\theta$ and $f \in \mathcal{F}(\theta)$, with probability at least $1-\delta/2$,

$$\alpha\phi(\hat{f}, \mathcal{D}) \le \phi(\hat{f}, S_n) + \widetilde{R}(\theta, \hat{f}, S_n) + 2^{\max(0,\beta-1)}\left(\frac{\ln(2/\delta)}{\lambda n}\right)^\beta$$

$$\le \phi(f, S_n) + \widetilde{R}(\theta, f, S_n) + 2^{\max(0,\beta-1)}\left(\frac{\ln(2/\delta)}{\lambda n}\right)^\beta + \widetilde{\epsilon}.$$

In addition, with probability at least $1-\delta/2$,

$$\phi(f, S_n) + \widetilde{R}(\theta, f, S_n) \le \mathbb{E}_{S_n}\left[\alpha'\phi(f, S_n) + \alpha''\widetilde{R}(\theta, f, S_n)\right] + \epsilon'(\theta, f, \delta/2).$$

Taking the union bound and summing the two inequalities, we obtain the desired oracle inequality. $\square$

The result demonstrates that one can turn any sample-dependent uniform convergence bound into a model selection method. The algorithm itself does not depend on the concentration result involving $\epsilon'$. In fact, an expected oracle inequality can be obtained even if we do not know $\epsilon'$, as shown in Exercises 8.2. The following example illustrates the roles of $\alpha$, $\alpha'$, $\alpha''$, $\beta$, and $\lambda$.

**Example 8.6** In Theorem 8.5, we consider the following absolute deviation loss

$$\phi(f,z)=|f(x)-y|,$$

and assume that $y\in[-1,1]$. Assume also that we have function families $\{\mathcal{F}(\theta)\}$, each with $N(\theta)$ elements, and $|f(x)|\leq\theta$ for all $f(x)\in\mathcal{F}(\theta)$ ($\theta=1,2,\ldots$). We thus have $\phi(f,z)\in[0,\theta+1]$. The multiplicative Chernoff bound in (2.11) implies that for any $\theta$, with probability at least $1-\delta$, for all $f\in\mathcal{F}(\theta)$,

$$(1-\gamma)\phi(f,\mathcal{D})\leq\phi(f,S_n)+\frac{(\theta+1)\ln(N(\theta)/\delta)}{2\gamma n}.$$

It implies the following result for $\gamma\in(0,1)$:

$$(1-\gamma)\phi(f,\mathcal{D})\leq\phi(f,S_n)+\frac{(\theta+1)\ln(N(\theta))}{2\gamma n}+\frac{\lambda^2(\theta+1)^2}{16\gamma^2}+\left(\frac{\ln(1/\delta)}{\lambda n}\right)^2.$$

In this derivation, we tried to decouple $\theta$ and $\delta$ so that the penalty term $\widetilde{R}$ in the model selection method (8.3) does not depend on $\delta$. Now we can take $\beta=2$. It follows that we can take

$$\widehat{\epsilon}(\theta,f,S_n)=\frac{(\theta+1)\ln(N(\theta))}{2\gamma n}+\frac{\lambda^2(\theta+1)^2}{16\gamma^2},$$

$$\widetilde{R}(\theta,f,S_n)=\frac{(\theta+1)\ln(N(\theta))}{2\gamma n}+\frac{\lambda^2(\theta+1)^2}{16\gamma^2}+2\left(\frac{\ln(1/q(\theta))}{\lambda n}\right)^2.$$

Both $\widehat{\epsilon}$ and $\widetilde{R}$ depend on the model index $\theta$ but not on the training data $S_n$.

Now for all $\theta$ and $f\in\mathcal{F}(\theta)$, the multiplicative Chernoff bound (2.12) implies that with probability $1-\delta$,

$$\phi(f,S_n)\leq(1+\gamma)\phi(f,\mathcal{D})+\frac{(1+\theta)(3+2\gamma)\ln(1/\delta)}{6\gamma n}.$$

Theorem 8.5 implies that the following oracle inequality holds:

$$(1-\gamma)\phi(\widehat{f},\mathcal{D})\leq\inf_{\theta,f\in\mathcal{F}(\theta)}\left[(1+\gamma)\phi(f,\mathcal{D})+\epsilon_n(\theta,\delta/2)\right]+\widetilde{\epsilon}+\left(\frac{\ln(2/\delta)}{\lambda n}\right)^2,$$

where

$$\epsilon_n(\theta,\delta)=\frac{(\theta+1)\ln N(\theta)}{2\gamma n}+\frac{\lambda^2(\theta+1)^2}{16\gamma^2}+2\left(\frac{\ln(1/q(\theta))}{\lambda n}\right)^2+\frac{(1+\theta)(3+2\gamma)\ln(1/\delta)}{6\gamma n}.$$

If we take $\lambda=1/\sqrt{n}$, then we have a complexity term of $\epsilon_n(\theta,\delta)=O(1/n)$.

Next we focus on bounded loss functions with Rademacher complexity analysis. In such case, we can simply apply Theorem 8.5 with $\alpha=\alpha'=\alpha''=1$ and $\beta=0.5$.
