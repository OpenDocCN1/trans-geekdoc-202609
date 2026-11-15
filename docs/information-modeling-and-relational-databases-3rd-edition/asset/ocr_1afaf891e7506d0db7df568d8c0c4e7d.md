For example, if we add the row (16, PKJ123) to the drives table in Fig. 4.31, then row (16, PKJ123, IT) is added to the ternary and is now contained twice in the ternary. Although join fact types are never used as asserted fact types, join paths are often involved in constraints and queries, as discussed later.

In an ORM schema, to navigate from one predicate to another, we must pass through an object type, performing a *conceptual join* (or *object join*) on that object type. By default, the join condition is that the object instance remains the same as we pass through. This is called a *conceptual inner join*. This is similar to a relational natural inner join (see later chapter), except that conceptual joins require the conceptual objects to be the same, instead of matching attribute names and values. ORM object types are conceptual domains, not attributes. Conceptual joins still apply if we declare different role names (cf. attribute names) for the join roles.

In terms of the fact tables, the column value of the role entering the join object type must equal the column value of the role that exits the object type. Fig. 4.33 depicts two predicates, R and S, sharing a common object type, B. From a fact table perspective, the conceptual inner join of R and S is obtained by pairing rows of R with rows of S where the B column values match, and arranging for the final B column to appear just once in the result.

![](bbox=[0.139, 0.462, 0.675, 0.582])

The dotted lines show how the rows are paired together. For example, row (a1, b1) is paired with rows (b1, c1) and (b1, c3) to give rows (a1, b1, c1) and rows (a1, b1, c3). Fig. 4.34 shows the result of this join operation. The final B column is the intersection of the original B columns. The natural inner join of any tables R and S is denoted by “R ⋈ S” or “R natural join S”. The “inner” is often omitted and assumed by default.

![](bbox=[0.139, 0.755, 0.62, 0.91])