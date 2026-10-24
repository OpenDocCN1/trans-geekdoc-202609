
![](img/90c930779c8f928df6ff4481fc59f9a3_248_0.png)

### FIGURE 5.19
Lexicographic search tree.

subscripted graph and its DFS code as the same. All the notations on subscripted graphs can also be applied to DFS codes. The graph represented by a DFS code \(\alpha\) is written \(G_\alpha\).

Second, we define an order among edge sequences. Since one graph may have several DFS codes, we want to build an order among these codes and select one code to represent the graph. Since we are dealing with labeled graphs, the label information should be considered as one of the ordering factors. The labels of vertices and edges are used to break the tie when two edges have the exactly same subscript, but different labels. Let the edge order relation \(\prec_T\) take the first priority, the vertex label \(l_i\) take the second priority, the edge label \(l_{(i,j)}\) take the third, and the vertex label \(l_j\) take the fourth to determine the order of two edges. For example, the first edge of the three DFS codes in Table 5.6 is (0, 1, _X_, _a_, _X_), (0, 1, _X_, _a_, _X_), and (0, 1, _Y_, _b_, _X_), respectively. All of them share the same subscript (0, 1). Therefore relation \(\prec_T\) cannot tell the difference among them. However, using label information, following the order of first vertex label, edge label, and second vertex label, we have (0, 1, _X_, _a_, _X_) < (0, 1, _Y_, _b_, _X_). The ordering based on the above rules is called **DFS Lexicographic Order**. According to this ordering, we have \(\gamma_0 \prec \gamma_1 \prec \gamma_2\) for the DFS codes listed in Table 5.6.

Based on the DFS lexicographic ordering, the **minimum DFS code** of a given graph _G_, written as dfs(_G_), is the minimal one among all the DFS codes. For example, code \(\gamma_0\) in Table 5.6 is the minimum DFS code of the graph in Fig. 5.17(a). The subscripting that generates the minimum DFS code is called the **base subscripting**.

