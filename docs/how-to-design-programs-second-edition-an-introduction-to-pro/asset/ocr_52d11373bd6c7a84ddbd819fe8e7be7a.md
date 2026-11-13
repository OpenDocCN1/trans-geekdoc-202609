node back to itself, find-path may not produce a result for some inputs.

*You know only one exception to this rule: random.*

The next part presents a program design technique that addresses just this kind of problem. In particular, it presents a variant of find-path that can deal with cycles in a graph.

**Exercise 473.** Test find-path on 'B, 'C, and the graph in figure 170. Also use test-on-all-nodes from exercise 472 on this graph. ▪

**Exercise 474.** Redesign the find-path program as a single function. ▪

**Exercise 475.** Redesign find-path/list so that it uses an existing list abstraction from figures 95 and 96 instead of explicit structural recursion. **Hint** Read the documentation for Racket’s ormap. How does it differ from ISL+’s ormap function? Would the former be helpful here? ▪

**Note on Data Abstraction** You may have noticed that the find-path function does not need to know how Graph is defined. As long as you provide a correct neighbors function for Graph, find-path works perfectly fine. In short, the find-path program uses data abstraction.

As part III says, data abstraction works just like function abstraction. Here you could create a function abstract-find-path, which would consume one more parameter than find-path: neighbors. As long as you always handed abstract-find-path a graph G from Graph and the matching neighbors function, it would process the graph properly. While the extra parameter suggests abstraction in the conventional sense, the required relationship between two of the parameters—G and neighbors—really means that abstract-find-path is also abstracted over the definition of Graph. Since the latter is a data definition, the idea is dubbed data abstraction.

When programs grow large, data abstraction becomes a critical tool for the construction of a program’s components. The next volume in the How to Design series addresses this idea in depth; the next section illustrates the idea with another example. **End**

**Exercise 476.** Chapter 12.8 poses a problem concerning finite state machines and strings but immediately defers to this chapter because the solution calls for generative recursion. You have now acquired the design knowledge needed to tackle the problem.