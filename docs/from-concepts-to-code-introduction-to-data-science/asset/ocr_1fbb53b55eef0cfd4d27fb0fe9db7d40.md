The count(*) function counts the number of records. The fetchone() function retrieves the result set.

Data aggregations are useful for partitioning a dataset and computing statistics on each piece of the partition. An example is the calculation of a town's daily average rainfall by month. These calculations are commonly and efficiently performed with a Split-Apply-Combine pattern. The first step in the strategy is to define one or more grouping variables (in this case, the grouping variable would be month). Next, the months are split into discrete groups. For the records in each group, a function is applied to the values. Here, we calculate the mean rainfall over the days in January, February, and so on. This yields the daily average rainfall for each month. In the final step, the results from each group (the months) are combined into a data structure, such as a table.

The Split-Apply-Combine pattern is supported in SQL and many other languages including Python and R. Let's demonstrate how to aggregate data using SQL. By creating a small dataset of concert venues with their states:

```
query = 'CREATE TABLE venues
(venue_name string, venue_state string);'

cur.execute(query)
conn.commit()

venue_data = [('Red Rocks', 'CO'),
('Santa Barbara Bowl', 'CA'),
('Greek Theater', 'CA'),
('Madison Square Garden', 'NY')]

query = 'INSERT INTO venues VALUES (?,?,?)'
cur.executemany(query, venue_data)
conn.commit()

query = 'SELECT * FROM venues;
for row in conn.execute(query):
    print(row)

OUT:
('Red Rocks', 'CO')
('Santa Barbara Bowl', 'CA')
('Greek Theater', 'CA')
('Madison Square Garden', 'NY')
```

Now we would like to calculate the number of concert venues in each state. This can be done by: