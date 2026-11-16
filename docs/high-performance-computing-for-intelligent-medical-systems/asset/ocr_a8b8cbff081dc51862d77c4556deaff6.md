# 8.9.7 The ABC-BM algorithm

Another iterative technique based on a natural phenomenon and using swarm intelligence for optimization is called Artificial Bee Colony optimization. The random food sources, that is, locations, are used as starting population. Three key operations listed below are implemented for the optimization process till limiting conditions are met. These are:

+   - send the employee bees;
+   - food sources are picked up by Onlooker bees;
+   - scout bees are specified.

The ABC optimization is implemented successfully for efficient ME and steps of ABC-BMA [41] are shown using the block diagram in figure 8.10.

# 8.9.8 ABC-DE

Warasucheep et al [58] amalgamated the concept of Differential evolution with Artificial Bee Colony Optimization to propose the algorithm called DE-ABC algorithm. Converse to that, ABC optimization is merged with DE based on some other criteria for ME which is known as ABC-DE and is suggested by Bhattacharjee _et al_ [60]. This BMA is designed ‘for an optimal solution of BM corresponding to the least no. of MAD calculation’. In this BMA, mutation, and cross-over operations of DE override the process to produce new food sources, that is, bee phase and onlooker bee phase, which is shown in figure 8.11.

This hybrid BMA has become advantageous as it picks up the exploration feature in the search space of DE and the exploitation feature of ABC.

# 8.9.9 HS-DE based BMA

DE-HS is a hybrid algorithm designed by Chakraborty _et al_ [59] which uses the mutation operator of DE instead of the pitch tuning approach of the HS algorithm to perturb the target vector. Bhattacharjee _et al_ [60] came up with a concept reverse to this algorithm known as HS-DE which uses cross-over operation instead of mutation operator of DE so that more variation can be added in the perturb vector, and figure 8.12 demonstrates the workflow of the HS-DE algorithm.

![](bbox=[0.31, 0.73, 0.68, 0.88])