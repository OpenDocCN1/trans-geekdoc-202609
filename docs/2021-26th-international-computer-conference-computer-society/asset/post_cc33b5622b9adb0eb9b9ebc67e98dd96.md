
environment); then, users choose one of them. The recommender agent performs this process sequentially over time steps to maximize cumulative reward. We model the recommendation process as a Markov Decision Process (MDP), which we adopted in reinforcement learning. An MDP is a markov process described as follows:

- State: $s_t$ is defined as embeddings of user's positive preference before time step $t$
- Action: $a_t \in \mathbb{R}$ is a continuous parameter vector used to construct a diverse recommendation list
- Reward: based on the choice $a_t$ in $s_t$ made by the recommender agent, a diverse yet relevant items is recommended to the user. The user interacts with these items and provides feedback, e.g., rating, click, or purchase, and the recommender receives immediate reward.
- Transition: The user's state changes from $s_t$ to $s_{t+1}$ when the recommender agent takes action $a_t$ at time step. If the user ignores the recommended list, the next state remains unchanged (i.e., $s_{t+1} = s_t$). Otherwise, the next state $s_{t+1}$ updates based on user's feedback.
- Discount: $\gamma \in [0,1]$ is a factor that determines the importance of future rewards relative to immediate reward. If $\gamma=0$, the agent is short-sighted by only considering immediate rewards. On the contrary, if $\gamma=1$, it prefers long-term rewards. The expected cumulative reward at time step $t$ is denoted as $G_t = \sum_{k=0}^{\infty} \gamma^k R(s_{t+k})$

of $r_t$ item in the user's positive interaction. When the recommender agent generates a list of items and then recommends to the user, if the user skips items then the next state remains unchanged, i.e., $s_{t+1} = s_t$. If $p = \{p_i \in \mathbb{R}^m, 1 \leq i \leq n\}$ are recommended items that the user has given positive feedback to, then the next state updates as follows:

```
$s_{t+1} = \{e_i | e_i \in s_t, n+1 \leq i \leq n\} \cup \{p_i | p_i \in p\}$
(1)
```

such that chronological order of items in $s_{t+1}$ is preserved. Since the current representation of items in the user's state has no sense of how the items are in chronological order, we use Positional Encoding to each item's embedding to determine the position of each item in the system. The positional formula is:

```
$PE(pos, i) = \sin(\frac{pos}{10000^{2i/d_{model}}}})$
$PE(pos, i) = \cos(\frac{pos}{10000^{2i/d_{model}}}})$
(2)
```

For example, if $s_t = \{e_1, e_2, \dots, e_n\}$ is the user's state, positional encoding of $PE \in \mathbb{R}^{d_{model}}$ would be used as follows:

```
$PE(pos, i) = pos + \sin(\frac{pos}{10000^{2i/d_{model}}}}), \cos(\frac{pos}{10000^{2i/d_{model}}),$
\dots,$
$\sin(pos, i) = pos + \sin(\frac{pos}{10000^{(2i+1)/d_{model}}}}), \cos(\frac{pos}{10000^{(2i+1)/d_{model}}}})$
(4)
```

the output of the positional encoder is fed into two convolutional layers and one tanh layer that maps the current state to a proto-action $a_t$:

```
$f_t(s_t) = a_t$
(5)
```

![](img/293e1bf91565016a8c5cd326223dbb9c_2_0.png)

Fig. 2. The recommender-users interactions

The general scenario of the recommender-users interactions in MDP is illustrated in Fig. 2. In each state the recommender (agent) chooses a proto-action $a_t$ based on current policy $\pi$. This proto-action is a continuous parameter vector used to generate a list of items. Then the user's feedback updates the policy $\pi$ based on user's state changes to $s_{t+1}$. The objective of the reinforcement learning is to learn a policy to maximize the expected reward.

## B. The Actor Network

The actor-network utilizes a deep neural network to learn the optimal policy, generating the best action $a_t$ for the current's state $s_t$. The state can be defined as $s_t = \{e_i | e_i \in \mathbb{R}^m, 1 \leq i \leq n\}$ such that

In this paper we use a probabilistic matrix factorization (PMF) technique

