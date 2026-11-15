resulting in a new model M'. Subsequently, a new state encoding M', \(\sigma^o_M\) is added to the states of the MDP. That is, \(\forall a \in A : a(M) \mapsto M', \Sigma \mapsto \Sigma \cup \{ \sigma^o_M \}\). In accordance with the Markov property of the underlying search process, in each state, the probability of executing action \(a \in A\) is determined by policy \(P_A\).

```
\(\text{update } Ta\big(M, s, t' \in \mathbb{R}^+_{0, \to \infty}\big) : M' = M \mid ta(s) = t'.\) (8.1)
```

The detailed list of atomic and coupled DEVS actions is provided in Ref. [32].

# 8.3.1.3 Reward Function

To guide the learning agent toward learning the right DEVS model, the reward function \(R_A\) maps each state to a metric. That is, \(R_A : \Sigma \mapsto \mathbb{R}\). The reward is calculated by simulating the candidate model and evaluating how similar its behavior is to the behavior of the modeled system.

The behavior of a simulation is reflected in its trace. Roughly speaking, \(t(S(M)) = \big\{(\tau_1, y_1), (\tau_2, y_2), \dots, (\tau_n, y_n), \dots \big\}\), so that each event \(y_i \in M.Y\). (\(M.Y\) denotes the set of output events – see Definition 1).

To measure the similarity of traces or the lack thereof, we need an appropriate distance metric. Roughly, a distance metric on the set of traces \(T\) is a non-negative real-valued function \(d : T \times T \mapsto \mathbb{R}\), such that \(d(t_1, t_2) = 0 \Leftrightarrow t_1 = t_2\) (identity); and \(d(t_1, t_2) = d(t_2, t_1)\) (commutativity).

Based on the above, we are ready to define the general reward function for learning DEVS models as \(R = -|d(t(M), t(S))|\). That is, the reward is inversely proportional to the distance between the trace of the model under construction \(M\) and the trace of the system to be modeled \(S\).

# 8.3.2 Agent Setup

Every reinforcement learning approach requires a specific setup. In this section, we show how a PPO agent (see Section 8.2.3.1) can be used to implement a reinforcement learning mechanism. Table 8.1 shows an example parameterization of the PPO agent implementation of Tensorflow, the reinforcement learning library of Tensorflow.\(^3\) These settings have been shown to be successful in the inference of DEVS models previously [32].

The number of updates per batch is defined by the \textit{multi\_step} parameter. The gradient ascent or descent update is performed on batches of action trajectories defined by the \textit{batch size}. A crucial element of policy update is the update step. If the policy is updated in too large steps, the policy performance