for the $6 \times 6$ and $12 \times 12$ sizes are with respect to a global termination criterion for the $24 \times 24$ size, as seen in eqs (11) and (12). The agent begins by removing elements from the 6x6 topology until the initial intermediate termination criterion is met.

Next, the agent interacts with an equivalent $12 \times 12$ topology and continues to remove elements until a second intermediate termination criterion is met. Finally, the agent interacts with the equivalent $24 \times 24$ topology until the final, user-specified termination criterion is satisfied. An example of this sequence is represented in Fig. 13, where the final termination criterion is $VF_{24\times24}=0.25$. It should be noted that Eqs (11) and (12) would need to be adjusted if the final topology refinement were to extend to 48x48 or 96x96 and should be addressed as future work.

$VF_{6\times6} = 1 - \left( \frac{1 - VF_{24\times24}}{2.5} \right)$ (11)

$VF_{12\times12} = 1 - \left( \frac{1 - VF_{24\times24}}{1.5} \right)$ (12)

![](bbox=[0.1, 0.485, 0.9, 0.605])

Figure 13: Sequential element removal using progressive refinement.

The sequential decrease in allowable VF follows the work, found that the optimization method works better by gradually tightening the criteria with increasing refinement.

Removing a single coarse element from the $6 \times 6$ topology is equivalent to removing the 4 or 16 corresponding elements from the $12 \times 12$ or $24 \times 24$ topologies, respectively.

Therefore, the agent interacts with the intermediate $6 \times 6$ topology to produce a general, non-detailed shape that can be formed into an equivalent $12 \times 12$ topology. The agent can begin to produce low-level details at the $12 \times 12$ topology but will ultimately achieve its sufficiently detailed optimal design at the $24 \times 24$ topology size.