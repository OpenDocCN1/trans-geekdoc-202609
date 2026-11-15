2.1 For each case where an object type A has simple and binary keys attached, where the other role of the binary key is played by B:

![](bbox=[0.42, 0.14, 0.57, 0.18])

+   if R is a binary
+   then if B has values b1,..., bn (and n is small)
+       then specialize R to n unaries or replace B by B' {b1, b2, both} (if n = 2)
+           making the key(s) simple
+       else if A's role in R has a frequency constraint n or n (and n is small)
+           then specialize R into n exclusive binaries simply keyed on A
+           else if A has just one functional role
+               and the predicates are compatible, pair-exclusive binaries
+               then generalize both to a single ternary with a restricted UC
+   else -- R is a ternary
+       if B has values b1,..., bn (and n is small)
+           then absorb B, specializing R into n binaries simply keyed on A.

2.2 For each case where an object type A has a functional role attached, as well as a 1:n binary predicate R connected to object type B:

![](bbox=[0.31, 0.39, 0.65, 0.47])

+   if B has no other functional roles (see (a))
+   then if A's role in R has a frequency constraint of n, or n (and n is small)
+       then specialize R into 1:n 1 binaries with B's roles mutually exclusive
+       else if B has values b1,..., bn (and n is small)
+           then consider specializing R into n unaries
+   else if B has exactly one more functional predicate, linked to C {c1,..., cn}
+       and an equality constraint spans B's functional roles
+       and an external UC spans B's co-roles (see (b))
+       then specialize R into 1:n 1 binaries with B's roles exclusive, by absorbing C
+           (this is PSG2 with corollary 2: see Figure 14. 16)

FIG. 14.43 Optimization step 2.

As an exercise, draw the schemas and perform the mappings. Step 2.2 completes the optimization strategy to reduce the number of mapped tables.

Before going on to step 3, let's consolidate the first four steps by considering an example for which substantial optimization is possible. Fig. 14.44 depicts a conceptual schema for postgraduate coursework in a computer science department. This UoD was first introduced in Exercise 4.2.

The pair-subset constraint reflects the fact that after students enroll in a subject, they choose a topic for it. Each topic has a lecturer in charge, and at most two (other) co-lecturers.

As an exercise, map the schema in Fig. 14.44 to a relational schema and then check your solution with the one in Fig. 14.45.

If you did this correctly, you should have obtained six tables. Notice the intertable constraints. The “O” superimposed on “X” in the relational schema denotes a partition of