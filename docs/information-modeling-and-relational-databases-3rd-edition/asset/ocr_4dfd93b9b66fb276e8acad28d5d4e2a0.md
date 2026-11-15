Here, the “level” column indicates the relative depth in the hierarchy, taking 1 as the top level (“level” is a delimited identifier here because it’s a recognized keyword in SQL).
We’ve taken as our anchor the topmost level by specifying where parentDept is null, so the anchor tuple is <101, ‘Management’, null, 1>. At the next level, we’re now looking for departments that have a deptId of 101. The union all operation adds the tuples <201, ‘Sales’, 101, 2> and <202, ‘Production’, 101, 2>.
The join in the recursive part of the CTE can now add the departments under Sales. Production has no subdepartments and so the join produces no results. After adding the three Sales subdepartments there are no other possibilities for the join (because no department has a parent deptId of 301, 302, or 303), so the recursion ends.

When the select statement after the CTE is executed, it creates the result set for myCTE and then applies its own query, which in this case just extracts three of the columns produced by the recursive CTE.
Of course, the final result depends on the query that operates on the CTE results and it does not have to list all the CTE rows.
For instance, the following recursive query finds the total number of staff below a particular point in the hierarchy—again, we’ve taken the top node, but with a simple change to the query defining the anchor, we could have taken any point in the hierarchy.

```
with myCTE (deptId, totalStaff, parentDept) as
(
 select anchor.deptId, anchor.totalStaff, anchor.parentDept
 from Dept as anchor
 where parentDept is null
 union all
 select child.deptId, child.totalStaff, child.parentDept
 from Dept as child join myCTE as parent
 on child.parentDept = parent.deptId
)
select sum(totalStaff) as totalStaff from myCTE
```

which produces the expected result:

| totalStaff |
|---|
| 20 |

Clearly, we could have produced this particular result using a much simpler query, but in general, recursion allows us to frame queries on hierarchical structures that would be difficult (or clumsy) to achieve in other ways. Most commercial dialects of SQL support CTEs and recursion, but the details may vary from the outline we’ve given here.

# 12.13 SQL: Updating Table Populations

Generically, an “update” of the population of the database tables may involve any of three relational operations: insert a row into a table, delete a row from a table, or modify one or