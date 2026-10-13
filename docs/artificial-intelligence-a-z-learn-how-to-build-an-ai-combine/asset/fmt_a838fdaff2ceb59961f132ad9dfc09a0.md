
# A3C Intuition: DQN, PPO, and A3C

## DQN

DQN is a value-iteration based method. The algorithm does not directly optimize for reward but instead focuses on learning a function approximator to predict Q-values that satisfy the recursive Bellman Equation. The optimal actions are then derived from the action which maximizes the Q-value. This is usually an offline method where transitions are stored in a buffer and sampled randomly to update the Q-value approximator.

## PPO

PPO is a policy-gradient type of method. The algorithm directly optimizes the expected reward by estimating the gradient of the policy from the trajectories taken by the agent. This is usually an on-line method, where only the most recent transitions taken by the agent are used to update the policy.

## Actor-Critic Methods

Actor-critic methods combine both value-iteration and policy gradient methods where a critic network estimates the value of a state while the actor optimizes for the expected reward directly.

## A3C

A3C is an extension of actor-critic where you have multiple agents learning in parallel and getting updated asynchronously.

## Deep Deterministic Policy Gradient

I’ll assume that by “Actor-Critic” you mean “Stochastic Actor-Critic (SAC)”. Both SAC and DDPG implement a model-free policy gradient and value based method.

Eponymously, SAC represents the policy as a parametric probability distribution (stochastic approach) `πθ(a|s)=Pr(a|s;θ)` whereas DDPG learns a deterministic policy `μθ(s)=a`. The gradient theorems that these two follow are also different.

### SAC: Stochastic Gradient Policy Theorem

SAC incorporates the Stochastic Gradient Policy Theorem:

```
∇θV(πθ) = E_{s∼ρπ, a∼πθ}[∇θ log πθ(a|s) Qπ(s,a)]
```

It calculates the expected gradient of the log-likelihood of the `Qπ` value if we start from state `s` and act according to policy `πθ` with respect to parameters `θ`.

### DDPG: Deterministic Gradient Policy Theorem

DDPG follows a deterministic policy version called the Deterministic Gradient Policy Theorem:

```
∇θV(πθ) = E_{s∼ρπ}[∇θ μθ(s) ∇a Qμ(s,a) |_{a=μθ(s)}]
```

Notice how this theorem only integrates over the state space and not the action space.

## Comparison: DDPG vs SAC

Since DDPG integrates only over the state space, it has an edge over its stochastic counterpart:

*   DDPG could perform more efficiently than SAC.
*   DDPG can outperform SAC in higher dimensions.
*   SAC could require more samples than DDPG if the action space has many dimensions.
