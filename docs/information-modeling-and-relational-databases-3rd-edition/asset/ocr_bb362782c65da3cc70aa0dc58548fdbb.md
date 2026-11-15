```
Employee ( empNr, empName, deptCode , gender )
(M,F)
Drives ( empNr, carRegNr )
Car ( carRegNr, carModel )
```

Suppose we want to list the employee number and name of each employee who drives as well as the model of their cars. Looking at the schema, the information is spread over three tables. As indicated in Fig. 12.43, we can join the Employee and Drives tables by matching empNr, and join with the Car table by matching carRegNr (join values are shown in bold). Using the special syntax for natural joins, this can be formulated simply as shown.

| empNr | empName | deptCode | gender |
|---|---|---|---|
| 001 | Hagar T | DV | M |
| 002 | Wong S | DV | F |
| 003 | Jones E | MK | F |
| 004 | Mifune K | SL | M |

| empNr | carRegNr |
|---|---|
| 001 | ABC123 |
| 003 | ABC123 |
| 003 | TAH007 |

| carRegNr | carModel |
|---|---|
| ABC123 | Ford |
| PKJ900 | Ford |
| TAH007 | Saturn |

```
select empNr, empName, carModel
from   Employee natural join Drives
       natural join Car
```

| empNr | empName | carModel |
|---|---|---|
| 001 | Hagar T | Ford |
| 003 | Jones E | Ford |
| 003 | Jones E | Saturn |

# FIG. 12.43 A projection on the natural join of three tables.

Currently, most SQL dialects (including SQL Server) do not support the natural join syntax. Instead, the conditional join syntax is often used to handle natural joins. For example, the query in Fig. 12.43 may be reformulated, thus:

```
select Employee.empNr, empName, carModel
from   Employee join Drives
on Employee.empNr = Drives.empNr
join Car
on Drives.carRegNr = Car.carRegNr
```

Alternatively, SQL-89 syntax can be used as follows:

```
select Employee.empNr, empName, carModel
from   Employee, Drives, Car
where Employee.empNr = Drives.empNr
and   Drives.carRegNr = Car.carRegNr
```

When the natural join operator is used, any join columns in the select list must be denoted by their local (unqualified) names. If a natural join is specified using other syntax (e.g., conditional join or SQL-89 syntax), the join columns must be qualified.