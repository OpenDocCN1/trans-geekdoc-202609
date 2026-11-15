![](bbox=[0.19, 0.11, 0.87, 0.29])

Figure 4.6: CDFs of end-to-end solver runtimes for Sia policy [169] in two clusters with 10k and 25k GPUs respectively. We compare COPTER to (1) POP, which partitions the ILP 16-way and solves the subproblems in parallel, and (2) LP*, which solves the LP-Relaxation with a commercial solver [154] and recovers binary solutions using a shim.

# 4.5.2 Empirical Evaluation

This section evaluates the effectiveness of applying continual optimization via COPTER to GPU Cluster scheduling problem Section 4.5.1.

**Testbed** We run all experiments on a 2-socket AMD EPYC 7742 64-core processor with 1TB of DDR4 memory, but limit solvers to 8 threads (no significant speedup was observed beyond 8 threads [182]). For POP, we follow the approach used in prior work [137, 182], solving each subproblem on a single thread, and report estimated parallel runtimes calculated mathematically for 64 cores.

**Evaluated approaches** We compare COPTER against two approaches: (a) POP [113] splits the ILP formulation of the Sia policy into 16 subproblems with equal resources (and jobs whenever possible), solves subproblems in parallel (using ray [77]+cvxpy [56]) with a Simplex-based solver [189], and (b) LP* solves the LP-relaxation of the Sia ILP using a commercial solver [154] and obtains binary allocations each round using the shim described in Section 4.5.1.

**Metrics** We consider the following metrics: (1) average job completion times (avg. JCTs) is the average time taken to execute a job from submission to completion, averaged over all jobs in the trace (lower is better), (2) makespan is the time taken for all jobs in a trace to complete (i.e. time between first job submission and last job