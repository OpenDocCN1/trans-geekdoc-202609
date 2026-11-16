On-policy methods evaluate or improve the behaviour policy, e.g., SARSA fits the action-value function to the current policy, i.e., SARSA evaluates the policy based on samples from the same policy, then refines the policy greedily with respect to action values. In off-policy methods, an agent learns an optimal value function/policy, maybe following an unrelated behaviour policy. For instance, Q-learning attempts to find action values for the optimal policy directly, not necessarily fitting to the policy generating the data, i.e., the policy Q-learning obtains is usually different from the policy that generates the samples. The notion of on-policy and off-policy can be understood as same-policy and different-policy.

The exploration vs exploitation dilemma is about the agent needs to exploit the currently best action to maximize rewards greedily, yet it has to explore the environment to find better actions, when the policy is not optimal yet, or the system is non-stationary.

In model-free methods, the agent learns with trail-and-error from experience directly; the model, i.e., for state transition and reward, is not known. RL methods that use models are model-based methods; the model may be given, e.g. in the game of computer Go, or learned from experience.

In an online mode, training algorithms are executed on data acquired in sequence. In an offline mode, or a batch mode, models are trained on the entire data set.

With bootstrapping, an estimate of state or action value is updated from subsequent estimates.

# 2.4.1 PROBLEM SETUP

An RL agent interacts with an environment over time. At each time step t, the agent receives a state s_t in a state space S, and selects an action a_t from an action space A, following a policy π(a_t|s_t), which is the agent's behavior, i.e., a mapping from state s_t to actions a_t. The agent receives a scalar reward r_t, and transitions to the next state s_t+1, according to the environment dynamics, or model, for reward function R(s, a), and, state transition probability P(s_t+1|s_t, a_t), respectively. In an episodic problem, this process continues until the agent reaches a terminal state and then it restarts. The return is the discounted, accumulated reward with the discount factor γ ∈ (0, 1],

R_t = ∑_{k=0}^{∞} γ^k r_{t+k}. (4)

The agent aims to maximize the expectation of such long term return from each state. The problem is set up in discrete state and action spaces. It is not hard to extend it to continuous spaces. In partially observable environments, an agent can not observe states fully, but has observations.

When an RL problem satisfies the Markov property, i.e., the future depends only on the current state and action, but not on the past, it is formulated as a Markov decision process (MDP), defined by the 5-tuple (S, A, P, R, γ). When the system model is available, we use dynamic programming methods: policy evaluation to calculate value/action value function for a policy, value iteration and policy iteration for finding an optimal policy. When there is no model, we resort to RL methods. RL methods also work when the model is available. An RL environment can be a multi-armed bandit, an MDP, a partially observable MDP (POMDP), a game, etc.

# 2.4.2 VALUE FUNCTION

A value function is a prediction of the expected, accumulative, discounted, future reward, measuring how good each state, or state-action pair, is. The state value,

v_π(s) = E[R_t | s_t = s], where, R_t = ∑_{k=0}^{∞} γ^k r_{t+k}, (5)

is the expected return for following policy π from state s. The action value,

q_π(s, a) = E[R_t | s_t = s, a_t = a], (6)

is the expected return for selecting action a in state s and then following policy π. Value function v_π(s) decomposes into the Bellman equation:

v_π(s) = ∑_a π(a|s) ∑_{s',r} p(s', r | s, a) [r + γ v_π(s')]. (7)