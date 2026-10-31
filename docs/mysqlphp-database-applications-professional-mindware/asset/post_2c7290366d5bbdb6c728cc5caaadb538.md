
This statement would work fine for Jay, but there’s going to be a problem for Brad because he’s not married and his spouse_id field is null. He will not show up in the result set even though the goal of the query is to get all the people in the contacts table and the associated spouses if they exist.

Again, this is just a preview, an example of why null is so important. In Chapter 3 you will see how the outer join solves problems like this.

## Index

Arguably the single greatest advantage of a relational database is the speed with which it can query and sort tremendous amounts of information. To achieve these great speeds, MySQL and all other database servers make use of optimized data-storage mechanisms called indexes.

An index allows a database server to create a representation of a column that it can search with amazing speeds. Indexes are especially helpful in finding a single row or groups of rows from a large table. They can also speed up joins and aggregate functions, like min() and max(), which we’ll cover in Chapter 3.

Given these advantages, why not just create an index for every column for every table? There are some very good reasons. First, indexes can actually slow some things down. It takes time for your database server to maintain indexes. You wouldn’t want to create overhead for your server that is not going to be a benefit to you down the road. There are also occasions when the indexes themselves are slower. If you need to iterate through every row in a table, you’re actually better off not using an index. Also, unnecessary indexes will use a lot of disk space.

A table’s primary key is often the subject of searches (for obvious reasons). Thus, in a table definition, the column or columns that you declare as your primary key will automatically be indexed.

There will be more on creating indexes later in this chapter.

## create database Statement

Before you can get to creating your tables, you’ll need to create a database. This should take all of a second. The basic Create syntax is fairly simple and can be run from any interface that has access to MySQL.

The general syntax is:

```
create database database_name
```

![](img/de0823012275cf4ceebdb822a56e6b71_58_0.png)

In case you’re wondering, after running this command MySQL creates a folder in which it stores all the files needed for your database. On my Linux machine, the database folders are stored in /var/lib/mysql/.

When naming databases, or for that matter columns or indexes, avoid using names that will cause confusion down the road. On operating systems where the file names are case sensitive, such as most Unix systems, database names will also be case sensitive. Come up with conventions that you plan on sticking to, such as using all lowercase names for tables and columns. Spaces are not allowed. Though MySQL can work around potentially bad choices, you should avoid using words that MySQL uses in the course of its business. For instance, naming a table “Select” is a really bad idea. In Chapter 7 of the MySQL reference manual, there is a list of over 150 reserved words. If you stay away from words used by SQL or MySQL functions you should be OK.

From the MySQL command line client, you can simply type in:

```
create database database_name;
```

![](img/de0823012275cf4ceebdb822a56e6b71_59_0.png)

The MySQL command-line client is in the /bin directory of your MySQL installation and has the file name mysql (on Unix) or mysql.exe on DOS/Windows.

From PHP, you can use either the mysql_create_db() or the mysql_query() function. The following piece of code would create two databases. Keep in mind that you will need to be logged into MySQL as a user with the proper rights for the code to work.

```
$conn = mysql_connect("localhost","username", "password")
    or die ("Could not connect to localhost");

mysql_create_db("my_database") or
    die ("Could not create database");
$string = "create database my_other_db";
mysql_query($string) or
    die(mysql_error());
```

## use database Statement

Before you can begin making tables in MySQL you must select a database that has been created. If you are accessing MySQL through the mysql command-line client, you will have to enter the statement:

```
use database_name
```

If you're accessing a database through PHP, use the mysql_select_db() function.

```
$conn = mysql_connect("localhost","username", "password")
    or die ("Could not connect to localhost");

mysql_select_db("test", $conn) or
    die ("Could not select database");
```

## create table Statement

Once you have created and selected a database, you are ready to create a table. The basic Create Table syntax is fairly simple and takes this basic form.

```
create table table_name
(
    column_1 column_type column attributes,
    column_2 column_type column attributes,
    primary key (column_name),
    index index_name(column_name)
)
```

Column types, column attributes, and details on indexes are covered in the following sections. Before we get to those, there are two simple column attributes to discuss:

- null | not null
- default

The first gives you the opportunity to forbid or allow null values. If you don't specify "null" or "not null" it is assumed that null values are allowed. The second, if declared, sets a value if none is declared when you insert a row into the table.

Here's an example create statement where you can see these two attributes, and a few others, put to use. This one was lifted from Chapter 12 and changed slightly.

```
create table topics2 (
    topic_id      integer not null auto_increment,
    parent_id     integer default 0 not null,
    root_id       integer default 0,
    name          varchar(255),
    description   text null,
    create_dt     timestamp,
    modify_dt     timestamp,
    author        varchar(255) null,
    author_host   varchar(255) null,
    primary key(topic_id),
    index my_index(parent_id)
)
```

This statement creates a table named “topics” with nine columns and two indexes, one for the primary key and one for the parent_id column. In the above statement four column types are used: integer, varchar, text, and timestamp. These, and many other column types are discussed in further detail below. You should have a good understanding of all the column types available as well as ways to create indexes before you set out to create tables.

To create tables from the command line client, key in the entire command. From PHP, use the mysql_query() function.

```
$conn = mysql_connect("localhost","username", "password") or
    die ("Could not connect to localhost");

mysql_select_db("test", $conn) or
    die("could not select database");
$query = "create table my_table (
    col_1 int not null primary key,
    col_2 text
)";
mysql_query($query) or
    die(mysql_error());
```

## Column Types

MySQL comes with a range of column types. Several are similar but have subtle yet important differences. Give this section a read and choose carefully when deciding on column types for your tables.

### Text column types

MySQL has seven column types suitable for storing text strings:

- char
- varchar
- tinytext
- text
- mediumtext
- longtext
- enum

### CHAR

Usage: char(length)

The char column type has a maximum length of 255 characters. This is a fixed-length type, meaning that when a value is inserted that has fewer characters than the maximum length of the column, the field will be right-padded with spaces. So if a column has been defined as char(10) and you want to store the value “happy”, MySQL will actually store “happy” and then five spaces. The spaces are removed from the result when the value is retrieved from the table.

### VARCHAR

Usage: varchar(length)

This is nearly identical to char and is used in many of the same places. It also has a maximum length of 255. The difference is that varchar is a variable-length column type. The values will not be padded with spaces. Instead MySQL will add one character to each varchar field, which stores the length of the field. MySQL removes spaces from the end of strings in varchar fields.

### USING CHAR OR VARCHAR

For the most part there is little practical difference between char and varchar. Which one you decide to use will depend on which will require more space, the trailing spaces in a char column or the single character in varchar. If your field stores something like last names, you’ll probably want to allow 25 characters, just to be safe. If you were to use the char column type and someone had the last name Smith, your column would contain 20 trailing spaces. There’s no need for it; you’re much better off using varchar and allowing MySQL to track the size of the column. However, when you want to store passwords of five to seven characters, it would be a waste to use varchar to track the size of the column. Every time a varchar field is updated, MySQL has to check the length of the field and change the character that stores the field length. You’d be better off using char(7).

![](img/de0823012275cf4ceebdb822a56e6b71_62_0.png)

> If you define a column as varchar with a column length of less than four, MySQL will automatically change the column to the char type.