We have the following important relationship between the minimum DFS code and the isomorphism of the two graphs: Given two graphs _G_ and \(G'\), _G_ is isomorphic to \(G'\) if and only if dfs(_G_) = dfs(\(G'\)). Based on this property, what we need to do for mining frequent subgraphs is to perform only the right-most extensions on the minimum DFS codes since such an extension will guarantee the completeness of mining results.

Fig. 5.19 shows how to arrange all DFS codes in a search tree through right-most extensions. The root is an empty code. Each node is a DFS code encoding a graph. Each edge represents a right-most extension from a (_k_-1)-length DFS code to a _k_-length DFS code. The tree itself is ordered: left siblings are smaller than right siblings in the sense of DFS lexicographic order. Since any graph has at least one DFS code, the search tree can enumerate all possible subgraphs in a graph data set. However, one graph may have several DFS codes, minimum and nonminimum. The search of nonminimum DFS codes does not produce a useful result. “Is it necessary to perform right-most extension on nonminimum DFS codes?” The answer is “no.” If codes _s_ and \(s'\) in Fig. 5.19 encode the same graph, the search space under \(s'\) can be safely pruned.

```
Algorithm: gSpan(s, D, minsup, S)
Input: A DFS code s, a graph data set D, and min_support.
Output: The frequent graph set S.
1: if s ≠ dfs(s), then
2:     return;
3: insert s into S;
4: set C to ∅;
5: scan D once, find all the edges e such that s can be right-most extended to s ⊕r e;
insert s ⊕r e into C and count its frequency;
6: sort C in DFS lexicographic order;
7: for each frequent s ⊕r e in C do
8:     Call gSpan(s ⊕r e, D, minsup, S);
9: return;
```

### FIGURE 5.20
gSpan: A pattern-growth algorithm for frequent substructure mining.

The details of gSpan are depicted in Fig. 5.20. gSpan is called recursively to extend graph patterns so that their frequent descendants are found until their support is lower than minsup or its code is not minimum any more. The difference between gSpan and PatternGrowth is at the right-most extension and extension termination of nonminimum DFS codes (lines 1–2). We replace the existence judgment in lines 1–2 of PatternGrowth with the inequation s ≠ dfs(s). Actually, s ≠ dfs(s) is more efficient to calculate. Line 5 requires exhaustive enumeration of s in D in order to count the frequency of all the possible right-most extensions of s.

The algorithm of Fig. 5.20 implements a depth-first search version of gSpan. Actually, breadth-first search works too: for each newly discovered frequent subgraph in line 8, instead of directly calling gSpan, we insert it into a global first-in-first-out queue Q, which records all subgraphs that have not been extended. We then “gSpan” each subgraph in Q one by one. The performance of a breadth-first search version of gSpan is very close to that of the depth-first search although the latter usually consumes less memory.

## 5.5.2 Mining variant and constrained substructure patterns

The frequent subgraph mining discussed in the previous section handles only one special kind of graph: labeled, undirected, connected simple graphs without any specific constraints. That is, we assume that the database to be mined contains a set of graphs each consisting of a set of labeled vertices and labeled but undirected edges, with no other constraints. However, many applications or users may need to enforce various kinds of constraints on the patterns to be mined or seek variant substructure patterns. For example, we may like to mine patterns, each of which contains certain specific vertices/edges, or where the total number of vertices/edges is within a specified range. Or what if we seek patterns where the average density of the graph patterns is above a threshold? Although it is possible to develop customized algorithms for each such case, there are too many variant cases to consider. Instead, a general framework is needed—one that can organize variants and constraints and help develop efficient mining methods systematically. In this section, we study several variants and constrained substructure patterns and look at how they can be mined.

### Mining closed frequent substructures

The first important variation of a frequent substructure is the **closed frequent substructure**. Take mining frequent subgraph as an example. Similar to mining frequent itemsets and mining sequential patterns, mining graph patterns may generate an explosive number of patterns. According to the Apriori property, all the subgraphs of a frequent graph are frequent. Thus a large graph pattern may generate an exponential number of frequent subgraphs. For example, among 423 confirmed active chemical compounds in an AIDS antiviral screen data set, there are nearly 1,000,000 frequent graph patterns whose support is at least 5%. This renders the further analysis on frequent graphs nearly impossible.

One way to alleviate this problem is to mine only frequent closed graphs, where a frequent graph _G_ is closed if and only if there does not exist a proper supergraph $G'$ that has the same support as _G_. Alternatively, we can mine maximal subgraph patterns where a frequent pattern _G_ is **maximal** if and only if there does not exist a frequent superpattern of _G_. A set of closed subgraph patterns has the same expressive power as the full set of subgraph patterns under the same minimum support threshold because the latter can be generated by the derived set of closed graph patterns. On the other hand, the maximal pattern set is a subset of the closed pattern set. It is usually more compact than the closed pattern set. However, we cannot use it to reconstruct the entire set of frequent patterns—the support information of a pattern is lost if it is a proper subpattern of a maximal pattern, yet carries a different support.

**Example 5.23. Maximal frequent graph.** The two graphs in Fig. 5.13 are closed frequent graphs but only the first graph is a maximal frequent graph. The second graph is not maximal because it has a frequent supergraph.

Mining closed graphs led to a complete but more compact representation. For example, for the AIDS antiviral data set mentioned above, among the one million frequent graphs, only about 2000 are closed frequent graphs. If further analysis, such as classification or clustering, is performed on closed frequent graphs instead of frequent graphs, it will achieve similar accuracy with less redundancy and higher efficiency.

An efficient method, called CloseGraph, was developed for mining closed frequent graphs by extension of the gSpan algorithm. The key for efficient mining of closed frequent subgraphs is to figure out at what condition that the further growth of a frequent subgraph _g_ should be pruned when its _e_-expanded subgraph $g'$ has the same support as _g_. Experimental study has shown that CloseGraph often generates far fewer graph patterns and runs more efficiently than gSpan, which mines the full subgraph pattern set.

### Extension of pattern-growth approach: mining alternative substructure patterns

A typical pattern-growth graph mining algorithm, such as gSpan or CloseGraph, mines _labeled_, _connected_, _undirected_ frequent or closed subgraph patterns. Such a graph mining framework can be extended easily for mining _alternative substructure patterns_. Here we discuss a few such alternatives.

First, the method can be extended for **mining unlabeled** or **partially labeled graphs**. Each vertex and each edge in our previously discussed graphs contain labels. Alternatively, if none of the vertices and edges in a graph are labeled, the graph is **unlabeled**. A graph is **partially labeled** if only some of the edges and/or vertices are labeled. To handle such cases, we can build a label set that contains the original label set and a new empty label, $\phi$. Label $\phi$ is assigned to vertices and edges that do not have labels. Notice that label $\phi$ may match with any label or with $\phi$ only, depending on the application
