
We can see that the Bellman-Ford algorithm also considers the edges and vertices in finding the shortest path between nodes. This is known as the relaxation process, which is also used in Dijkstra's algorithm. The relaxation process in graph algorithms refers to the updating of the cost of all vertices connected to a vertex `V` if those costs would be improved by including the path via `V`. In simple words, the relaxation process is trying to lower the cost of getting to a vertex using another vertex. Now, we will implement this algorithm for the same graph we used in Dijkstra's algorithm. The only difference is that here we will use numeric labels for our nodes and vertex here:

![](Image00086.jpg)

Now it is time to represent the graph in an adjacency matrix format. Here is the matrix in PHP:

```
$graph = [ 

    0 => [0, 3, 5, 9, 0, 0], 

    1 => [3, 0, 3, 4, 7, 0], 

    2 => [5, 3, 0, 2, 6, 3], 

    3 => [9, 4, 2, 0, 2, 2], 

    4 => [0, 7, 6, 2, 0, 5], 

    5 => [0, 0, 3, 2, 5, 0] 

]; 
```

Previously, we used a value of 0 to indicate that there was no edge between two vertices. If we do the same here, then taking a minimum between two edges where one represents 0 will always yield a 0 during the relaxation process, which actually means that there is no connection between two vertices. As a result, we have to choose a larger number to represent the non-existent edges. We can use the `MAX_INT_VALUE` constant of PHP to represent those edges so that those non-existent edges are not considered. This can be our new graph representation:

```
define("I", PHP_INT_MAX); 



$graph = [ 

    0 => [I, 3, 5, 9, I, I], 

    1 => [3, I, 3, 4, 7, I], 

    2 => [5, 3, I, 2, 6, 3], 

    3 => [9, 4, 2, I, 2, 2], 

    4 => [I, 7, 6, 2, I, 5], 

    5 => [I, I, 3, 2, 5, I] 

]; 
```

Now, let's write the implementation for the Bellman-Ford algorithm. We will use the same approach we defined in the pseudocode:

```
function bellmanFord(array $graph, int $source): array { 

    $dist = []; 

    $len = count($graph); 



    foreach ($graph as $v => $adj) { 

      $dist[$v] = PHP_INT_MAX; 

    } 



    $dist[$source] = 0; 



    for ($k = 0; $k < $len - 1; $k++) { 

      for ($i = 0; $i < $len; $i++) { 

          for ($j = 0; $j < $len; $j++) { 

            if ($dist[$i] > $dist[$j] + $graph[$j][$i]) { 

            $dist[$i] = $dist[$j] + $graph[$j][$i]; 

        } 

          } 

      } 

    } 



    for ($i = 0; $i < $len; $i++) { 

      for ($j = 0; $j < $len; $j++) { 

          if ($dist[$i] > $dist[$j] + $graph[$j][$i]) { 

           echo 'The graph contains a negative-weight cycle!'; 

           return []; 

          } 

      } 

        } 

    return $dist; 

} 
```

Unlike Dijkstra's algorithm, we are not tracking the predecessors. We are considering the distance during the relaxation process. Since we are using the maximum value for an integer in PHP, it automatically cancels out the possibility of choosing a nonexistent edge with a value of 0 as the minimum path. The last part of the implementation detects any negative cycle in the given graph and returns an empty array in that case:

```
$source = 0; 

$distances = bellmanFord($graph, $source); 



foreach($distances as $target => $distance) { 

    echo "distance from $source to $target is $distance \n"; 

} 
```

This will have the following output, which shows the shortest path distance from our source node to other nodes:

```
distance from 0 to 0 is 0



distance from 0 to 1 is 3



distance from 0 to 2 is 5



distance from 0 to 3 is 7



distance from 0 to 4 is 9



distance from 0 to 5 is 8
```

The Bellman-Ford algorithm has the run-time complexity of `O(V, E)`.

# Understanding the minimum spanning tree (MST)

