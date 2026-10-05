where we have created two tables: at1 is the one that drives the times at which
want to know the last valid observations, can be found in the other table at2.
The notion of last valid is derived from the variable t – we have started with one
variable in the initial case. The as-of-join is then performed as:

```
aj[ `t; at1; at2]`
```

giving the output:

| t a b c |
|---|---|---||
| 0 10 1000 |
| 5 20 500 50000 |
| 7 30 7000 |

The first row of at1 has t=0, for which there is no “last valid” value in the other
table2. The output is a table, which has the same number of rows as the table at1 .
contains all the columns of table at1 as well as the columns from the other table at2.
This simple example illustrates the difference in join behaviour what we saw till.
fully changed. Second, column b is present in both tables, taking different values in
each of them. First, column a is present in table at1 only and thus as such, it is present in the output
fully changed. The output contains only the corresponding column in the output, where
t values are mixed from both tables. If there is no last valid value from the look-up
table, as is the case for the first observation, the value from at1 is used, otherwise, the
last value from at2 is used. The column c is taken from the table at2 which,
where the row is missing as there is no value prior to t=0 and there is no
default value of at1.

The ordering of rows in table at1 does not matter. Let us change the order of
table at1, perform the as-of join and compare it with the original join, having the
outputs (and outputs only) sorted by the t:

```
aj[ `t; at1; at2` ] ~ t xasc[ `t; at1[1 2 0]; at2]`
```

1b

What is required in sorting is that the second table is sorted by the last
column specified in the first argument (`t` in our example). The reason for this is
to the lookup algorithm used in an aj being binary search. Also, note that the
common columns in both tables are of the same type.

Let us further that more than one column may be provided for the last-
valid code. The order of the columns specified matters: all columns specified prior
to the last column are used for the exact join. The last column is used as an approx-
imate lookup using binary search, which allows us to align two differently sampled
time series.

The additional columns may correspond to the symbol named, traded venue or
ay further characteristics. The aj operation thus us to provide as-of join