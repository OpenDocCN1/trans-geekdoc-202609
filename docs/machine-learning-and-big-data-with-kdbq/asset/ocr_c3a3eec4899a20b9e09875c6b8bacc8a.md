# Joins

q is thus equipped with eight additional commands to perform particular types of\ joins. In the following section, we cover these commands one by one.

# 7.2 JOIN FUNCTIONS

The dedicated join functions are: ij, ej, lj, lj, upsert, uj, pj, aj, asof, wj. They algo-
get provide a powerful suite of join operations, which naturally incorporates within
a table-driven framework.

# 7.2.1 ij

ij, or "inner" join, joins two tables on the key columns of the second table. Thus, the
table on the right must be a keyed table, and the keys of that table have to be contained
in the table on the left. As a result, the combined table contains each row from the left
table, matching values from the columns of the right table:

```
t10: [[ a: 1 2 3; b: 10 20 30;c: 100 200 300];
t11: [[a:1 2 4] c:-100 ON -400; d:-1000 -2000 -4000];
t10 ij t11
```

| a b c |
|---|---|---|
| 1 10 -1000 |
| 2 20 -2000 |

The output contains only two rows, the rows which are matched based on the values
of a table t11. The output is an unkeyed table. Finally, the provided example also
illustrates the role of missing/null entries in the table, which replace the not null values
during the null values in column c.

The inner join works in the case when the table is keyed by more than one column as
well:

```
t12: [[a:1 2 4; b:10 ON ON] c:-100 ON -400; d:-1000 -2000 -4000];
t10 ij t12
```

| a b c |
|---|---|---|
| 1 10 -1000 |

If the table on the left does not contain all the key columns of the other table, an
er is returned:

```
t13: [[a:1 2 4; bb:10 ON ON] c:-100 ON -400; d:-1000 -2000 -4000];
t10 ij t13
```

```
'bb
[0] t10 ij t13
^
```