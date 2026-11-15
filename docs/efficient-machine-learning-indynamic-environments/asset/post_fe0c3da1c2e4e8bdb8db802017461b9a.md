
where the indicator functions $\mathcal{I}_C(x)$ for some set $C$ takes the value of $0$ when $x \in C$ and $+\infty$ when $x \notin C$. Let,

```
$g(x) = c^T x + \mathcal{I}_{Ax \le b}(x) + \mathcal{I}_{x \ge 0}(x),$
```

and our original optimization problem becomes equivalent to finding,

```
$x^* \in \arg \min_x g(x).$ (4.3)
```

The PPA algorithm can be thought of as solving Equation (4.3), by starting some initial point $x_t := x_0$ and repeatedly applying the following operator, referred to as the proximal operator to $x_t$ to find subsequent iterates:

```
$x_{k+1} = \text{prox}_{\eta g}(x_k) = \arg \min_x g(x) + \frac{1}{2\eta} \|x_k - x\|^2.$ (4.4)
```

In general, the proximal operator is a non-expansive operation (see Theorem 11, [47]); that is, it never increases the distance of the current iterate to the optimum, $\|x_t - x^*\|$. In the particular case of constrained linear programs, it can be shown that with an appropriate choice of $\eta$, the proximal operator is strictly contractive (Theorem 4, [54] or Theorem 4.5 and Proposition 4.4 from [19]). That is,

```
$\|\partial g(x_{k+1})\| \le \min \left( \frac{L}{\eta}, 1 \right) \|\partial g(x_k)\|.$
```

Here $\partial g(x)$ denote the sub-gradient of $g(x)$. A minimizer of the linear program can then be characterized as being a feasible point with $\|\partial g(x)\| = 0$. Here $L$ is a problem dependent constant. This means that, for an appropriate choice of $\eta$, say $\eta \ge 2L$, the sub-optimality gap measured through $\|\partial g(x_k)\|$, decreases by a factor of at least 2 in each round, starting from $\|\partial g(x_0)\|$. Initial points $x_0$ that are close to $x^*$ thus benefit from starting from a low $\|\partial g(x_0)\|$, compared to randomly initializing or initializing from a predetermined fixed choice (such as $x_0 = 0$). Finding the next iterate $x_{t+1}$ in PPA requires solving an inner subproblem corresponding to Equation (4.4). We solve the dual form of this problem using a coordinate descent based method similar to [54].

## 4.5 Application: GPU Cluster Scheduling

### 4.5.1 SIA: Job-resource co-adaptivity for GPU clusters

The SIA scheduler [169] co-optimizes allocated GPU resources and execution parameters for DNN training jobs to maximize cluster-wide goodput in heterogeneous GPU clusters. Its scheduler policy is formulated as a MILP with one variable for each (job, configuration) pair. Here configurations are a bundle of resources similar to virtual machines in commercial clouds. SIA is a round-based (1 minute) scheduler that periodically re-optimizes the MILP to determine the optimal configuration for each job to maintain high cluster goodput.

The MILP formulation for SIA policy starts with the goodput matrix $G$ where $G_{ij}$ is the normalized goodput for job $i$ estimated on configuration $j$. $X$ is an allocation matrix (same dimension as $G$) and job $i$ is allocated configuration $j$ if $X_{ij} = 1$, or no resources if $X_{ij} = 0$. Let \(\text{NGPU}(C_j, k)\) be the number of GPUs of type $k$ in configuration $C_j$, and $N_k$ be the total number of GPUs of type $k$ in the cluster. The MILP formulation for the SIA policy is as follows:

```
\(\max_X \sum_{i=1}^{N_J} \sum_{j=1}^{N_C} X_{ij} \cdot G_{ij} + \lambda \sum_i \left(1 - \sum_j X_{ij}\right) \quad (a)\)

\(\text{subject to:} \quad \sum_{j=1}^{N_C} X_{ij} \le 1 \quad \forall i \quad (b)\)

\(\sum_{i=1}^{N_J} \sum_{j=1}^{N_C} \text{NGPU}(C_j, k) \cdot X_{ij} \le N_k \quad \forall k \quad (c)\)

\(X_{ij} \in \{0, 1\} \quad \forall i, j \quad (d)\)
```

where (a) is the objective that maximizes cluster-wide goodput with an incentive \(\lambda \ge 0\) to reduce scheduler queue occupancy [169], (b) ensures each job is allocated at most one configuration, (c) ensures that each GPU type $k$ is not over-subscribed (i.e. allocations do not exceed capacity), and (d) ensures that for any job, choice of a configuration is binary.

