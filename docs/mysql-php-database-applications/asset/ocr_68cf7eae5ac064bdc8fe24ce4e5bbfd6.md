# # group by and aggregate functions

Remember back to when we were talking about using `select` with `distinct` and how that removes rows you don't need? That may have seemed pretty cool, but it's nothing compared to what you can get out of the `group by` predicate and its associated aggregate functions.

Consider this task: You wish to know the number of entries from each state in the database (for example, six from California, seven from New York, two from Vermont). If you did a `select distinct state from users order by state` query, you would get a listing of each state in the database, but there would be no way to get the numbers. As MySQL goes through the table to process the query it simply skips over rows that would return identical values.

However, with `group by`, MySQL creates a temporary table where it keeps all the information on the rows and columns fitting your criteria. This allows the engine to perform some very important tasks on the temporary table. Probably the easiest way to show what `group by` can do is by showing one of the aggregate functions. We'll start with `count()`.

> > MySQL may not actually create a temporary table for each `group by`; however, the actual inner workings of a `group by` are pretty complex, and this is a good way to think about what MySQL is doing.

# ## count()

Once again, the goal of your query is to find out the number of people from each state in your users table. To do that you will use `group by` with `count()`.

Remember that when the `group by` clause is used you can imagine MySQL creating a temporary table where it assembles like rows. The `count()` function then (you guessed it) counts the number of rows in each of the groups. Check out the following query and the result returned in Figure 3-5:

```
select state, count(*) from users group by state;
```

Here the asterisk (*) indicates that all rows within the group should be counted. The `count(*)` function is also handy for getting the total number of rows in a table.

```
select count(*) from users;
```

Within a `group by`, you can also indicate a specific field that is to be counted. `count` will look for the number of non-null values. Take, for example, the table in Figure 3-6.