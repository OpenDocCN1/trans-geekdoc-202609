requires changes to the fact types and relational columns each year. In this case, the ternary approach might be preferred because no structural change is needed (the year changes are made only to rows of data, not the table structure itself).

The wording of optimization step 3 reflects this trade-off between query efficiency and the ease of table display and schema evolution. Although default choices can be built into an automated optimizer, interaction with human modelers is advisable to ensure the best trade-off.

The final steps (4 and 5) of the optimization procedure deal with exclusive roles (see Fig. 14.51).

+   4. Generalize each group of _n_ exclusive unaries (_n_ ≥ 2) to a functional binary by extracting an object type with _n_ values.

![](bbox=[0.321, 0.331, 0.751, 0.413])

+   5. if _A_ plays exclusive, functional roles in _n_ 1:many predicates with _C_, and _C_ has no other functional role then replace these _n_ predicates by two binaries, by extracting _B_ {_b_<sub>1</sub>, ...,_b_<sub>_n_</sub>} as per the LHS of PSG2.

![](bbox=[0.273, 0.497, 0.725, 0.597])

# FIG. 14.51 Optimization steps 4 and 5: further aspects of exclusive roles.

Step 4 is straightforward. Different unaries attached to the same object type map to different columns of the same table. If these unaries are exclusive, we may replace them all by a functional binary that maps to just one column. Moreover, the transformation of the exclusion constraint to a uniqueness constraint enables it to be simply enforced by the primary key constraint of the table. Recall Fig. 14.7 where three exclusive unaries (Employee is a manager; Employee is a clerk; Employee is a secretary) are replaced by the functional binary Employee has Rank {'M', 'C', 'S'}.

Step 5 helps us decide when to favor predicate generalization in applying theorem PSG2. This is illustrated, along with other optimizations, by our next example. Consider the conceptual schema shown in Fig. 14.52.

The interpreticate uniqueness constraint in Fig. 14.52 asserts that a team may have only one player of each sex. This conceptual schema maps to seven tables. As an exercise, you might like to check this for yourself and then optimize the conceptual schema before reading on.