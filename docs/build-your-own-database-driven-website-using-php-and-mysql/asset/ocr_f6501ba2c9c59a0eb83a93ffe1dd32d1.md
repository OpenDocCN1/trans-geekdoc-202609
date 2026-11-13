```
| 1 | why did the chicken cross the road? To get to the
other side! | 2000-04-01 |
+-----+...
1 row in set (0.05 sec)
```

It looks a little messed up, because the text in the JokeText column is too long for the table to fit properly on the screen. For this reason, you might want to tell MySQL to leave out the JokeText column. The command for doing this is as follows:

```
mysql> SELECT ID, JokeDate FROM Jokes;
```

This time instead of telling it to "select everything", we told it precisely which columns we wanted to see. The results look like this:

```
+----+------------+
| ID | JokeDate   |
+----+------------+
| 1  | 2000-04-01 |
+----+------------+
1 row in set (0.00 sec)
```

Not bad, but we'd like to see at least some of the joke text, wouldn't we? In addition to listing the columns that we want the SELECT command to show us, we can modify those columns with functions. One function, called LEFT, lets us tell MySQL to display up to a specified maximum number of characters when it displays a column. For example, let's say we wanted to see only the first 20 characters of the JokeText column:

```
mysql> SELECT ID, LEFT(JokeText,20), JokeDate FROM Jokes;
```

```
+----+-------------------------+------------+
| ID | LEFT(JokeText,20)       | JokeDate   |
+----+-------------------------+------------+
| 1  | why did the chicken     | 2000-04-01 |
+----+-------------------------+------------+
1 row in set (0.05 sec)
```

See how that worked? Another useful function is COUNT, which simply lets us count the number of results returned. So, for example, if we wanted to find out how many jokes were stored in our table, we could use the following command:

```
mysql> SELECT COUNT(*) FROM Jokes;
```

```
+----------+
| COUNT(*) |
+----------+
| 1        |
+----------+
1 row in set (0.06 sec)
```

As we can see, we only have one joke in our table.