Even with no joins, similar problems with nulls arise if the view excludes a column used in its search condition. For example, suppose we try the following insertion on our FemaleCompScientist view:

```
insert into FemaleCompScientist
values ( 105, 'Bird', 'L', 'Lec' )
```

If we allow this update, is "Bird, L" included in the result? Given our earlier view definition, if the update were accepted it would translate into the following row being inserted into the Academic table: (105, “Bird, L”, null, null, “Lec”). The new row fails the view definition because the condition ( dept = 'CS' and gender = 'F' ) evaluates to unknown. So, if the update is accepted, it is not part of the view!

It is better to reject any update that fails to satisfy the view definition. This is done by appending “with check option” to the view definition. For example, the following view may be used for computer science professors:

```
create view CSProfessor ( empNr, name, dept, rank ) as
select empNr, empName, dept, grade
from Academic
where grade = 'Prof' and dept = 'CS'
with check option
```

The following attempts to update this view would now have the results shown.

```
insert into CSProfessor
values ( 106,'Wirth N','CS','Prof' ) → accepted
insert into CSProfessor
values ( 107,'Russell B','MA','Prof' ) → rejected
update CSProfessor
set rank = 'Lec'
where empNr = 103 → rejected
```

The type of view we have considered so far is basically a predefined query on one or more base tables. The result of the query is not stored in the view, only the query definition. A subsequent query on the view is combined with the query in the view definition, and the composite query is run against the base table(s). This ensures that the result is always up to date with the content of the base tables, but may be inefficient if a view is queried frequently.

Another option is to execute the query defined for the view and cache the result. Now, the view represents an actual data structure held in physical storage, not just the definition of a data structure. This is known as a _materialized view_. Such views have obvious advantages in efficiency, but subsequent changes to data in the base table(s) can lead to the view becoming increasingly unrepresentative of the “real” data. Commercial systems that support materialized views normally provide some mechanism for periodically refreshing them.