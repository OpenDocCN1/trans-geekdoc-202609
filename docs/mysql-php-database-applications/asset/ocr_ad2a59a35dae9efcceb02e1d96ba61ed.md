| company_id | company_name | address |
|---|---|---|
| 1 | Big Co Company | 1121 43rd St |
| 2 | Little Co Company | 4444 44th St |

| contact_id | company_id | Name | Title | Phone | Email |
|---|---|---|---|---|---|
| 1 | 1 | Jay Greenspan | Vice President | 4155551212 | 1121 43rd St |
| 2 | 1 | Brad Bulber | President | 4155552222 | 4444 44th St |
| 3 | 2 | John Doe | Lacky | 2125556666 | 4444 44th St |

Figure 3-11: Tables in need of a join

Making this join is easy enough in SQL. All the tables to be joined must be listed in the from portion of the select statement. And the fields on which the join takes place must be listed in the where portion:

```
select *
from companies, contacts
where companies.company_id = contacts.company_id;
```

At those times when a reference to a field name is ambiguous, you need to specify which table the column comes from by using the syntax table_name.column_name. You can do this in the where clause in Figure 3-12. If you fail to indicate the table from which you're pulling the column in the SQL statements, MySQL will return an error.

This type of join, in which tables are merged based on quality in a common field, is extremely common. It is known as an equi-join or inner join. The name “inner join” will make more sense when you learn about the outer join later in this chapter.

Once you begin performing joins, aliases become convenient. By specifying an alias in the from clause you can save yourself some typing. In the following code, t1 is an alias for companies and t2 is an alias for contacts.

```
select *
from companies t1, contacts t2
where t1.company_ID = t2.company_ID;
```

# The multi-table join

An equi-join can be applied to more than one table. Many of your SQL statements will join three, four, or more tables. All you’ll need to do is add additional columns after select, additional tables in the from clause, and the additional join parameters in the where clause. Take a look at the tables that need multiple joins in Figure 3-13.