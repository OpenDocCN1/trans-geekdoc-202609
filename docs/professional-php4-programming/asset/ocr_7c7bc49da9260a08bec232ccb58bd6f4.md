As we can see, ALL is used for each table. This indicates that MySQL is doing a full join using full table scans for all tables, which is a badly executed query that has to be improved. In the example, 45,268,558,720 rows (74*2135*74*3872) must be examined. This would be a long query.

One problem is that MySQL can’t use indices on columns efficiently if they are declared differently. In this context, VARCHAR and CHAR are the same unless they are declared as different lengths. In our example tt.ActualPC is a CHAR(10) and et.EMPLOYID is a CHAR (15), so there's a length mismatch. Therefore, we need to change ActualPC from 10 to 15 characters:

```
mysql> ALTER TABLE tt MODIFY ActualPC VARCHAR(15);
```

Now tt.ActualPC and et.EMPLOYID are both VARCHAR(15), let's run EXPLAIN again:

| Table | Type | Possible Keys | Key | Key Length | Ref | Rows |
|---|---|---|---|---|---|---|
| tt | ALL | AssignedPC, ClientID, ActualPC | NULL | NULL | NULL | 3872 |
| do | ALL | PRIMARY | NULL | NULL | NULL | 2135 |
| et_1 | ALL | PRIMARY | NULL | NULL | NULL | 74 |
| et | eq_ref | PRIMARY | PRIMARY | 15 | tt. ActualPC | 1 |

We have reduced the number of rows to be examined by a factor of 74.

A second alteration can be made to eliminate the column length mismatches for the tt.AssignedPC = et_1.EPLOYID and tt.ClientID = do.CUSTNMBR comparisons:

```
mysql> ALTER TABLE tt MODIFY AssignedPC VARCHAR(15),
MODIFY ClientID VARCHAR(15);
```

Now EXPLAIN will show:

| Table | Type | Possible Keys | Key | Key Length | Ref | Rows |
|---|---|---|---|---|---|---|
| et | ALL | PRIMARY | NULL | NULL | NULL | 74 |
| tt | ref | AssignedPC, ClientID, ActualPC | ActualPC | 15 | et. EMPLOYID | 52 |
| et_1 | eq_ref | PRIMARY | PRIMARY | 15 | tt. AssignedPC | 1 |
| do | eq_ref | PRIMARY | PRIMARY | 15 | tt. ClientID | 1 |

The query is optimized to be as good as it can be. This work is very common for most queries, so use EXPLAIN and create indices and solve different length problems. Take into consideration MySQL's attitude toward different length keys when designing the data model so that there does not arise a need to change a lot of tables if the queries are slow.