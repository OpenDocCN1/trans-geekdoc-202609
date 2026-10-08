# Chapter 8 Designing Your Web Database

+   - Chapter 10, "Working with Your MySQL Database," explains how to query the database and add, delete, and update records, all from the command line.
- Chapter 11, "Accessing Your MySQL Database from the Web with PHP," explains how to connect PHP and MySQL so that you can use and administer your database from an interface. You will learn two methods of doing this: using the MySQL native driver, and the database agnostic.
- Chapter 12, "Advanced MySQL Administration," covers MySQL administration in more detail, including details of the privilege system, security, and optimization.
- Chapter 13, "Advanced MySQL Programming," covers the storage engines in more detail, including coverage of transactions, full text search, and stored procedures.

# Relational Database Concepts

Relational databases are, by far, the most commonly used type of database. They depend on a sound theoretical basis in relational algebra. You don't need to understand relational theory to use a relational database (which is a good thing), but you do need to understand some basic relational database concepts.

# Tables

Relational databases are made up of relations, more commonly called tables. A table is exactly what it sounds like—a table of data. If you've used an electronic spreadsheet, you've already used a table.

Look at the sample table in Figure 8.1. It contains the names and addresses of the customers of a bookstore named Book-O-Rama.

| CustomerID | Name | City |
|---|---|---||
| 1 | Julie Smith | 25 Oak Street | Airport West |
| 2 | Alan Wong | 1/47 Haines Avenue | Box Hill |
| 3 | Michelle Arthur | 357 North Road | Yarraville |

Figure 8.1 Book-O-Rama's customer details are stored in a table

The table has a name (Customers); a number of columns, each corresponding to a different piece of data; and rows that correspond to individual customers.