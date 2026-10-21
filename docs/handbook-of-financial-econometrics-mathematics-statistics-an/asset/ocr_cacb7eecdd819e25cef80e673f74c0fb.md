where Γ_N is the multivariate gamma function defined as

$$\Gamma_N(T/2) = \pi^{N(N-1)/4} \prod_{j=1}^{N} \Gamma\left(\frac{T}{2} + \frac{1 - j}{2}\right).$$

With the term |A|, it is easily seen that in general any pair (a_{ik}, a_{uv}) will not be independent even though the standardized returns (z_i, z_j, z_u, z_v) are uncorrelated.

This property can be also easily understood from a geometric viewpoint. Consider a market with four stocks. Suppose that the joint distribution for (z_1, z_2, z_3, z_4)' follows a multivariate normal distribution. Then z_i, i = 1, ..., 4, can be viewed as a point in a T-dimensional space. The edge between the (i, j) pair exists when the angle between the vectors z_i and z_j is smaller than some certain threshold. So we may map all the points to a (T − 1)-dimensional sphere. Figure 8.1 illustrates this example. Now consider the conditional probability under the null hypothesis

$$P(E_{12}, E_{34} \mid E_{13} = E_{14} = E_{23} = E_{24} = 0).$$

Clearly, even though the two edges E_{12} and E_{34} share no common vertices, they are still dependent on each other given the rest of the edges. With the information about the non-existence of other four edges, it is seen that the two sets of vertices (1, 2) and (3, 4) should be some distance away from each other on the sphere. However, when E_{34} =1, vertex 3 and 4 are close and the space allowed to allocate vertices 1 and 2 becomes larger and thus the probability for E_{12} = 1 becomes lower, and vice versa. Thus, while we have a finite number of stocks, any pairs of edges are dependent conditional on the rest of the edges.

![](bbox=[0.27, 0.6, 0.72, 0.88])

Figure 8.1: Dependency of edges. The four stocks are mapped onto a (T−1) dimensional sphere. The two edges (1, 2) and (3, 4) are conditionally dependent on (E13, E14, E23, E24).