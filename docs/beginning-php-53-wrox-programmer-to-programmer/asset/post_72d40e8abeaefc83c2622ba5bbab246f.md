
## Adding Data to a Table

Now try adding some fruit to your table. To add a new row to a table, you use the SQL INSERT statement. In its basic form, an INSERT statement looks like this:

```sql
INSERT INTO table VALUES ( value1, value2, ... );
```

This inserts values into each of the fields of the table, in the order that the fields were created. Alternatively, you can create a row with some fields populated. The remaining fields will contain NULL (if allowed), or in the case of special fields such as an AUTO_INCREMENT field, the field value will be calculated automatically. To insert a part of partial data:

```sql
INSERT INTO table ( field1, field2, ... ) VALUES ( value1, value2, ... );
```

So you can add three fruit to the table by inserting data into name and color fields (the id field will be filled automatically):

```sql
mysql> INSERT INTO fruit ( name, color ) VALUES ( 'banana', 'yellow' );
Query OK, 1 row affected (0.06 sec)
\mysql> INSERT INTO fruit ( name, color ) VALUES ( 'tangerine', 'orange' );
Query OK, 1 row affected (0.00 sec)
\mysql> INSERT INTO fruit ( name, color ) VALUES ( 'plum', 'purple' );
Query OK, 1 row affected (0.00 sec)
mysql>
```

## Reading Data from a Table

To read data in SQL, you create a query using the SELECT statement. Thanks to the flexibility of SQL, it's possible to run very complex queries on your data (for example, "Give me a list of all transactions over $500 from John Smith to Henry Hargreaves between 13 October and 17 November last year"). For now, you'll need to stick with simple examples.

To retrieve all of the data in your fruit table, you can use:

```sql
mysql> SELECT * from fruit;
+----+------+----------+
| id | name      | color  |
+----+------+----------+
| 1 | banana    | yellow |
| 2 | tangerine | orange |
| 3 | plum      | purple |
+----+------+----------+
3 rows in set (0.00 sec)
```

## Chapter 12: Introducing Databases and SQL

(The asterisk means "all fields.") You can also specify just the field or fields you want to retrieve:

```sql
mysql SELECT name, color from fruit;
+--------------------------+
| name      | color  |
+--------------------------+
| banana    | yellow |
| tangerine | orange |
| plum      | purple |
+--------------------------+
3 rows in set (0.00 sec)
```

To retrieve a selected row or rows, you will need to introduce a WHERE clause at the end of the SELECT statement. A WHERE clause filters the results according to the condition in the clause. You can use practically any expression in a WHERE condition. Here are some example WHERE clauses in action:

```sql
mysql SELECT * from fruit WHERE name = 'banana';
+----+----------+
| id | name   | color  |
+----+----------+
| 1  | banana | yellow |
+----+----------+
1 row in set (0.08 sec)
```

```sql
mysql SELECT * from fruit WHERE id >= 2;
+----+-----------+----------+
| id | name      | color  |
+----+-----------+----------+
| 2  | tangerine | orange |
| 3  | plum      | purple |
+----+-----------+----------+
2 rows in set (0.06 sec)
```

You may build more complex queries using SELECT and WHERE clauses in the next chapter.

## Updating Data in a Table

You change data in a table with the UPDATE statement. As with the SELECT statement, you (and usually) add a WHERE clause to specify exactly which rows you want to update. If you leave out the WHERE clause, the entire table gets updated.

Here's how to UPDATE to change values in your fruit table:

```sql
mysql UPDATE fruit set name = 'grapefruit', color = 'yellow' WHERE id = 2;
Query OK, 1 row affected (0.29 sec)
Rows matched: 1 Changed: 1 Warnings: 0
```

```sql
mysql SELECT * from fruit;
+--------------------------+
| id | name      | color  |
+--------------------------+
| 1  | banana    | yellow |
| 2  | grapefruit| yellow |
| 3  | plum      | purple |
+--------------------------+
3 rows in set (0.00 sec)
```

## Deleting Data from a Table

Deleting works in a similar way to updating. To delete rows, you use the DELETE statement. If you add a WHERE clause, you can choose which rows to delete; otherwise all the data in the table are deleted (though the table itself remains). Here's an example:

```sql
mysql> DELETE FROM fruit WHERE id = 2;
Query OK, 1 row affected (0.02 sec)

mysql> SELECT * from fruit;
+----------------------+
| id | name   | color |
+----------------------+
| 1  | banana | yellow|
| 3  | plum   | purple|
+----------------------+
2 rows in set (0.00 sec)
```

## Deleting Tables and Databases

To delete a table entirely, use the DROP TABLE statement. Similarly, you can delete an entire database with DROP DATABASE.

First, here's how to use DROP TABLE:

```sql
mysql> SHOW TABLES;
+----------------------+
| Tables_in_database |
+----------------------+
| fruit                
+----------------------+
```

```sql
mysql> DROP TABLE fruit;
Query OK, 0 rows affected (0.01 sec)
```

```sql
mysql> SHOW TABLES;
+----------------------+
| Tables_in_database |
+----------------------+
Empty set (0 sec)
```

```sql
mysql> DROP DATABASE database_name;
Query OK, 0 rows affected (0.01 sec)
```
