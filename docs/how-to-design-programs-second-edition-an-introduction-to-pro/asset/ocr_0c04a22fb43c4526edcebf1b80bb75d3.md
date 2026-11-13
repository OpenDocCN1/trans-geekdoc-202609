4. Finally, once the algorithm has a path from a neighbor of origination to destination, it is easy to construct a complete path from the former to the latter—just add the origination node to the list.

From a programming perspective, the third point is critical. Since a node can have an arbitrary number of neighbors, the “inspect all neighbors” task is too complex for a single primitive. We need an auxiliary function that consumes a list of nodes and generates a new path problem for each of them. Put differently, the function is a list-oriented version of find-path.

Let’s call this auxiliary function find-path/list and let’s formulate a wish for it:

```
; [List-of Node] Node Graph -> [Maybe Path]
; finds a path from some node on lo-originations to
; destination; otherwise, it produces #false
(define (find-path/list lo-originations destination G)
 #false)
```

Using this wish, we can fill in the generic template for generative-recursive functions to get a first draft of find-path:

```
(define (find-path origination destination G)
 (cond
  [(symbol=? origination destination)
   (list destination)]
  [else
   (... origination ...
   ...(find-path/list (neighbors origination G)
   destination G) ...)])
```

It uses the neighbors from exercise 471 and the wish-list function find-path/list and otherwise uses the answers to the four questions about generative recursive functions.

The rest of the design process is about details of composing these functions properly. Consider the signature of find-path/list. Like find-path, it produces [Maybe Path]. That is, if it finds a path from any of the neighbors, it produces this path; otherwise, if none of the neighbors is connected to