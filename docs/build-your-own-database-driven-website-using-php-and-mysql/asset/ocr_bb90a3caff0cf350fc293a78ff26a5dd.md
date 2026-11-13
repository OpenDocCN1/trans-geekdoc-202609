MySQL will tell you there was a problem with the query you typed, and will try to give you some indication of where it had trouble understanding what you meant.

For such a complicated command, Query OK is pretty a pretty boring response. Let's have a look at your new table to make sure it was created properly. Type the following command:

```
mysql> SHOW TABLES;
```

The response should look like this:

| Tables in jokes |
|---|
| Jokes           |

1 row in set

This is a list of all the tables in our database (which I named jokes above). The list contains only one table: the Jokes table we just created. So far everything looks good. Let's have a closer look at the Jokes table itself:

```
mysql> DESCRIBE Jokes;
```

| Field   | Type      | Null | Key | Default | Extra          |
|---------|-----------|------|-----|---------|----------------|
| ID      | int(11)   |      | PRI | 0       | auto_inc       |
| JokeText| text      | YES  |     | NULL    |                |
| JokeDate| date      |      |     | 0000-00-00|                |

3 rows in set

This provides a list of the columns (or fields) in the table. As we can see, there are three columns in this table, which appear as the 3 rows in this table of results. The details are somewhat cryptic, but if you look at them closely for a while you should be able to figure out what most of them mean. Don't worry about it too much, though. We've got better things to do, like adding some jokes to our table!

We need to look at just one more thing before we get to that, though: deleting a table. This is just as frighteningly easy to do as it is to delete a database. In fact, the command is almost identical:

```
mysql> DROP TABLE tableName;
```

# Inserting Data into a Table

Our database is created and our table is built; all that's left is to put some actual jokes into our database. The command for inserting data into our database is called (appropriately enough) INSERT. There are two basic forms of this command: