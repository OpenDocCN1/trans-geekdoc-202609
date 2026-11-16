agent must first understand how the pixel observation relates to the internal state of the game before it is able to solve the puzzle. Nevertheless, in combination with action masking, the agents manage to solve a large percentage of all puzzle instances, with 10 of the puzzles consistently solved within the optimal upper bound.

Furthermore, Figure 8.5 shows the individual training performance on the puzzle Flood. It can be seen that RL agents using action masking and the discrete internal game state observation converge significantly faster and to better policies compared to the baselines. The agents using pixel observations and no action masking struggle to converge to any reasonable policy.

# 8.4.4 Effect of Episode Length and Early Termination

We evaluate whether the cutoff episode length or early termination have an effect on training performance of the agents. For computational reasons, we perform these experiments on a selected subset of the puzzles on the easiest preset human level difficulty and only for DreamerV3 (see Section E.6.4 for details). As we can see in Table 8.6, increasing the maximum episode length during training from 10,000 to 100,000 does not improve performance. Only when episodes get terminated after visiting the exact same state more than 10 times, the agent is able to solve more puzzle instances on average (31.5% vs. 25.2%). Given the sparse reward structure, terminating episodes early seems to provide a better trade-off between allowing long trajectories to successfully complete and avoiding wasting resources on unsuccessful trajectories. Interestingly, the solution for the puzzle Cube found by DreamerV3 requires fewer steps than the human expert.

Table 8.6: Comparison of the effect of the maximum episode length (# Steps) and early termination (ET) on final performance. For each setting, we report average success episode length with standard deviation with respect to the random seed, all averaged over all selected puzzles. In brackets, the percentage of successful episodes is reported.

| #Steps | ET | DreamerV3 |
| :--- | :--- | :--- |
| 1e5 | 10 | 2950.9 ± 1260.2 (31.6%) |
| 1e5 | - | 2975.4 ± 1503.5 (25.2%) |
| 1e4 | 10 | 3193.9 ± 1044.2 (26.1%) |
| 1e4 | - | 2892.4 ± 908.3 (26.8%) |