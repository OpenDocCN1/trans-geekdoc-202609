# Chapter 17. DATABASE INTEGRATION

Building HTML Tables from SQL Queries

Tracking Visitors with Session Identifiers

Storing Content in Database

Database Abstraction Layers

PHP has strong support for many databases. If native support for your favorite database doesn't exist, there's always ODBC, which is a standard for external database drivers. Support for new databases seems to show up regularly. The universal remark in this regard from the PHP developers have "give us a machine to test on and we'll support."

MySQL is undoubtedly the most popular database used by PHP coders. Apart from being free, it suits development because of its blazing speed. In the examples for this chapter I'll use a MySQL database. If you don't, you can either go to the MySQL Web site : http://www.mysql.com/ and investigate downloading and installing, or you can change the examples to work with another database.

Most databases use the Structured Query Language, or SQL. It is a fourth-generation language (4GL), which reads it more like English than PHP source code. A tutorial on SQL is beyond the scope of this book. If you're completely new to SQL, I recommend investigating the tutorials listed on the documentation page on the MySQL home page : http://www.mysql.com/doc.html. An alternative would be to find a book such as Hands-On SQL by Robert Groth and David Gerber, published by Prentice Hall.

# Building HTML Tables from SQL Queries

Perhaps the simplest task you can perform with a database and PHP is to extract data from a table and display it in an HTML table. The table could contain a catalog of items for sale, a list of projects, or a list of Internet name servers and ping times. For illustration purposes, I'll use the first scenario. Imagine a supermarket wants to list the items they have for sale on their Web site. We'll use the database that's created when MySQL is installed. The PHP script for viewing the catalog of products will produce on the same machine as the database server.

The first step is to create the table. Listing 17.1 displays SQL code for creating a simple, three-column table. The table is named catalog. It has a column called ID that is an integer with at most 11 digits. It cannot be null, and new rows will automatically be assigned consecutive values. The last line of the definition specifies ID as a primary key.