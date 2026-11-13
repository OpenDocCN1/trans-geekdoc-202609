The following statement would affect only Don Corleone:

```
update folks set fname='Vito' where id=2;
```

As you can see, it would be risky to run an update statement based on the fname column, as you could accidentally update every column in this table.

```
update folks set fname='Vito' where fname='Don';
```

You can also use update to give your underpaid employees a raise:

```
update folks set salary=50000 where salary<50,000;
```

As of MySQL 4.0, you can also update a table based on data in other tables. This is an extremely helpful feature, since it enables you to make changes using only SQL statements that previously would have required a program or script (or some very dodgy workarounds).

To demonstrate, we add another table (Table 3-2) to the example set, recording the income brought in by the people in folks:

| id | Income |
|---|---|
| 1 | 500,000 |
| 2 | 1,500,000 |
| 3 | 250 |
| 4 | 1,250,000 |

We can use a multi-table update to give the top performers a raise:

```
update folks, income
 set folks.salary = folks.salary * 1.1
 where folks.id = income.id and income.income >= 1000000
;
```

As you might guess from the syntax, you can update multiple tables with a single update statement. You might have good reasons to do that, but be careful – the results might not be what you expect. The reason is that the order in which