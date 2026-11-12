After you run this command, you see the happy, friendly (albeit nearly meaningless) message:

```
Query OK, 0 rows affected (0.01 sec)
```

This message means that you successfully created the table.

# ## Adding rows to a table

If you have a table, you probably don't want to leave it sitting around bored doing nothing. Instead, you want to put some data in it. (Hey, you made the thing — you may as well use it.) In Book VI, Chapter 3, I talk about the types of data you can put in your tables and how you can relate your tables to one another. For now, I stick with the table called candy that I created in the preceding section, “Creating a table.”

The candy table holds rows that each consist of a name in the form of a string, a weight in the form of a double-precision floating-point variable, and a price and quantity, both as integers. Here’s how you add a row of data to this table from the mysql utility (make sure you’re using the phpbase database):

```
insert into candy values(
 'OozingPeanutbutterExplosion',
 6.95,
 275,
 100,
 );
```

This code adds a new row to the candy table consisting of the name ‘OozingPeanutbutterExplosion’ (yum), the weight 6.95 (I suppose that’s ounces, which is still a lot), the price $2.75 shown as 275 cents, and the quantity 100, representing the number that will soon to be in my stomach.

This code added only one row, or record. You can add more rows by using different names and values. And you don’t need to break up the line into multiple lines if you don’t want to:

```
insert into candy values('ChunkableCrunchableChocolate', 2.80, 75, 50);
```

# ## Viewing the data in a table

If you have a table (such as one called candy) that has data in it, you can use the mysql command-line utility to look at the data in the table. To do so, you use the select statement. (The word select is a part of the SQL language that I talk about in Book VI, Chapter 5.)