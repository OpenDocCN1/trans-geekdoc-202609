# Music Query: Multiple Tables

+   * Forming groups of records by the grouping variable venue.state

+   * Counting the number of records in each group

+   * Combining the counts per state

The aggregation can be done like this:

```
query = 'SELECT venue_state
```

```
for row in conn.execute(query):
  print(row)
OUT:
  ('CA', 2)
  ('CD', 1)
  ('NY', 1)
```

The line of code SELECT venue_state, count(*)

will return each state and its associated count.

The line

GROUP BY venue_state

will perform the grouping operation.

From the result set, are tuples containing each state and its associated number of venues. The GROUP BY command is very powerful and can aggregate across multiple grouping variables.

In the next section, we will get to the main purpose of relational databases: joining datasets. This will allow for queries which can extract information from across the database.

# 7.4  Music Query: Multiple Tables

When doing data science, the required data may be spread across two or more tables. In such a case, we can join the tables two at a time on common fields.