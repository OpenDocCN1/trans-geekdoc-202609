Unlike union and intersection, the difference operator is not commutative. For example, reversing the order of the operands in the previous query results in {“Colleen”} because the reversed query has the different meaning, “Which Ford drivers are not American?”

If the **all** option is used after **intersect** or **except**, it returns a bag intersection or bag difference, respectively. In general, if a row appears _m_ times in one table and _n_ times in another, then it appears min(_m_, _n_) times in the bag intersection and max(_m - n_, 0) times in the bag difference.

Although all the main commercial SQL dialects support the **union** operator, several do not yet support the **intersect** and **except** operators. As we now discuss, these two operators can be emulated using subqueries, so their absence does not entail a loss of functionality.

SQL **subqueries** are like component queries within nested formulations in relational algebra. Although SQL subqueries are queries in their own right, they must be enclosed in parentheses (unlike **select** queries that are unioned), and they have some limitations on their use. Ideally, a language ought to be orthogonal—wherever a value or result is legal, an expression that returns that value or result should be legal. In SQL-89, however, subqueries are allowed only in a few places where their result is legal. Although SQL-92 removed these restrictions, few commercial SQLs are fully orthogonal.

A subquery is a parenthesized **select** query embedded in another query. Let Θ denote one of the comparison operators (=, <<, >, <, <=, >=). In SQL-89, a subquery is legal only in the following three contexts:

+   expression [not] **in** (subquery) -- membership subquery
+   expression Θ [all | some | any] (subquery) -- [quantified] comparison subquery
+   exists (subquery) -- existential subquery

A **membership subquery** follows an **in** operator. In SQL-89, a membership subquery must be a **singleton** query (i.e., it must return a single column). This is consistent with the use of the **in** operator with a bag of values (a column is just a bag of values, displayed vertically). In SQL-92, the **in** operator may be preceded by a row value expression, in which case the subquery may return a multicolumn table.

A **comparison subquery** follows a comparator (e.g., =). If the comparator is modified by one of the quantifiers **all**, **some**, or **any**, this is a _quantified comparison_. In SQL-89, a comparison subquery must return a single column; if the comparison is not quantified, the subquery must return a single value. This is consistent with the normal use of comparison operators. In SQL-92, a comparator may be preceded by a row value expression, in which case the subquery may return a multicolumn table or, if unquantified, a row value. An **existential subquery** appears after the **exists** quantifier and may return any table.

In SQL-92, subqueries may be used in other places (e.g., **from** clauses and **check** clauses), as long as their result table makes sense there (orthogonality). **From** clause subqueries require an alias for the derived table even if not needed. The syntax is:

```
... **from** (subquery) [**as**] _alias_
```