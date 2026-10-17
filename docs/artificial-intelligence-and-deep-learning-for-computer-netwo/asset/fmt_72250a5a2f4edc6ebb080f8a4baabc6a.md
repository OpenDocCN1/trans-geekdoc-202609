
The MDP is a stochastic control process with a discrete-time horizon. It gives a mathematical framework for modelling an agent's decision dilemma and optimizing the result. The MDP's purpose is to determine the best strategy for the agent under consideration. It has been widely used to model SDN for different problems. Four essential components define an MDP:

> *`S`*: A finite set of states,

> 

> *`A`*: A finite set of actions,

> 

> *`p`*: The probability of transitioning from state `s` to state `s 0` after performing action “`a`,”

> 

> *`r`*: The immediate reward gained after performing action “`a`.”

### [3.5.3 Problem Formulation Using Markov Decision Process](#ch03.xhtml#c_sec3_005_003)

We formulate the load balancing problem as a Markov decision process (`MDP`), in which 3-tuple (`S`, `A`, `R`) is used to characterize it.

#### [3.5.3.1 State Space (`S`)](#ch03.xhtml#c_sec3_005_003_001)

`S` is the finite state space. In our problem, state-space `S` is the set of controllers to which a switch can migrate, also called the migration domain. In other words, the state space denotes the list of underloaded controllers. A state `ST` ∈ `S` corresponds to the index of a controller. For instance, consider a scenario where we have five controllers. The state (0, 0, 0, 0, 1) represents the first controller as part of the migration domain. There are five possible states, but not all of them may be part of the migration domain.

#### [3.5.3.2 Action Space (`A`)](#ch03.xhtml#c_sec3_005_003_002)

`A` is the finite action space. An action is defined as the process of selecting a controller from the migration domain (i.e. set of under loaded controllers). Each action `a` ∈ `A` is represented by the index of under loaded controller selected for migration, also called the target controller.

#### [3.5.3.3 Reward Function (`R`)](#ch03.xhtml#c_sec3_005_003_003)

`R` represents the immediate reward associated with state-action pairs, denoted by `R`(`ST`, `a`), where `ST` ∈ `S` and `a` ∈ `A`. `R`(`ST`, `a`) denotes the change in degree of load balancing after the migration is affected. Mathematically it is defined as:

`R`(`ST`, `a`) = |(`D`[`i`, `j`] − `D`′[`i`, `j`])| (3.5)

The term `D`[`i,j`] is the load deviation coefficient (or discrete coefficients) between two controllers, `c`[`i`] and `c`[`j`]. Similarly, `D`′[`i`, `j`] is the load deviation after a switch is migrated from controller `c`[`i`] to `c`[`j`]. It is computed as

```
$\left. D\_{i,j}:=D\_{c\_{i},c\_{j}} = \left( \sqrt{\sum\limits_{k = i,j}{{({IL\_{c\_{k}} - L\_{c\_{i},c\_{j}}^{I}})}^{2}/2}} \right)/L\_{c\_{i},c\_{j}}^{I}. \right.$ (3.6)
```

For `n` controllers the load deviation coefficient is calculated as follows

```
$\left. D = \left( \sqrt{\sum\limits_{i = 1}^{n}{\left( {IL\_{c\_{k}} - L^{I}} \right)^{2}/n}} \right)/L^{I}. \right.$ (3.7)
```

**Example 3.1:** MDP formulation