Suppose we are designing our new office campus with multiple buildings interconnected to each other. If we approach the problem by considering the interconnectivity between each building, it will take a huge number of cables. However, if we could somehow connect all the buildings through a common connectivity where each building is connected to every other building with only one connection, then this solution will reduce the redundancy and cost. If we think of our buildings as vertices and the connectivity between buildings as the edges, we can construct a graph using this approach. The problem we are trying to solve is also known as the **minimum spanning tree**, or **MST**. Consider the following graph. We have 10 vertices and 21 edges. However, we can connect all 10 vertices with only nine edges (the dark line). This will keep our cost or distance to a minimal level:

![](Image00087.jpg)

There are several algorithms that we can use to find an MST from a given graph. The two most popular are Prim's algorithm and Kruskal's algorithm. We will explore these two algorithms in the upcoming sections.

# 读累了记得休息一会哦~

**公众号：古德猫宁李**

*   电子书搜索下载
*   书单分享
*   书友学习交流

**网站：**[沉金书屋 https://www.chenjin5.com](https://www.chenjin5.com)

*   电子书搜索下载
*   电子书打包资源分享
*   学习资源分享

# Implementing Prim's spanning tree algorithm

Prim's algorithm for finding the minimum spanning tree relies on a greedy approach. A greedy approach is defined as an algorithm paradigm where we try to find the global optimal solution by considering the local optimal solution at each stage. We will explore greedy algorithms in [Chapter 11](#text00238.html), *Solve Problems with Advanced Techniques*. In a greedy approach, the algorithm creates subsets of edges and finds out the least costly one from the subset of edges. This subset of edges will include all vertices. It starts from an arbitrary position and grows the tree one vertex at a time by choosing the cheapest possible connection between the vertices. Let's consider the following graph:

![](Image00088.jpg)

Now, we will apply a very basic version of Prim's algorithm to get the minimum spanning tree as well as the minimum cost or weight of the edges. The graph will look like this as an adjacency matrix:

```
$G = [ 

    [0, 3, 1, 6, 0, 0], 

    [3, 0, 5, 0, 3, 0], 

    [1, 5, 0, 5, 6, 4], 

    [6, 0, 5, 0, 0, 2], 

    [0, 3, 6, 0, 0, 6], 

    [0, 0, 4, 2, 6, 0] 

]; 
```

Now, we will implement the algorithm for Prim's minimum spanning tree. We are assuming that we are going to start from vertex 0 to find out the whole spanning tree, so we will just pass the graph adjacency matrix in the function, and it will display the connecting edges for the spanning tree along with the minimum cost:

```
function primMST(array $graph) { 

    $parent = [];   // Array to store the MST 

    $key = [];     // used to pick minimum weight edge         

    $visited = [];   // set of vertices not yet included in MST 

    $len = count($graph); 



    // Initialize all keys as MAX 

    for ($i = 0; $i < $len; $i++) { 

      $key[$i] = PHP_INT_MAX; 

      $visited[$i] = false; 

    } 



    $key[0] = 0; 

    $parent[0] = -1; 



    // The MST will have V vertices 

    for ($count = 0; $count < $len - 1; $count++) { 

  // Pick the minimum key vertex 

  $minValue = PHP_INT_MAX; 

  $minIndex = -1; 



  foreach (array_keys($graph) as $v) { 

      if ($visited[$v] == false && $key[$v] < $minValue) { 

        $minValue = $key[$v]; 

        $minIndex = $v; 

      } 

  } 



  $u = $minIndex; 



  // Add the picked vertex to the MST Set 

  $visited[$u] = true; 



  for ($v = 0; $v < $len; $v++) { 

      if ($graph[$u][$v] != 0 && $visited[$v] == false && 

        $graph[$u][$v] < $key[$v]) { 

          $parent[$v] = $u; 

          $key[$v] = $graph[$u][$v]; 

      } 

  } 

    } 



    // Print MST 

    echo "Edge\tWeight\n"; 

    $minimumCost = 0; 

    for ($i = 1; $i < $len; $i++) { 

      echo $parent[$i] . " - " . $i . "\t" . $graph[$i][$parent[$i]] 

         "\n"; 

      $minimumCost += $graph[$i][$parent[$i]]; 

    } 

    echo "Minimum cost: $minimumCost \n"; 

} 
```
