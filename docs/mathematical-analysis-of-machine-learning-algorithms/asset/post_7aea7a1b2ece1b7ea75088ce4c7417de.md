
## 8.2 Model Selection on Validation Data

A frequently employed method for model hyperparameter tuning is to split a labeled data set \(\mathcal{S}_N\) into a training data \(\mathcal{S}_n\) and a validation data \(\bar{\mathcal{S}}_m\) with \(N = m+n\). We can then train the models on the training data \(\mathcal{S}_n\), and then evaluate on validation data \(\bar{\mathcal{S}}_m\). We select the models according to their performance on the validation set.

In this section, we consider a countable sequence of models \(\{\mathcal{A}(\theta,\cdot): \theta = 1,2,\dots\}\) that can produce \(\hat{f}_\theta = \mathcal{A}(\theta,\mathcal{S}_n) \in \mathcal{F}\) from the training data \(\mathcal{S}_n\). Let \(\{q(\theta) \ge 0\}\) be a sequence of nonnegative numbers that satisfies the inequality

\[
\sum_{\theta=1}^{\infty} q(\theta) \le 1. \tag{8.1}
\]

Consider the following model selection algorithm, which trains a prediction function \(\mathcal{A}(\theta,\mathcal{S}_n)\) on training data for any given model \(\theta\), and then selects a model \(\hat{\theta}\) to approximately minimize the following generic model selection criterion on the validation data:

\[
Q(\hat{\theta},\mathcal{A}(\hat{\theta},\mathcal{S}_n),\bar{\mathcal{S}}_m) \le \inf_{\theta} Q(\theta,\mathcal{A}(\theta,\mathcal{S}_n),\bar{\mathcal{S}}_m) + \tilde{\epsilon}, \tag{8.2}
\]

where

\[
Q(\theta, f, \bar{\mathcal{S}}_m) = \phi(f, \bar{\mathcal{S}}_m) + r_m(q(\theta)).
\]

We have the following generic model selection result using the union bound and additive Chernoff bound. Similar results can be obtained for multiplicative Chernoff bounds, and Bernstein's inequalities.

### Theorem 8.2 (Model Selection on Validation Data)

Assume \(\sup_{Z,Z'}[\phi(f,Z)-\phi(f,Z')] \le M\) for all \(f\), and the validation data \(\bar{\mathcal{S}}_m\) contains \(m\) iid samples from \(\mathcal{D}\). Given training data \(\mathcal{S}_n\), consider (8.2) with

\[
r_m(q) = M \sqrt{\frac{\ln(1/q)}{2m}}.
\]

Then with probability at least \(1 - \delta\) over the random selection of \(\bar{\mathcal{S}}_m\),

\[
\phi(\mathcal{A}(\hat{\theta},\mathcal{S}_n),\mathcal{D}) \le \inf_{\theta} Q(\theta,\mathcal{A}(\theta,\mathcal{S}_n),\bar{\mathcal{S}}_m) + \tilde{\epsilon} + M \sqrt{\frac{\ln(1/\delta)}{2m}}.
\]

This implies the following oracle inequality. With probability at least \(1 - \delta\) over the random sampling of \(\bar{\mathcal{S}}_m\),

\[
\phi(\mathcal{A}(\hat{\theta},\mathcal{S}_n),\mathcal{D}) \le \inf_{\theta}[\phi(\mathcal{A}(\theta,\mathcal{S}_n),\mathcal{D}) + r_m(q(\theta))] + \tilde{\epsilon} + M \sqrt{\frac{2\ln(2/\delta)}{m}},
\]

where \(q(\theta)\) satisfies (8.1).

**Proof.** For each model \(\theta\), let \(\hat f_\theta = \mathcal A(\theta, \mathcal S_n)\). We obtain from the additive Chernoff bound that with probability at least \(1 - q(\theta)\delta\),

\[
\mathbb E_{Z\sim\mathcal D}\phi(\hat f_\theta, Z) \le \frac{1}{m} \sum_{Z\in\bar\mathcal S_m} \phi(\hat f_\theta, Z) + M\sqrt{\frac{\ln(1/(q(\theta)\delta))}{2m}}
\]

\[
\le \frac{1}{m} \sum_{Z\in\bar\mathcal S_m} \phi(\hat f_\theta, Z) + M\sqrt{\frac{\ln(1/q(\theta))}{2m}} + M\sqrt{\frac{\ln(1/\delta)}{2m}}.
\]

Taking the union bound over \(\theta\), we know that the claim holds for all \(\theta \ge 1\) with probability at least \(1 - \delta\). This result, combined with the definition of \(\hat\theta\) in (8.2), leads to the first desired bound.

Now by applying the Chernoff bound for an arbitrary \(\theta\) that does not depend on \(\bar\mathcal S_m\), we obtain with probability at least \(1 - \delta/2\),

\[
Q(\theta, \hat f_\theta, \bar\mathcal S_m) \le \mathbb E_{Z\sim\mathcal D}\phi(\hat f_\theta, Z) + r_m(q(\theta)) + M\sqrt{\frac{\ln(2/\delta)}{2m}}.
\]

By combining this inequality with the first bound of the theorem, we obtain the second desired inequality.

A frequent choice of \(q(\theta)\) is \(q(\theta)=1/(\theta(\theta+1))\). In this case, \(r_m\) depends only logarithmically on \(\theta\), and the penalty \(r_m(\theta)\) grows very slowly as \(\theta\) increases. It means that for model selection with bounded loss functions, we can compare exponentially (in \(m\)) many models without paying a significant penalty.

Theorem 8.2 can be combined with uniform convergence results such as Corollary 6.21 to obtain a more precise statement for the ERM method, showing that a near optimal generalization bound can be obtained using the method of (8.2). This leads to an oracle inequality for model selection with ERM learners.

