
On many English-language keyboard layouts, the backtick key is the one to the immediate left of the numeric `1` key and below `Esc`. Its location may differ on non-English keyboards and/or on various devices such as laptops and tablets.

## Viewing Stored Data

The command that we use to view data stored in database tables is `SELECT`. You saw an example `SELECT` query generated for you by MySQL Workbench earlier. The `SELECT` query is the most complicated command in SQL. The reason for this complexity is that the chief strength of a database is its flexibility in data retrieval. At this early point in our experience with databases, we need only focus on fairly simple lists of results, so let’s consider the simpler forms of the `SELECT` command here.

This command will list everything that’s stored in the `joke` table:

```
SELECT * FROM `joke`
```

This command says “select everything from joke”, with the `*` meaning “all columns”. By default, a `SELECT` query will return every record in the table. If you try this command, your results will resemble the image below.

![MySQL Workbench results](Images/mysql-workbench-results.png)

Notice that there are some values in the `id` column, even though you didn’t specify them in the `INSERT` queries you ran earlier. MySQL has automatically assigned an ID to the joke. This is because you checked the “AI” (Auto Increment) checkbox when you created the table. If you hadn’t checked the box, you’d have needed to specify the ID for each joke you inserted.

If you were doing serious work on such a database, you might be tempted to stop and read all the hilarious jokes in the database at this point. To save yourself the distraction, you might want to tell MySQL to omit the `joketext` column. The command for doing this is as follows:

```
SELECT `id`, `jokedate` FROM joke
```

This time, instead of telling it to “select everything”, we told it precisely which columns we wanted to see. The result should look like the image below.

![You can select only what you need](Images/mysql-workbench-select-columns.png)

What if we’d like to see *some* of the joke text? As well as being able to name specific columns that we want the `SELECT` command to show us, we can use functions to modify each column’s display. One function, called `LEFT`, enables us to tell MySQL to display a column’s contents up to a specified number of characters. For example, let’s say we wanted to see only the first 20 characters of the `joketext` column. Here’s the command we’d use:

```
SELECT `id`, LEFT(`joketext`, 20), `jokedate` FROM `joke`
```

![The LEFT function trims the text to a specified length](Images/mysql-workbench-select-left.png)

See how that worked? Another useful function is `COUNT`, which lets us count the number of results returned. If, for example, you wanted to find out how many jokes were stored in your table, you could use the following command:

```
SELECT COUNT(`id`) FROM `joke`
```

As you can see in the image below, you have just two jokes in your table.

![The COUNT function counts the rows](Images/mysql-workbench-count.png)

### Using * Instead

You can use `COUNT(*)` for the same result, but this is slower, as all the columns will be selected from the table. By using the primary key, only one column needs to be retrieved.

So far, the examples we’ve looked at have fetched all the entries in the table. However, you can limit your results to only those database entries that have the specific attributes you want. You set these restrictions by adding what’s called a `WHERE` clause to the `SELECT` command. Consider this example:

```
SELECT COUNT(*) FROM `joke` WHERE `jokedate` >= "2021-01-01"
```

This query will count the number of jokes that have dates greater than or equal to January 1, 2021. In the case of dates, “greater than or equal to” means “on or after”. Another variation on this theme lets you search for entries that contain a certain piece of text. Check out this query:

```
SELECT `joketext` FROM `joke` WHERE `joketext` LIKE "%programmer%"
```

This query displays the full text of all jokes containing the text “programmer” in their `joketext` column. The `LIKE` keyword tells MySQL that the named column must match the given pattern. In this case, the pattern we’ve used is `"%programer%"`. The `%` signs (called **wildcards**) indicate that the text “programmer” may be preceded and/or followed by any string of text. (Interestingly, `LIKE` is case-insensitive, so this pattern will also match a joke that contains “Programmer”, or even “FuNkYProGRammeR”.)

Conditions may also be combined in the `WHERE` clause to further restrict results. For example, to display knock-knock jokes from April 2021 only, you could use the following query:

```
SELECT `joketext` FROM `joke` WHERE
`joketext` LIKE "%knock%" AND
`jokedate` >= "2021-04-01" AND
`jokedate` < "2021-05-01"
```

Enter a few more jokes into the table. (For example, “Why did the programmer quit his job? He didn’t get arrays.”) Then experiment with `SELECT` queries.

You can do a lot with the `SELECT` command, so I’d encourage you to become quite familiar with it. We’ll look at some of its more advanced features later, when we need them.

## Modifying Stored Data

Having entered data into a database table, you might find that you’d like to change it. Whether you’re correcting a spelling mistake, or changing the date attached to a joke, such alterations are made using the `UPDATE` command. This command contains elements of the `SELECT` and `INSERT` commands, since the command both picks out entries for modification and sets column values. The general form of the `UPDATE` command is as follows:

```
UPDATE `tableName` SET
  `colName` = newValue, …
WHERE conditions
```

So, for example, if we wanted to change the date on the joke we entered earlier, we’d use the following command:

```
UPDATE `joke` SET `jokedate` = "2021-04-01" WHERE id = "1"
```

Here’s where that `id` column comes in handy, enabling you to easily single out a joke for changes. The `WHERE` clause used here works just as it did in the `SELECT` command. This next command, for example, changes the date of all entries that contain the word “programmer”:

```
UPDATE `joke` SET `jokedate` = "2021-04-01"
WHERE `joketext` LIKE "%programmer%"
```

### WHERE is Optional

Believe it or not, the `WHERE` clause in the `UPDATE` command is optional. Consequently, you should be very careful when typing this command! If you leave the `WHERE` clause out, the `UPDATE` command will then apply to *all entries in the table*.

The following command will set the date for all the records in the table!

```
UPDATE `joke` SET `jokedate` = "2021-04-01"
```

## Deleting Stored Data

Deleting entries in SQL is dangerously easy, which you’ve probably noticed is a recurring theme. Here’s the command syntax:

```
DELETE FROM `tableName` WHERE conditions
```

To delete all programmer jokes from your table, you’d use the following query:

```
DELETE FROM `joke` WHERE `joketext` LIKE "%programmer%"
```

### Again, WHERE is Optional

As with `UPDATE`, the `WHERE` clause in the `DELETE` command is optional. Consequently, you should be very careful when using it. If you leave the `WHERE` clause out, the `DELETE` command will then apply to *all entries in the table*.

The following command will empty the joke table in one fell swoop:

```
DELETE FROM `joke`
```

Scary, huh?

## Let PHP Do the Typing

There’s a lot more to the MySQL database server software and SQL than the handful of basic commands I’ve presented here, but these commands are by far the most commonly used and most useful!

At this stage, you might be thinking that databases seem a little cumbersome. SQL can be tricky to type, as its commands tend to be long and verbose compared with those of other computer languages. You’re probably dreading the thought of typing in a complete library of jokes in the form of `INSERT` commands.
