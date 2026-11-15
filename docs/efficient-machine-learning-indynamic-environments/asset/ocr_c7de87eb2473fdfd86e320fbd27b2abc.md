![](bbox=[0.18, 0.1, 0.88, 0.43])

Figure 5.6: Summary of experiments with Bimodal demands for Kd1 (upper) and ASN (lower) topologies.

# ## 5.3.3 Attribution of benefits

COPTER provides a varying amount of benefits in our benchmarks. Differential program updates help if the set of resources and requests change, so this only benefits the GPU cluster scheduling problem. While all three problems benefit from our factorization-free, sparsity-aware efficiently warm-started solver, lightweight integerization via problem-specific shims only benefits GPU cluster scheduling and shard load balancing problems.

Figure 5.7 illustrates the stacking benefits from COPTER on the LP-relaxation of the Sia ILP [169] in the previously described 10k GPU cluster. We choose the LP relaxation, and not the ILP directly, as many problems are directly formulated as LPs (like WAN traffic engineering) and do not benefit from using lightweight shims to resolve integer infeasibilities.

Figure 5.7 shows the impact of (a) using the custom solver implementation that benefits from problem and solution sparsity, (b) using a differential interface to reflect problem updates efficiently, and (c) efficiently warm-starting the custom solver using previous round's solution as the initial guess for the current round. On average, each of these contribute a stacking 5×, 3.5×, and 1.5× speedup, respectively,