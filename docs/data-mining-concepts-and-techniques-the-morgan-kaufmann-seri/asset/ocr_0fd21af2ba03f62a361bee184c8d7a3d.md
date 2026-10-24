![](bbox=[0.3, 0.12, 0.67, 0.63])

**FIGURE 3.24**
BUC partitioning snapshot given an example 4-D data set.

$(a_1, b_1, c_1, *)$. That is, it avoids partitioning this cell on dimension $D$. It backtracks to the $a_1, b_1$ partition and recurses on $(a_1, b_1, c_2, *)$, and so on. By checking the iceberg condition each time before performing a recursive call, BUC saves a great deal of processing time whenever a cell's count does not satisfy the minimum support.

The partition process is facilitated by a linear sorting method, CountingSort. CountingSort is fast because it does not perform any key comparisons to find partition boundaries. For example, to sort 10,000 tuples according to an attribute $A$ whose value is an integer in the range between 1 and 100, we can set up 100 counters and scan the data once to count the number of 1's, 2's, ..., 100's on attribute $A$. Suppose there are $i_1$ tuples having 1 on $A$, $i_2$ tuples having 2 on $A$, and so on. Then, in the next scan, we can move all the tuples having value 1 on attribute $A$ to the first $i_1$ slots, the tuples having value 2 on attribute $A$ to the slots $i_1 + 1, ..., i_1 + i_2$, and so on. After those two scans, the tuples are