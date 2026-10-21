![](bbox=[0.11, 0.09, 0.9, 0.38])

# FIGURE 4.10 Time executed by each query on a 1 GB database using physical design and the default Neo4j evaluation.

# TABLE 4.1
Percentage of Improvements in Runtime of Our Physical Design Strategy w.r.t. the Default Neo4j Evaluation for Each Query on a 1 GB Database

| Query | BI 3 | BI 4 | BI 6 | BI 7 | BI 9 | BI 14 | BI 16 | BI 18 | BI 19 | BI 21 | BI 22 | BI 23 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Time improv. (%) | -1.48 | 31.05 | 14.53 | 97.53 | 15.67 | 53.19 | 20.92 | 9.77 | 11.83 | -0.94 | 98.14 | 9.6 |
| DB Hits improv. (%) | 10.55 | 13.91 | 17.54 | 96.02 | 18.04 | 53.32 | 62.63 | 5.66 | 2.15 | 0.3 | 95.91 | 0.36 |

are unavoidable, and they still impact on the final execution plan. Additionally, path materialization was more effective for queries BI 4, BI 9, and BI 16 if we compared them against queries BI 18, BI 19, and BI 23. Their improvement percentages vary from 15.67% to 31.05% because the materialized paths have a higher impact on the query performance.

The third highest performance improvement was obtained for the query BI 14 in half the time of the strategy without physical design. Its improvement is 53.19%, because an index structure was defined for a high selectivity condition. Also, the initial execution plan expanded two different paths, and then they were joined with the remaining nodes. However, the planner improves its execution plan filtering intermediate results instead of completely expanded paths. In consequence, unnecessary traversals are avoided significantly reducing the cost of retrieving nodes. In addition, the performance of query BI 6 was a little better when the index was created, and its improvement percentage was 14.53%.