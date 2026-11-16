several ensemble algorithms to determine the actions or action probabilities.
In supervised learning, ensemble algorithms such as bagging, boosting, and
mixtures of experts [13] are often used for learning and combining multiple
classifiers. But in RL, ensemble algorithms are used for representing and
learning the value function.

Based on an agent integrated with multiple reinforcement learning
algorithms, multiple value functions are learned at the same time. The
ensembles combine the policies derived from the value functions in a final
policy for the agent. The majority voting (MV), the rank voting (RV), the
Boltzmann multiplication (BM), and the Boltzmann addition (BA) are
used to combine RL algorithms. While these methods are costly in deep
reinforcement learning (DRL) algorithms, we combine different DRL
algorithms that learn separate value functions and policies. Therefore in our
ensemble approaches we combine the different policies derived from the
update targets learned by deep Q-networks, deep Sarsa networks, double
deep Q-networks, and other DRL algorithms. As a consequence, this leads
to reduced overestimations, more stable learning process, and improved
performance.

# RELATED WORK

# Reinforcement Learning

Reinforcement learning is a machine learning method that allows the system
to interact and learn from the environment to maximize cumulative return
rewards. Assume that the standard reinforcement learning setting where an agent
interacts with the environment E. We can describe this process with Markov
Decision Processes (MDP) [2, 9]. It can be specified as a tuple (S, A, π, R, γ). At
each step t, the agent receives a state s, and select an action aₜ from the set of legal
actions A according to the policy π, where π is a policy mapping sequences to
actions. The action is passed to the environment E. In addition, the agent receives
the next state sₜ₊₁ and a reward signal rₜ. This process continues until the agent
reaches a terminal state. The agent seeks to maximize the expected discounted
return, where we define the future discounted return at time t as Rₜ = Σₖ₌₀^∞ γᵏ rₜ₊ₖ
with discount factor γ ∈ (0, 1]. The goal of the RL agent is to learn a policy which
makes the future discounted return maximize. For an agent behaving according
to a stochastic policy π, the value of the state action pair can be defined as
follows: Q^π(s,a) = E[Rₜ | sₜ = s, aₜ = a, π]. Te optimal action-value function