no more values will be generated once **maxvalue** (counting up) or **minvalue** (counting down) is reached or exceeded. Depending on the relationship between the start value and increment size, the sequence may or may not land exactly on a **maxvalue** or **minvalue**.

A sequence will not cycle back and duplicate values already generated unless the **cycle** option is specified. If **cycle** is specified, the sequence will stop at **maxvalue** and reset to **minvalue** if counting up, and the converse if counting down. The start value can be anywhere in the range defined by these two values.

Identity columns are supported in most implementations, although not necessarily with the SQL standard syntax. The guarantee that the generated value will be unique within a table makes them attractive to use as a primary key. In cases where the natural primary key for the table is clumsy, for example, a combination of multiple **varchar** columns, an identity column is often introduced as a surrogate key.

The SQL:1999 standard allowed the creation of tables based on existing table definitions. This capability was refined in SQL:2003 to provide more precise control over the columns that should be included or excluded in the new table. The basic syntax is as follows.

```
create table new-tablename like existing-tablename
[ { including identity | excluding identity } |
{ including defaults | excluding defaults } |
{ including generated | excluding generated } [...] ]
```

The result of the **create table ... like ...** statement is an empty table with the same column names, data types, and nullability as the original table. No dependency is established between existing and new tables. The options specify what action should be taken for “special” columns.

# Maintaining Referential Integrity

Let’s now discuss the notion of *referential integrity* in more detail. Recall that referential integrity is a special case of a subset constraint. The following relational schema outline shows a typical case, where *S.a* is a foreign key referencing *R.a*. Basically, the subset constraint is satisfied if each value in *S.a* either occurs as a value of *R.a* or is null.

```
R ( a b , ... )
  ^
  |
S ( a c , d, ... )
```

The subset constraint may be violated in any of the following four ways:

+   (1) insert a row into S with a value for S.a that is not a value in R.a

+   (2) update a row of S to replace the value for S.a with a value that is not in R.a