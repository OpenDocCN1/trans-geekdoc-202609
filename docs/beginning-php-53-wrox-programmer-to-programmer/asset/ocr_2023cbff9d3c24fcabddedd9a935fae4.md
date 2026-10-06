# Part III: Using PHP Practice

So when creating indexes on a table, don't create more than you need. Limit indexed columns to those that will be searched or sorted frequently. If required, you can create additional indexes on a table as you need them to increase performance.

# Introducing SQL Statements

To actually work with databases and tables, you use SQL statements. Common statements include:

+   - SELECT — Retrieves data from one or more tables
- INSERT — Inserts data into a table
- REPLACE — Replaces data in a table. If the same record exists in the table, the statement overwrites the record with the new data
- UPDATE — Updates data in a table
- DELETE — Deletes data from a table

Other often-used statements create or modify tables and databases themselves, rather than manipulating the data stored in table:

+   - CREATE — Creates a database, table or index
- ALTER — Modifies the structure of a table
- DROP — Wipes out a database or table

You learn more about these statements as you work through the next few chapters. Just to give you a taste though, let's take a look at the typical form of a MySQL SELECT statement, which retrieves records from a table. Operations performed with SELECT are known as queries (hence the name "Structured Query Language")

```
SELECT field1, field2, ..., fieldn FROM table WHERE condition
```

A statement may extend to multiple lines. Here is a simple example of a real multi-line SQL statement:

```
SELECT lastName, firstName
FROM users
WHERE firstName = 'John'
```

Take a closer look at the FROM and WHERE clauses in query. The query returns any record from the users where the value of the firstName is "John". Assuming there actually a table called users in the database, the query's output might look like this:

```
Simpleton John
Smith John
Thomas John
```

The returned values are known as the result set. As you see, you can loop through the rows in a result set within your PHP script. If your query finds no results, NULL (discussed in the next section) is returned instead.

Other SQL statements such as DELETE or INSERT don not return a result set.