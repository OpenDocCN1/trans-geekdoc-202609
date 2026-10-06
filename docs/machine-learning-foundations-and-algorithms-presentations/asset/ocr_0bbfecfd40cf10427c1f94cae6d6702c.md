# Kernel Matrix (aka Gram Matrix)

Properties:

+   * **K** is always an $n \times n$ matrix, whatever the nature of data: the same algorithm will work for any type of data (vectors, strings, ...)
* Total modularity between the choice of function k and the choice of the algorithm.
* Poor scalability with respect to the dataset size ($n^2$) to compute and store **K**...
* We will restrict ourselves to a particular class of pairwise comparison functions.