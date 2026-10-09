**P6.** Consider a general topology (that is, not the specific network shown above) and a synchronous version of the distance-vector algorithm. Suppose that at each iteration, a node exchanges its distance vectors with its neighbors and receives their distance vectors. Assuming that the algorithm begins with each node knowing only the costs to its immediate neighbors, what is the maximum number of iterations required before the distributed algorithm converges? Justify your answer.

**P7.** Consider the network fragment shown below. $x$ has only two attached neighbors, $w$ and $y$. $w$ has a minimum-occur path to destination $u$ (not shown) of 5, and $y$ has a minimum-cost path to $u$ of 6. The complete paths from $w$ and $y$ to $u$ (and between $w$ and $y$) are not shown. All link costs in the network have strictly positive integer values.

![](bbox=[0.45, 0.37, 0.63, 0.47])

+   a. Give $x$'s distance vector for destinations $w$, $y$, and $u$.
b. Give a link-cost change for either $c_{(x, w)}$ or $c_{(x, y)}$ such that $x$ will inform its neighbors of a new minimum-cost path to $u$ as a result of executing the distance-vector algorithm.
c. Give a link-cost change for either $c_{(x, w)}$ or $c_{(x, y)}$ such that $x$ will *not* inform its neighbors of a new minimum-cost path to $u$ as a result of executing the distance-vector algorithm.

**P8.** Consider the three-node topology shown in Figure 5.6. Rather than having the link costs shown in Figure 5.6, the link costs are $c_{(x, y)} = 3$, $c_{(y, z)} = 6$, $c_{(z, x)} = 4$. Compute the distance tables after the initialization step and after each iteration of a synchronous version of the distance-vector algorithm (as we did in our earlier discussion of Figure 5.6).

**P9.** Consider the count-to-infinity problem in the distance vector routing. Will the count-to-infinity problem occur if we decrease the cost of a link? Why? How about if we connect two nodes which do not have a link?

**P10.** Argue that for the distance-vector algorithm in Figure 5.6, each value in the distance vector $D(x)$ is non-increasing and will eventually stabilize in a finite number of steps.

**P11.** Consider Figure 5.7. Suppose there is another router $w$, connected to router $y$ and $z$. The costs of all links are given as follows: $c_{(x, y)} = 4$, $c_{(x, z)} = 50$, $c_{(y, w)} = 1$, $c_{(z, w)} = 1$, $c_{(y, z)} = 3$. Suppose that poisoned reverse is used in the distance-vector routing algorithm.