Given proto-action by the actor-network, a list of items is recommended to the user. Unlike the usual ranking mechanisms [15]–[17], which compute the distance from the proto-action to item in the item space to find similar items, we use $\kappa$-similar items to the proto-action using Approximate Nearest Neighbors Or Hey (ANNY) [99], which has high performance in benchmarks [34]–[35]. The ANNOY algorithm builds a binary tree structure to search items by picking two points in space and splitting them by the hyperplane equidistant between them. This process is done recursively in each sub-space until each node contains

## C. Diversification

![](img/293e1bf91565016a8c5cd326223dbb9c_3_0.png)

at $m$ users. The first 400 items in the Movielens-100K dataset are shown in Fig. 3a and construct binary tree in Fig. 3b. The roots of these trees are built, after removing duplicate candidates and angular distance,

Once the tree is built, we find $k$-nearest neighbors for the generated proto-action $a_i$ (i.e. sub-space) by traversing the binary tree from root to leaf. Since each leaf $v \approx a_i$. To overcome this problem, we construct multiple trees (i.e. forest) and combine results from all trees. The roots are stored in a priority queue, and the search continues until $k$ candidates are collected. To generate a diverse recommendation list, we

we store items in $C_s$, and then compute the Total Diversity Effect (TDE) of each item $c_i$ in $C_s$ as follows:

```
$TDE(c_i) = \sqrt{\sum_{j \in C_s, j \neq i} \frac{\|c_i - c_j\|^2}{\|c_i\|^2 + \|c_j\|^2}}; ; j \neq i \& c_j \in C_s$
```

Finally, we sort items $C_s$ in descending order of TDE and select Top-N items as recommendation list. The pseudo code of this method is shown in Algorithm 1.

- **Algorithm 1 Diverse recommendation list**
**Input:** $a_i$: generated proto-action by actor-network
**Output:** $d_i$: diverse recommendation
1. find $k$-similar items to $a_i$ and in $C_s$
2. **for** $i = 1$ to $|C_s|$ **do**
   **compute** $TDE(c_i)$ using Eq. 6
   **end**
3. $candidates$ = **sort** $C_s$ in descending order of TDE
4. $d_i$ = select Top-N items
5. **return** $d_i$

the computational complexity of ANN algorithm is $O(\log N)$. In the worst case, if only one item is selected in each query, the number of queries is $k$, so the computational complexity of our method is $O(k \log N)$.

## D. The Critic Network

As shown in Fig. 1, the critic network takes (s_i$, action) pair and outputs the action value $Q(s, t)$, namely $Q$-function denotes the density of generated action $a_i$ in $s$ by following policy $\pi$. The critic utilizes a Q-network (DQN) with parameter $\theta^Q$, which uses a deep neural network as a function approximator. Therefore, the critic specifies the expected return from state $s_i$ by taking an action under policy $\pi$. We define the reward as follows:

$Q(s_i, a_i) = E_t[r_i + \gamma Q(s_{i+1}, a_{i+1})]$

## E. Reward Function

The recomm receives reward $R(s_i, a_i)$ according to the diversity of the generated recommendation list and the user's feedback. The reward function directly affects the result of Eq. 7, which estimates the action-value function $Q(s_i, a_i)$. Therefore, we need to ensure the performance of the reward during training. In this paper, we define reward as follows:

$R(s_i, a_i) = Diversity(t).Rating(t) - \lambda_1\lambda_2$

The function $Diversity(t)$ is the intra-list distance (IID) [26] of recommended items $d_i$, and $Rating(t)$ is the user's rating of recommended items $d_i$, which is defined as follows:

```
$Diversity(t) = \frac{2}{|d_i|(|d_i| -1)} \sum_{i,j \in d_i} distance(i, k)$
```

```
$Rating(t) = \frac{\sum_{i \in d_i} r(i)}{\|d_i|}$
```

where $r(i)$ is current user's rating to item $i$, which is simulated by pre-trained MF model [36]. The parameters $\lambda_1$ and $\lambda_2$ are diversity and rating weights, respectively. As shown in Fig. 4, we can count $Rating(t)$ in terms of $Diversity(t)$ to

In Zhao et al. [16] we generate a list of recommendations of size $k$, length $N$ is the size of the item space; the computational complexity is $O(KN)$. In [15], the proto-action by actor-network is used to rank items in item space; consequently, the computational complexity is $O(VN)$. In [32], a greedy MAP inference algorithm is proposed, whose computational complexity is $O(k^2)$.
