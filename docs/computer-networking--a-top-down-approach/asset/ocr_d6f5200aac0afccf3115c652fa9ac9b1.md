+   * For each neighbor $v$, the cost $c(x,v)$ from $x$ to directly attached neighbor, $v$* Node $x$'s distance vector, that is, $\mathbf{D}_{x} = [D_{x}(y): y \text{ in } N]$, containing $x$'s estimate of its cost to all destinations, $y$, in $N$* The distance vectors of each of its neighbors, that is, $\mathbf{D}_{v} = [D_{v}(y): y \text{ in } N]$ for each neighbor $v$ of $x$

In the distributed, asynchronous algorithm, from time to time, each node sends a copy of its distance vector to each of its neighbors. When a node $x$ receives a new distance vector from any of its neighbors $w$, it saves $w$'s distance vector, and then uses the Bellman-Ford equation to update its own distance vector as follows:

$$D_{x}(y) = \min_{v} \{c(x, v) + D_{v}(y)\} \quad \text{for each node } y \text{ in } N$$

If node $x$'s distance vector has changed as a result of this update step, node $x$ will then send its updated distance vector to each of its neighbors, which can in turn update their own distance vectors. Miraculously enough, as long as all the nodes continue to exchange their distance vectors in an asynchronous fashion, each cost estimate $D_{x}(y)$ converges to $d_{x}(y)$, the actual cost of the least-cost path from node $x$ to node $y$ [Bertsekas 1991]!

# Distance-Vector (DV) Algorithm

At each node, $x$:

```
1. **Initialization:**
2. for all destinations y in N:
3. `D_x(y) = c(x,y) /* if y is not a neighbor then c(x,y) = \infty */` 
4. for each neighbor w
5. `D_w(y) = ? for all destinations y in N` 
6. for each neighbor w
7. send distance vector `D_x = [D_x(y): y in N]` to w
8. 
9. **loop** 
10. **wait** (until I see a link cost change to some neighbor w or
11. until I receive a distance vector from some neighbor w)
12. 
13. for each y in N:
14. `D_x(y) = min_v {c(x,v) + D_v(y)}` 
15. 
16. **if** `D_x(y)` changed for any destination y 
17. send distance vector `D_x = [D_x(y): y in N]` to all neighbors
18. 
19. **forever**
```