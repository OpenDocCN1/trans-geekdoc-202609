equally well (e.g. by using nonlinear G-optimal design). It is similar to pure exploration in contextual bandit of Section 17.5, which also employs nonlinear G-optimal design. Nevertheless, the algorithm can solve the low-Bellman-rank MDP problem with a nonlinear Q-function class, and without knowing the underlying Bellman factorization. If we consider linear MDP with d-dimensional unknown feature maps, and assume that we have finite K actions, with F containing M_F members and G containing M_G members, then \tilde d = \tilde O(HdK), \beta_t^2 = \tilde O(ln(M_F M_G)). Therefore the regret of \pi_t return by Algorithm 18.3 satisfies

\mathbb{E}[V_*^1(x_1^1) - V_{\pi_t}^1(x_1^1)] = \tilde O\left( H\sqrt{dK\ln(M_\mathcal{F}M_\mathcal{G})}\right).

Compared to that of Theorem 18.21, this result is worse by a factor of \sqrt{HK}. The \sqrt{H} factor is due to the random h_t choice, which does not efficiently use all data in a trajectory. The \sqrt{K} factor is due to pure exploration with a nonlinear Q-function class without knowing the feature maps of the underlying Bellman factorization.

# 18.5 Model-Based Reinforcement Learning

In linear MDP, the version space UCB algorithm does not need to know or to learn the transition probability P^h(x^{h+1}|x^h,a^h). Such an algorithm is referred to as model free in reinforcement learning. On the other hand, if the learning algorithm estimates and employs the transition probability P^h(x^{h+1}|x^h,a^h) information, then the corresponding method is referred to as model based. Instead of looking at Q-function class, in model-based RL, we consider a class of MDP models and explicitly estimate the transition probabilities.

# Definition 18.35

In a model-based RL problem, we are given an MDP model class \mathcal{M}. Each M \in \mathcal{M} includes explicit transition probability

P_M^h(x^{h+1}|x^h,a^h),

and expected reward

R_M^h(x^h,a^h) = \mathbb{E}_M[r^h|x^h,a^h].

We use \mathbb{E}_M[\cdot] to denote the expectation with respect to model M's transition dynamics P_M. Given any f^{h+1} on \mathcal{X}, we define the model Bellman operator

(\mathcal{T}_M^h f)(x^h,a^h) = R_M^h(x^h,a^h) + \mathbb{E}_M[f^{h+1}(x^{h+1})|x^h,a^h].

We use f_M = \{f_M^h(x^h,a^h)\}_{h=1}^H to denote the Q function of model M, and use \pi_M = \pi_{f_M} to denote the corresponding optimal policy under model M.

We will also impose the following assumption for model-based RL.

# Assumption 18.36

Let \mathcal{M} be a class of MDP models. We assume that the correct model M_* \in \mathcal{M}: the true transition probability is given by P_{M_*}^h(x^{h+1}|x^h,a^h), and the true expected reward is given by