# Single asset American options

![](bbox=[0.285, 0.103, 0.735, 0.368])

**Figure 5.1** A standard binomial lattice process of six time steps. The root lattice node R corresponds to the current time $t_0$, and the terminal nodes G to M are at option maturity; the asset value at node R is $S$, where $S$ is the current asset value. Asset values at other nodes, for example, node S: $S_u$, node T: $T_d$, node V: $S_s$, and node A: $S^u$. Option values are computed using a backward iterative process: the option values at A–F on the penultimate time step are computed from the payouts of the terminal nodes G–M, and this process continues until the root node is reached which yields the current value of the option. Here we compute the Greeks using the following nodes: Delta uses nodes S and T, Gamma uses nodes U, V, and $W$, and Theta uses nodes R and V.

The asset values at the labelled nodes are:

+   Lattice level 1: Time $t$
$S_R = S$
Lattice level 2: Time $t + \Delta t$
$S_S = Su, \quad S_T = Sd$
Lattice level 6: Time $t + 5\Delta t$
$S_A = Su^5, \quad S_B = Su^3, \quad S_C = Su$,
$S_D = Sd, \quad S_E = S, \quad S_F = Sd^5$\nLattice level 7: Time $t + 6\Delta t$
$S_G = Su^6, \quad S_H = Su^4, \quad S_I = Su^2, \quad S_J = S,
$S_K = Sd^2, \quad S_L = Sd^4, \quad S_M = Sd^6$