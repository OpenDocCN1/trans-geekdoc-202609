# 5.3 Experiments

This section evaluates the effectiveness of applying continual optimization via COPTER to the two resource-allocation problems formulated as LP/MILPs:

+   * Shard Load Balancing. We follow the experiment setup described in [137] and simulate time-varying load distributions. We re-use the code open-sourced by authors of POP [137] wherever possible and use the same load distributions to benchmark COPTER (implemented separately).

+   * Traffic Engineering. We optimize the max flow objective for two network topologies—the Kentucky Data Link network (Kdl [137, 182]), and an AS-level topology (ASN [182]). We implement COPTER in the same evaluation framework as POP [137] to simulate identical traffic patterns.

**Testbed.** We run all experiments on a 2-socket AMD EPYC 7742 64-core processor with 1TB of DDR4 memory, but limit solvers to 8 threads (no significant speedup is observed beyond 8 threads [182]). For POP, we follow the approach used in prior work [137, 182], solving each subproblem on a single thread, and report estimated parallel runtimes calculated mathematically for 64 cores.

# 5.3.1 Shard Load Balancing

**Evaluated approaches.** We compare COPTER against three approaches: (a) Heuristic is a greedy algorithm from E-Store [43], (b) Exact is the MILP formulation described in Section 5.1 and solved using a commercial MILP solver [154], (c) LP-Relaxed solves the LP-relaxation of the MILP formulation, and applies the shim described in Section 5.1 to resolve integer infeasibilities, and (d) POP-k splits the set of servers and shards into k pieces and solves the MILP formulation using a commercial MILP solver [154].

**Metrics.** We are interested in the three metrics: (a) average shard movements is the average number of shards movements per round in response to changing load distributions (lower is better), (b) average load imbalance is the difference in load between the most and least loaded servers (lower is better), and (c) average load balancer time is the time taken to compute shard-server assignments in each round and includes the time spent in the shim for approaches that use it (lower is better).