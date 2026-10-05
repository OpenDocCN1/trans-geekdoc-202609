
# Joins

q is thus equipped with eight additional commands to perform particular types of joins. In the following section, we cover these commands one by one.

## 7.2 JOIN FUNCTIONS

The dedicated join functions are: ij, ej, lj, lj, upsert, uj, pj, aj, asof, wj. They also provide a powerful suite of join operations, which naturally incorporates within a table-driven framework.

### 7.2.1 ij

ij, or "inner" join, joins two tables on the key columns of the second table. Thus, the table on the right must be a keyed table, and the keys of that table have to be contained in the table on the left. As a result, the combined table contains each row from the left table, matching values from the columns of the right table:

```
t10: [[ a: 1 2 3; b: 10 20 30;c: 100 200 300];
t11: [[a:1 2 4] c:-100 ON -400; d:-1000 -2000 -4000];
t10 ij t11
```

| a b c |
|---|---|---|
| 1 10 -1000 |
| 2 20 -2000 |

The output contains only two rows, the rows which are matched based on the values of a table t11. The output is an unkeyed table. Finally, the provided example also illustrates the role of missing/null entries in the table, which replace the not null values during the null values in column c.

The inner join works in the case when the table is keyed by more than one column as well:

```
t12: [[a:1 2 4; b:10 ON ON] c:-100 ON -400; d:-1000 -2000 -4000];
t10 ij t12
```

| a b c |
|---|---|---|
| 1 10 -1000 |

If the table on the left does not contain all the key columns of the other table, an error is returned:

```
t13: [[a:1 2 4; bb:10 ON ON] c:-100 ON -400; d:-1000 -2000 -4000];
t10 ij t13
```

```
'bb
[0] t10 ij t13
^
```

The error 'bb' denotes that this symbol is unknown and cannot be found during the ij call, which expected a bb column to be present in t10.

In an IDE, for example in qPad, we will get the following error, which gives us hints on what is wrong with our command:

```
ERROR: 'bb
(attempt to use variable bb without defining/assigning first (or user-defined signal))
```

### 7.2.2 ej

ej, or 'equi' join joins two tables on the list of columns which are provided as an additional argument of the join. As a result, the operation returns all rows with common entries for the selected column(s). The join works as follows:

