we present the adversarial attacks on DRL and how to defend against DRL system attacks through providing robust DRL systems.

Section 6.2 covers four essential topics to introduce DRL: Markov decision process (MDP), value-based methods, policy-based methods, and actor-critic methods [1].

# ### 6.2.1 Markov Decision Process

MDP is critical to RL and DRL, a framework that solves most RL problems with discrete or continuous actions. If you frame your task in an MDP, you define your environment, where an agent achieves optimal policy by learning moves to obtain maximum rewards over a series of time steps (see Figure 6.1).

![](bbox=[0.116, 0.402, 0.87, 0.537])

**FIGURE 6.1** Markov decision process where an agent interacts with the environment to obtain a maximal reward for each step with optimal policy function π.

MDP aims to train an agent to find an optimal policy that will return a maximum cumulative reward by taking a series of actions for each step with a set of states created from observations in an environment.

An MDP is a 5-tuple $(S, A, P, R, \gamma)$, where

+   - $S$ is a set of state space;
+   - $A$ is a set of action space;
+   - $P$ is the transition probability that takes action $a$ in state $s$ at the time $t$ that will lead to state $s'$ at the time $t+1$;
+   - $R$ is the immediate reward $R$ received after taking action $a$ with the state transition from a state $s$ to a state $s'$;
+   - $\gamma$ is a discount factor for a discounted reward.