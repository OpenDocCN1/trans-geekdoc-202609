![](bbox=[0.153, 0.112, 0.825, 0.325])

Figure 5.7: Speedups in end-to-end solver runtimes from two of the three techniques that make up COPTER compared to a commercial LP solver (CPLEX [154]). We show mean, median, 10th and 90th percentile speedups for the LP-relaxation of the Sia ILP [169] for 1 minute rounds on a 10k GPU cluster.

for a total speedup of 24× over independently solving problems using existing LP solvers. Additionally, from Section 5.3.1, we see that solving MILPs by first solving its LP-relaxation and then applying a problem-specific shim leads to an end-to-end speedup of 2–3× (using the same solver [154] for both MILP and LP-relaxation of the load balancing problem). Thus, we can expect COPTER to provide 24–72× speedup for MILPs.

# 5.4 Conclusion

This chapter showed how COPTER extends beyond machine-learning workflows to optimize two additional large-scale tasks: shard load balancing and wide-area-network traffic engineering. Together with Chapter 4, these results underscore a central message of Part II: many resource-allocation problems are best viewed as a sequence of slowly evolving instances and therefore lend themselves naturally to continual optimization.

Across three domains—GPU-cluster scheduling, shard load balancing, and WAN traffic engineering—COPTER delivers allocations 10–100× faster than state-of-the-art, round-agnostic solvers, with negligible loss in solution quality.