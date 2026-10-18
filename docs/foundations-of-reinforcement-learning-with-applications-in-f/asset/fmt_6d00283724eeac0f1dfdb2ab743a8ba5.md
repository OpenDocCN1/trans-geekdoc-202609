
Note that the Probability Matching method is also based on the principle of `Optimism in the Face of Uncertainty` because an action with more uncertainty in its mean reward is more likely to have the highest mean reward among all actions (all else being equal), and hence deserves to be selected more frequently.

We see that the Probability Matching approach is mathematically disciplined in driving towards cumulative reward maximization while balancing exploration and exploitation. However, the right-hand-side of Equation 15.1 can be difficult to compute analytically from the posterior distributions. We resolve this difficulty with a sampling approach to Probability Matching known as `Thompson Sampling`.

### 15.5.1 Thompson Sampling

We can reformulate the right-hand-side of Equation 15.1 as follows:

$$
\begin{aligned} {{\mathbb{P}}\lbrack A\_{t + 1}|H\_{t}\rbrack} & {= {\mathbb{P}}_{\mathcal{D}\_{t}\sim{\mathbb{P}}\lbrack\mathcal{R}|H\_{t}\rbrack}\lbrack\mathbb{E}_{\mathcal{D}\_{t}}\lbrack r|A\_{t + 1}\rbrack > \mathbb{E}_{\mathcal{D}\_{t}}\lbrack r|a\rbrack\text{for~all~}a \\neq A\_{t + 1}\rbrack} \\\\ & {= \mathbb{E}_{\mathcal{D}\_{t}\sim{\mathbb{P}}\lbrack\mathcal{R}|H\_{t}\rbrack}\lbrack\mathbb{I}\_{A\_{t + 1} = \text{arg}\mspace{2mu}\text{max}\_{a \in \mathcal{A}}\mathbb{E}_{\mathcal{D}\_{t}}\lbrack r|a\rbrack}\rbrack} \\\\ \end{aligned}
$$

where `𝕀` refers to the indicator function. This reformulation in terms of an `Expectation` is convenient because we can estimate the Expectation by sampling various `𝒟[*t*]` probability distributions and for each sample of `𝒟[*t*]`, we simply check if an action has the best mean reward (compared to other actions) under the distribution `𝒟[*t*]`. This sampling-based approach to Probability Matching is known as `Thompson Sampling`. Specifically, Thompson Sampling performs the following calculations for time step `t + 1`:

* Compute the posterior distribution `ℙ[ℛ|H[t]]` by performing Bayesian updates of the hyperparameters that govern the estimated probability distributions of the parameters of the reward distributions for each action.

* `Sample` a joint (across actions) rewards distribution `𝒟[t]` from the posterior distribution `ℙ[ℛ|H[t]]`.

* Calculate a sample Action-Value function with sample `𝒟[t]` as:

    $$
    \begin{array}{r} {{\hat{Q}}\_{t}(a) = \mathbb{E}_{\mathcal{D}\_{t}}\lbrack r|a\rbrack} \\\\ \end{array}
    $$

* Select the action (for time step `t + 1`) that maximizes this sample Action-Value function:

    $$
    \begin{array}{r} {A\_{t + 1} = \text{arg}\,\text{max}\_{a \in \mathcal{A}}{\hat{Q}}\_{t}(a)} \\\\ \end{array}
    $$

