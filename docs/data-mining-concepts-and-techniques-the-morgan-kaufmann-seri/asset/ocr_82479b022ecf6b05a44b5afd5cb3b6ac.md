b. Suppose we want to compute a data cube where the condition is that the minimum number of records is 10 and the average fare is over $500. Outline an efficient cube computation method (based on common sense about flight data distribution).

# 3.27. (Implementation project) There are four typical data cube computation methods: MultiWay [ZDN97], BUC [BR99], H-Cubing [HPDW01], and Star-Cubing [XHLW03].

+   a. Implement any one of these cube computation algorithms and describe your implementation, experimentation, and performance. Find another student who has implemented a different algorithm on the same platform (e.g., C++ on Linux) and compare your algorithm performance with his or hers.

Input:

+   i. An n-dimensional base cuboid table (for n < 20), which is essentially a relational table with n attributes.

+   ii. An iceberg condition: count (C) >= k, where k is a positive integer as a parameter.

Output:

+   i. The set of computed cuboids that satisfy the iceberg condition, in the order of your output generation.

+   ii. Summary of the set of cuboids in the form of “cuboid ID: the number of nonempty cells,” sorted in alphabetic order of cuboids (e.g., A: 155, AB: 120, ABC: 22, ABCD: 4, ABCE: 6, ABD: 36), where the number after : represents the number of nonempty cells. (This is used to quickly check the correctness of your results.)

+   b. Based on your implementation, discuss the following:

+   i. What challenging computation problems are encountered as the number of dimensions grows large?

+   ii. How can iceberg cubing solve the problems of part (a) for some data sets (and characterize such data sets)?

+   iii. Give one simple example to show that sometimes iceberg cubes cannot provide a good solution.

+   c. Instead of computing a high-dimensionality data cube, we may choose to materialize the cuboids that have only a small number of dimension combinations. For example, for a 30-D data cube, we may only compute the 5-D cuboids for every possible 5-D combination. The resulting cuboids form a shell cube. Discuss how easy or hard it is to modify your cube computation algorithm to facilitate such computation.

# 3.28. The sampling cube was proposed for multidimensional analysis of sampling data (e.g., survey data). In many real applications, sampling data can be of high dimensionality (e.g., it is not unusual to have more than 50 dimensions in a survey data set).

+   a. How can we construct an efficient and scalable high-dimensional sampling cube in large sampling data sets?

+   b. Design an efficient incremental update algorithm for such a high-dimensional sampling cube.

+   c. Discuss how to support quality drill-down given that some low-level cells may be empty or contain too few data for reliable analysis.

# 3.29. The ranking cube was designed to support top-k (ranking) queries in relational database systems. However, ranking queries are also posed to data warehouses, where ranking is on multidimensional aggregates instead of on measures of base facts. For example, consider a product manager