# # Chapter 6 : Part 2
Reinforcement Learning
Thompson Sampling

# ## 6.2.1 Thompson Sampling

We're going to be using this algorithm to solve the *Multi Armed Bandit Problem.*

+   - **Multi Bandit Problem**: We have several slot machines each of them has a distribution behind it. We don't know what these distributions are and we need to start playing these machines and at the same time figure out which one has the best distribution.

So we have to find that **ideal balance** or tradeoff between *exploration* and *exploitation*

![](bbox=[0.585, 0.135, 0.905, 0.295])

Multi arm Bandit Problem Assumptions

+   [1] We have *d* arms. For example, arms *Ad*: $ad_1, ad_2, \dots, ad_d$ that we display to users each time we connect to a **web page**.
[2] Each time a user connects to us, it makes a **round**.
[3] At each round *n*, we choose *one* *ad* to display to the user.
[4] At each round *n*, we give $r_n(n)$ defined as:
$$r_n(n) \in \{0, 1\} : r_n(n) = egin{cases} 1 & 	ext{if the user clicked on the ad} \ 0 & 	ext{if the user didn't click} \end{cases}$$n[5] Our goal is to maximize the total reward we get over many rounds.

# ## Bayesian Inference

+   - Ad *i* gets *y* from Bernoulli distribution $p(y|	heta_i) \sim B(	heta_i)$.
- $	heta_i$ is unknown but we set its uncertainty by assuming it has a uniform distribution $p(	heta_i) \sim \mathcal{U}([0,1])$, which is the prior distribution.
- Bayes Rules: we approach $	heta_i$ by the posterior distribution

> $$\frac{p(	heta_i|y)p(	heta_i)}{\int p(y|	heta_i)p(	heta_i)d	heta_i} \propto \frac{p(y|	heta_i)}{	ext{likelihood function}} 	imes p(	heta_i) 	ext{prior distribution}$$

+   - We get $p(	heta_i|y) \sim eta(	ext{number of successes} +1, 	ext{number of failures} +1)$
- At each round *n* we take a random draw $	heta(n)$ from this posterior distribution $p(	heta_i|y)$, for each *ad*.
- At each round *n* we select the *ad* that has the highest $	heta_i(n)$.

![](bbox=[0.175, 0.765, 0.825, 0.925])

So we've got a scale. For simplicity we consider *3 bandits*. *Vertical* line represents the *expected value* and *horizontal* line represents *return*.