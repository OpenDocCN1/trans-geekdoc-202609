# Table 3. Evaluating edge composition of optimal densest swam solutions using five reward functions on two hypergraphs: CHS and CPS.

| | atleast-two | atleast-half | all-but-one | |E(S)| | |S| |
|---|---|---|---|---|---|---|
| | CHS CPS | CHS CPS | CHS CPS | CHS CPS | CHS CPS |
| atleast-two | 3791 7932 | 3791 7932 | 3762 7956 | 3053 6052 | 140 131 |
| atleast-half | 3791 7932 | 3791 7932 | 3762 7956 | 3053 6052 | 140 131 |
| all-but-one | 4055 8349 | 4055 8349 | 4039 8303 | 3404 6574 | 150 138 |
| standard | 6182 11341 | 6182 11341 | 6175 11337 | 6041 10895 | 236 200 |
| quadratic | 757 4206 | 757 4206 | 755 4152 | 651 3040 | 29 75 |

$s_e = r_e$) usually produces the best approximation results among peeling methods, despite the fact that our approximation guarantees do not apply to this approach.

**Qualitative Comparison.** As a final point of comparison, Table 3 reports qualitative aspects of the dense subsets produced by exactly solving SWAMP (using Exact) with different reward functions on two hypergraphs (CFS and CPS). The columns atleast-two, atleast-half, and all-but-one list the number of hyperedges (fully or partially contained in S) that intersect S in at least two nodes, at least $\lceil |e|/2 \rceil$ nodes, or at least $|e| - 1$ nodes, respectively. We also report the number of edges completely contained ($|E(S)|$) and the subset size ($|S|$). Each reward function leads to a dense subset with distinct characteristics: for instance, the standard objective tends to produce larger subgraphs whereas the quadratic objective tends to produce smaller subgraphs. This provides a simple check that finding the densest SWAMP using different reward functions does indeed allow us to capture meaningfully different types of density patterns in practice.

# 8 Conclusions and Discussion

We have presented comprehensive hardness results and new approximation algorithms for a dense subhypergraph objective where rewards are given for partially included edges. Our most significant finding is that peeling algorithms can achieve the same approximation guarantee for **NP**-hard variants of the problem as they do for poly-time variants that are special cases of the densest supermodular subset problem. This is somewhat surprising given that previous approximations for peeling seem to inherently rely on the supermodularity property. As one interesting observation, our theory does not apply to the standard greedy peeling strategy ($s_e = r_e$), but this strategy still seems to work well in practice. One open direction is to explore whether there are cases where the standard greedy strategy performs poorly, or whether we can prove an approximation for this approach using a different technique. Another direction for future work is to explore hardness of approximation results for **NP**-hard variants of SWAMP.