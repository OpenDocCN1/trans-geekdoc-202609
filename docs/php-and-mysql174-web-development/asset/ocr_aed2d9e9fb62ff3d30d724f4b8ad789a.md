# # Updating Records in the Database

In addition to retrieving data from the database, you often want to change it. For example, you might want to increase the prices of the books in the database. You can do this using an UPDATE statement.

The usual form of an UPDATE statement is

```
UPDATE [LOW_PRIORITY] [IGNORE] tab
SET column1=expression1,column2=expression2,...
WHERE condition
ORDER BY order_criteria
[LIMIT number]
```

The basic idea is to update the table called tableName, setting each of the columns named to the appropriate expression. You can limit an UPDATE to particular rows with a WHERE clause and limit the total number of rows to affect with a LIMIT clause. ORDER BY is used only in conjunction with a LIMIT clause; for example, if you are going to update only the first 10 rows, you can put them in kind of order first. LOW_PRIORITY and IGNORE, if specified, work the same way they do in an INSERT statement.

Let's look at some examples. If you want to increase the price of books by 10%, you can use an UPDATE statement without a WHERE clause:

```
UPDATE Books
SET Price = Price * 1.1;
```

If, on the other hand, you want to change a single row—say, to update a customer's address—you can do it like this:

```
UPDATE Customers
SET Address = '25 Olsens Road'
WHERE CustomerID = 4;
```

# # Altering Tables After Creation

In addition to updating rows, you might want to alter the structure of the tables within your database. The basic form of this purpose is to use the ALTER TABLE statement.

```
ALTER TABLE [IGNORE] tableName alteration [, alteration ...]
```

Note that in ANSI SQL you can make only one alteration per ALTER TABLE statement, but MySQL allows you to make as many as you like. Each of the alterations used can be to change different aspects of the table.

If the IGNORE clause is specified and you are trying to make an alteration that causes duplicate primary keys, the first one will go into the altered table and the rest will be deleted. If it is not specified (the default), the alteration will fail and be rolled back.