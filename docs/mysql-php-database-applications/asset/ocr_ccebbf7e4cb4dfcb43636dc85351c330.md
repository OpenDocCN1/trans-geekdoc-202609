# USING distinct

At times, your query will contain duplicate data. For instance, if your goal is to see all the cities in California, your first instinct might be to run a query like `select city, state from users where state='CA'`. But look at the result returned in Figure 3–3.

![](bbox=[0.15, 0.21, 0.81, 0.58])

Figure 3–3: Results of query using select city, state from users where state='CA'

Notice that the first three rows are identical. You could use PHP to sort through the identical results and return only unique city names in California, but that would be a fair amount of scripting. You can get what you want directly from the database by using `select distinct`. When you use `distinct`, the MySQL engine will remove rows with identical results. So here the better query is `select distinct city, state from users where state='CA'`, which returns the data in Figure 3–4, which is exactly what you want.

# USING between

You can also choose values within a range by using the `between` predicate. The `between` predicate works for numeric values as well as dates. In the following query, `lastchanged` is a `timestamp` column. If you want to find the people who signed up on June 26, 2002, you could use this query:

```
select * from users where lastchanged between 20020626000000 and
20020626235959;
```