It turns out that Thompson Sampling achieves the Lai-Robbins lower bound for Logarithmic Total Regret. To learn more about Thompson Sampling, we refer you to the excellent tutorial on Thompson Sampling by Russo, Roy, Kazerouni, Osband, Wen ([Russo et al. 2018](#bib01.xhtml#refbib_51)).

Now we implement Thompson Sampling by assuming a Gaussian distribution of rewards for each action. The posterior distributions for each action are produced by performing Bayesian updates of the hyperparameters that govern the estimated Gaussian-Inverse-Gamma Probability Distributions of the parameters of the Gaussian reward distributions for each action. [Section G.1](#appG.xhtml#secG_1) of [Appendix G](#appG.xhtml#appG) describes the Bayesian updates of the hyperparameters `θ`, `α`, `β`, and the code below implements this update in the variable `bayes` in method `get_episode_rewards_actions()` (this method implements the `@abstractmethod` interface of abstract base class `MABBase`). The sample mean rewards are obtained by invoking the `sample` method of `Gaussian` and `Gamma` classes, and assigned to the variable `mean_draws`. The variable `theta` refers to the hyperparameter `θ`, the variable `alpha` refers to the hyperparameter `α`, and the variable `beta` refers to the hyperparameter `β`. The rest of the code in the method `get_episode_rewards_actions()` should be self-explanatory.

![](images/comp15_5.jpg)

The above code is in the file `rl/chapter14/ts_gaussian.py`. The code in `__main__` sets up a `ThompsonSamplingGaussian` instance with 6 arms, each having a Gaussian rewards distribution. When run with 1000 time steps and 500 episodes, we get the Total Regret Curve as shown in [Figure 15.5](#chapter15.xhtml#fig15_5).

![Figure 15.5 Thompson Sampling (Gaussian) Total Regret Curve](images/fig15_5.jpg)

[Figure 15.5](#chapter15.xhtml#b15fig15_5) Thompson Sampling (Gaussian) Total Regret Curve

We encourage you to modify the code in `__main__` to try other mean and variance settings for the Gaussian reward distributions of the arms, examine the results obtained, and develop more intuition for Thompson Sampling for Gaussians.

Now we implement Thompson Sampling by assuming a Bernoulli distribution of rewards for each action. The posterior distributions for each action are produced by performing Bayesian updates of the hyperparameters that govern the estimated Beta Probability Distributions of the parameters of the Bernoulli reward distributions for each action. [Section G.2](#appG.xhtml#secG_2) of [Appendix G](#appG.xhtml#appG) describes the Bayesian updates of the hyperparameters `α` and `β`, and the code below implements this update in the variable `bayes` in method `get_episode_rewards_actions()` (this method implements the `@abstractmethod` interface of abstract base class `MABBase`). The sample mean rewards are obtained by invoking the `sample` method of the `Beta` class, and assigned to the variable `mean_draws`. The variable `alpha` refers to the hyperparameter `α` and the variable `beta` refers to the hyperparameter `β`. The rest of the code in the method `get_episode_rewards_actions()` should be self-explanatory.

![](images/comp15_6.jpg)

The above code is in the file `rl/chapter14/ts_bernoulli.py`. The code in `__main__` sets up a `ThompsonSamplingBernoulli` instance with 6 arms, each having a Bernoulli rewards distribution. When run with 1000 time steps and 500 episodes, we get the Total Regret Curve as shown in [Figure 15.6](#chapter15.xhtml#fig15_6).

![Figure 15.6 Thompson Sampling (Bernoulli) Total Regret Curve](images/fig15_6.jpg)

[Figure 15.6](#chapter15.xhtml#b15fig15_6) Thompson Sampling (Bernoulli) Total Regret Curve

We encourage you to modify the code in `__main__` to try other mean settings for the Bernoulli reward distributions of the arms, examine the results obtained, and develop more intuition for Thompson Sampling for Bernoullis.

## 15.6 Gradient Bandits

Now we cover a MAB algorithm that is similar to Policy Gradient for MDPs. This MAB algorithm's action selection is randomized and the action selection probabilities are constructed through Gradient Ascent (much like Stochastic Policy Gradient for MDPs). This MAB Algorithm and its variants are cheekily referred to as `Gradient Bandits`. Our coverage below follows the coverage of Gradient Bandit algorithm in the RL book by Sutton and Barto ([Richard S. Sutton and Barto 2018](#bib01.xhtml#refbib_62)).

The basic idea is that we have `mScore` parameters (to be optimized), one for each action, denoted as `{s[a]|a∈𝒜}` that define the action-selection probabilities, which in turn defines an `Expected Reward` Objective function to be maximized, as follows:

$$
\begin{array}{r} {J(s\_{a\_{1}},\ldots,s\_{a\_{m}}) = {\sum\limits\_{a \in \mathcal{A}}\pi}(a) \cdot \mathbb{E}\lbrack r|a\rbrack} \\\\ \end{array}
$$

where `π`:𝒜→[0,1] refers to the function for action-selection probabilities, that is defined as follows:

$$
\begin{array}{r} {\pi(a) = \frac{e^{s\_{a}}}{\sum\limits\_{b \in \mathcal{A}}e^{s\_{b}}}\text{~for~all~}a \in \mathcal{A}} \\\\ \end{array}
$$
