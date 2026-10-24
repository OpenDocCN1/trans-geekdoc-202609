Site B's timestamp matrix is:

```
( 2 1 0 )
( 2 1 2 )
( 2 1 2 )
```

Site C's timestamp matrix is the same as that of site B:

```
( 2 1 0 )
( 2 1 2 )
( 2 1 2 )
```

It is apparent that site A cannot garbage collect any operation because the third row in its timestamp matrix is (0, 0, 0). For site B, the minimum of the first column (corresponding to the status of site A) is 2, the minimum of the second column (corresponding to the status of site B) is 1, and the minimum of the third column (corresponding to the status of site C) is 0. Then, site B can safely garbage collect the first two operations from site A: O_A1 and O_A2, and the first operation from site B itself: O_B1. Similarly, site C can safely purge the three operations as well.

Even though the effectiveness of using timestamp matrices for update commit also depends on good connectivity of different sites, a site that has few or no operations submitted would not prevent other sites from committing updates and performing garbage collection.

# 4.4 CAP Theorem

The CAP theorem was introduced by Eric Brewer in 2000 [6] regarding what can be achieved in a practical distributed system. The theorem states that it is impossible to satisfy all three of the following guarantees:

+   - Consistency (C): the replicated data is always consistent with each other.
+   - Availability (A): the data is highly available to the users.
+   - Partition tolerance (P): the system can continue providing services to its users even when the network partitions.