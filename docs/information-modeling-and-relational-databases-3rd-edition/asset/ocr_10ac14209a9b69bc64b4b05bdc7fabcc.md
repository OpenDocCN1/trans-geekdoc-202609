To visualize the connection between roles and columns of the fact table, think of the role boxes as the holes in which the objects get placed to complete the fact. No matter what the arity of the fact type, a UC across a combination of role boxes means that any instance of that column combination that does appear in the table must occur on one row only, and hence can be used to identify that row.

Because a role combination governed by a UC provides a “key to unlock” any row of the fact table, this combination is referred to as a *key* for that table. This notion will be elaborated later in the context of the (often non-elementary) tables used in relational databases.

![](bbox=[0.35, 0.27, 0.62, 0.36])

FIG. 4.29 A uniqueness constraint over roles 1, 2, and 4.

![](bbox=[0.3, 0.43, 0.66, 0.53])

FIG. 4.30 The enrollment association is objectified as a nested object type.

Now, let's consider *nesting*. In Fig. 4.23, the subject ratings example was set out in flattened form. Suppose instead we use a nested approach, as shown in Fig. 4.30. Here each (Person, Subject) enrollment is treated as an object that may result in a rating. For example, the enrollment of Adams in CS112 results in a 7.

Fig. 4.23 is not actually equivalent to Fig. 4.30 unless a further constraint is added that a rating must be known for each enrollment. Such mandatory role constraints are discussed in the next chapter.

The Enrollment entity type in Fig. 4.30 is called an objectified association, an objectified relationship type, an objectified predicate, a nested entity type, or a nested object type. Most objectified associations are spanned by a UC (as in Fig. 4.30). This spanning UC indicates that each person may enroll in many subjects, and the same subject may be enrolled in by many people. The simple UC on the binary predicate indicates that each (Person, Subject) enrollment resulted in at most one rating.

Section 10.5 includes a discussion of objectification of associations with nonspanning UCs (e.g., 1:1 associations and n:1 associations). While currently allowed in ORM, such cases can violate elementarity, and are better modeled in other ways.