**Applying COPTER.** To apply our approach, we first relax the binary constraints on $X_{ij}$ to \(0 \le X_{ij} \le 1 \quad \forall i, j\). Then, we solve the relaxed LP and apply a shim to its optimum solution to recover binary and feasible allocations in each round. For each job, the shim simply picks the configuration with highest weight in the solution to the LP-relaxation without violating GPU constraints. If it finds no such configuration for the job, it receives no allocation in this round.

The resulting allocations are both binary and feasible, but possibly suboptimal. We show in Section 4.5.2 that COPTER's allocations result in negligible increases to average job completion times and makespan in clusters with 10,000+ GPUs.

![](img/32fe6d02b4faa69c4646a6e93e0375fc_81_0.png)

Figure 4.6: CDFs of end-to-end solver runtimes for SIA policy [169] in two clusters with 10k and 25k GPUs respectively. We compare COPTER to (1) POP, which partitions the ILP 16-way and solves the subproblems in parallel, and (2) LP*, which solves the LP-Relaxation with a commercial solver [154] and recovers binary solutions using a shim.

### 4.5.2 Empirical Evaluation

This section evaluates the effectiveness of applying continual optimization via COPTER to GPU Cluster scheduling problem Section 4.5.1.

**Testbed** We run all experiments on a 2-socket AMD EPYC 7742 64-core processor with 1TB of DDR4 memory, but limit solvers to 8 threads (no significant speedup was observed beyond 8 threads [182]). For POP, we follow the approach used in prior work [137, 182], solving each subproblem on a single thread, and report estimated parallel runtimes calculated mathematically for 64 cores.

**Evaluated approaches** We compare COPTER against two approaches: (a) POP [113] splits the ILP formulation of the SIA policy into 16 subproblems with equal resources (and jobs whenever possible), solves subproblems in parallel (using ray [77] + cvxpy [56]) with a Simplex-based solver [189], and (b) LP* solves the LP-relaxation of the SIA ILP using a commercial solver [154] and obtains binary allocations each round using the shim described in Section 4.5.1.

**Metrics** We consider the following metrics: (1) average job completion times (avg. JCTs) is the average time taken to execute a job from submission to completion, averaged over all jobs in the trace (lower is better), (2) makespan is the time taken for all jobs in a trace to complete (i.e. time between first job submission and last job

| | Avg JCT (hours) | Makespan (hours) | Solve time (p99, seconds) |
|---|---|---|---|
| **Cluster size: 10k GPUs** | | | |
| LP* | **0.35** | **29.3** | 233.4 |
| POP | 0.41 | 31.0 | **2.9** |
| COPTER | 0.36 | 29.4 | 6.5 |
| **Cluster size: 25k GPUs** | | | |
| LP* | **0.35** | **29.3** | 2277 |
| POP | 0.39 | 30.9 | 66.5 |
| COPTER | 0.36 | 29.4 | **40.3** |

**Table 4.1:** Summary of experiments for the GPU cluster scheduling using the SIA policy [169] for 10k and 25k GPU clusters using COPTER, POP and a commercial LP solver [154].

completion, lower is better), and (3) _solver runtime_ measures the end-to-end runtime for the policy (including the time spent in _shim_ for COPTER and _LP\*_, lower is better).

We summarize the results of our experiments in Table 4.1 and the CDF of the solver runtimes in Figure 4.6. From Table 4.1, we see that for both cluster sizes, COPTER is 30-40× faster than _LP\*_ and achieves a similar average JCT and makespan. POP’s 99th percentile solve time is faster than COPTER for the 10k GPU cluster, but exceeds the 60-second threshold for the 25k GPU cluster owing to the combinatorial explosion for the MILP solved in each subproblem. Despite solving the ILP formulation directly, POP’s solutions result in 11-17% and 6% increase in average JCT and makespan, respectively. This also highlights the efficacy of our _shims_ – despite using a heuristic to obtain integer solutions to the MILP, solutions for both COPTER and _LP\*_ result in lower average job completion times and makespan. This indicates that the combinatorial explosion from the _integerization_ stage can be bypassed for large resource-allocation problems without much penalty.

Figure 4.6 also highlights another characteristic of MILP solvers: the number of variables in the ILP does not always dictate the solver runtime due to the unpredictability of the runtimes for the _integerization_ stage. Since POP solves the ILP formulation directly in each subproblem, we see a large spread of runtimes – over a 30× difference between the 90th and 100th percentile solver times. COPTER, on the other hand, shows predictable runtimes – the slowest runtime (70.4s) corresponds to the problem with the most number of variables (over 11 million variables) with just a 2-3× difference between the 90th and 100th percentile solver times.
