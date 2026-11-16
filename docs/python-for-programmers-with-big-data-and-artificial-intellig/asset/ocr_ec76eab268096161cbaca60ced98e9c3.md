| Clause | Description |
| :--- | :--- |
| BY | Criteria for ordering rows. Optional in a SELECT query. |
| INNER JOIN | Merge rows from multiple tables. |
| INSERT | Insert rows into a specified table. |
| UPDATE | Update rows in a specified table. |
| DELETE | Delete rows from a specified table. |

# ## 16.2.2 SELECT Queries

The previous section used SELECT statements and the * wildcard character to get all the columns from a table. Typically, you need only a subset of the columns, especially in big data where you could have dozens, hundreds, thousands or more columns. To retrieve only specific columns, specify a comma-separated list of column names. For example, let's retrieve only the columns first and last from the authors table:

lick here to view code image

```
In [9]: pd.read_sql('SELECT first, last FROM authors', connection)
Out[9]:
      first     last
0     Paul     Deitel
1    Harvey     Deitel
2     Abbey     Deitel
3      Dan     Quirk
4  Alexander     Wald
```

# ## 16.2.3 WHERE Clause

You'll often select rows in a database that satisfy certain selection criteria, especially in big data where a database might contain millions or billions of rows. Only rows that satisfy the selection criteria (formally called predicates) are selected. SQL's WHERE clause specifies a query's selection criteria. Let's select the title, edition and copyright for all books with copyright years greater than 2016. String values in SQL queries are delimited by single (') quotes, as in '2016':

lick here to view code image

```
In [10]: pd.read_sql("""SELECT title, edition, copyright
                   ...:                   FROM titles
                   ...:                   WHERE copyright > '2016'""", connection)
Out[10]:
```