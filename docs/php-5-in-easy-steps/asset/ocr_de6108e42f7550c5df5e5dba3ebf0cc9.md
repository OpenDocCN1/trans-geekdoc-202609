# Altering an existing table

The definition of a column in an existing table can be altered using the SQL commands “alter table” and “modify”, with the following syntax:

alter table table-name modify field-name modifiers;

New columns can be added to an existing table using the same “alter table” command, but now with the SQL “add” keyword. The syntax to add an extra column looks like this:

alter table table-name add field-name modifiers;

The example shown in the MySQL monitor below uses the “alter table” command to add a new extra column called “top_mph” to the cars table from the previous page. Data can now be entered into the new column using the SQL “update” command, which is demonstrated on the next page.

![](bbox=[0.273, 0.452, 0.923, 0.933])

The new top_mph column does not have “not null” modifier, so it is to enter data here.

```
mysql> use garage;
Database changed
mysql> select * from cars;
+------+-----------+----------+
| id | make      | model    |
+------+-----------+----------+
| 1 | Porsche    | Carrera |
| 2 | Ferrari    | Dino     |
| 3 | Lamborghini| Diablo  |
+------+-----------+----------+
3 rows in set (0.00 sec)
mysql> alter table cars add top_mph int;
Query OK, 3 rows affected (0,02 sec)
Records: 3 Duplicates: 0 Warnings: 0
mysql> select * from cars;
+------+-----------+----------+----------+
| id | make      | model    | top_mph |
+------+-----------+----------+----------+
| 1 | Porsche    | Carrera | NULL |
| 2 | Ferrari    | Dino     | NULL |
| 3 | Lamborghini| Diablo  | NULL |
+------+-----------+----------+----------+
3 rows in set (0.00 sec)
mysql> 
```