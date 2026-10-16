You get the following results table, with the same four columns, but with still different rows:

| petName | petType | petName | petColor |
|---|---|---|---|
| Unicorn | Horse | Unicorn | white |
| Unicorn | Horse | Unicorn | silver |
| <NULL> | <NULL> | Fish | Gold |

Notice that these results contain all the rows for the `Color` table on the right but not for the `Pet` table. Notice the blanks in the columns for the `Pet` table, which doesn’t have a row for `Fish`.

The joins that I’ve talked about so far find matching entries in tables. Sometimes it’s useful to find out which rows in a table have no matching entries in another table. For example, suppose that you want to know who has never logged into your Members Only section. Because you have one table with the member’s login name and another table with the dates when the user logged in, you can ask this question by using the two tables. Doing a join and looking at all the matches to try to see who is missing might be impossible with a large number of user names in the table. However, you can find out which login names do not have an entry in the login table with the following query:

```
SELECT loginName from Member LEFT JOIN Login
       ON Member.loginName=Login.loginName
       WHERE Login.loginName IS NULL
```

This query will give you a list of all the login names in `Member` that are not in the `Login` table.

# Updating information

Changing information in an existing row is *updating* the information. For instance, you might need to change the address of a member because she has moved, or you might need to add a fax number that a member left blank when he originally entered his information.

The `UPDATE` query is very straightforward:

```
UPDATE tablename SET column=value,column=value,...
                 WHERE clause
```

In the SET clause, you list the columns to be updated and the new values to be inserted. List all the columns that you want to change in one query. Without a WHERE clause, the values of the column(s) would be changed in all the rows. But with the WHERE clause, you can specify which rows to update. For instance, to update an address in the `Member` table, use this query: