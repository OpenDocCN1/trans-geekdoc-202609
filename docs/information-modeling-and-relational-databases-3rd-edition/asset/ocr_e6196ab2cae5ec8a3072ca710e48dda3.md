Although most joins in practice are natural inner joins, sometimes natural joins should be avoided. The natural join operation cannot be used to join columns with different names. For example, it can't join dept. and deptCode in the query of Fig. 12.42. Moreover, the natural join operation must not be used if different tables in the **from** clause include columns with the same name that should not be equated. For example, consider the table schemas for our column-list join example: Department (deptCode, name); Employee (empNr, name, deptCode, gender).

A natural join between Department and Employee would equate not just deptCode but name as well. Any row in the result would equate the employee's name with the department's name, which is nonsense.

Sometimes, we do wish to naturally join two tables on more than one column. For example, recall the following schema discussed in the relational algebra section.

```
Account (branchNr, accountNr, balance)
          |
          v
AcUser (branchNr, accountNr clientNr)
          |
          v
Client (clientNr, clientName)
```

To list the balance and client details for all the accounts requires a composite join on account (compound identifier) and a simple join on client. This may be specified with the natural join syntax as:

```
select * from Account natural join AcUser natural join Client
```

or as a conditional join:

```
select Account.branchNr, Account.accountNr, balance,
Client.clientNr, clientName
from Account join AcUser
on Account.branchNr = AcUser.branchNr
and Account.accountNr = AcUser.accountNr
join Client
on AcUser.clientNr = Client.clientNr
```

For conditional, column-list, and natural joins, join is assumed to mean inner join unless an outer join is explicitly specified (see later). In these cases, inner may be explicitly declared (e.g., inner join or natural inner join). If natural is declared, an on clause or a using clause must not be. If three or more tables are included in a join expression, the joins are normally evaluated in a left-to-right order. The join order can also be controlled by inserting parentheses. Because natural inner joins are associative, their order doesn't affect the actual result.

As a more complex example, consider the relational schema in Fig. 12.44. In the first table, "mgrEmpNr" denotes the employee number of the department manager (where there is a manager). The pair-subset constraint indicates that an employee manages a