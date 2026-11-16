An optimal state value,

$$v_*(s) = \max_\pi v_\pi(s) = \max_a q_{\pi*}(s, a),$$

is the maximum state value achievable by any policy for state $s$, which decomposes into the Bellman equation:

$$v_*(s) = \max_a \sum_{s', r} p(s', r | s, a) [r + \gamma v_*(s')].$$

Action value function $q_\pi(s, a)$ decomposes into the Bellman equation:

$$q_\pi(s, a) = \sum_{s', r} p(s', r | s, a) [r + \gamma \sum_{a'} \pi(a' | s') q_\pi(s', a')].$$

An optimal action value function,

$$q_*(s, a) = \max_\pi q_\pi(s, a),$$

is the maximum action value achievable by any policy for state $s$ and action $a$, which decomposes into the Bellman equation:

$$q_*(s, a) = \sum_{s', r} p(s', r | s, a) [r + \gamma \max_{a'} q_*(s', a')].$$

We denote an optimal policy by $\pi^*$.

Consider the shortest path problem as an example. In graph theory, the single-source shortest path problem is to find the shortest path between a pair of nodes so that the sum of weights of edges in the path is minimized. In RL, the state is the current node. At each node, following the link to each neighbour is an action. The transition model indicates that, after choosing a link to follow, the agent goes to a neighbour. The reward is then the negative of link weight/cost/distance. The discount factor can be $\gamma = 1$, since it is an episodic task. The goal is to find a path to maximize the negative of the total cost, i.e., to minimize the total distance. An optimal policy is to choose the best neighbour to traverse to achieve the shortest path; and, for each state/node, an optimal value is the shortest distance from that node to the destination. Dijkstra's algorithm is an efficient algorithm, with the information of the graph, including nodes, edges, and weights. RL can work in a model-free approach, by wandering in the graph according to some policy, without such global graph information. RL algorithms are more general than Dijkstra's algorithm, although with global graph information, Dijkstra's algorithm is very efficient.

# 2.4.3 EXPLORATION VS. EXPLOITATION

An RL agent needs to trade off between exploration of uncertain policies and exploitation of the current best policy, a fundamental dilemma in RL. Here we introduce a simple approach, $\epsilon$-greedy, where $\epsilon \in (0, 1)$, usually a small value close to 0. In $\epsilon$-greedy, an agent selects a greedy action $a = \arg \max_{a \in \mathcal{A}} Q(s, a)$, for the current state $s$, with probability $1 - \epsilon$, and, selects a random action with probability $\epsilon$. That is, the agent exploits the current value function estimation with probability $1 - \epsilon$, and explores with probability $\epsilon$.

We will discuss more about the exploration vs exploitation dilemma in Chapter 7, including several principles: naive methods such as $\epsilon$-greedy, optimistic initialisation, upper confidence bounds, probability matching, and, information state search, which are developed in the settings of multi-armed bandit, but are applicable to RL problems (Silver, 2015).

# 2.4.4 DYNAMIC PROGRAMMING

Dynamic programming (DP) is a general method for problems with optimal substructure and overlapping subproblems. MDPs satisfy these properties, where, Bellman equation gives recursive decomposition, and, value function stores and reuses sub-solutions (Silver, 2015). DP assumes full knowledge of the transition and reward models of the MDP. The prediction problem is to evaluate the value function for a given policy, and the control problem is to find an optimal value function and/or an optimal policy.