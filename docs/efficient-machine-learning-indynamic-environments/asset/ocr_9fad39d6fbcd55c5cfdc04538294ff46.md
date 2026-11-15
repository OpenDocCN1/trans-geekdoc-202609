memory capacity constraints. However, our solver and Simplex based solvers produce mostly binary solutions to the LP-relaxation natively (see Figure 4.4).

# ## 5.2 WAN Traffic Engineering

In WAN traffic engineering, demands (i.e. flows) are allocated link capacities in the network to maximize total flow through the network of links and routers(*max-flow* [121, 137]) or minimize the maximum link utilization (*MLU* [12, 137, 182]) for better network performance. As the demands fluctuate, TE systems must frequently re-optimize flow allocations (often at 5-minute intervals [121, 137, 182]) to maintain optimal network performance. We describe the LP formulation for the maximize total flow, or *max-flow* for short, objective below.

**Problem Formulation.** Let \( D = \{d_1, ... d_k\} \) be the set of demands such that demand \( j \) for source \( s_j \) and destination \( t_j \) requests bandwidth \( d_j \). Let \( P = \{P_1, ... P_k\} \) be a set of \( N \) pre-configured paths for each pair of routers in the network: \( P_j = \{p_j^1, ... p_j^N\} \), and \( c_e \) be the capacity of the link connecting routers \( u \) and \( v \) for each edge \( e = (u, v) \in E \) in the graph \( G = (V, E) \) with routers as vertices \( V \) and links as edges \( E \).

The *path formulation LP*[32, 33, 72], is defined as follows:

```
max_X \sum_j \sum_{p \in P_j} X_j^p \qquad (a)

subject to: \sum_{p \in P_j} X_j^p \le d_j \quad \forall j \qquad (b)

\sum_{j, p \in P_j | e \in p} X_j^p \le c_e \quad \forall e \in E \qquad (c)

X_j^p \ge 0 \quad \forall p \in P_j, \forall j \qquad (d)
```

where (a) is the objective maximizing the total allocated flow through the network, (b) ensures each demand \( j \) is allocated at-most the requested bandwidth \( d_j \) split across its \( N \) pre-configured paths, (c) ensures that the sum of all flows through a link \( e \) is limited by the link capacity \( c_e \), and (d) ensures that all flow allocations are non-negative.

**Applying COPTER.** The variables \( X_j^p \) are continuous as they represent flow values in Mb/s, so COPTER will solve the above LP as-is using continual optimization without the use of shims. We show in Section 5.3.1 that COPTER's flow allocations result in optimal *max-flow* and for changes to demands across time, new and optimal allocations are quickly computed from previous allocations.