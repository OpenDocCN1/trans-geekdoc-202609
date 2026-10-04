# Chapter 2: The Structured Query Language for Creating and Altering Tables

```
author varchar(255) null,
author_host varchar(255) null,
primary key(topic_id),
index my_index(parent_id)
```

This statement creates a table “topics” with nine columns and two indexes, for the primary key and the parent_id column. In the above statement column types are used: integer, varchar, and timestamp. These and many other column types are discussed in further detail. You should have a good understanding of all the column types available as well as ways to create indexes before you set out create tables.

To create tables from the command line client, key in the entire command. For PHP, use the mysql_query() function.

```
$conn = mysql_connect("localhost","username","password") or
die("could not connect to localhost");

mysql_select_db("test", $conn) or
die("could not select database");
$query = "create table my_table (
col_1 int not null primary key,
col_2 text
);

mysql_query($query) or
die(mysql_error()));
```

# # Column Types

MySQL comes with a range of column types. Several are similar but have subtle yet important differences. Give this section a read and choose carefully when deciding on types for your tables.

# # Text column types

MySQL has seven column types suitable for storing text strings:

+   - char
- varchar
- tinytext
- text