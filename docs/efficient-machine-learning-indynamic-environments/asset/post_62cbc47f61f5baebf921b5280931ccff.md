
![](img/32fe6d02b4faa69c4646a6e93e0375fc_65_0.png)

Figure 4.1: [Left] Solver runtime of three approaches for solving the Sia scheduler policy MILP [169] and their [Right] quality-runtime trade-offs. The approaches are evaluated on a trace with 100k jobs submitted to a 25k GPU cluster with 7 GPU types over 24-hours. LP* solves the LP-relaxation of the MILP in each round independently using a commercial LP solver [154]. POP-k partitions the set of GPUs and jobs into k equal sizes (whenever possible) and solves the MILP for each partition using an MILP solver [189] in parallel. COPTER uses continual optimization (see Section 4.3).

turn to mathematical programming or optimization-based methods, which frame resource allocation as linear programs (LPs) or mixed-integer linear programs (MILPs) solvable by modern numerical solvers [59, 113, 138, 169, 183, 193].

Although these methods are practical at small-to-medium scales, they can falter quickly as problem sizes grow—a reality driven by the recent explosive growth of computational infrastructure. Deep learning clusters now deploy over 100,000 GPUs (up from a few thousand in 2019 [93]), with a corresponding increase in users and jobs requesting these resources. Solving allocation problems at this scale with off-the-shelf solvers often exceeds practical time limits. For example, scaling up a state-of-the-art GPU cluster scheduling policy [169] from a 10k GPU cluster to 25k GPUs leads to an ≈ 100× increase in solver run-times (Figure C.2, Appendix).

As a result, the fraction of problems solved within the allotted 1 minute round duration decreases from 85% to only 15%. Increasing round duration is not sustainable: resources released by completed jobs idle longer while newly arrived jobs wait for resources in the scheduler queue, leading to reduced utilization and increased job completion times.

Practitioners have developed various strategies to scale optimization-based resource-allocation to large problem sizes: Warm-starting can be beneficial, but is not universally applicable and/or supported by existing commercial solvers [154, 202]; solver computation cannot be efficiently parallelized [182]; and GPU acceleration is not always applicable and/or beneficial [115] due to the sparse nature of the solver computation. Forcibly terminating solvers early by setting a compute/time budget can return suboptimal and/or infeasible solutions that are often meaningless. Partitioning problems by exploiting problem-specific properties can help scale many resource-allocation problems to larger sizes with minimal effort, albeit at the cost of solution quality.

All the approaches discussed thus far employ a commercial or open-source solver in a black-box manner. This means that the allocation problem in each round is treated as an independent problem instance that is to be passed on to the solver. However, this leads to a fundamental mismatch between the modeling of round-based resource-allocation problems and the dynamics of many systems to which these problems are applied: many large-scale systems evolve slowly across rounds, exhibiting certain structure across rounds. For example, in a small enough round duration (2–5 minutes) in GPU cluster scheduling, few GPUs fail, most jobs from the previous round continue executing with little change to their allocations, and few new jobs arrive into the cluster. By ignoring this structure and treating each round as an independent problem, existing methods forgo an opportunity to amortize solving effort over time.

Adapting existing solvers to reuse computational effort from prior rounds is not straightforward. First, a small change to the input problem (e.g., the addition of just one new request) would require reconstructing solver-specific problem representations (e.g., constraint matrices), inducing significant setup cost for even the smallest change. Second, solvers need to reconstruct key internal transformations, such as matrix (Barrier methods [23, 202]) or basis (Simplex methods [10, 23, 75, 154]) factorizations, discarding all prior computational effort. Third, for MILP resource-allocation problems [169, 183], since converting non-integer valued variables to their integer counterparts dominates solver time, this further exacerbates the scalability challenge for large problems.

To address these limitations, we propose and study *continual optimization*—a paradigm that formulates resource allocation problems as a sequence of interconnected optimization programs with overhead over multiple rounds.

We present COPTER as a system for performing continual optimization and demonstrate that it is possible to (a) reflect small changes in the resource-allocation problem to its optimization formulation using an efficient *differential* update interface; (b) exploit the slow evolution of the optimal solution to efficiently warm-start subsequent problem solves; and (c) use lightweight heuristics to recover high quality integer solutions for MILPs that bypass expensive combinatorial searches entirely.

## 4.2 Linear Program Formation

