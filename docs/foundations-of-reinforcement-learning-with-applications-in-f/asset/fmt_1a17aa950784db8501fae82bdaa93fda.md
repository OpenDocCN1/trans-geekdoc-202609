
The `Score` parameters are meant to represent the relative value of actions based on the rewards seen until a certain time step, and are adjusted appropriately after each time step (using Gradient Ascent). Note that `π(⋅)` is a Softmax function of the `Score` parameters.

Gradient Ascent moves the `Score` parameters `s[a]` (and hence, action probabilities `π(a)`) in the direction of the gradient of the objective function `J(s[a[1]], …, s[a[m]])` with respect to `(s[a[1]], …, s[a[m]])`. To construct this gradient of `J(⋅)`, we calculate $\frac{\partial J}{\partial s_{a}}$ for each `a` ∈ 𝒜, as follows:

$$
\begin{aligned}
\frac{\partial J}{\partial s_{a}} & {= \frac{\partial({\sum\limits_{a^{\prime} \in \mathcal{A}}\pi}(a^{\prime}) \cdot \mathbb{E}\lbrack r|a^{\prime}\rbrack)}{\partial s_{a}}} \\
& {= {\sum\limits_{a^{\prime} \in \mathcal{A}}\mathbb{E}}\lbrack r|a^{\prime}\rbrack \cdot \frac{\partial\pi(a^{\prime})}{\partial s_{a}}} \\
& {= {\sum\limits_{a^{\prime} \in \mathcal{A}}\pi}(a^{\prime}) \cdot \mathbb{E}\lbrack r|a^{\prime}\rbrack \cdot \frac{\partial\log\pi(a^{\prime})}{\partial s_{a}}} \\
& {= \mathbb{E}_{a^{\prime}\sim\pi,r\sim\mathcal{R}^{a^{\prime}}}\lbrack r \cdot \frac{\partial\log\pi(a^{\prime})}{\partial s_{a}}\rbrack} \\
\end{aligned}
$$

We know from standard softmax-function calculus that:

$$
\begin{array}{r}
{\frac{\partial\log\pi(a^{\prime})}{\partial s_{a}} = \frac{\partial(\log\frac{e^{s_{a^{\prime}}}}{\sum\limits_{b \in \mathcal{A}}e^{s_{b}}})}{\partial s_{a}} = \mathbb{I}_{a = a^{\prime}} - \pi(a)}
\\
\end{array}
$$

Therefore, $\frac{\partial J}{\partial s_{a}}$ can be re-written as:

$$
\begin{array}{r}
{\frac{\partial J}{\partial s_{a}} = \mathbb{E}_{a^{\prime}\sim\pi,r\sim\mathcal{R}^{a^{\prime}}}\lbrack r \cdot (\mathbb{I}_{a = a^{\prime}} - \pi(a))\rbrack}
\\
\end{array}
$$

At each time step `t`, we approximate the gradient with the `(A[t], R[t])` sample as:

$$
\begin{array}{r}
{R_{t} \cdot (\mathbb{I}_{a = A_{t}} - \pi_{t}(a))\text{~for~all~}a \in \mathcal{A}}
\\
\end{array}
$$

`π[t](a)` is the probability of selecting action `a` at time step `t`, derived from the `Score` `s[t](a)` at time step `t`.

We can reduce the variance of this estimate with a baseline `B` that is independent of `a`, as follows:

$$
\begin{array}{r}
{(R_{t} - B) \cdot (\mathbb{I}_{a = A_{t}} - \pi_{t}(a))\text{~for~all~}a \in \mathcal{A}}
\\
\end{array}
$$

This doesn't introduce any bias in the estimate of the gradient of `J(⋅)` because:

$$
\begin{aligned}
{\mathbb{E}_{a^{\prime}\sim\pi}\lbrack B \cdot (\mathbb{I}_{a = a^{\prime}} - \pi(a))\rbrack} & {= \mathbb{E}_{a^{\prime}\sim\pi}\lbrack B \cdot \frac{\partial\log\pi(a^{\prime})}{\partial s_{a}}\rbrack} \\
& {= B \cdot {\sum\limits_{a^{\prime} \in \mathcal{A}}\pi}(a^{\prime}) \cdot \frac{\partial\log\pi(a^{\prime})}{\partial s_{a}}} \\
& {= B \cdot {\sum\limits_{a^{\prime} \in \mathcal{A}}\frac{\partial\pi(a^{\prime})}{\partial s_{a}}}} \\
& {= B \cdot \frac{\partial({\sum\limits_{a^{\prime} \in \mathcal{A}}\pi}(a^{\prime}))}{\partial s_{a}}} \\
& {= B \cdot \frac{\partial 1}{\partial s_{a}}} \\
& {= 0} \\
\end{aligned}
$$

