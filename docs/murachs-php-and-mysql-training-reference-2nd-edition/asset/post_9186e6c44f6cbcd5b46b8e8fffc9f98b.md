
## How to alter a table

After you create a table, you may need to modify the table. To do that, you can use the ALTER TABLE statement as shown in figure 17-5.

To start, the first example in this figure shows how to rename an existing table. Here, the statement changes the name of the products table to product. This is useful if you want to change the name of a table without modifying its column definitions or the data that’s stored in the table.

The second example shows how to add a new column to a table at the end of the list of columns. To do that, you code the column definition the same way you do when you create a new table. To start, you specify the column name. Then, you code the data type and its attributes. In this example, the statement adds a column of the DATE type named lastTransactionDate.

The third example shows how to add a new column after a specified column. To do that, you can include an optional AFTER clause that specifies where to add the column. In this example, the statement adds the new column after the column named emailAddress.

The fourth example shows how to drop an existing column. This example drops the column named lastTransactionDate that was created by the code in the second example.

The fifth example shows how to rename an existing column. In this case, the code changes the name of the column from emailAddress to email. Note that you must include the data type and all of the attributes for the column when you rename it.

The sixth example shows how to change the definition of an existing column by modifying the length of the data type for that column. In this case, a column that was defined as VARCHAR(60) is changed to VARCHAR(100). Since the new data type is bigger than the old data type, you can be sure that the existing data will still fit.

The seventh example shows how to change the data type to a different data type. In this case, a column that was defined as VARCHAR(100) is changed to CHAR(100). Since these data types both store the same type of characters, you can be sure that no data will be lost.

The eighth example shows how to change the data type to a different data type that may result in lost data. If, for example, the firstName column contains one or more values that has more than 8 characters, this may result in lost data. On most systems, MySQL will truncate this data. As a result, a name of “Alexandra” will be truncated to “Alexandr”.

The ninth example shows how to change the default value for a column. Here, the statement assigns a default value of an empty string to the firstName column. However, since the firstName column is of the VARCHAR type, you could assign any string literal or a NULL value as the default value.

The tenth example shows how to drop the default value from a column. In this example, the statement drops the default value that was set in the previous example.

**A statement that renames a table**

```sql
ALTER TABLE products RENAME TO product;
```

**A statement that adds a new column at the end of the table**

```sql
ALTER TABLE customers ADD lastTransactionDate DATE;
```

**A statement that adds a new column after a specified column**

```sql
ALTER TABLE customers ADD lastTransactionDate DATE
AFTER emailAddress;
```

**A statement that drops a column**

```sql
ALTER TABLE customers DROP lastTransactionDate;
```

**A statement that renames a column**

```sql
ALTER TABLE customers
CHANGE emailAddress email VARCHAR(255) NOT NULL UNIQUE;
```

**A statement that changes the definition of a column**

```sql
ALTER TABLE customers MODIFY firstName VARCHAR(100) NOT NULL;
```

**A statement that changes the data type of a column**

```sql
ALTER TABLE customers MODIFY firstName CHAR(100) NOT NULL;
```

**A statement that may cause data to be lost**

```sql
ALTER TABLE customers MODIFY firstName VARCHAR(8);
```

**A statement that sets the default value of a column**

```sql
ALTER TABLE customers ALTER firstName SET DEFAULT '';
```

**A statement that drops the default value of a column**

```sql
ALTER TABLE customers ALTER firstName DROP DEFAULT;
```

**Description**

- You can use the ALTER TABLE statement to modify the columns of an existing table.

**Warning**

- You should never alter a table or other database object in a production database without first consulting the DBA, but you probably won’t have the privileges for doing that.

Figure 17-5  How to alter a table

## How to drop a table

Figure 17-6 shows how to use the DROP TABLE statement. When you use this statement, use it cautiously, especially when you’re working on a production database.

You can use the DROP TABLE statement to delete the definition of a table. In addition, the DROP TABLE statement deletes all data that’s stored in the table. In this figure, for instance, the first example drops the customers table. However, if the customers table doesn’t exist, this generates an error that stops a SQL script from continuing. To prevent this error, you can add the IF EXISTS keywords to the DROP TABLE statement as shown in the second statement.

If you have configured MySQL to enforce referential integrity for your database, MySQL checks whether other tables depend on the table you’re trying to drop. If so, MySQL won’t allow you to drop the table. For example, you can’t delete the customers table if a foreign key in the orders table refers to the customers table. In that case, you must drop the orders table before you can drop the customers table.

When you drop a table, MySQL also drops any indexes that have been defined for that table. In the next figure, you’ll learn how to work with the indexes of a table.

**A statement that drops a table**

```sql
DROP TABLE customers;
```

**A statement that drops a table if it exists**

```sql
DROP TABLE IF EXISTS customers;
```

**Description**

- You can use the DROP TABLE statement to delete a table.
- If you drop a table, MySQL deletes its definition (including its indexes) and its data.

**Warning**

- You should never drop a table in a production database without first consulting the DBA, but you probably won’t have the privileges for doing that.

## How to work with indexes

An index speeds joins and searches by providing a way for a database management system to go directly to a row rather than having to search through all the rows until it finds the one you want. By default, MySQL creates indexes for the primary keys and unique constraints of a table, which is usually what you want. In addition, you may want to create indexes for foreign keys and other columns that are used frequently in search conditions or joins. However, you’ll want to avoid creating indexes on columns that are updated frequently since this slows insert, update, and delete operations.

### How to create an index

Figure 17-7 presents the basic syntax of the CREATE INDEX statement, which creates an index based on one or more columns of a table. This syntax omits some of the optional clauses that you can use for tuning the indexes for better performance. This tuning is typically done by DBAs working with large databases, but usually isn’t necessary for smaller databases.

To create an index, you use the ON clause to specify the name of the table and the column or columns for the index. In this figure, the first two examples create an index based on a single column, and the third example creates an index based on two columns. For each column, you can use the UNIQUE keyword to specify that an index contains only unique values. In addition, you can specify the ASC or DESC keyword to indicate whether you want the index sorted in ascending or descending sequence.

In these examples, the index names follow a standard naming convention. Here, the index name is the same as the name of the column or columns for the index. For instance, the first example creates an index named customerID for the customerID column of the customers table, and the third example creates an index named customerIDOrderNumber for the customerID and orderNumber columns of the orders table.

Although you can use the CREATE INDEX statement to add indexes to an existing table, you can use the CREATE TABLE statement to create indexes for a new table. In this figure, the fifth example creates a customers table that has the same indexes that were created by the first two examples. Note that the syntax is slightly different, but you still need to specify the name of the index before the parentheses, and you need to specify the column or columns for the index within the parentheses.

### How to drop an index

The sixth example shows how to use the DROP INDEX statement to drop an index. You may want to drop an index if you suspect that it isn’t speeding up your joins and searches and that it may be slowing down your insert, update, and delete operations.