Many resource allocation problems can be formulated as *linear programs (LPs)* or *mixed-integer linear programs (MILPs)*. Given a set of resources (e.g., GPUs, CPUs, network bandwidth) and resource requests (e.g., jobs, flow demands), the goal with these programs is to find an allocation of resources to requests in a way that optimizes the given objective (e.g., maximizing throughput, minimizing job completion time, or ensuring fairness). Additionally, constraints are added to ensure that the resulting allocations are valid, realizable, and satisfy any policy requirements (e.g., priority requests must be satisfied before other requests).

**Standard form linear program** Without loss of generality, let us consider linear programs in their *standard form*:

\(\min_x \ f(x) = c^T x\)

**subject to:** \(Ax \le b, x \ge 0\) (4.1)

where: \(x \in \mathbb{R}^n\) is a vector of decision variables, \(f(x) = c^T x\) is the *linear* objective function on the decision variables, \(A \in \mathbb{R}^{m \times n}\) is the constraint matrix, \(b \in \mathbb{R}^m\) is the right-hand side vector. Additionally, in *mixed-integer* LPs (MILPs), some or all variables are constrained to integral values. MILPs are particularly useful in resource allocation as the decision variables in many problems are inherently discrete. For example, a resource is either allocated to some job or not; likewise a job is allocated some resource or none.

**Example: GPU Cluster Scheduling** Consider a simplified GPU cluster scheduling problem. Let the cluster have \(N\) GPUs and \(M\) jobs. Let \(g_j\) be the number of GPUs requested by job \(j\), and \(c_j\) be its throughput when using \(g_j\) GPUs. We wish to allocate resources to maximize the throughput of jobs in the cluster under the GPU capacity constraints. This can be stated as the following linear program:

\(\min_x \ -c^T x\)

**subject to:** \(G \cdot x \le N, x_j \in \{0, 1\} \quad \forall j\)

where \(c = [c_1, c_2, \dots, c_M]\) is the throughput vector, \(G = [g_1, g_2, \dots, g_M]\) is a \(1 \times M\) matrix, and \(x = [x_1, x_2, \dots x_M]\) is the vector of variables. The variable \(x_j = 1\) iff \(g_j\) GPUs are allocated to job \(j\) (0 otherwise).

### 4.2.1 Solving linear programs

The LP/MILP formulations of a resource allocation (RA) problem are solved in two stages, with an additional third stage for MILPs.

- **1. Program compilation** This stage transforms the resource allocation problem into a form that existing solvers can consume. In the example GPU scheduling problem in Section 4.2, this involves (a) ordering the \(M\) active jobs and assigning them an index in \(\{1 \dots M\}\), (b) building the \(c\) vector and (c) building the \(G\) matrix.

- **2. Program solving** The solver then uses one or more optimization algorithms to find an optimal solution to the *compiled* linear program. If the input program constrains some variables to take only integral values (MILPs), this stage ignores such constraints and finds an optimal solution to the *LP relaxation* of the MILP instead.

- **3. (Optional) Integerization.** This stage only applies to MILPs and converts any noninteger values for integer constrained variables to an integer value. Techniques like *branch-and-cut* often require alternating between the *solving* and *integerization* stages as it progressively assigns integral values to variables with integer constraints [23].

High-level modeling frameworks, such as CVXPY and Google OR-Tools [56, 197], provide powerful abstractions to specify optimization problems common in systems, like resource allocation. Developers define problems programmatically using symbolic variables and functions mirroring the mathematical formulation that are then automatically compiled into solver-compatible representations, shielding users from low-level implementation details.

### 4.2.2 Scalability challenges in solving linear programs

Traditional approaches to round-based resource allocation reformulate and solve one RA problem *from scratch* in each round. This means that, in each round, we recompile the current linear program from scratch, pass this to an LP solver, and use a procedure like branch-and-bound [23, 202] to recover integer solutions to the problem as needed. As problem sizes grow (e.g., clusters with tens of thousands of GPUs/jobs), each stage in solving an LP faces scalability challenges we discuss below.

**Program recompilation discards prior computational effort** For any RA problem, the bulk of the compilation time is spent in constructing the constraint matrix. Constraint matrices are often quite sparse— each row in the matrix corresponds to a constraint on a resource or request, and applies to a small subset of variables at once. For large resource-allocation problems, even the sparse representation can contain tens of millions of nonzero values and can take tens of seconds to populate in each round. Further, since current approaches trigger full recompilation for small changes to the problem (e.g., add/remove resources/requests), they discard all prior computational effort spent in creating constraint matrices in prior rounds. We show in Section 4.3 that it is possible to reduce this overhead of recompilation every round by adopting a problem-level *differential* interface, significantly reducing end-to-end runtimes.

**Independently solving LPs ignores problem evolution** Many large-scale resource-allocation problems *evolve slowly*, i.e., between two consecutive rounds *t* and
