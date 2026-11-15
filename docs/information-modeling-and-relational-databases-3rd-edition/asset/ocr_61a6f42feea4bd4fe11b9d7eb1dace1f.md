In the previous two examples, a table with overlapping keys had to be split. Sometimes, overlapping keys are permitted. Recall the example from Chapter 4 where students are assigned unique positions in subjects, with no ties. This leads to this BCNF table scheme:

```
Enrollment( studentNr, subjectCode, position )
```

The previous normal forms considered only FDs. The next normal form is due to Ronald Fagin (1977) and considers multivalued dependencies (MVDs). For a given relation with attributes X, Y, and Z (possibly composite), X multidetermines Y (written as X -> Y) if and only if the set of Y values is a function of X only (independent of the value of Z). In this case, Y is said to be multivalued dependent, or multidependent, on X; in such a case, Z will also be multidependent on X. A FD is a special case of an MVD, namely when the set of dependent values is a unit set. An MVD X ->> Y is trivial if and only if X includes Y, or X and Y together include all the attributes in the relation.

For example, the Athlete table considered earlier in Fig. 14.58(b) is repeated in Fig. 14.67(a), this time showing the nontrivial MVD athleteName ->> sport. As the ORM schema in Fig. 14.67(b) indicates, MVDs usually arise from m:n associations. Although this poor design would be detected earlier because of its embedded FD (it is not even in 2NF), some relations with MVDs are in BCNF yet still have redundancy problems. To address such cases, we now consider the next normal form.

| athleteName | sport | height |
|---|---|---|
| Jones E | hockey | 180 |
| Jones E | tennis | 180 |
| Smith T | tennis | 170 |

![](bbox=[0.54, 0.53, 0.76, 0.64])

FIG. 14.67 The MVD athleteName ->> sport in (a) is due to the m:n association in (b).

A relation is in fourth normal form (4NF) if and only if it is in BCNF and all its nontrivial dependencies are functional (single-valued) dependencies. So, a 4NF relation cannot have any nontrivial MVDs that are not FDs. Basically, each nonfunctional MVD requires a separate table for itself.

Consider the Lecturer table in Fig. 14.68(a). It is in BCNF because it is “all-key”. The table is not in 4NF because language and sport are each multidependent (but not functionally dependent) on surname. The MVDs are depicted as double arrows above the table. Assuming that the ternary means Lecturer plays Sport and speaks Language, the table exhibits redundancy. The facts that Halpin plays judo and karatedo and speaks English and Japanese are duplicated. To avoid this problem, the table is split into two 4NF tables (as obtained by Rmapping the ORM schema) as shown in Fig. 14.68(c).