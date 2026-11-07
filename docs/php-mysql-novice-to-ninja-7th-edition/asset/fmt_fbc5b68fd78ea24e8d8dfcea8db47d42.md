
# Database Schema Updates and Joins

## Removing Columns with ALTER TABLE

This is a DDL `ALTER TABLE` query for removing columns. As with all of these DDL queries, you could have typed this into the query panel manually and executed it, but we’ve used the GUI to avoid having to remember all the different commands.

## Creating Author Table

Now, we need to create a new table to store the authors. To do this, follow the same procedure you used to create the `joke` table: right-click on the Tables entry in the `SCHEMAS` panel and select `Create Table`.

Set the table name to `author` and add the following fields:
* `id`, and check the `PK`, `AI` and `NN` boxes
* `name`, `VARCHAR(255)`
* `email`, `VARCHAR(255)`

Click `Apply`, and MySQL Workbench will generate a `CREATE TABLE` query similar to this:

```
CREATE TABLE `author` (
  `id` INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
  `name` VARCHAR(255),
  `email` VARCHAR(255)
) DEFAULT CHARACTER SET utf8 ENGINE=InnoDB
```

Finally, we add the `authorid` column to our `joke` table. Edit the `joke` table and add a column called `authorid` with the type `INT`.

If you prefer, here are the `CREATE TABLE` commands that will create the two tables from scratch:

```
# Code to create a simple joke table that stores an author ID

CREATE TABLE `joke` (
  `id` INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
  `joketext` TEXT,
  `jokedate` DATE NOT NULL,
  `authorid` INT
) DEFAULT CHARACTER SET utf8 ENGINE=InnoDB;

# Code to create a simple author table

CREATE TABLE `author` (
  `id` INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
  `name` VARCHAR(255),
  `email` VARCHAR(255)
) DEFAULT CHARACTER SET utf8 ENGINE=InnoDB;
```

All that’s left to do is add some authors to the new table, and assign authors to all the existing jokes in the database by filling in the `authorid` column. (For now, you’ll have to do this manually, but rest assured that, in Chapter 8, we’ll see how PHP can insert entries with the correct IDs automatically, reflecting the relationships between them.) Go ahead and do this now if you like, as it will give you some practice with `INSERT` and `UPDATE` queries. If you’re rebuilding the database from scratch, however, here’s a series of `INSERT` queries that will do the trick:

```
# Adding authors to the database
# We specify the IDs so they're known when we add the jokes below.

INSERT INTO `author` SET
  `id` = 1,
  `name` = 'Kevin Yank',
  `email` = 'thatguy@kevinyank.com';

INSERT INTO `author` (`id`, `name`, `email`)
VALUES (2, 'Tom Butler', 'tom@r.je');

# Adding jokes to the database

INSERT INTO `joke` SET
  `joketext` = 'How many programmers does it take to screw in a lightbulb? None, it\'s a hardware problem.',
  `jokedate` = '2021-04-01',
  `authorid` = 1;

INSERT INTO `joke` (`joketext`, `jokedate`, `authorid`)
VALUES (
  'Why did the programmer quit his job? He didn\'t get arrays',
  '2021-04-01',
  1
);

INSERT INTO `joke` (`joketext`, `jokedate`, `authorid`)
VALUES (
  'Why was the empty array stuck outside? It didn\'t have any keys',
  '2021-04-01',
  2
);
```

### Both Kinds of `INSERT`

I’ve used this opportunity to refresh your memory about both kinds of `INSERT` query syntax. They both do exactly the same job and have the same result, so it’s up to you which you use, and boils down mainly to personal preference rather than any practical reason.

## `SELECT` with Multiple Tables

With your data now separated into two tables, it may seem that you’re complicating the process of data retrieval. Consider, for example, our original goal: to display a list of jokes with the name and email address of the author next to each joke. In the single-table solution, you could gain all the information needed to produce such a list using a single `SELECT` query in your PHP code:

```
try {
  $pdo = new PDO('mysql:host=mysql;dbname=ijdb;charset=utf8mb4', 'ijdbuser', 'mypassword');
  $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

  $sql = 'SELECT `id`, `joketext` FROM `joke`';

  $jokes = $pdo->query($sql);

  $title = 'Joke list';

  ob_start();

  include  __DIR__ . '/../templates/jokes.html.php';

  $output = ob_get_clean();
}
catch (PDOException $e) {
  $title = 'An error has occurred';

  $output = 'Database error: ' . $e->getMessage() . ' in ' .
  $e->getFile() . ':' . $e->getLine();
}

include  __DIR__ . '/../templates/layout.html.php';
```

With our new database layout, this would, at first, no longer seem possible. As the author details of each joke are no longer stored in the `joke` table, you might think that you’d have to fetch those details separately for each joke you wanted to display. The code required would involve a call to the `PDO` `query` method for each and every joke to be displayed. This would be messy and involve a considerable amount of extra code.

Taking all this into account, it would seem that the “old way” was the better solution, despite its weaknesses. Fortunately, relational databases like MySQL are designed to make it easy to work with data stored in multiple tables! Using a new form of the `SELECT` statement, called a `join`, you can have the best of both worlds. Joins allow you to treat related data in multiple tables as if they were stored in a single table. Here’s what the syntax of a simple join looks like:

```
SELECT columns
FROM `table1`
INNER JOIN `table2`
  ON condition(s) for data to be related
```

In your case, the columns we’re interested in are `id` and `joketext` in the `joke` table, and `name` and `email` in the `author` table. The condition for an entry in the `joke` table to be related to an entry in the `author` table is that the value of the `authorid` column in the `joke` table is equal to the value of the `id` column in the `author` table.

Let’s look at an example of a join. The first two queries show you what’s contained in the two tables; they’re unnecessary to perform the join. The third query is where the action’s at:

```
SELECT `id`, LEFT(`joketext`, 20), `authorid` FROM `joke`
```

This query should now give the results shown below.

![Results of the joke table query](Images/joke-authorid.png)

```
SELECT * FROM `author`
```

And this query, as you’d expect, will show all the authors.

![All of the authors from the authors table](Images/authors.png)

It’s possible to query data from both tables by using the SQL `JOIN` statement:

```
SELECT `joke`.`id`, LEFT(`joketext`, 20), `name`, `email`
FROM `joke` INNER JOIN `author`
  ON `authorid` = `author`.`id`
```

This will display all the data from both tables.

![The results of your first join](Images/my-first-join.png)

See? The results of the third `SELECT`—a `join`—group the values stored in the two tables into a single table of results, with related data correctly appearing together. Even though the data is stored in two tables, you can still access all the information you need to produce the joke list on your web page with a single database query. Note in the query that, since there are columns named `id` in both tables, you must specify the name of the table when you refer to either `id` column. The joke table’s ID is referred to as `joke.id`, while the author table’s ID column is `author.id`. If the table name is unspecified, MySQL won’t know which `id` you’re referring to, and will produce the following error:

```
Error Code: 1052. Column 'id' in field list is ambiguous
```

Now that you know how to access the data stored in your two tables efficiently, you can rewrite the code for your joke list to take advantage of joins:
