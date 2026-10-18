
We propose two different methods in this section to achieve load balancing. In the first approach, the switch and target controller are selected randomly. In the second case, the switch with the maximum load and target controller is selected with a Q-table algorithm. The core driving force for optimizing the migration model is the decision-making process in reinforcement learning, which happens in the knowledge plane. The control loop between the knowledge and the control plane is used to exchange load statistics and switch migration decisions. Finally, the control plane implements the switch migration on the data plane. The optimal switch migration model is shown in [Figure 3.3](#ch03.xhtml#fig3_3).

![Figure 3.3 Optimal switch migration model based on RL.](images/fig3_3.jpg)

[Figure 3.3 Optimal switch migration model based on RL.](#ch03.xhtml#Ffig3_3)

## [3.6.1 Random Approach](#ch03.xhtml#c_sec3_006_001)

We compute the optimal load for each time step. The controllers are categorized as underloaded, `I[domain]`, and overloaded, `O[domain]`. One of the overloaded controllers, `c[i] ∈ O[domain]`, is chosen and load balancing is performed by migrating a random switch, `s[j]`, to a target controller, `c[t] ∈ I[domain]`. The process is continued until load balancing is achieved.

## [3.6.2 Q-Learning with ϵ-greedy](#ch03.xhtml#c_sec3_006_002)

In the ϵ-greedy approach, we try to find a trade-off between exploiting the immediate benefit and exploring a long-term reward. We train the Q-network by studying a random action with probability ϵ. At the same time, we exploit an action that maximizes the expected long-term reward with probability 1 – ϵ. We shall correspondingly obtain its new state and the resultant reward for each action taken. This is treated as the experience in RL and shall be reserved for future use. The core principle of reinforcement learning is applied to the SDN controller selection process. An optimal migration model based on reinforcement learning is established, where the target controller is selected by the migration action derived from reinforcement learning.

The input to the algorithm is the set of the controllers and switches, the flow-request rate of the switches for each time, and the various parameters required for Q-learning. The Q-matrix, that is, the `state * action` pair, is initialized with value 1, as shown in the first line of the algorithm. The iteration repeats at a time step of 30 seconds. The ideal load of a controller and the set of overloaded (`O[domain]`) and underloaded (`I[domain]`) controllers are computed in lines 3–5 of the algorithm. A random overloaded controller is selected from the (`O[domain]`) and the switch with the highest load is selected for migration (shown in line 9). Next, we generate a random number and if its value is less than `E`, we explore. An underloaded controller is chosen at random from the `I[domain]` (shown in line 12). Otherwise, if the value of the random number is greater than `E`, we exploit. That is, we select the best possible action for the given state, the one that yields the maximum Q-value (shown in lines 10–14). The switch migration is then performed. The reward is calculated, and the Q-value is updated accordingly using Equation 3.8 (shown in lines 15–16). The value of ϵ is updated as shown in lines 17–20. Finally, we compute the load balancing rate.

**Example 3.2:** In [Figure 3.4](#ch03.xhtml#fig3_4), we show a SDN network with nine SDN switches distributed across three SDN domains (controllers). The flow arrival rate of the switches for the first time step is shown in [Table 3.3](#ch03.xhtml#table3_3). The instantaneous load of controllers `c[1]`, `c[2]`, and `c[3]` in terms of number of flows are 75, 130, and 60, respectively.

![Figure 3.4 Unbalanced switch to controller mapping.](images/fig3_4.jpg)

[Figure 3.4 Unbalanced switch to controller mapping.](#ch03.xhtml#Ffig3_4)

[Table 3.3 Flow Arrival Rate of Switches at Time `t[0]`](#ch03.xhtml#Ttable3_3)

| Switch | `s[1]` | `s[2]` | `s[3]` | `s[4]` | `s[5]` | `s[6]` | `s[7]` | `s[8]` | `s[9]` |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `s[i](t[0])` | 25 | 25 | 25 | 25 | 25 | 35 | 45 | 25 | 35 |
| `s[i](t[1])` | – | – | – | – | – | – | – | – | – |

The corresponding state space is {`S1 → 〈0, 0, 1〉`, `S2 → 〈0, 1, 0〉`, `S3 → 〈1, 0, 0〉`}. The action space is {`A1 → 〈0, 0, 1〉`, `A2 → 〈0, 1, 0〉`, `A3 → 〈1, 0, 0〉`}. We have already discussed the MDP formulation in detail in [Subsection 3.5.2](#ch03.xhtml#sec3_005_002) with an example.

We assume homogeneous controllers with maximum processing capacity of 150 flows per second. The controller load ratios are `R[c1] = 75/150 = 0.5`; `R[c2] = 130/150 = 0.866`; and `R[c3] = 60/150 = 0.4`. Using these values, we compute the pairwise average load ratio of the controllers. The values are `R[c1c2] = 205/300 = 0.683`; `R[c1c3] = 135/300 = 0.45`; and `R[c2c3] = 190/300 = 0.633`. Finally, we compute the overall average load ratio (i.e., ideal load) as `R[c1c2c3] = 265/450 = 0.5888`. The discrete coefficient for two controllers is calculated using Equation (3.6). The values are `D[c1c2] = 0.26`; `D[c1c3] = 0.11`; and `D[c2c3] = 0.368`. For `n` controllers, the discrete coefficient is calculated using Equation (3.7), `D[c1c2c3] = 0.34066`.

The discrete coefficients are used to distinguish the controllers as overloaded and underloaded. In our example, {`c[2]`} is overloaded and {`c[1]`, `c[3]`} are underloaded controllers. The switch with maximum load (`s[7]`) is selected for migration. Initially, the Q-matrix is initialized to 1, as shown in [Table 3.4](#ch03.xhtml#table3_4).

[Table 3.4 Q-matrix](#ch03.xhtml#Ttable3_4)

| | Action |
| --- | --- |
| | A1 | A2 | A3 |
| **State** | S1 | 1 | 1 | 1 |
| **S2** | 1 | 1 | 1 |
| **S3** | 1 | 1 | 1 |

**Decayed epsilon greedy approach:** In our example, the initial value of E is set to 0.7 and it decays to 0.05 with a decay factor 0.0025. Assuming that we make use of exploitation, we transfer switch `s[7]` to controller `c[3]` because all entries are 1 in the table and so the maximum Q-value will select `c[3]` from {`c[1]`, `c[3]`}. After the migration of `s[7]`, the new system will appear as follows:

```
\begin{array}{lll}
{c_{1}\ :s_{1},s_{2},s_{3} = 75;} & {c2\ :s4,s5,s6 = 95;} & {c3\ :s8,s9,s7 = 105} \\
\end{array}
```

Again, we compute the controller load ratios, average controller load ratio, and the discrete coefficient `D'[ij] = 0.19451894`. The value of the new discrete coefficient is smaller, which means the system has become more stable after the transfer of the switch. The reward is computed using Equation (3.5).

`Reward = |(D'[ij] − D[ij])| = 0.19451894`

The rewards become larger when the system become more stable. The Q-matrix is updated using equation (3.8). We take γ to be 0.7, α to be 0.6 in the first step, and `Q[S2,A3] = 1 + 1(0.19451894 + 0.7 ∗ 0.6 − 1) = 0.61451894`. The new Q-table for the next iteration is shown in [Table 3.5](#ch03.xhtml#table3_5).

[Table 3.5 State of Q-matrix Update (from time `t[0]` to time `t[1]`)](#ch03.xhtml#Ttable3_5)

| | Action |
| --- | --- |
| | A1 | A2 | A3 |
| **State** | S1 | 1 | 1 | 1 |
| **S2** | 1 | 1 | 0.61451894 |
| **S3** | 1 | 1 | 1 |

## [3.7 Results and Implementation](#ch03.xhtml#c_sec3_7)

The following section describes the experiment setup, performance measures, and the outcome analysis of the experiment.

## [3.7.1 Experiment Setup](#ch03.xhtml#c_sec3_007_001)
