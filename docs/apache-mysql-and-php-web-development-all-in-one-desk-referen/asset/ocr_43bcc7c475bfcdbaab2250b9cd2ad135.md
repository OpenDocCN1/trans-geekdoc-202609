through every row in the table, checking whether the row satisfies your match. For enormous tables, this linear search (linear because the search goes one by one through the rows) can be extremely time consuming.

You will often design better tables if you use a primary key rather than a unique key. A primary key forces you to put data for the keyed column in every row.

In order for MySQL to look up data in two tables at once by relating the data, you must use primary keys. For example, if you have a CustomerID column in your order table and you want MySQL to use that to find information from a Customer table that also contains a CustomerID column, then the CustomerID column in the Customer table must be a primary key.

# Coding the keys

Here are three create table statements, each specifying a different type of key. First, here's a simple key:

```
```
create table key1 (
 num integer,
 name varchar(30),
 key(num)
);
```
```

Notice that you specify the key after you specify the columns. You do so by using the word key, followed by the name of the column in parentheses.

Here's a unique key:

```
```
create table key2 (
 num integer,
 name varchar(30),
 unique key(num)
);
```
```

This is the same as the simple key example, except that you add the word unique prior to the word key.

And now here's a primary key:

```
```
create table key3 (
 num integer NOT NULL,
 name varchar(30),
 primary key(num)
);
```
```