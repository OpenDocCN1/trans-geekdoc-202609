
# Offline RL

In offline reinforcement learning, the policy is learned by observing the behavior of other agents, including the rewards they receive, *without* the ability to change the policy. It is related to imitation learning, where the goal is to copy the behavior of another agent without access to rewards (see Hussein et al., 2017). One approach is to treat offline RL in the same way as off-policy reinforcement learning. However, in practice, the distributional shift between the observed and applied policy manifests in overly optimistic estimates of the action value and poor performance (see Fujimoto et al., 2019; Kumar et al., 2019a; Agarwal et al., 2020). Conservative Q-learning (Kumar et al., 2020b) learns conservative, lower-bound estimates of the value function by regularizing the Q-values. The decision transformer (Chen et al., 2021c) is a simple approach to offline learning that takes advantage of the well-studied self-attention architecture. It can subsequently be fine-tuned with online training (Zheng et al., 2022).

# Reinforcement learning and chatbots

Chatbots can be trained using a technique known as *reinforcement learning with human feedback* or *RLHF* (Christiano et al., 2018; Stiennon et al., 2020). For example, *InstructGPT* (the forerunner of ChatGPT, Ouyang et al., 2022) starts with a standard transformer decoder model. This is then fine-tuned based on prompt-response pairs where the response was written by human annotators. During this training step, the model is optimized to predict the next word in the ground truth response.

Unfortunately, such training data are expensive to produce in sufficient quantities to support high-quality performance. To resolve this problem, human annotators then indicate which of several model responses they prefer. These (much cheaper) data are used to train a *reward model*. This is a second transformer network that ingests the prompt and model response and returns a scalar indicating how good the response is. Finally, the fine-tuned chatbot model is further trained to produce high rewards using the reward model as supervision. Here, standard gradient descent cannot be used as it's not possible to compute derivatives through the sampling procedure in the chatbot output. Hence, the model is trained with proximal policy optimization (a policy gradient method where the derivatives are tractable) to generate higher rewards.

# Other areas of RL

Reinforcement learning is an enormous area, which easily justifies its own book, and this literature review is extremely superficial. Other notable areas of RL that we have not discussed include *model-based RL*, in which the state transition probabilities and reward functions are modeled (see Moerland et al., 2023). This allows forward planning and has the advantage that the same model can be reused for different reward structures. *Hybrid methods* such as AlphaGo (Silver et al., 2016) and MuZero (Schrittwieser et al., 2020) have separate models for the dynamics of the states, the policy, and the value of future positions.

This chapter has only discussed simple methods for exploration, like the epsilon-greedy approach, noisy Q-learning, and adding an entropy term to penalize overconfident policies. *Intrinsic motivation* refers to methods that add rewards for exploration and thus imbue the agent with "curiosity" (see Barto, 2013; Aubret et al., 2019). *Hierarchical reinforcement learning* (see Pateria et al., 2021) refers to methods that break down the final objective into sub-tasks. *Multiagent reinforcement learning* (see Zhang et al., 2021a) considers the case where multiple agents coexist in a shared environment. This may be in either a competitive or cooperative context.

# Problems

## Problem 19.1

[Figure 19.18](#c019.xhtml#c19-fig-0018) shows a single trajectory through the example MDP. Calculate the return for each step in the trajectory given that the discount factor *γ* is 0.9.

![Figure 19.18 One trajectory through an MDP. The penguin receives a reward of +1 when it reaches the first fish tile, -2 when it falls in the hole, and +1 for reaching the second fish tile. The discount factor γ is 0.9.](images/c19-fig-0018.jpg)

[Figure 19.18](#c019.xhtml#c19-fig-0018a) One trajectory through an MDP. The penguin receives a reward of +1 when it reaches the first fish tile, -2 when it falls in the hole, and +1 for reaching the second fish tile. The discount factor *γ* is 0.9.

## Problem 19.2**

Prove the policy improvement theorem. Consider changing from policy *π* to policy *π′*, where for state *s[t]* the new policy *π′* chooses the action that maximizes the expected return:

![c19-fig-5047.jpg](images/c19-fig-5047.jpg)

(19.43)

and for all other states, the policies are the same. Show that the value *v*\[*s[t]*|*π*\] for the original policy must be less than or equal to *v*\[*s[t]*|*π′*\] = *q*(*s[t]*, *π′*\[*a*|*s[t]*\]|*π*\] for the new policy:

![c19-fig-5048.jpg](images/c19-fig-5048.jpg)

(19.44)

Hint: Start by writing the term *v*\[*s[t]*[+1]|*π*\] in terms of the new policy.

## Problem 19.3

Show that when the state values and policy are initialized as in [figure 19.10a](#c019.xhtml#c19-fig-0010), they become those in [figure 19.10b](#c019.xhtml#c19-fig-0010) after two iterations of (i) policy evaluation (in which all states are updated based on their current values and then replace the previous ones) and (ii) policy improvement. The state transition allots half the probability to the direction the policy indicates and divides the remaining probability equally between the other valid actions. The reward function returns -2 irrespective of the action when the penguin leaves a hole. The reward function returns +3 regardless of the action when the penguin leaves the fish tile and the episode ends, so the fish tile has a value of +3.

## Problem 19.4

The *Boltzmann policy* strikes a balance between exploration and exploitation by basing the action probabilities *π*\[*a*|*s*\] on the current state-action reward function *q*\[*s, a*\]:

![c19-fig-5049.jpg](images/c19-fig-5049.jpg)

(19.45)

Explain how the temperature parameter *τ* can be varied to prioritize exploration or exploitation.

## Problem 19.5**

When the learning rate *α* is one, the Q-Learning update is given by:

![c19-fig-5050.jpg](images/c19-fig-5050.jpg)

(19.46)

Show that this is a contraction mapping (equation 16.30) so that:

![c19-fig-5051.jpg](images/c19-fig-5051.jpg)

(19.47)

where ||•||*[∞]* represents the *ℓ[∞]* norm. It follows that a fixed point will exist by Banach's theorem and that the updates will eventually converge.

***

Appendix B.3.2

Vector norms

***

## Problem 19.6

Show that:

![c19-fig-5052.jpg](images/c19-fig-5052.jpg)

(19.48)

and so adding a baseline update doesn't change the expected policy gradient update.

## Problem 19.7**

Suppose that we want to estimate a quantity 𝔼\[*a*\] from samples *a*[1], *a*[2] … *a[I]*. Consider that we also have paired samples *b*[1], *b*[2] … *b[I]* that are samples that co-vary with *a* where 𝔼\[*b*\] = *μ[b]*. We define a new variable:

![c19-fig-5053.jpg](images/c19-fig-5053.jpg)

(19.49)

Show that Var\[*a*′\] ≤ Var\[*a*\] when the constant *c* is chosen judiciously. Find an expression for the optimal value of *c*.

## Problem 19.8

The estimate of the gradient in equation 19.34 can be written as:

![c19-fig-5054.jpg](images/c19-fig-5054.jpg)

(19.50)

where

![c19-fig-5055.jpg](images/c19-fig-5055.jpg)

(19.51)

and

![c19-fig-5056.jpg](images/c19-fig-5056.jpg)

(19.52)

Show that the value of *b* that minimizes the variance of the gradient estimate is given by:

![c19-fig-5057.jpg](images/c19-fig-5057.jpg)

(19.53)

# Chapter 20

Why does deep learning work?
