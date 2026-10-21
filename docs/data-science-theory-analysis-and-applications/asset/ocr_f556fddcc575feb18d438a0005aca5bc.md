# FIGURE 4.14 Time executed by each query on a 100 GB database using physical design and the default Neo4j evaluation.

| Query | BI 3 | BI 4 | BI 6 | BI 9 | BI 14 | BI 16 | BI 18 | BI 19 | BI 21 | BI 23 |
|-------|------|------|------|------|-------|-------|-------|-------|-------|-------|
| Time improv. (%) | 98.65 | 64.42 | 36.74 | 68.82 | 71.48 | 77.82 | 70.78 | 78.71 | 58.89 | 38.39 |
| DB Hits improv. (%) | 8.34 | 16.65 | 0.32 | 39.78 | 42.6 | 60.55 | 2.64 | 1.06 | 0.08 | 0.1 |

0.05, the mean of the query execution times on a 100 GB database without physical design is significantly higher than the mean of the query execution times on a 100 GB database with physical design.

In addition, Figure 4.15 shows the DB Hits for each query and strategy. The X axis contains the query identifiers, and the Y axis corresponds to the DB Hits normalized in the range (0, 1). Also, Table 4.6 includes the percentage of improvements in DB Hits for each query.

It can be noted that Figure 4.15 and Table 4.6 that the DB Hits results are similar to the execution time. However, we can observe that the performance of queries BI 6 were lower w.r.t. the execution of this query for a 1 GB database and a 10 GB execution GB database.



Physical database design has attracted much interest in the database community during decades [17,18,19,20,21]. These works propose guidelines to follow in the field