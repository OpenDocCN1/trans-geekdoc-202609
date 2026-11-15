maximum value on each node in the current part. This dynamic programming algorithm costs slightly more time but can get a much tighter upper bound.

# Merging $T$ independent sets

To refine the relatively loose single-level bound, the multilevel algorithm partitions the graph into $K/T$ subgraphs, each with $T$ independent sets. Within each subgraph, we find all the $T$-cliques and use a new “pseudo-node” to represent each $T$-clique. $T$-cliques in a subgraph can be enumerated efficiently if we choose $T$ to be a relatively small number (e.g., 2 or 3 in the experiments).

Next, we need to form the graph at the next level by merging nodes in the previous level. By Lemma 4 we know that the intersection of $T$ boxes will still be a box, so each $T$-clique is still a box and can be represented as a pseudo-node in the level-2 graph. Also, because each pseudo-node is still a box, we can easily form edges between pseudo-nodes to indicate the nonempty overlapping between them, and this will be a $(K/T)$-partite boxicity graph since no edge can be formed for the cliques within the same subgraph. Thus we get the level-2 graph. With the level-2 graph, we can again run the single-level algorithm to compute an upper bound on $v^*$ to get a lower bound of $r^*$, but differently from the level-1 graph, now we already considered all the within-subgraph edges, so the bounds will be much tighter.

# The overall multilevel framework

We can run the algorithm level-by-level, and at each level the single-level algorithm will output a valid upper bound for verification. As we go to the next level, since the interconnections between the merged parts will be considered, the bounds will also get tighter. In the final level, the pseudo-nodes will correspond to the $K$-cliques in the original graph, and the maximum value will be the exact solution for the max clique problem. Therefore the algorithm can be viewed as an anytime algorithm that refines the upper bound level-by-level until reaching the maximum value.

# Training robust tree ensembles

Similar to neural networks, to enhance the robustness of tree ensembles, we can consider both empirical defense and certified defense. For both of