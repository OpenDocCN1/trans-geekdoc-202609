
## Independent subproblems

Independence can be ascertained simply by finding connected components of the constraint graph. Each component corresponds to a subproblem `CSPi`. If assignment `Si` is a solution of `CSPi`, then `⋃iSi` is a solution of `⋃iCSPi`. Why is this important? Suppose each `CSPi` has `c` variables from the total of `n` variables, where `c` is a constant. Then there are `n/c` subproblems, each of which takes at most `dc` work to solve, where `d` is the size of the domain. Hence, the total work is `O(dcn/c)`, which is linear in `n`; without the decomposition, the total work is `O(dn)`, which is exponential in `n`. Let’s make this more concrete: dividing a Boolean `CSP` with 100 variables into four subproblems reduces the worst-case solution time from the lifetime of the universe down to less than a second.

## Connected component

Completely independent subproblems are delicious, then, but rare. Fortunately, some other graph structures are also easy to solve. For example, a constraint graph is a tree when any two variables are connected by only one path. We will show that any tree-structured `CSP` can be solved in time linear in the number of variables.[4](#Chapter05-07.xhtml#sup05-4) The key is a new notion of consistency, called directional arc consistency or `DAC`. A `CSP` is defined to be directional arc-consistent under an ordering of variables `X1,X2,...,Xn` if and only if every `Xi` is arc-consistent with each `Xj` for `j > i`.

## Directional arc consistency

To solve a tree-structured `CSP`, first pick any variable to be the root of the tree, and choose an ordering of the variables such that each variable appears after its parent in the tree. Such an ordering is called a topological sort. [Figure 5.10(a)](#Chapter05-05.xhtml#fig5-10) shows a sample tree and [(b)](#Chapter05-05.xhtml#fig5-10) shows one possible ordering. Any tree with `n` nodes has `n – 1` edges, so we can make this graph directed arc-consistent in `O(n)` steps, each of which must compare up to `d` possible domain values for two variables, for a total time of `O(nd2)`. Once we have a directed arc-consistent graph, we can just march down the list of variables and choose any remaining value. Since each edge from a parent to its child is arc-consistent, we know that for any value we choose for the parent, there will be a valid value left to choose for the child. That means we won’t have to backtrack; we can move linearly through the variables. The complete algorithm is shown in [Figure 5.11](#Chapter05-05.xhtml#fig5-11).

## Topological sort

 Description 

Two three-level binary trees are shown. Up and down triangles represent `MAX` and `MIN` nodes, respectively, and circles represent `CHANCE` nodes. Binary tree 1: The first level of the game tree is labeled `MAX` and a `MAX` node is present. The node connects to two nodes in the second level. The second level is labeled `CHANCE` and the two nodes are `CHANCE` nodes labeled 2.1 and 1.3. An arrow labeled “a” subscript 1 from the `MAX` node connects to node 2.1. A path labeled “a” subscript 2 from the `MAX` node connects to node 1.3. The two nodes in the `CHANCE` level each have two child nodes in the third level. The third level is labeled `MIN` and has four `MIN` nodes. The two child nodes of 2.1 are labeled 2 and 3. Paths labeled 0.9 and 0.1 from node 2.1 connect to nodes 2 and 3, respectively. The two child nodes of 1.3 are labeled 1 and 4. Paths labeled 0.9 and 0.1 from node 1.3 connect to nodes 1 and 4, respectively. The two child nodes of 1 are labeled 1 and 1. The two child nodes of 2 are labeled 2 and 2. The two child nodes of 3 are labeled 3 and 3. The two child nodes of 4 are labeled 4 and 4. Binary tree 2: The first level of the game tree is labeled `MAX` and a `MAX` node is present. The node connects to two nodes in the second level. The second level is labeled `CHANCE` and the two nodes are `CHANCE` nodes labeled 21 and 40.9. An arrow labeled “a” subscript 2 from the `MAX` node connects to node 40.9. A path labeled “a” subscript 1 from the `MAX` node connects to node 21. The two nodes in the `CHANCE` level each have two child nodes in the third level. The third level is labeled `MIN` and has four `MIN` nodes. The two child nodes of 21 are labeled 20 and 30. Paths labeled 0.9 and 0.1 from node 21 connect to nodes 20 and 30, respectively. The two child nodes of 40.9 are labeled 1 and 400. Paths labeled 0.9 and 0.1 from node 40.9 connect to nodes 1 and 400, respectively. The two child nodes of 1 are labeled 1 and 1. The two child nodes of 20 are labeled 20 and 20. The two child nodes of 30 are labeled 30 and 30. The two child nodes of 400 are labeled 400 and 400.

×![](images/Fig-81.jpg)

Figure 5.10(a) The constraint graph of a tree-structured CSP. (b) A linear ordering of the variables consistent with the tree with `A` as the root. This is known as a topological sort of the variables.

## Topological sort

 Description 

Five reduced chess boards are shown. The chess boards are reduced to 4 by 4, with row labels “a” to d from left to right and column labels 1 to 4 from bottom to top. Board 1: The blacks are in the following positions. Kings, “a” 4, b 4, and c 4. The whites are in the following positions. King, d 2. Rook d 3. A line labeled K c 3 question mark from Board 1 connects to a circular node. An arrow labeled Illegal from the node points to board 2. Board 2: The blacks are in the following positions. Kings, b 4 and c 4. The whites are in the following positions. King, d 2. Rook d 3. A line labeled R c 3 connects Board 2 to a second circular node. An arrow labeled OK from the second node points to board 3. Board 3: A black is in the following position. King, b 4. The whites are in the following positions. King, d 2. Rook c 3. Another arrow labeled Check from the second node points to board 4. Board 4: A black is in the following position. King, b 4. The whites are in the following positions. King, d 2. Rook c 3. An arrow labeled OK from the first node points to board 5. Board 5: A black is in the following position. King, "a" 4. The whites are in the following positions. King, c 3. Rook d 3.

×![](images/Fig-82.jpg)

Figure 5.11The `TREE\-CSP-SOLVER` algorithm for solving tree-structured CSPs. If the `CSP` has a solution, we will find it in linear time; if not, we will detect a contradiction.

Now that we have an efficient algorithm for trees, we can consider whether more general constraint graphs can be reduced to trees somehow. There are two ways to do this: by removing nodes ([Section 5.5.1](#Chapter05-05.xhtml#sec5-5-1)) or by collapsing nodes together ([Section 5.5.2](#Chapter05-05.xhtml#sec5-5-2)).

## 5.5.1 Cutset conditioning

The first way to reduce a constraint graph to a tree involves assigning values to some variables so that the remaining variables form a tree. Consider the constraint graph for Australia, shown again in [Figure 5.12(a)](#Chapter05-05.xhtml#fig5-12). Without South Australia, the graph would become a tree, as in [(b)](#Chapter05-05.xhtml#fig5-12). Fortunately, we can delete South Australia (in the graph, not the country) by fixing a value for `SA` and deleting from the domains of the other variables any values that are inconsistent with the value chosen for `SA`.

 Description 

The first level of game tree is labeled `MAX` and the node is labeled "A". Node "A" has two child nodes. Node "A" is represented by an up triangle. The second level is labeled `MIN` and the two nodes are labeled 99 and 100. The two nodes are represented by down triangles and each has four child nodes. The four child nodes of B are labeled 99, 1000, 1000, and 1000 and represented by up triangles. The four child nodes of 100 are labeled 100, 101, 102, and 103 and represented by up triangles.

×![](images/Fig-83.jpg)

Figure 5.12(a) The original constraint graph from [Figure 5.1](#Chapter05-01.xhtml#fig5-1). (b) After the removal of `SA`, the constraint graph becomes a forest of two trees.
