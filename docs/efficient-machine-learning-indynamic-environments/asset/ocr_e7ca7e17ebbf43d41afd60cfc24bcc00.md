# ## 4.6 Conclusion

This chapter introduced *continual optimization* (CO)—a principled framework for exploiting the *gradual evolution* of large-scale resource allocation problems. Leveraging the insight that successive rounds in many systems differ marginally, CO amortizes solver effort across time rather than treating each round as an isolated instance.

We formalized this intuition through the notion of path lengths and demonstrated how schedulers follow a Follow-The-Leader (FTL) process, which enjoys path dependent dynamic regret. Building on this analysis, we explained how a warm-started **Proximal Point Algorithm** naturally suits continual optimization in terms of run-time: its proximal updates are contractive, benefit directly from good initializations, and—when paired with a coordinate-descent inner solver—remain factorization-free. We instantiated the framework as COPTER, which combines

+   1. a *differential update interface* that modifies the LP/MILP incrementally,
+   
+   2. a *factorization-free* first-order solver that reuses work across rounds, and
+   
+   3. lightweight *shim* heuristics that convert near-integral LP relaxations into high-quality integer solutions without an exhaustive branch-and-cut search.

Experiments on realistic GPU-cluster traces confirmed the practical impact: COPTER delivers up to **100×** faster end-to-end scheduling than environment-agnostic baselines, while matching—or surpassing—baseline job-completion times. Together, the theoretical basis and empirical results illustrate that recognizing, and systematically exploiting, gradually evolving dynamics can unlock substantial efficiency gains in modern machine-learning infrastructure.

# ## 4.7 Related Work and Discussion

# ### Cluster Scheduling as Optimization Problems

Plan-ahead schedulers like Tetri-Sched [59] and Shockwave [183] solve one MILP to determine allocations for multiple rounds, and as a result, are reasonably robust to missing scheduler deadlines in large clusters at the cost of increased queue times and reduced resource utilization. Meta’s RAS [138] solves MILPs hourly for large-scale capacity reservation uses a two-stage decomposition (MILP for server-reservation assignment, then parallel container allocation), but requires problem-specific optimizations and heuristics to scale the MILP stage to large-scale problems. Tetris [185] solves MILPs for load balancing ML workloads and data placement optimization across regions, and employs multi-level scheduling for scalability at the cost of global