We can use $B = {\overline{R}}_{t} = \frac{1}{t}{\sum\limits_{s = 1}^{t}R_{s}}$ (average of all rewards obtained until time step `t`). So, the update to scores `s[t](a)` for all `a` ∈ 𝒜 is:

$$
\begin{array}{r}
{s_{t + 1}(a) = s_{t}(a) + \alpha \cdot (R_{t} - {\overline{R}}_{t}) \cdot (\mathbb{I}_{a = A_{t}} - \pi_{t}(a))}
\\
\end{array}
$$

It should be noted that this Gradient Bandit algorithm and its variant Gradient Bandit algorithms are simply a special case of policy gradient-based RL algorithms.

Now let's write some code to implement this Gradient Algorithm. Apart from the usual constructor inputs `arm_distributions`, `time_steps` and `num_episodes` that are passed along to the constructor of the abstract base class `MABBase`, `GradientBandits`' constructor also takes as input `learning_rate` (specifying the initial learning rate) and `learning_rate_decay` (specifying the speed at which the learning rate decays), which influence how the variable `step_size` is set at every time step. The variable `scores` represents `s[t](a)` for all `a` ∈ 𝒜 and the variable `probs` represents `π[t](a)` for all `a` ∈ 𝒜. The rest of the code below should be self-explanatory, based on the above description of the calculations.

![](images/comp15_7.jpg)

The above code is in the file `rl/chapter14/gradient_bandits.py`. The code in `__main__` sets up a `GradientBandits` instance with 6 arms, each having a Gaussian reward distribution. When run with 1000 time steps and 500 episodes, we get the Total Regret Curve as shown in [Figure 15.7](#chapter15.xhtml#fig15_7).

![Figure 15.7 Gradient Algorithm Total Regret Curve](images/fig15_7.jpg)

[Figure 15.7](#chapter15.xhtml#b15fig15_7) Gradient Algorithm Total Regret Curve

We encourage you to modify the code in `__main__` to try other mean and standard deviation settings for the Gaussian reward distributions of the arms, examine the results obtained, and develop more intuition for this Gradient Algorithm.

## 15.7 Horse Race

We've implemented several algorithms for the MAB problem. Now it's time for a competition between them, that we will call a `Horse Race`. In this Horse Race, we will compare the `Total Regret` across the algorithms, and we will also examine the number of times the different arms get pulled by the various algorithms. We expect a good algorithm to have small total regret and we expect a good algorithm to pull the arms with high `Gap`s few number of times and pull the arms with low (and zero) gaps large number of times.

The code in the file `rl/chapter14/plot_mab_graphs.py` has a function to run a horse race for Gaussian arms with the following algorithms:

* Greedy with Optimistic Initialization
* `ϵ`-Greedy
* Decaying `ϵ[t]`-Greedy
* Thompson Sampling
* Gradient Bandit

Running this horse race for 7 Gaussian arms with 500 time steps, 500 episodes and the settings as specified in the file `rl/chapter14/plot_mab_graphs.py`, we obtain [Figure 15.8](#chapter15.xhtml#fig15_8) for the Total Regret Curves for each of these algorithms.

![Figure 15.8 Gaussian Horse Race—Total Regret Curves](images/fig15_8.jpg)

[Figure 15.8](#chapter15.xhtml#b15fig15_8) Gaussian Horse Race—Total Regret Curves

[Figure 15.9](#chapter15.xhtml#fig15_9) shows the number of times each arm is pulled (for each of these algorithms). The X-axis is sorted by the mean of the reward distributions of the arms. For each arm, the left-to-right order of the arm-pulls count is the order in which the 5 MAB algorithms are listed above. As we can see, the arms with low means are pulled only a few times and the arms with high means are pulled often.

![Figure 15.9 Gaussian Horse Race—Arms Count](images/fig15_9.jpg)

[Figure 15.9](#chapter15.xhtml#b15fig15_9) Gaussian Horse Race—Arms Count

The file `rl/chapter14/plot_mab_graphs.py` also has a function to run a horse race for Bernoulli arms with the following algorithms:

* Greedy with Optimistic Initialization
* `ϵ`-Greedy
* Decaying `ϵ[t]`-Greedy
* UCB1
* Thompson Sampling
* Gradient Bandit

Running this horse race for 9 Bernoulli arms with 500 time steps, 500 episodes and the settings as specified in the file `rl/chapter14/plot_mab_graphs.py`, we obtain [Figure 15.10](#chapter15.xhtml#fig15_10) for the Total Regret Curves for each of these algorithms.

![Figure 15.10 Bernoulli Horse Race—Total Regret Curves](images/fig15_10.jpg)

[Figure 15.10](#chapter15.xhtml#b15fig15_10) Bernoulli Horse Race—Total Regret Curves
