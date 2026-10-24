3.21. Suppose that a base cuboid has three dimensions, A, B, C, with the following number of cells: |A| = 1,000,000, |B| = 100, and |C| = 1000. Suppose that each dimension is evenly partitioned into 10 portions for chunking.

+   a. Assuming each dimension has only one level, draw the complete lattice of the cube.

+   b. If each cube cell stores one measure with four bytes, what is the total size of the computed cube if the cell is dense?

+   c. State the order for computing the chunks in the cube that requires the least amount of space, and compute the total amount of main memory space required for computing the 2-D planes.

3.22. When computing a cube of high dimensionality, we encounter the inherent curse of dimensionality problem: There exists a huge number of subsets of combinations of dimensions.

+   a. Suppose that there are only two base cells, {(a1, a2, a3, ..., a100) and (a1, a2, b3, ..., b100)}, in a 100-D base cuboid. Compute the number of nonempty aggregate cells. Comment on the storage space and time required to compute these cells.

+   b. Suppose we are to compute an iceberg cube from (a). If the minimum support count in the iceberg condition is 2, how many aggregate cells will there be in the iceberg cube? Show the cells.

+   c. Introducing iceberg cubes will lessen the burden of computing trivial aggregate cells in a data cube. However, even with iceberg cubes, we could still end up having to compute a large number of trivial uninteresting cells (i.e., with small counts). Suppose that a database has 20 tuples that map to (or cover) the two following base cells in a 100-D base cuboid, each with a cell count of 10: {(a1, a2, a3, ..., a100) : 10, (a1, a2, b3, ..., b100) : 10}.

+   i. Let the minimum support be 10. How many distinct aggregate cells will there be like the following: {(a1, a2, a3, a4, ..., a99, *) : 10, ..., (a1, a2, *, a4, ..., a99, a100) : 10, ..., (a1, a2, a3, *, ..., *) : 10}?

+   ii. If we ignore all the aggregate cells that can be obtained by replacing some constants with *'s while keeping the same measure value, how many distinct cells remain? What are the cells?

3.23. Propose an algorithm that computes closed iceberg cubes efficiently.

3.24. Suppose that we want to compute an iceberg cube for the dimensions, A, B, C, D, where we wish to materialize all cells that satisfy a minimum support count of at least v, and where cardinality(A) < cardinality(B) < cardinality(C) < cardinality(D). Show the BUC processing tree (which shows the order in which the BUC algorithm explores a data cube's lattice, starting from all) for the construction of this iceberg cube.

3.25. Discuss how you might extend the Star-Cubing algorithm to compute iceberg cubes where the iceberg condition tests for an avg that is no bigger than some value, v.

3.26. A flight data warehouse for a travel agent consists of six dimensions: traveler, departure (city), departure_time, arrival, arrival_time, and flight; and two measures: count() and avg_fare(), where avg_fare() stores the concrete fare at the lowest level but the average fare at other levels.

+   a. Suppose the cube is fully materialized. Starting with the base cuboid [traveler, departure, departure_time, arrival, arrival_time, flight], what specific OLAP operations (e.g., roll-up flight to airline) should one perform to list the average fare per month for each business traveler who flies American Airlines (AA) from Los Angeles in 2009?