```
t14: ([ a:1 2 4 2; c:-100 0 -400 10; d:-1000 -2000 -4000 -500]);
ej[`a; t10;
```

```
| a b c d
|---|---|---|---|
| 1 10 -100 -1000 |
| 2 20 -2000 |
| 2 10 -500 |
```

The equi join ignores the presence of keys:

```
ej[`a; t10; t11]
```

```
| a b c d
|---|---|---|---|
| 1 10 -100 -1000 |
| 2 20 -2000 |
```

```
ej[`a;b; t10; t12]
```

```
| a b c d
|---|---|---|---|
| 1 10 -100 -1000 |
```

### 7.2.3 lj

lj, or 'left' join, joins two tables on the key columns of the second table. Thus, the righthand side table must be a keyed table, where keys of that table have to be contained in the lefthand side table. A left join differs from an inner join in way it treats the entries in the left table which are not matched by the other table. The result of the left join operation is a combined table, which contains each row from the left-hand side table and updates from the right-hand side if the keys are matched, or nulls when the rows are not matched.

We use the tables defined in the inner join section to show the difference between the two verbs:

```
t10 lj t11
```

| a b c d |
|---|---|---|---|
| 1 10 -100 -1000 |
| 2 20 | -2000 |
| 3 30 300 | |

The left join output table contains all rows of row t10. The first two rows have a matching entry in left join t11. In such a case, entries are updated in the same way as we have experienced in an inner join. The row with a=1 does not have a matching entry in t11 and was omitted in the inner join. In the left join, the other row is inserted without any modification, and the missing values populate columns from the table t11. Remark: The left join can be constructed using comma functionality. This can be proved by:

```
(t10 , t11) [t10]
```

In other words, lj and , are almost identical, but lj is a bit more general it will still work if the table on the left is keyed.

### 7.2.4 pj

pj, or “plus” join, works like a “left” join, instead of replacing values it adds them:

```
t10 pj t11
```

| a b c d |
|---|---|---|---|
| 1 10 0 -1000 |
| 2 20 0 0 |
| 3 0 0 0 |

Let us further denote that missing entries are filled with zeros. The columns are supposed to be summed together to be of the same type. If there is a mismatch between types, a type error is returned:

```
t10 pj update c:"s"c from t11
```

The type error does not occur for columns which can be promoted, like integer vs floats:

```
t10 pj update c:"f"c from t11
```

| a b c d |
|---|---|---|---|
| 1 10 0 -1000 |
| 2 20 0 0 |
| 3 0 0 0 |

The contents of the c column converted into float. The conversion is performed for mixing numeric and time formats as we recall the time formats is either integer or float:

```
t10 pj update c:"z"c from t11
```

| a b c d |
|---|---|---|---|
| 1 10 2000.0.T00:00:000 |
| 2 20 2000.0.T00:00:000 |
| 3 0 2000.0.T00:00:000 |

### 7.2.5 upsert

The upsert function is used to add entries into an existing table. The upsert of new entries assumes two tables have an identical structure or the table on the righthand side has a subset of columns of the left. The operation works in two modes: For keyed tables, upsert will update the matching entries and add (append) those who are not:

```
t15: [[a: 4 7]; b: 400 700];
t5 upsert t15
```

| a b |
|---|---|
| 4 | 400 |
| 5 | 50 |
| 6 | 60 |
| 7 | 700 |

The second mode is for unkeyed tables, where new entries are always added at the end of the table:

```
(t5) upsert t15
```

| a b |
|---|---|
| 4 | 40 |
| 5 | 50 |
| 6 | 60 |
| 4 | 400 |
| 7 | 700 |

We have used the same tables as in the previous example while we have removed keys to tables. The function (!) reads the first columns of the table. The order of entries in the two tables is preserved. When we try to add two tables with non-matching structure, the mismatch error occurs:

```
(t5) upsert update:1 from t15
```

If the table is passed by reference, the table is updated:

```
t5 upsert t15
```

The output of the adding can be recovered by inspecting the content of the referred table:

```
t5
```

| a b |
|---|---|
| 4 | 400 |
| 5 | 50 |
| 6 | 60 |
| 7 | 700 |
```

### 7.2.6 uj

The "union" join is a generalization of the comma-join (,) and upsert functions. Its purpose is to provide both a sideways join, as well as an insert or upsert functionality, when two table schemas do not necessarily match. Let us take, for example, tables t5 and t15.

```
t5
```

| a b |
|---|---|
| 4 | 40 |
| 5 | 50 |
| 6 | 60 |

```
t15
```

| a b |
|---|---|
| 4 | 400 |
| 7 | 700 |
```

We just saw that we can join these tables using upsert. If, however, we changed the schema of one of the tables and attempted to do the same operation:

```
update c:`A`B from `t15
```

```
t5 upsert t15
```

'mismatch
[0] t5 upsert t15
^
```

we will get the above mismatch error since the shapes of the two tables do not conform anymore. To create the union of the two tables, we rely on uj:

```
t5 uj t15
```

| a b c |
|---|---|---|
| 4 | 40 A |
| 5 | 50 |
| 6 | 60 |
| 7 | 700 B |

We now have a union where the missing values are left with null. An important caveat to uj: Although the function will also work on unkeyed tables, we strongly recommend using it in these cases. The reason is that uj internally uses an append (,), which is not in-place (as opposed to the upsert function), and therefore any types of columns can be appended to each other. To illustrate this, let's unkey tables t5 and t15, and change the datatype of column b on t5 from long to a symbol:

```
t5():() zkey t5;
t15():() zkey t15;
update b:`40``50``60 from `t5
meta t5
```

| c t f a |
|---|---|---|---|
| a | j |
| b | s |

meta t15

```
| c t f a |
|---|---|---|---|
| a | j |
| b | j |
| c | s |
```
