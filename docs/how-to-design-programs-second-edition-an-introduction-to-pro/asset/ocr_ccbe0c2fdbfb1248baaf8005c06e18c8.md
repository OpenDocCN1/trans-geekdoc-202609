What this header leaves open is the exact shape of the result. It implies that the result is a list of nodes, but it does not say which nodes it contains.

To appreciate this ambiguity and why it matters, let's study the examples from above. In ISL+, we can now formulate them like this:

```
(find-path 'C 'D sample-graph)
(find-path 'E 'D sample-graph)
(find-path 'C 'G sample-graph)
```

The first call to find-path must return a unique path, the second one must choose one from two, and the third one must signal that there is no path from 'c to 'G in sample-graph. Here are two possibilities, then, on how to construct the return value:

+   * The result of the function consists of all nodes leading from the origination node to the destination node, including those two. In this case, an empty path could be used to express the lack of a path between two nodes.

+   * Alternatively, since the call itself already lists two of the nodes, the output could mention only the “interior” nodes of the path. Then the answer for the first call would be '() because 'D is an immediate neighbor of 'c. Of course, '() could then no longer signal failure.

> It is easy to imagine others, such as skipping either of the two given nodes.

Concerning the lack-of-a-path issue, we must choose a distinct value for signaling this notion. Because #false is distinct, is meaningful, and works in either case, we opt for it. As for the multiple-paths issue, we postpone making a choice for now and list both possibilities in the example section: