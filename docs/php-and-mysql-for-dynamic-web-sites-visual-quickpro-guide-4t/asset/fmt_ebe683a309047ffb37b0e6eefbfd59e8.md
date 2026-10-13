
![Image](graphics/circle-f.jpg)Populating the `messages` table requires knowing foreign key values from `users` and `forums`.

Because two of the fields in the `messages` table (`forum_id` and `user_id`) relate to values in other tables, you need to know those values before inserting new records into this table. For example, when the `troutster` user creates a new message in the `MySQL` forum, the `INSERT` will have a `forum_id` of 1 and a `user_id` of 1.

This is further complicated by the `parent_id` column, which should store the `message_id` to which the new message is a reply. The second message added to the database will have a `message_id` of 2, so replies to that message need a `parent_id` of 2.

With your PHP scripts—once you’ve created an interface for this database, this process will be much easier, but it’s important to comprehend the theory in SQL terms first.

For the `date_entered` field, the value returned by the `UTC_TIMESTAMP()` function will be used. Using the `UTC_TIMESTAMP()` function, the record will store the UTC date and time, not the date and time on the server.

**6.** Repeat Steps 1 through 3 to populate the database.

The rest of the examples in this chapter and the next will use the populated database. You’ll probably want to download the SQL commands from the book’s corresponding Web site, although you can populate the tables with your own examples and then just change the queries in the rest of the chapter accordingly.

**7.** View the most recent record in the messages table, using the stored date and time ![Image](graphics/circle-g.jpg):

```sql
SELECT message_id, subject, date_entered FROM messages
ORDER BY date_entered DESC LIMIT 1;
```

![Image](graphics/06_figure_26_g.jpg)

![Image](graphics/circle-g.jpg)The record that was just inserted, which reflects a time four hours ahead (the server is UTC-4).

As you can see in the figure and the table definition, UTC times are stored just the same as non-UTC times. What’s not obvious in the figure is that the record just inserted reflects a time four hours ahead of the server (because my particular server is in a time zone four hours behind UTC).

**8.** Retrieve the same record converting the `date_entered` to your time zone ![Image](graphics/circle-h.jpg):

```sql
SELECT message_id, subject,
CONVERT_TZ(date_entered, 'UTC', 'America/New_York') AS local
FROM messages ORDER BY date_entered DESC LIMIT 1;
```

![Image](graphics/06_figure_27_h.jpg)

![Image](graphics/circle-h.jpg)The UTC-stored date and time converted to my local time.

Using the `CONVERT_TZ()` function, you can convert any date and time to a different time zone. For the `from` time zone, use `UTC`. For the `to` time zone, use yours.

If you get a `NULL` result ![Image](graphics/graycircle-b.jpg), either the name of one of your time zones is wrong or MySQL hasn’t had its time zones loaded yet (see the sidebar).

***

Tip

However you decide to handle dates, the key is to be consistent. If you decide to use UTC, then *always* use UTC.

***

***

Tip

UTC is also known as Zulu time, represented by the letter *Z*.

***

***

Tip

Besides being time zone and daylight saving time agnostic, UTC is also more accurate. It factors in irregular leap seconds that compensate for the inexact movement of the planet.

***

### Foreign Key Constraints

A feature of the InnoDB table type, not supported in other storage engines, is the ability to apply *foreign key constraints*. When you have related tables, the foreign key in Table B relates to the primary key in Table A (for ease of understanding, it may help to think of Table B as the child to Table A’s parent). For example, in the `forums` database, the `messages.user_id` is tied to `users.user_id`. If the administrator were to delete a user account, the relationship between those tables would be broken (because the `messages` table would have records with a `user_id` value that doesn’t exist in `users`). Foreign key constraints set rules as to what should happen when a break would occur, including preventing that break.

The syntax for creating a foreign key constraint is:

```sql
FOREIGN KEY (item_name) REFERENCES table (column)
```

(This goes within a `CREATE TABLE` or `ALTER TABLE` statement.)

The item name is the foreign key column in the current table. The `table(column)` clause is a reference to the parent table column to which this foreign key should be constrained. If you just use the above, thereby only identifying the relationship, without stating what should happen when the constraint would be broken, MySQL will throw an error if you attempt to delete the parent record while child records exist ![Image](graphics/circle-a.jpg). MySQL will also throw an error if you attempt to create a child record using a parent ID that doesn’t exist ![Image](graphics/circle-b.jpg).

![Image](graphics/06_figure_28_a.jpg)

![Image](graphics/circle-a.jpg)This error indicates that MySQL is preventing a query from deleting a parent record because the record is constrained to one or more existing children records.

![Image](graphics/06_figure_29_b.jpg)

![Image](graphics/circle-b.jpg)Foreign key constraints also affect `INSERT` queries.

You can dictate what alternative actions should occur by following the above syntax with one or both of these:

```sql
ON DELETE action
ON UPDATE action
```

There are five action options, but two—`RESTRICT` and `NO ACTION`—are synonymous and also the default (i.e., the same as if you don’t specify the action at all). A third action option—`SET DEFAULT`—doesn’t work (don’t ask me, ask the MySQL manual!). That leaves `CASCADE` and `SET NULL`. If the action set is `SET NULL`, the removal of a parent record will result in setting the corresponding foreign keys in the child table to `NULL`. If that table defines that column as `NOT NULL` (which it almost always should), deletion of the parent record will trigger an error.

The `CASCADE` action is the most useful option. It tells the database to apply the same changes to the related table. With this instruction, if you delete the parent record, MySQL will also delete the child records with that parent ID as its foreign key.

As only the InnoDB table type supports foreign key constraints, both tables in the relationship must be of the InnoDB type. Also, in order for MySQL to be able to compare the foreign key-primary key values, the related columns must be of equitable types. This means that numeric columns must be the same type and size; text columns must use the same character set and collation.

With the `forums` example, it’s not possible to use foreign key constraints as the sole table related to another—`messages` relates to both `forums` and `users`—must use the MyISAM table type (to support `FULLTEXT` searches). Instead, let’s take a look at a new hypothetical example for banking ![Image](graphics/circle-c.jpg).

![Image](graphics/06_figure_30_c.jpg)

![Image](graphics/circle-c.jpg)The `banking` database could be used for virtual banking.
