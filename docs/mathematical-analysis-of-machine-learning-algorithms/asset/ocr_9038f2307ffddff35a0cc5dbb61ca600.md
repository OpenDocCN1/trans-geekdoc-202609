# Contextual Bandits

In the standard multiarmed bandit problem, one observes a fixed number of arms. To achieve optimal regret bounds, one estimates confidence intervals of the arms by counting. In the contextual bandit problem, one observes side information for each arm, which can be used as features for more accurate confidence interval estimation.

**Definition 17.1 (Contextual Bandit Problem)** In contextual bandits, we consider a context space $\mathcal{X}$ and an action space $\mathcal{A}$. Given context $x \in \mathcal{X}$, we take an action $a \in \mathcal{A}$, and observe a reward $r \in \mathbb{R}$ that can depend on $(x,a)$. The contextual bandit problem is a repeated game: at each time step $t$:

+   - The player observes a sample $x_t \in \mathcal{X}$.
+   - The player chooses precisely one action (or arm) $a_t \in \mathcal{A}$.
+   - The reward $r_t$ is revealed.

Note that in this chapter, we will follow the convention in the bandit literature of using $\mathcal{A}$ to denote the action space instead of the learning algorithm. We may also introduce the notation of *policy* for contextual bandits. Using the notation of Section 13.4, a bandit learning algorithm returns a policy $\hat{q}(\mathcal{S}_{t-1})$ based on the history $\mathcal{S}_{t-1}$.

**Definition 17.2** A policy $\pi$ for a contextual bandit is a map $\mathcal{X} \to \Delta(\mathcal{A})$, where $\Delta(\mathcal{A})$ denotes probability measures over $\mathcal{A}$ with an appropriately defined $\sigma$-algebra. One may also write it as a conditional distribution $\pi(a|x)$, and the policy draws $a \sim \pi(\cdot|x)$ when it observes context $x$. A contextual bandit algorithm $\hat{q}$ maps historic observations

$$\mathcal{S}_{t-1} = \{(x_1,a_1,r_1),\dots,(x_{t-1},a_{t-1},r_{t-1})\}$$

to a policy $\pi_t = \hat{q}(\cdot|\mathcal{S}_{t-1})$ at each time step $t$, and pulls an arm $a_t \sim \pi_t(\cdot|x_t)$ based on the observation $x_t$. In this chapter, we will also write the history-dependent policy as $a_t \sim \hat{q}(a_t|x_t,\mathcal{S}_{t-1})$.

The contextual bandit problem includes the multiarmed bandit problem as a special case if we take $x = x_0$ to be a fixed context for all time steps.

Similar to the case of multiarmed bandit problem, we may also consider the adversarial setting with an oblivious adversary as follows. At each time step $t$, we