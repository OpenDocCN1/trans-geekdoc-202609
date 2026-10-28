# The script for the Guitar Shop database

Figure 17-15 presents a script that contains the DDL statements that are used to create a database for the Guitar Shop web application. As you learned in chapter 3, a script is a file that contains one or more SQL statements, and scripts are often used to create the tables and indexes for a database. When you code a script, you need to end each SQL statement with a semicolon.

This script starts with a DROP DATABASE statement that deletes the entire database named my_guitar_shop2 if that database exists. This deletes the structure and the data for the database. Then, the CREATE DATABASE statement creates the database named my_guitar_shop2. At this point, the database has no tables or data in it. Finally, the USE statement selects the newly created database named my_guitar_shop2. As a result, the rest of the statements in the script are executed against this database.

The CREATE TABLE statements in this script create the eight tables of the database. Of these tables, the first six are related, and the seventh is a standalone table that stores information about the administrative users of the web application. This shows that not all tables in a database need to be related. Some tables can be used to store unrelated data that’s needed by the web application.

Each CREATE TABLE statement begins with its primary key column (or columns) first, followed by its foreign key columns. Although this isn’t required, it’s a good programming practice. Since the order in which you declare the columns defines the default order for the columns, this script defines these columns in a logical order. That way, when you use a SELECT * statement to retrieve all of the columns, they’re returned in this order.

For most of the columns in these tables, this script includes a NOT NULL constraint or a DEFAULT attribute. In general, it’s a good practice to only allow a column to accept NULL values when you want to allow for unknown values. If, for example, a customer doesn’t supply the second line of an address, the second line of the address is unknown. In that case, you can store a NULL value in the line2 column.

Another option is to store an empty string for this column. To do that, you can define the address columns like this:

```
line2 VARCHAR(60) DEFAULT '' ,
```

In this case, empty strings are stored for this column unless other values are assigned to it.

In practice, a NULL value is a more intuitive representation of an unknown value than an empty string. In other words, an empty string typically indicates that the value is known and is empty. Although how you use NULL values and empty strings is largely a matter of personal preference, it does affect the way you query a table.

For the sake of consistency, this script codes all primary key constraints, unique constraints, and indexes at the end of the CREATE TABLE statement. In addition, this script follows a strict convention for naming these constraints where each constraint name is the same as the name of the column (or columns) of the constraint.