***Consider the following scenario:** We have 11 switches that are distributed among three controllers: `c`[1], `c`[2], *and `c`[3]*. The network is depicted in* [Figure 3.2](#ch03.xhtml#fig3_2)*. Consider at a particular time step `t`[`i`]*, `c`[1] *is overloaded, that is `O`[`domain`] \=* {`c`[1]}*. Now to balance controller `c`[1]*, the switch with maximum load assigned to the controller is selected for migration (say `s`[2]*). The action to select the target controller is based on ϵ-greedy selection. In the example, we assume controller `c`[3] *is selected for migration*.

![Figure 3.2 A state-action example for the MDP formulation.](images/fig3_2.jpg)

[Figure 3.2 A state-action example for the MDP formulation.](#ch03.xhtml#Ffig3_2)

*The state space for the given scenario is* {(0, 0, 1), (0, 1, 0), (1, 0, 0)}*, since a switch can connect to any of the three controllers. At time `t`[`i`]*, switch `s`[2] *is connected to controller `c`[1]*. Thus, state for switch `s`[2] *is* (0, 0, 1)*. At this time instant, we assume controller `c`[1] *is overloaded while the other two controllers are underloaded. The migration domain is thus* {(0, 1, 0) (1, 0, 0)}. *Based on the reward function defined in* *Equation* 3.5*, an action (state, action pair) will be chosen. In this work, we chose the action based on Q-learning*.

Solving the MDP involves obtaining the best strategy for the considered agent. Our problem domain translates to selecting an appropriate switch, migration controller pair that optimizes the objective function. The action should also not lead to *switch oscillation*, that is, a switch moving to and fro between an overloaded and underloaded controller. We assume that the agent has no prior knowledge of the action, rewards, or transition probability. The actions are based only on the current network traffic. Hence, we use a model-free simulation tool. We use Q-learning, the most well-known model-free technique within the family of reinforcement learning algorithms.

### [3.5.4 Q-Learning](#ch03.xhtml#c_sec3_005_004)

Q-learning is an RL technique that works by learning an action-value function. It presents the expected utility of action in a given state and follows a fixed policy afterwards. One of the strengths of Q-learning is that it can compare the expected utility of the possible actions without requiring a model of the environment and it can be used online.

Q-learning is an off-policy reinforcement learning algorithm. It is termed *off-policy* since the Q-learning function learns from activities that aren’t covered by the current policy, such as random acts. Hence, a policy isn’t required. In other words, Q-learning aims to discover a policy that maximizes the total reward. In Example 3.1, the number of state is 3 and number of action is 2 at time `t`[`i`]. Action `a`[1] is not valid at this point. Thus, the corresponding Q-table is as follows: ([Table 3.2](#ch03.xhtml#table3_2))

 [Table 3.2 Q-table for Example 3.1 at Time `t`[`i`]](#ch03.xhtml#Ttable3_2) 

|  || Action |

| --- | --- |

| a2 || a3 |

| State || s1 || Q(s1,a2) || Q(s1,a3) |

| --- | --- | --- | --- |

| s2 || Q(s2,a2) || Q(s2,a3) |

| s3 || Q(s3,a2) || Q(s3,a3) |

The value of `Q`(`ST`, `a`) is iteratively modified by selecting the largest item in each epoch. The iteratively updated method of the valuation matrix is shown as follows:

```
$Q{(ST,a)}\_{t + 1} = Q{(ST,a)}\_{t} + \\alpha(R(ST,a) + \\gamma \\ast \\underset{a}{max}Q{(S{T\\prime},{a\\prime})}\_{t} - Q{(ST,a)}\_{t})$ (3.8)
```

The sum of the current return value and the next-largest maximum value `Q`(`ST‘`, `a’`)[`t`] in the memory is used as the expected value. The incremental iterative learning is performed by using the difference between the expected value and the true estimate, so as to obtain the value of `Q`(`ST`, `a`)[`t`] in the (`t` + 1)*th* round. The learning rate `α` is set between 0 and 1. A value of 0 means that the Q-values are never updated; hence, nothing is learned. Setting a high Q-value such as 0.9 means that learning can occur quickly. A large magnitude of the discount factor `γ` considers the long-term benefits, while smaller values emphasize immediate consideration. Initially, the Q-table is initialized with “0.” Exploration and exploitation trade-offs are used to tune the Q-values gradually.

#### [3.5.4.1 Exploration and Exploitation Trade-off](#ch03.xhtml#c_sec3_005_004_001)

By exploitation, we refer to the scenario where an agent chooses the action that gives greater immediate benefit, although it may be suboptimal. Exploration refers to the case where an agent chooses a different action to achieve a better payoff in the future instead of concentrating on the immediate benefit. Maintaining a balance between exploration and exploitation is essential.

To balance strategies such as exploiting the agent's existing knowledge against exploring random actions, we employ the `ϵ`-greedy Q-learning strategy, which is detailed in [Section 3.6.2](#ch03.xhtml#sec3_006_002).

## [3.6 Methodology](#ch03.xhtml#c_sec3_6)
