# Chapter 10 Working with Your MySQL Database

There's an ANSI standard for SQL, and database systems such as MySQL generally strive to implement this standard. There are some subtle differences between standard SQL and MySQL's SQL. Some of these differences are planned to become standard in future versions of MySQL, and some are deliberate. We point out the more important ones as we go. A complete list of the differences between MySQL's SQL and ANSI SQL in any given version can be found in the MySQL online manual. You can find this page at this URL and in many other locations:

http://dev.mysql.com/doc/refman/5/en/compatibility.html.

You might have heard the Data Definition Language (DDL), used for defining databases, and Data Manipulation Language (DML), used for querying databases. SQL covers both of these. In Chapter 9, we looked at data definition (DDL) in SQL, so we've already been using it a little. You use DDL when you're initially setting up a database.

You will use DML aspects of SQL far more frequently because these are the parts that you will use to store and retrieve data in a database.

#  Inserting Data into the Database

Before you can do with a lot of data, you need to store some data in. The way you most commonly this is to use the INSERT statement.

Recall that RDBMS contains tables, which in turn contain rows of data organized into columns. Each row in a table normally describes some real-world object or relationship, and the column values for that row store information about the real-world object. You can use the INSERT statement to put data into the database.

The most common form of an INSERT statement is

```
INSERT [INTO] table [column1, column2, column3...] VALUES
(value1, value2, value3...)
```

For example, to insert a record into Book-O-Rama's Customers table, you can type

```
INSERT INTO Customers VALUES
(NULL, 'Julie Smith', '25 Oak Street', 'Airport West');
```

You can see that we use the actual table where we want to put the data and the values with specific values. The values in this example are all enclosed in quotation marks. Strings should always be enclosed in pairs of single or double quotation marks in MySQL (We use both in this book). Numbers and dates do not need quotes.

There are few interesting things to think about the INSERT statement. The values specified will be used to fill in the table columns of order. If you want to fill in some of the columns, or if you want to specify them in a different order, you can list the specific columns in the columns of the statement. For example,

```
INSERT INTO Customers (name, city) VALUES
('Melissa Jones', 'Nar Nar Goon North');
```