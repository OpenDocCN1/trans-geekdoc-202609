54 / 120 for either of them, or any other page with probability 3 / 120 for each one of them.

We are now able to give the final definition of the PageRank algorithm:

+   1. Form the Google matrix of the graph.
2. Start with initial pagerank estimates, giving a pagerank of $1 / n$ to each page, where $n$ is the total number of pages.
3. Apply the power method, multiplying the pagerank vector by the Google matrix until the values of the pagerank vector converge.

We simply substituted “Google matrix” for “hyperlink matrix” of the initial algorithm. If we trace this algorithm in our graph with the group of sink nodes, we'll get:

| Round | Page 1 | Page 2 | Page 3 | Page 4 | Page 5 | Page 6 |
| --- | --- | --- | --- | --- | --- | --- |
| start | 0.17 | 0.17 | 0.17 | 0.17 | 0.17 | 0.17 |
| 1 | 0.10 | 0.14 | 0.14 | 0.10 | 0.31 | 0.21 |
| 2 | 0.07 | 0.15 | 0.17 | 0.07 | 0.31 | 0.23 |
| 3 | 0.05 | 0.14 | 0.18 | 0.05 | 0.32 | 0.26 |
| 4 | 0.05 | 0.14 | 0.17 | 0.05 | 0.33 | 0.27 |

It works out fine; we get no zero pageranks anymore.