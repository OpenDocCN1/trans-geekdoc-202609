
Substitute the definitions from equation 18.27 into this expression and show that the only term that depends on the parameters `ϕ` is the first term from equation 18.28.

### Problem 18.9

If `c18-fig-5071.jpg`, then show that:

`c18-fig-5072.jpg`

 (18.48)

### Problem 18.10

If `c18-fig-5073.jpg`, then show that:

`c18-fig-5074.jpg`

 (18.49)

### Problem 18.11

Prove equation 18.37.

### Problem 18.12

Classifier-free guidance allows us to create more stereotyped “canonical” images of a given class. When we described transformer decoders, generative adversarial networks, and the GLOW algorithm, we also discussed methods to reduce the amount of variation and produce more stereotyped outputs. What were these? Do you think it's inevitable that we should limit the output of generative models in this way?

# Chapter 19

Reinforcement learning

Reinforcement learning (RL) is a sequential decision-making framework in which agents learn to perform actions in an environment with the goal of maximizing received rewards. For example, an RL algorithm might control the moves (actions) of a character (the agent) in a video game (the environment), aiming to maximize the score (the reward). In robotics, an RL algorithm might control the movements (actions) of a robot (the agent) in the world (the environment) to perform a task (earning a reward). In finance, an RL algorithm might control a virtual trader (the agent) who buys or sells assets (the actions) on a trading platform (the environment) to maximize profit (the reward).

Consider learning to play chess. Here, there is a reward of +1, −1, or 0 at the end of the game if the agent wins, loses, or draws and 0 at every other time step. This illustrates the challenges of RL. First, the reward is sparse; here, we must play an entire game to receive feedback. Second, the reward is temporally offset from the action that caused it; a decisive advantage might be gained thirty moves before victory. We must associate the reward with this critical action. This is termed the `temporal credit assignment problem`. Third, the environment is stochastic; the opponent doesn't always make the same move in the same situation, so it's hard to know if an action was truly good or just lucky. Finally, the agent must balance exploring the environment (e.g., trying new opening moves) with exploiting what it already knows (e.g., sticking to a previously successful opening). This is termed the `exploration-exploitation trade-off`.

Reinforcement learning is an overarching framework that does not necessarily require deep learning. However, in practice, state-of-the-art systems often use deep networks. They encode the environment (the video game display, robot sensors, financial time series, or chessboard) and map this directly or indirectly to the next action (figure 1.13).

## 19.1 Markov decision processes, returns, and policies

Reinforcement learning maps observations of an environment to actions, aiming to maximize a numerical quantity that is connected to the rewards received. In the most common case, we learn a `policy` that maximizes the expected `return` in a `Markov decision process`. This section explains these terms.

### 19.1.1 Markov process

A `Markov process` assumes that the world is always in one of a set of possible states. The word *Markov* implies that the probability of being in a state depends only on the previous state and not on the states before. The changes between states are captured by the `transition probabilities Pr(s[t+1]|s[t])` of moving to the next state `s[t+1]` given the current state `s[t]`, where `t` indexes the time step. Hence, a Markov process is an evolving system that produces a sequence `s[1], s[2], s[3] …` of states (figure 19.1).

![Figure 19.1 Markov process. A Markov process consists of a set of states and transition probabilities Pr(st+1|st) that define the probability of moving to state st+1 given the current state is st. a) The penguin can visit 16 different positions (states) on the ice. b) The ice is slippery, so at each time, it has an equal probability of moving to any adjacent state. For example, in position 6, it has a 25% chance of moving to states 2, 5, 7, and 10. A trajectory τ = [s1, s2, s3, …] from this process consists of a sequence of states.](images/c19-fig-0001.jpg)

**Figure 19.1** Markov process. A Markov process consists of a set of states and transition probabilities `Pr(s[t+1]|s[t])` that define the probability of moving to state `s[t+1]` given the current state is `s[t]`. a) The penguin can visit 16 different positions (states) on the ice. b) The ice is slippery, so at each time, it has an equal probability of moving to any adjacent state. For example, in position 6, it has a 25% chance of moving to states 2, 5, 7, and 10. A trajectory `τ = [s1, s2, s3, …]` from this process consists of a sequence of states.

### 19.1.2 Markov reward process

A `Markov reward process` also includes a distribution `Pr(r[t+1]|s[t])` over the possible rewards `r[t+1]` received at the next time step, given that we are in state `s[t]`. This produces a sequence `s[1], r[2], s[2], r[3], s[3], r[4] …` of states and the associated rewards (figure 19.2).

---

**Problem 19.1**

---

![Figure 19.2 Markov reward process. This associates a distribution Pr(rt+1|st) of rewards rt+1 with each state st. a) Here, the rewards are deterministic; the penguin will receive a reward of +1 if it lands on a fish and 0 otherwise. The trajectory τ now consists of a sequence s1, r2, s2, r3, s3, r4 … of alternating states and rewards, terminating after eight steps. The return Gt of the sequence is the sum of discounted future rewards, here with discount factor γ = 0.9. b-c) As the penguin proceeds along the trajectory and gets closer to reaching the rewards, the return increases.](images/c19-fig-0002.jpg)

**Figure 19.2** Markov reward process. This associates a distribution `Pr(r[t+1]|s[t])` of rewards `r[t+1]` with each state `s[t]`. a) Here, the rewards are deterministic; the penguin will receive a reward of +1 if it lands on a fish and 0 otherwise. The trajectory `τ` now consists of a sequence `s[1], r[2], s[2], r[3], s[3], r[4] …` of alternating states and rewards, terminating after eight steps. The return `G[t]` of the sequence is the sum of discounted future rewards, here with discount factor `γ = 0.9`. b-c) As the penguin proceeds along the trajectory and gets closer to reaching the rewards, the return increases.

The Markov reward process also includes a `discount factor γ ∈ (0, 1]` that is used to compute the `return G[t]` at time `t`:

`c19-fig-5001.jpg`

 (19.1)

The return is the sum of the cumulative discounted future rewards; it measures the future benefit of being on this trajectory. A discount factor of less than one makes rewards that are closer in time more valuable than rewards that are further away.

### 19.1.3 Markov decision process

A `Markov decision process` or `MDP` adds a set of possible `actions` at each time step. The action `a[t]` changes the transition probabilities, which are now written as `Pr(s[t+1]|s[t], a[t])`. The rewards can also depend on the action and are now written as `Pr(r[t+1]|s[t], a[t])`. An MDP produces a sequence `s[1], a[1], r[2], s[2], a[2], r[3], s[3], a[3], r[4] …` of states, actions, and rewards (figure 19.3). The entity that performs the actions is known as the `agent`.
