# Algorithm 35.1: Q-learning with $\epsilon$-greedy exploration

```
1 Initialize value function parameters $\boldsymbol{w}$
2 repeat
3   Sample starting state $s$ of new episode
4   repeat
5     Sample action \(a = \begin{cases} \text{argmax}_b Q_w(s, b), & \text{with probability } 1 - \epsilon \\ \text{random action}, & \text{with probability } \epsilon \end{cases}\)
6     Observe state $s'$, reward $r$
7     Compute the TD error: \(\delta = r + \gamma \max_{a'} Q_w(s', a') - Q_w(s, a)\)
8     $\boldsymbol{w} \leftarrow \boldsymbol{w} + \eta \delta \nabla_{\boldsymbol{w}} Q_w(s, a)$
9     $s \leftarrow s'$
10   until state $s$ is terminal
11 until converged
```

for a set of random variables \(\{X_a\}\). Thus, if we pick actions greedily according to their random scores \(\{X_a\}\), we might pick a wrong action just because random noise makes it appealing.

Figure 35.5 gives a simple example of how this can happen in an MDP. The start state is A. The right action gives a reward 0 and terminates the episode. The left action also gives a reward of 0, but then enters state B, from which there are many possible actions, with rewards drawn from \(\mathcal{N}(-0.1, 1.0)\). Thus the expected return for any trajectory starting with the left action is \(-0.1\), making it suboptimal. Nevertheless, the RL algorithm may pick the left action due to the maximization bias making B appear to have a positive value.

One solution to avoid the maximization bias is to use two separate $Q$-functions, $Q_1$ and $Q_2$, one for selecting the greedy action, and the other for estimating the corresponding $Q$-value. In particular, upon seeing a transition \((s, a, r, s')\), we perform the following update

> \(Q_1(s, a) \leftarrow Q_1(s, a) + \eta \left[ r + \gamma Q_2(s', \text{argmax}_{a'} Q_1(s', a')) - Q_1(s, a) \right] \quad (35.13)\)

and may repeat the same update but with the roles of $Q_1$ and $Q_2$ swapped. This technique is called **double Q-learning** [Has10]. Figure 35.5 shows the benefits of the algorithm over standard Q-learning in a toy problem.

# 35.2.6 Deep Q-network (DQN)

When function approximation is used, Q-learning may be hard to use in practice due to instability problems. Here, we will describe two important heuristics, popularized by the **deep Q-network** or **DQN** work [Mni+15], which was able to train agents to outperform humans at playing Atari games, using CNN-structured Q-networks.

The first technique, originally proposed in [Lin92], is to leverage an **experience replace buffer**, which stores the most recent \((s, a, r, s')\) transition tuples. In contrast to standard Q-learning which updates the $Q$-function when a new transition occurs, the DQN agent also performs additional updates using transitions sampled from the buffer. This modification has two advantages. First, it