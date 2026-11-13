where the time index $t$ is not very relevant and omitted in the notation of the function. The index $\pi$ under the expectation operator $\mathbb{E}[\cdot]$ simply indicates that the average is taken when the policy $\pi$ is enforced. The value function is simply equal to the average gain conditionally on the state being equal to $s$. In financial terms, this is equivalent to the average profit if the agent takes actions driven by $\pi$ when the market environment is $s$. More generally, it is also possible to condition not only on the state, but also on the action taken. We thus introduce the $q_\pi$ action-value function:

```
q_\pi(s, a) = \mathbb{E}_\pi [G_t|S_t = s, A_t = a] . \quad (16.5)
```

The $q_\pi$ function is highly important because it gives the average gain when the state and action are fixed. Hence, if the current state is known, then one obvious choice is to select the action for which $q_\pi(s, \cdot)$ is the highest. Of course, this is the best solution if the optimal value of $q_\pi$ is known, which is not always the case in practice. The value function can easily be accessed via $q_\pi$: $v_\pi(s) = \sum_a \pi(a,s)q_\pi(s,a)$.

The optimal $v_\pi$ and $q_\pi$ are straightforwardly defined as

```
$v_*(s) = \max_\pi v_\pi(s), \forall s \in \mathcal{S}, \quad \text{and} \quad q_*(s, a) = \max_\pi q_\pi(s, a), \forall (s, a) \in \mathcal{S} \times \mathcal{A}.$
```

If only $v_*(s)$ is known, then the agent must span the set of actions and find those that yield the maximum value for any given state $s$.

Finding these optimal values is a very complicated task and many articles are dedicated to solving this challenge. One reason why finding the best $q_\pi(s, a)$ is difficult is because it depends on two elements ($s$ and $a$) on one side and $\pi$ on the other. Usually, for a fixed policy $\pi$, it can be time consuming to evaluate $q_\pi(s, a)$ for a given stream of actions, states and rewards. Once $q_\pi(s, a)$ is estimated, then a new policy $\pi'$ must be tested and evaluated to determine if it is better than the original one. Thus, this iterative search for a good policy can take long. For more details on policy improvement and value function updating, we recommend chapter 4 of Sutton and Barto (2018) which is dedicated to dynamic programming.

# 16.1.2 Q-learning

An interesting shortcut to the problem of finding $v_*(s)$ and $q_*(s, a)$ is to remove the dependence on the policy. Consequently, there is then of course no need to iteratively improve it. The central relationship that is required to do this is the so-called Bellman equation that is satisfied by $q_\pi(s, a)$. We detail its derivation below. First of all, we recall that

```
$q_\pi(s, a) = \mathbb{E}_\pi [G_t|S_t = s, A_t = a]$
$= \mathbb{E}_\pi [R_{t+1} + \gamma G_{t+1} | S_t = s, A_t = a],$
```

where the second equality stems from (16.3). The expression $\mathbb{E}_\pi [R_{t+1}|S_t = s, A_t = a]$ can be further decomposed. Since the expectation runs over $\pi$, we need to sum over all possible actions $a'$ and states $s'$ and resort to $\pi(a', s')$. In addition, the sum on the $s'$ and $r$ arguments of the probability $p(s', r|s, a) = \mathbb{P}[S_{t+1} = s', R_{t+1} = r | S_t = s, A_t = a]$ gives access to the distribution of the random couple $(S_{t+1}, R_{t+1})$ so that in the end $\mathbb{E}_\pi [R_{t+1}|S_t = s, A_t = a] = \sum_{a', r, s} \pi(a', s')p(s', r|s, a)r$. A similar reasoning applies to the