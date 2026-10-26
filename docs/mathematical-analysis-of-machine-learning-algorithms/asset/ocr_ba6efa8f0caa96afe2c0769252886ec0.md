Proof For each model $\theta$, let $\hat f_\theta = \mathcal A(\theta, \mathcal S_n)$. We obtain from the additive Chernoff bound that with probability at least $1 - q(\theta)\delta$,

$$\mathbb E_{Z\sim\mathcal D}\phi(\hat f_\theta, Z) \le \frac{1}{m} \sum_{Z\in\bar\mathcal S_m} \phi(\hat f_\theta, Z) + M\sqrt{\frac{\ln(1/(q(\theta)\delta))}{2m}}$$ $$\le \frac{1}{m} \sum_{Z\in\bar\mathcal S_m} \phi(\hat f_\theta, Z) + M\sqrt{\frac{\ln(1/q(\theta))}{2m}} + M\sqrt{\frac{\ln(1/\delta)}{2m}}.$$

Taking the union bound over $\theta$, we know that the claim holds for all $\theta \ge 1$ with probability at least $1 - \delta$. This result, combined with the definition of $\hat\theta$ in (8.2), leads to the first desired bound.

Now by applying the Chernoff bound for an arbitrary $\theta$ that does not depend on $\bar\mathcal S_m$, we obtain with probability at least $1 - \delta/2$,

$$Q(\theta, \hat f_\theta, \bar\mathcal S_m) \le \mathbb E_{Z\sim\mathcal D}\phi(\hat f_\theta, Z) + r_m(q(\theta)) + M\sqrt{\frac{\ln(2/\delta)}{2m}}.$$

By combining this inequality with the first bound of the theorem, we obtain the second desired inequality.

A frequent choice of $q(\theta)$ is $q(\theta)=1/(\theta(\theta+1))$. In this case, $r_m$ depends only logarithmically on $\theta$, and the penalty $r_m(\theta)$ grows very slowly as $\theta$ increases. It means that for model selection with bounded loss functions, we can compare exponentially (in $m$) many models without paying a significant penalty.

Theorem 8.2 can be combined with uniform convergence results such as Corollary 6.21 to obtain a more precise statement for the ERM method, showing that a near optimal generalization bound can be obtained using the method of (8.2). This leads to an oracle inequality for model selection with ERM learners.

# Corollary 8.3

Consider a countable family of approximate ERM algorithms $\{\mathcal A(\theta,\cdot): \theta=1,2,\dots\}$, each of which is characterized by its model space $\mathcal F(\theta)$ and returns a function $\hat f_\theta \in \mathcal F(\theta)$ such that $$\phi(\hat f, \mathcal S_n) \le \inf_{f\in\mathcal F(\theta)} \phi(f, \mathcal S_n) + \epsilon',$$ where we use the notation of Definition 8.1.

Assume further that $\sup_{Z,Z'}[\phi(f,Z)-\phi(f,Z')] \le M$ for all $f$, and we use (8.2) to select the best model $\hat\theta$ on the validation data $\bar\mathcal S_m$, with the choice $$r_m(q)=M\sqrt{\frac{\ln(1/q)}{2m}}.$$

Then the following result holds with probability at least $1-\delta$ over random selection of $\mathcal S_n$ and $\bar\mathcal S_m$: $$\phi(\mathcal A(\hat\theta,\mathcal S_n),\mathcal D) \le \inf_\theta \Big[\inf_{f\in\mathcal F(\theta)} \phi(f,\mathcal D) + 2R_n(\mathcal G(\theta),\mathcal D) + r_m(q(\theta))\Big] + \tilde\epsilon + \epsilon' + M\sqrt{\frac{2\ln(4/\delta)}{n}} + M\sqrt{\frac{2\ln(4/\delta)}{m}},$$