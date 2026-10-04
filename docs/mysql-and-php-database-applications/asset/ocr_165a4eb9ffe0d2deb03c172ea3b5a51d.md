# 258 Part IV: Not So Simple Applications

```
select name from Names where first_name not in (select first_name
from Other_names)
```

However, in MySQL the best way to go about this is to perform an outer join.
Something like this:

```
select N.first_name
from Names N
left Join Other_names Otn on
N.first_name = Otn.first_name
where Otn.first_name is null
```

With an outer join we can be sure that the Names table will be preserved in
entire. In the joined table, there will be non-null results where there are
matching values. For instance, since 'Jay' in both tables, string will exist in
both columns of the resulting query. But if there is no matching value, there will be
a null value in the joined table.
You will see sub-selects for statements such as this:

```
select first_name from Names where first_name in (select first_name
from Other_names)
```

In a case like this straight join would produce the same result.

```
select N.first_name
from Names N, Other_names Otn
where Otn.first_name = Otn.first_name
```

MySQL will not support unions until version 3.24. However, there is a way to
work around this without too much difficulty in version 3.23. You can create a
temporary table into which you can insert different select statements. For instance
in other database packages you might do something like this:

```
select first_name, last_name from table_1
union
select first_name, last_name from table_2
```

In MySQL 3.23 you would create a temporary table and then insert the results
of the select statements into that table. The preceding code would be re-created
like this:

```
create temporary table name_union
select first_name, last_name from table_1;
```