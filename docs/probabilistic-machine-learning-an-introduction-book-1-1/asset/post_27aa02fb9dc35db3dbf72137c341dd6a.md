
We can think of this setup in terms of an agent at a casino who is faced with multiple slot machines, each of which pays out rewards at a different rate. A slot machine is sometimes called a **one-armed bandit**, so a set of such machines is called a **multi-armed bandit (MAB)**; each different action corresponds to pulling the arm of a different slot machine, but there is just one fixed state (namely being in a given casino). The goal is to quickly figure out which machine pays out the most money, and then to keep playing that one until you become as rich as possible.

## 8.3.1 Contextual bandits

In the basic bandit problem, the state of nature $s_t$ is fixed, meaning that the world does not change. However, the agent's internal model of the world does change, as it learns about which actions have highest reward. If we allow the state of the environment $s_t$ to vary randomly over time, the model is known as a **contextual bandit**, which is a more flexible model.

For example, consider an **online advertising system**. We can regard the page that the user is currently looking at as the state $s_t$, and the ad which we choose to show as the action $a_t$. Since the reward function has the form $R(s_t, a_t)$, we can see that the value of an ad $a_t$ depends on the context $s_t$. The goal is to maximize the expected reward, which is equivalent to the expected number of times people click on ads; this is known as the **click through rate** or **CTR**. (See e.g., [Gra+10; Li+10; McM+13; Aga+14] for more information about this application.)

Another application of contextual bandits arises in **clinical trials** [VBW15]. In this case, the state $s_t$ are features of the current patient we are treating, and the action $a_t$ is the treatment we choose to give them (e.g., a new drug or a **placebo**). Our goal is to maximize expected reward, i.e., the expected number of people who get cured. (In fact, the goal is often stated in terms of determining which treatment is best, rather than maximizing expected reward; this variant is known as **best-arm identification** [ABM10].)

So far we have assumed the state and reward are sampled from fixed distributions, $s_t \sim p(s_t)$ and $r_t \sim p(r|s_t, a_t)$. This is known as a **stochastic bandit**. It is also possible to allow the reward, and possibly the state, to be chosen in an adversarial manner, where nature tries to minimize the reward of the agent. This is known as an **adversarial bandit**. However, we do not consider this version in this book.

## 8.3.2 Markov decision processes

We can consider a generalization of the contextual bandit model, in which the next state $s_{t+1}$ depends on $s_t$ and the agent's action $a_t$; this is called a **Markov decision process** or **MDP**. This defines a **controlled Markov chain**,

$$p(s_{0:T}|a_{0:T-1}) = p(s_0) \prod_{t=1}^T p(s_t|s_{t-1}, a_{t-1}) \tag{8.62}$$

where $p(s_t|s_{t-1}, a_{t-1})$ is known as the **state transition model**. A further generalization of this assumes that the agent does not see the world state $s_t$ directly, but instead only sees a potentially noisy observation generated from the hidden state, $y_t \sim p(\cdot|s_t, a_t)$; this is called a **partially observable Markov decision process** or **POMDP** (pronounced “pom-dee-pee”). Now the agent's policy is a mapping from all the available data to actions, $a_t \sim \pi(\mathcal{D}_t)$, where $\mathcal{D}_t = (x_0, a_0, r_0, x_1, a_1, r_1, \dots, x_t)$.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_281_0.png)

*Figure 8.6: Illustration of a partially observable Markov decision process (POMDP) with hidden environment state s_t which generates the observation x_t, controlled by an agent with internal belief state b_t which generates the action a_t. The reward r_t depends on s_t and a_t. Nodes in this graph represent random variables (circles) and decision variables (squares).*

See Fig. 8.6 for an illustration. (MDPs are a special case where x_t = s_t.) Finding optimal policies for MDPs and POMDPs is studied in the field of reinforcement learning.

For more details on MDPs and POMDPs, see e.g., [Koc15]. For more details on RL, see other books such as [Sze10; SB18; Ber19] or the sequel to this book, [Mur22].

## 8.3.3 Exploration-exploitation tradeoff

The fundamental difficulty in solving bandit problems is known as the exploration-exploitation tradeoff. This refers to the fact that the agent needs to try new state/action combinations (this is known as exploration) in order to learn the reward function R(s, a) before it can exploit its knowledge by picking the predicted best action for each state.

