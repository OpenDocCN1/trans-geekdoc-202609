+   3. For each neighbor vertex, compare its value to the searched value.
+   4. Move to the next neighbor's neighbors.
+   5. Repeat steps 3 and 4.

Using the same graph above and the value 9 as the target, start the breadth-first search by invoking the graph list, and then each vertex sublist, without visiting the neighbors in the vertex.

```
a -> 2 b:d:f
b -> 4 e
d -> 8 e:f
f -> 3 c:g
e -> 1 c:f
c -> 9 ... a match in 6 iterations.
```

# 17.3.7 Graph Paths

Graph theory includes a category of problems for computing the shortest path between any two vertices. This involves computing the cumulative weights of all adjoining vertices between any two terminal vertices. The solution for a shortest-path problem is the path having the minimum cumulative distance. To avoid infinite loops, traversal of the graph must avoid cycles by not revisiting vertices.3

There are variety of complex algorithms for computing path lengths. Some are considered brute-force approaches, as they compute the shortest path between all vertex pairs. Such brute-force algorithms generally have O(n^3) efficiency. One example is the all-pairs or Floyd-Marshall algorithm. However,