### Corollary 8.3

Consider a countable family of approximate ERM algorithms \(\{\mathcal A(\theta,\cdot): \theta=1,2,\dots\}\), each of which is characterized by its model space \(\mathcal F(\theta)\) and returns a function \(\hat f_\theta \in \mathcal F(\theta)\) such that

\[
\phi(\hat f_\theta, \mathcal S_n) \le \inf_{f\in\mathcal F(\theta)} \phi(f, \mathcal S_n) + \epsilon',
\]

where we use the notation of Definition 8.1.

Assume further that \(\sup_{Z,Z'}[\phi(f,Z)-\phi(f,Z')] \le M\) for all \(f\), and we use (8.2) to select the best model \(\hat\theta\) on the validation data \(\bar\mathcal S_m\), with the choice

\[
r_m(q)=M\sqrt{\frac{\ln(1/q)}{2m}}.
\]

Then the following result holds with probability at least \(1-\delta\) over random selection of \(\mathcal S_n\) and \(\bar\mathcal S_m\):

\[
\phi(\mathcal A(\hat\theta,\mathcal S_n),\mathcal D) \le \inf_\theta \Big[\inf_{f\in\mathcal F(\theta)} \phi(f,\mathcal D) + 2R_n(\mathcal G(\theta),\mathcal D) + r_m(q(\theta))\Big] + \tilde\epsilon + \epsilon' + M\sqrt{\frac{2\ln(4/\delta)}{n}} + M\sqrt{\frac{2\ln(4/\delta)}{m}},
\]

where \(R_n(\mathcal{G}(\theta),\mathcal{D})\) is the Rademacher complexity of \(\mathcal{G}(\theta)=\{\phi(f,\cdot):f\in\mathcal{F}(\theta)\}\) and \(q(\theta)\) satisfies (8.1).

**Proof.** Consider any model \(\theta\). We have from Theorem 8.2 that with probability \(1-\delta/2\),

\[
\phi(\mathcal{A}(\hat{\theta},\mathcal{S}_n),\mathcal{D})\leq \phi(\mathcal{A}(\theta,\mathcal{S}_n),\mathcal{D})+r_m(q(\theta))+\tilde{\epsilon}+M\sqrt{\frac{2\ln(4/\delta)}{m}}.
\]

Moreover, from Corollary 6.21 with \(h(\cdot)=0\), we know that with probability at least \(1-\delta/2\),

\[
\phi(\mathcal{A}(\theta,\mathcal{S}_n),\mathcal{D})\leq \inf_{f\in\mathcal{F}(\theta)}\phi(f,\mathcal{D})+\epsilon'+2R_n(\mathcal{G}(\theta),\mathcal{D})+2M\sqrt{\frac{\ln(4/\delta)}{2n}}.
\]

Taking the union bound, both inequalities hold with probability at least \(1-\delta\), which leads to the desired bound. \(\square\)

In the application of Corollary 8.3, we often choose a nested function class \(\mathcal{F}(\theta)\subset\mathcal{F}(\theta')\) when \(\theta\leq\theta'\). This means we consider a sequence of model families that become more complex. A larger function class \(\mathcal{F}(\theta)\) can achieve a smaller test loss \(\inf_{f\in\mathcal{F}(\theta)}\phi(f,\mathcal{D})\), but it also has a larger Rademacher complexity \(R_n(\mathcal{G}(\theta),\mathcal{D})\). With the choice of \(q(\theta)=1/(\theta+1)^2\), \(r_m\) depends only logarithmically on \(\theta\), and hence \(R_n(\mathcal{G}(\theta),\mathcal{D})\) is the dominant penalty for overall generalization performance. It also implies that we should usually choose \(n\) to be larger than \(m\) in the training/validation split, as the dominant penalty \(R_n(\mathcal{G}(\theta),\mathcal{D})\) decreases as \(n\) increases.

### Example 8.4

Consider a \(\{0,1\}\)-valued binary classification problem, with binary classifiers \(\mathcal{F}(\theta)=\{f_{\theta}(w,x)\in\{0,1\}:w\in\Omega(\theta)\}\) of VC-dimension \(d(\theta)\). The Rademacher complexity of \(\mathcal{G}(\theta)\) is no larger than \((16\sqrt{d(\theta)})/\sqrt{n}\) (see Example 6.26). Take \(q(\theta)=1/(\theta+1)^2\). Then we have from Corollary 8.3 that

\[
\mathbb{E}_{\mathcal{D}}\mathbf{1}(f_{\hat{\theta}}(\hat{w},X)\neq Y)\leq\inf_{\theta,w\in\Omega(\theta)}\left[\mathbb{E}_{\mathcal{D}}\mathbf{1}(f_{\theta}(w,X)\neq Y)+\frac{32\sqrt{d(\theta)}}{\sqrt{n}}+\sqrt{\frac{\ln(\theta+1)}{m}}\right]+\tilde{\epsilon}+\epsilon'+\sqrt{\frac{2\ln(4/\delta)}{n}}+\sqrt{\frac{2\ln(4/\delta)}{m}}.
\]

This result shows that the model selection algorithm of (8.2) can automatically balance the model accuracy \(\mathbb{E}_{\mathcal{D}}\mathbf{1}(f_{\theta}(w,X)\neq Y)\) and model dimension \(d(\theta)\). It can adaptively choose the optimal model \(\theta\), up to a penalty of \(O(\sqrt{\ln(\theta+1)/m})\).

While we only considered the selection of discrete models with training data and validation data split, it is also possible to consider continuous models, if the learning algorithm is stable with respect to model hyperparameter \(\theta\). In such a case, we may introduce a notion similar to covering numbers and then discretize the continuous model space accordingly.
