# Portions of SQL the SQL Standard that MySQL Doesn’t Support

The MySQL developers are constantly working on improvements to the software. It is possible that within the next couple of years they will support most of the features you'd found in high-priced commercial software, like Oracle, Sybase, Informix, or Microsoft's SQL Server. As of the writing of this book, there are a couple of portions of the select syntax that MySQL doesn't support.

# Unions

Unions allow query with the same number of columns to be returned in one result set. For instance, if you had two tables user names, you could have all of the names in one query returned with a statement like this:

```
select first_name, last_name
from table_1
union
select first_name, last_name
from table_2
```

Unions are convenient, but their absence in MySQL isn't that big of a deal. In the preceding example, you could easily run a second query.

# Correlated subqueries

If you're coming from a background of using a package like Oracle, you may find the absence of correlated subqueries troubling. The good news is that subquery support is on the developers' priority list. For those new to the concept, subqueries allow you to define an entire query in the where clause. For example, if you had a table that stored students and their test scores, you could easily find all the students with better-than-average scores:

```
select first_name, last_name, score
from test_scores
where (select avg(score) from test_scores)
```

You can achieve the same effect by running two queries. In all cases you can work around the absence of subqueries by running additional queries. You lose some elegance, but the effect is identical.