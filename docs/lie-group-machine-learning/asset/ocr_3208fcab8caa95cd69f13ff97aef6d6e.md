The algorithm lays the foundation for the establishment of the cell boundary homomorphism model.

Let $X$ be a cell complex. We denote $\{e_i^q\}$ as a set of cells in $X$. Then, in the $q$-dimensional cell chain group, marginal homomorphism $\partial_q$ can be written as $\partial_q(e_i^q) = \sum_j [e_i^q: e_j^{q-1}] e_j^{q-1}$. The coefficient $[e_i^q: e_j^{q-1}]$ is the coefficient of correlation between the two cells. The matrix $\{[e_i^q: e_j^{q-1}]\}$ consisting of correlation coefficients is called an incidence matrix.

To calculate the correlation coefficient $([e_i^q: e_j^{q-1}])$, we take a point $b \in e^{q+1}$. Its preimage under paste map $\pi_{(q+1)}$ is a pair of radial points $a, a'$ in $S^{(q-1)}$. Because the degree of path mapping is in $S^{(q-1)}$, the two preimage points $a, a'$ differ by $(-1)^q$ times. The adjustable orientation $e^q$ allows the value of $a$ to be positive.

Thus, the chain $C_*(P^n)$ assumes the following shape:

$$ \begin{array}{ccccccc} \text{Odem} & 0 & \text{1dem} & 2 & \dots & 0 \text{ odd dem} & 2 \text{ even dem} & 0 \text{ odd dem} & 2 & \dots & 1+(−1)^n \text{ n dem} \\ \mathbb{Z} & \longleftarrow & \mathbb{Z} & \longleftarrow & \dots & \longleftarrow & \mathbb{Z} & \longleftarrow & \mathbb{Z} & \longleftarrow & \dots & \longleftarrow & \mathbb{Z} \end{array} $$

The regular cell complex is smaller than the cell complex but is simpler than the simplicial complex. By introducing the concept of regular cell complex, the coherence and the edge of the cell complex are discussed.

A cellular complex structure in a compact Hausdorff space is defined as the decomposition of a cell $X$ into the union of finite disjoint cells $\{s_i^q|q \geq 0, 1 \leq i \leq r_q; r_q \geq 0\}$, such that: (1) For any $q$-dimensional cell $s_i^q$, there exists a continuous mapping $\varphi_i^q: D^q \rightarrow X$ that homeomorphically maps $D^q - S^{q-1}$ to $s_i^q$. (2) Every point of the edge $\bar{s}_i^q: = \bar{s}_i^q - s_i^q$ of the $q$-dimensional cell belongs to the cell whose dimension is less than $q$.

The $q$-dimensional skeleton $X^q: = \cup_{k \leq q} s_i^k$ of $X$ is the union of cells whose dimension $\leq q$ in $X$. It is a closed subset of $X$.

A closed subset $A$ of $X$ is called the sub-complex of $X$ if $A$ is the union of some cells in $X$. These cells naturally give the cell subdivision $A^q = A \cap X^q$ of $A$.

**Definition 14.12.** The complex structure on the cell $X$ is called regular if it satisfies a stronger condition than (1) and (2) of the above definition:

+   - (1') For any $q$-dimensional cell $s_i^q$, there exists $\varphi_i': (D^q, S^{q-1}) \rightarrow (\bar{s}_i^q, s_i^q)$;
- (2') The margin of each cell $s_i^q$ is the union of cells in $X$. In other words, the edge of each cell is a child complex of $X$. In this section, we only consider the regular cell complex.

The simplicial complex is obviously a regular cell, and it can be proved that any regular cellular complex can be further divided into simplicial complexes.

The cell chain group is further considered, and each cell $s$ of the regular cell complex K is assumed to have an orientation. Obviously, the zero-dimensional simplex has only one orientation. As can be seen from the front, the q-dimensional cell chain