The condition c used to express this comparison of attributes between tables is called the join condition. The join condition may be composite (e.g., a1 < b1 and a2 < b2). Because of the Cartesian product, the resulting table has a number of columns equal to the sum of the number of columns in A and B, but because of the selection operation, it typically has far fewer rows than the product of the numbers of rows of the joined tables.

With most joins, the comparison operator used is =. The Θ-join is then called an equijoin. Thus, the equijoin of A and B equating values in column a of A with column b of B is A × B restricted to the rows where A.a = B.b. If the join column names are different in each table, there is no need to qualify them with table names. We write this as shown here. In general, the join condition may contain many equalities.

```
(A x B) where A.a = B.b
or
(A x B) where a = b   { if a, b occur in only one of A, B }
```

Let's consider an example. Fig. 12.17 includes a simple conceptual schema and its corresponding relational schema.

![](bbox=[0.16, 0.45, 0.85, 0.6])

FIG. 12.17 The ORM schema (a) maps to the relational schema (b).

A sample population is given in Fig. 12.18.

**Employee:**
| empNr | empName | gender |
|---|---|---|
| 001 | Haggar, T | M |
| 002 | Wong, S | F |
| 003 | Jones, E | F |
| 004 | Mifune, K | M |

**Drives:**
| empNr | carRegNr |
|---|---|
| 001 | ABC123 |
| 003 | ABC123 |
| 003 | TAH007 |

FIG. 12.18 A sample population for the schema in Fig. 12.17.

Before formulating queries, familiarize yourself with the structure and contents of the database. From the schema, we see that employees are identified by their employee number, and their name and gender must also be recorded. An employee may drive many cars, and the same car may be driven by many employees. The population is