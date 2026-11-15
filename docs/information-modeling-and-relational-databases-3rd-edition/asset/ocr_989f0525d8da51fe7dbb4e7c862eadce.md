are designed to ensure internal consistency, external consistency, lack of redundancy, and completeness. We now consider these in order.

A conceptual schema is *internally consistent* if and only if each role sequence used as a predicate or constraint argument can be populated in some state. This topic was discussed in the previous chapter, where it was called “population consistency” or “strong satisfiability”. Basically, it means that the specified constraints do not contradict one another when the system is populated. For example, the schema in Fig. 7.28 has three faults. Can you spot them?

![](bbox=[0.32, 0.275, 0.65, 0.39])

FIG. 7.28 This schema is population inconsistent on three counts.

First, the frequency constraint of 2 on predicate R clashes with the uniqueness constraint; moreover, any frequency above 1 should be rejected if it spans the whole predicate. Second, the mandatory roles on A imply an equality constraint between these roles, so if A is populated, the exclusion constraint cannot be satisfied (recall theorem NXS).

Finally, the frequency constraint of 3 on the first role of S cannot be satisfied once A is populated. If it were satisfied, then C would include at least three instances (because each row of S is unique, but this is impossible because C is a proper subtype of B and hence has a maximum cardinality of 2 (the value constraint shows B has only three possible values). With practice, it is usually easy to spot contradictory constraint patterns. Computer-aided software engineering (CASE) tools can be of assistance here. For example, the NORMA tool prevents most inconsistencies from even being entered.

A conceptual schema is *externally consistent* if it agrees with the original examples and requirements used to develop the schema. If not done earlier, we populate the schema with some of the sample data and look to see if some constraints are violated by the population. If they are, then the constraints are *too strong* in this respect because they reject legal examples. We should then modify the schema, typically by removing or softening some constraints, until the population is permitted.

As a simple illustration, consider Table 7.2. To simplify the discussion, assume that people may be identified by their first name. The null value indicates that Bob seeks a BA degree but we do not know any of Bob’s subjects.