One of the simplest approaches to this problem is to use a two-stage strategy. In the first stage, the agent explores, by trying many different actions, and then computes an estimate of the reward function, \hat{R}(s, a). It stops exploring once it is sufficiently confident in all its estimates (as measured by the posterior variance, for example). In the second stage, it exploits its knowledge using the greedy policy π(s) = argmax_a \hat{R}(s, a). (This is similar to the A/B testing method in Sec. 8.2.) However, we can often do better by interleaving exploration and exploitation. We discuss various methods for this below.

## 8.3.4 Optimal solution

In this section, we discuss the optimal solution to the exploration-exploitation tradeoff. We start with a simple example, namely the context-free Bernoulli bandit, where p_R(r|a) = Ber(r|μ_a), and μ_a = p_R(r = 1|a) = R(a) is the expected reward for taking action a. Let the estimated reward function have the form \hat{R}(a; θ) = θ_a, which (in the context-free case) is just a lookup table. The MLE estimate for the reward function at time t, based on the history of observations,

$\mathbf{h}_t=\{s_{1:t-1},a_{1:t-1},r_{1:t-1}\}$, is given by

$$\hat{\theta}_t(a)=\frac{N_{t,1}(a)}{\max\{N_t(a),1\}}$$

$$N_{t,r}(a)=\sum_{\tau=1}^{t-1}\mathbb{I}(r_\tau=r)\,\mathbb{I}(a_\tau=a)$$

$$N_t(a)=N_{t,0}(a)+N_{t,1}(a)=\sum_{\tau=1}^{t-1}\mathbb{I}(a_\tau=a)$$

Thus $\hat{\theta}_t(a)$ is just the fraction of times we received a reward of 1 when taking action $a$.

In order to decide when to stop exploring and start exploiting, we need some notion of confidence in this estimate. The natural approach is to compute the posterior $p(\theta\mid\mathcal{D}_t)$. If we use a factored beta prior, $p(\theta)=\prod_a \operatorname{Beta}(\theta_a\mid\alpha,\beta)$, then we can compute the posterior in closed form, as we discuss in Sec. [7.2.1](#). In particular, we find

$$p(\theta\mid\mathcal{D}_t)=\prod_a \operatorname{Beta}(\theta_a\mid\alpha+N_{t,1}(a),\beta+N_{t,0}(a))$$

We can use a similar method for a **Gaussian bandit**, where $p_R(r\mid a)=\mathcal{N}(r\mid\mu_a,\sigma_a^2)$, using results from Sec. [7.2.3](#).

In the case of contextual bandits, the problem becomes slightly more complicated. If we assume a conditional Gaussian bandit with a linear reward function, $\mathbb{E}[R\mid s,a;\theta]=\phi(s,a)^\mathsf{T}\theta$, we can use Bayesian linear regression to compute $p(\theta\mid\mathcal{D}_t)$ in closed form, as we discuss in Sec. [11.6](#). If we assume a conditional Bernoulli bandit with a linear-logistic reward function, $\mathbb{E}[R\mid s,a;\theta]=\sigma(\phi(s,a)^\mathsf{T}\theta)$, we can use Bayesian logistic regression to compute $p(\theta\mid\mathcal{D}_t)$, as we discuss in Sec. [10.6](#); however, this posterior cannot be computed in closed form, so we must use approximate inference methods. We can also use nonlinear models, although posterior inference becomes more challenging. Details can be found in the sequel to this book, [Mur22].

In general, let us denote the posterior over the parameters of the reward function by $\mathbf{b}_t=p(\theta\mid\mathbf{h}_t)$; this is known as the **belief state** or **information state**. It is a finite sufficient statistic for the history $\mathbf{h}_t$.

It can be verified that the information state can be updated deterministically using Bayes’ rule (see Fig. [8.7](#) for a visualization). An MDP is thus induced, where the state space consists of the real-valued vectors $\mathbf{b}_t$, and the transition and reward models are given by

$$p(\mathbf{b}_t\mid\mathbf{b}_{t-1},a_t,r_t)=\mathbb{I}\bigl(\mathbf{b}_t=\operatorname{BayesRule}(\mathbf{b}_{t-1},a_t,r_t)\bigr)$$

$$p(R\mid\mathbf{b}_t,a_t=a)=\int p_R(R\mid\mu_a)p(\mu_a\mid\mathbf{b}_t)\,d\mu_a$$

This MDP is called the **belief-state MDP**. Since the transition model and reward model are known, we can solve for the optimal MDP policy using dynamic programming. The resulting optimal policy can be represented as a tabular decision tree, similar to Fig. [8.7](#); this is known as **Gittins index** [Git89].

Unfortunately, computing the optimal policy for contextual bandits (and MDPs) is much more difficult, so we will need to use other methods. We discuss several options below.
