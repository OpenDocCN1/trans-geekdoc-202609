![](bbox=[0.18, 0.1, 0.42, 0.26])

![](bbox=[0.44, 0.1, 0.86, 0.29])

![](bbox=[0.18, 0.3, 0.8, 0.57])

FIG. 18.33 Modeling ORM set-comparison constraints in ORM and extended UML.

# **Table 18.5** Metatable for storing ORM constraints.

| constraintNr | constraintType | roles | argLength |
|---|---|---|---|
| C1 | UC | r1, r2 | |
| C2 | UC | r4 | |
| C3 | SS | r4, r2 | 1 |
| C4 | X | r1, r2, r3, r4 | 2 |

# **Exercise 18.7**

1. Devise a conceptual metaschema (in ORM, UML, or ER) to store simple SQL schemas where each table has at most one primary key (possibly none). A primary key may be composite (multicolumn), but each foreign key references a simple (single column) primary key. Tables are identified by simple names. Columns are ordered by position, and may be optional or mandatory. Each column in a primary key is mandatory, but it is possible that all columns in a keyless table are optional. Ignore domains and all other constraints (e.g., uniqueness constraints on column sets