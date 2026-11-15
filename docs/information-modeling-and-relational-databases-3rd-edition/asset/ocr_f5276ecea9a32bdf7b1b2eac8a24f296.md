Q3 shows one way to express this in ConQuer.

```
Q3 ✓Employee1
   |-- lives in City1
   |-- was born in Country1
   |-- supervises Employee2
         |-- lives in City1
         |-- was born in Country2 <> Country1
```

When an object type appears more than once, ActiveQuery automatically appends subscripts to distinguish the occurrences. You can equate instances by equating their subscripts (e.g., City1). More generally, you can use comparators to compare instances (e.g., Country2 <> Country1). Try this in SQL. It’s not that hard, but you have to admit it’s easier in ConQuer!

As a final example, suppose the ORM model includes the m:n fact type Employeee has Rating. Now, consider the query, “List each branch and those of its employees whose maximum individual rating exceeds the average of his/her branch” (remember that an employee may have many ratings). Query Q4 shows how to do this in ConQuer, illustrating the use of bag functions in for-clauses.

```
Q4 ✓Branch
   |-- employs ✓Employee
         |-- achieves Rating
               |-- max(Rating) for Employee >
               |   avg(Rating) for Branch
```

At the relational level, two tables are needed: Employee( empNr, branchNr, ...); Achieves ( empNr, rating ). The SQL for this query is shown here. This is tricky, especially the final correlation between branch numbers, and even experienced SQL programmers might have difficulty with it. The equivalent ConQuer query would be easy for most end users who have even minimal experience with the language. This gives some indication of the potential of a language such as ConQuer for empowering end users.

```
select max(X1.branchNr), X2.empNr
from Employee as X1, Achieves as X2
where X1.empNr = X2.empNr
group by X2.empNr
having max(X2.rating) >
       (select avg(X4.rating)
       from Employee as X3, Achieves as X4
       where X3.empNr = X4.empNr
       and X3.branchNr = X1.branchNr)
```

ActiveQuery allows you to define derived predicates and store these definitions. These derived predicates (or “macros”) can then be used just like base predicates in other