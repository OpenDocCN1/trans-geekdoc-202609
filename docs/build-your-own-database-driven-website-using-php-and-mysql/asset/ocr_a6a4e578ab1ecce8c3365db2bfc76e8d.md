```
mysql> INSERT INTO table_name SET
    ->    columnName1 = value1,
    ->    columnName2 = value2,
    ->    ...
    ->    ;
mysql> INSERT INTO table_name
    ->    (columnName1, columnName2, ...)
    ->    VALUES (value1, value2, ...);
```

So, to add a joke to our table, we can choose from either of these commands:

```
mysql> INSERT INTO Jokes SET
    ->    JokeText = "why did the chicken cross the road? To get to the other side!",
    ->    JokeDate = "2000-04-01";
```

```
mysql> INSERT INTO Jokes
    ->    (JokeText, JokeDate) VALUES (
    ->    "why did the chicken cross the road? To get to the other side!",
    ->    "2000-04-01"
    ->    );
```

Note that in the second form of the INSERT command, the order in which you list the columns must match the order in which you list the values.
Otherwise, the order of the columns doesn't matter, as long as you give values
for all required fields.

Now that you know how to add entries to a table, let's see how we can view
those entries.

# Viewing Stored Data

The command we use to view data stored in your database tables, SELECT, is
the most complicated command in the SQL language. The reason for this
complexity is that the chief strength of a database is its flexibility in data
retrieval and presentation. As, at this point in our experience with databases,
we only need fairly simple lists of results, we'll consider only the simpler
forms of the SELECT command.

This command will list everything stored in the Jokes table:

```
mysql> SELECT * FROM Jokes;
```

Read aloud, this command says "select everything from Jokes". If you try
this command, your results will resemble this:

```
+----+----------+------------+
| ID | JokeText | JokeDate   |
+----+----------+------------+
+----+----------+------------+
```