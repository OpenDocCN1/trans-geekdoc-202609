procedure to break it down. Otherwise, the expectation is that the road data from the Tools department will be some list of roads in an array (or some container), since storing them this way assigns a unique “ID” to each road. For the purposes of this chapter, the index of each road in the container will be assigned to the corresponding vertex and assume they are indexes, instead of the output of some hash function. This is handy, as the road connections can be stored as a multimap of integers mapping to integers. In other words, a map<int, array<int>> or a dictionary<int, array<int>>. This can be seen in Table 13.1.

# TABLE 13.1

# Example Unique ID for Roads with Adjacent Roads Listed

| Vertex ID/Road Index | Adjacent Roads |
|---|---|
| 0 | 1, 2, 3 |
| 1 | 4 |
| 2 | 4 |
| 3 | 4 |
| 4 | None |

The benefit of taking this DAG approach is in a very central property, specific to this type of graph. Unlike the other types of graphs, where searching and pathfinding involves heavy-handed heuristics and cycle-braking techniques (A* and its cousins), while querying a complex, sometimes multidimensional container, nodes in DAGs have the mathematical property of having an order. This powerful property can be exploited by performing an operation called a topological sort and storing the sorted information in a linear container – an array (Cornen et al., 2009a).

There are multiple algorithms for performing a topological sort (Dasgupta et al., 2008; Cornen et al., 2009a) and while each has intrinsic benefits over the other, one relatively straightforward technique is to piggy-back on depth-first search (DFS). The high-level concept of DFS is that, starting at a vertex, you perform an operation on the current vertex and then recursively repeat this on adjacent vertices. Piggybacking on this idea is shown in Code Listing 13.1.

```
Code Listing 13.1: Recursive TOPO_SORT depth-first search.

function TOPO_SORT(array<int> vertices, multimap<int, array<int>> adjacent):
{
    stack<int> sorted = { empty }
    array<bool> visited = { all false };
    lambda onTopoSort(int vertex):
    {
        foreach(int otherVertex : adjacent[vertex])
        {
            if(visited[otherVertex])
            {
                onTopoSort(otherVertex);
```