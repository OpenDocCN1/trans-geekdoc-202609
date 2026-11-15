![](bbox=[0.26, 0.09, 0.76, 0.19])

# FIG. 14.31 Another nest/flatten equivalence.

We generally favor the nested version in this case because it is more compact and it Rmaps directly to just one table. In contrast, if the flattened version is passed to our standard Rmap Rmap procedure, two tables result. Nevertheless, the flattened approach is quite natural, and it verbalizes easily. If you prefer the flattened approach for these reasons, it would be nice if your CASE tool displayed it this way, but gave you the option of having it mapped to a single table in the same way as the nested version. However, such flexibility is typically not provided by current CASE tools. So, the nested approach is generally preferable for this case.

In the flattened version in Fig. 14.31, the S predicate is compatible with the subpredicate comprising the first two roles of R (they are played by the same object types A and B). This compatibility enables the nesting to occur. For this subset case, any (a, b) pair in the population of either must belong to the population of S. So, we objectify S and add an optional connection to C to handle the R facts.

Recall that in our CSDP, whenever different predicates have compatible role sequences (of two or more roles), we should ask ourselves to what extent the populations of these [sub-] predicates must overlap. If a set-comparison (subset, equality or exclusion) constraint exists between them, it must be declared.

The kind of nesting transformation that may now occur depends partly on what kind of set-comparison constraint exists (if any) and on whether other roles occur in the full predicates. Let's look at some more examples before summarizing the overall procedure.

Consider the output report shown in Table 14.5. This may be modeled with two flat fact types, as shown in Fig. 14.32(a). Notice the equality constraint between the two role-pairs. An assignment mark is recorded for a student in a subject if and only if an exam mark is recorded for that student in that subject.

# Table 14.5 Student assignment and exam marks.

| Subject: | CS102 | | CS115 | |
|---|---|---|---|---|
| StudentNr | Assignmt | Exam | Assignmt | Exam |
| 1001 | 17 | 65 | 15 | 58 |
| 1002 | 20 | 79 | 20 | 67 |
| 1003 | 15 | 60 | 12 | 55 |