What the above two tables show are three jokes and two authors. The AID column (short for "Author ID") of the Jokes table provides a relationship between the two tables (indicating that Kevin Yank submitted jokes 1 and 2 and Joan Smith submitted joke 3). Notice also that, since each author now only appears once in the database, and appears independently of the jokes he or she has submitted, we've avoided all the problems outlined above.

The most important characteristic of this database design, however, is that, since we're storing information about two types of "things" (jokes and authors), it's most appropriate to have two tables. This is a rule of thumb that you should always keep in mind when designing a database: each type of entity (or "thing") that you want to be able to store information about should be given its own table.

To set up the above database from scratch is fairly simple (involving just two CREATE DATABASE queries), but since we'd like to make these changes in a non-destructive manner (i.e. without losing any of our precious knock-knock jokes), we'll use the ALTER command again. First, we get rid of the author-related columns in the Jokes table:

```
mysql> ALTER TABLE Jokes DROP COLUMN AuthorName;
Query OK, 0 rows affected (0.00 sec)
Records: 0  Duplicates: 0  warnings: 0
```

```
mysql> ALTER TABLE Jokes DROP COLUMN AuthorEMail;
Query OK, 0 rows affected (0.00 sec)
Records: 0  Duplicates: 0  warnings: 0
```

Now we create our new table:

```
mysql> CREATE TABLE Authors (
-> ID INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
-> Name VARCHAR(100),
-> EMail VARCHAR(100)
-> );
```

Finally, we add the AID column to our Jokes table:

```
mysql> ALTER TABLE Jokes ADD COLUMN AID INT;
```

If you prefer, the CREATE TABLE commands that will create the two tables from scratch are provided in 2tables.sql in the code archive (located at http://www.sitepoint.com/books/).

All that's left is to add some authors to the new table, and assign authors to all the existing jokes in the database by filling in the AID column. Go ahead and do this now if you like. This should give you some practice with INSERT and UPDATE queries.