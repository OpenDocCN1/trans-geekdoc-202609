
![Figure 19.3 Markov decision process. a) The agent (penguin) can perform one of a set of actions in each state. The action influences both the probability of moving to the successor state and the probability of receiving rewards. b) Here, the four actions correspond to moving up, right, down, and left. c) For any state (here, state 6), the action changes the probability of moving to the next state. The penguin moves in the intended direction with 50% probability, but the ice is slippery, so it may slide to one of the other adjacent positions with equal probability. Accordingly, in panel (a), the action taken (gray arrows) doesn't always line up with the trajectory (orange line). Here, the action does not affect the reward, so Pr(rt+1|st, at) = Pr(rt+1|st). The trajectory τ from an MDP consists of a sequence s1, a1, r2, s2, a2, r3, s3, a3, r4 … of alternating states st, actions at, and rewards, rt+1. Note that here the penguin receives the reward when it leaves a state with a fish (i.e., the reward is received for passing through the fish square, regardless of whether the penguin arrived there intentionally or not).](images/c19-fig-0003.jpg)

[Figure 19.3](#c019.xhtml#c19-fig-0003a) Markov decision process. a) The agent (penguin) can perform one of a set of actions in each state. The action influences both the probability of moving to the successor state and the probability of receiving rewards. b) Here, the four actions correspond to moving up, right, down, and left. c) For any state (here, state 6), the action changes the probability of moving to the next state. The penguin moves in the intended direction with 50% probability, but the ice is slippery, so it may slide to one of the other adjacent positions with equal probability. Accordingly, in panel (a), the action taken (gray arrows) doesn't always line up with the trajectory (orange line). Here, the action does not affect the reward, so `Pr(r[t+1]|s[t], a[t]) = Pr(r[t+1]|s[t])`. The trajectory `τ` from an MDP consists of a sequence `s[1], a[1], r[2], s[2], a[2], r[3], s[3], a[3], r[4] …` of alternating states `s[t]`, actions `a[t]`, and rewards, `r[t+1]`. Note that here the penguin receives the reward when it *leaves* a state with a fish (i.e., the reward is received for passing through the fish square, regardless of whether the penguin arrived there intentionally or not).

### 19.1.4 Partially observable Markov decision process

In a *partially observable Markov decision process* or *POMDP*, the state is not directly visible ([figure 19.4](#c019.xhtml#c19-fig-0004)). Instead, the agent receives an observation `o[t]` drawn from `Pr(o[t]|s[t])`. Hence, a POMDP generates a sequence `s[1], o[1], a[1], r[2], s[2], o[2], a[2], r[3], o[3], a[3], s[3], r[4], …` of states, observations, actions, and rewards. In general, each observation will be more compatible with some states than others but insufficient to identify the state uniquely.

![Figure 19.4 Partially observable Markov decision process (POMDP). In a POMDP, the agent does not have access to the entire state. Here, the penguin is in state three and can only see the region in the dashed box. This is indistinguishable from what it would see in state nine. In the first case, moving right leads to the hole in the ice (with -2 reward) and, in the latter, to the fish (with +3 reward).](images/c19-fig-0004.jpg)

[Figure 19.4](#c019.xhtml#c19-fig-0004a) Partially observable Markov decision process (POMDP). In a POMDP, the agent does not have access to the entire state. Here, the penguin is in state three and can only see the region in the dashed box. This is indistinguishable from what it would see in state nine. In the first case, moving right leads to the hole in the ice (with -2 reward) and, in the latter, to the fish (with +3 reward).

### 19.1.5 Policy

The rules that determine the agent's action for each state are known as the *policy* ([figure 19.5](#c019.xhtml#c19-fig-0005)). This may be stochastic (the policy defines a distribution over actions for each state) or deterministic (the agent always takes the same action in a given state). A stochastic policy `π[a|s]` returns a probability distribution over each possible action `a` for state `s`, from which a new action is sampled. A deterministic policy `π[a|s]` returns one for the action `a` that is chosen for state `s` and zero otherwise. A *stationary* policy depends only on the current state. A *non-stationary* policy also depends on the time step.

![Figure 19.5 Policies. a) A deterministic policy always chooses the same action in each state (indicated by arrow). Some policies are better than others. This policy is not optimal but still generally steers the penguin from top-left to bottom-right where the reward lies. b) This policy is more random. c) A stochastic policy has a probability distribution over actions for each state (probability indicated by size of arrows). This has the advantage that the agent explores the states more thoroughly and can be necessary for optimal performance in partially observable Markov decision processes.](images/c19-fig-0005.jpg)

[Figure 19.5](#c019.xhtml#c19-fig-0005a) Policies. a) A deterministic policy always chooses the same action in each state (indicated by arrow). Some policies are better than others. This policy is not optimal but still generally steers the penguin from top-left to bottom-right where the reward lies. b) This policy is more random. c) A stochastic policy has a probability distribution over actions for each state (probability indicated by size of arrows). This has the advantage that the agent explores the states more thoroughly and can be necessary for optimal performance in partially observable Markov decision processes.

The environment and the agent form a loop ([figure 19.6](#c019.xhtml#c19-fig-0006)). The agent receives the state `s[t]` and reward `r[t]` from the last time step. Based on this, it can modify the policy `π[a[t]|s[t]]` if desired and choose the next action `a[t]`. The environment then assigns the next state according to `Pr(s[t+1]|s[t], a[t])` and the reward according to `Pr(r[t+1]|s[t], a[t])`.

***

Notebook 19.1

Markov decision processes

***

![Figure 19.6 Reinforcement learning loop. The agent takes an action at at time t based on the state st, according to the policy π\[at|st\]. This triggers the generation of a new state st+1 (via the state transition function) and a reward rt+1 (via the reward function). Both are passed back to the agent, which then chooses a new action.](images/c19-fig-0006.jpg)

[Figure 19.6](#c019.xhtml#c19-fig-0006a) Reinforcement learning loop. The agent takes an action `a[t]` at time `t` based on the state `s[t]`, according to the policy `π[a[t]|s[t]]`. This triggers the generation of a new state `s[t+1]` (via the state transition function) and a reward `r[t+1]` (via the reward function). Both are passed back to the agent, which then chooses a new action.

## 19.2 Expected return

The previous section introduced the Markov decision process and the idea of an agent carrying out actions according to a policy. We want to choose a policy that maximizes the expected return. In this section, we make this idea mathematically precise. To do that, we assign a *value* to each state `s[t]` and state-action pair `{s[t], a[t]}`.

### 19.2.1 State and action values

The return `G[t]` depends on the state `s[t]` and the policy `π[a|s]`. From this state, the agent will pass through a sequence of states, taking actions and receiving rewards. This sequence differs every time the agent starts in the same place since, in general, the policy `π[a[t]|s[t]]`, the state transitions `Pr(s[t+1]|s[t], a[t])`, and the rewards issued `Pr(r[t+1]|s[t], a[t])` are all stochastic.
