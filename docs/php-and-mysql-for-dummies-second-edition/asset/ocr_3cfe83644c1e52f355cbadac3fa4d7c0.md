+   - All the select queries must select the same number of columns.
+   - The columns selected in the queries must contain the same type of data.

The results set will contain all the rows from the first query followed by all the rows from the second query and so on. The column names used in the results set are the column names from the first `SELECT` query.

The series of `SELECT` queries can select different columns from the same table, but situations in which you want a new table with one column in a table followed by another column from the same table are unusual. It’s much more likely that you want to combine columns from different tables. For example, you might have a table of members who have resigned from the club and a separate table of current members. You can get a list of all members, both current and resigned, with the following query:

```
```sql
SELECT lastName,firstName FROM Member UNION ALL
    SELECT lastName,firstName FROM OldMember
```
```

The result of this query is the last name and first name of all current members, followed by the last name and first name of all the members who have resigned.

Depending on how you organized your data, you might have duplicate names. For instance, perhaps a member resigned, and his name is in the `OldMember` table — but he joined again, so his name is added to the `Member` table. If you don’t want duplicates, don’t include the word `ALL`. If `ALL` is not included, duplicate lines are not added to the result.

You can use `ORDER BY` with each `SELECT` query, as I discuss in the previous section, or you can use `ORDER BY` with a `UNION` query to sort all the rows in the result set. If you want `ORDER BY` to apply to the entire result set, rather than just to the query that it follows, use parentheses as follows:

```
```sql
(SELECT lastName FROM Member UNION ALL
    SELECT lastName FROM OldMember) ORDER BY lastName
```
```

![](bbox=[0.122, 0.711, 0.211, 0.781])

The `UNION` statement was introduced in MySQL 4.0. It is not available in MySQL 3.

# Join

Combining tables side by side is a *join*. Tables are combined by matching data in a column — the column that they have in common. The combined results table produced by a join contains all the columns from both tables. For instance, if one table has two columns (`memberID` and `height`), and the second table has two columns (`memberID` and `weight`), a join results in a table with four columns: `memberID` (from the first table), `height`, `memberID` (from the second table), and `weight`.