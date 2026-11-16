

## Logout

The script Logout.php, logs out the user:

```
<?php
include_once("Common.php");
include_once("User.php");
```

If the user is not authenticated, then send an error page:

```
setSessionHandlers();
header("Content-Type: text/vnd.wap.wml" );
checkSessionAuthenticated();
```

Destroy the user's session:

```
session_destroy();
?>
```

The WML Document Type Declaration:

```
<!DOCTYPE wml PUBLIC "--//WAPFORUM//DTD WML 1.1//EN"
"http://www.wapforum.org/DTD/wml_1.1.xml">
<wml>
<card>
```

Display a Thank you message:

```
<p>
Thanks <i><?php echo($user->getUserId()) ?></i>
for using the Shopping Cart Application
</p>
</card>
</wml>
```

## Summary

In this chapter we wrote a complete real-life shopping cart application for mobile devices, using PHP in
the middle tier. This illustrates how PHP can be effectively used in the middle tier, to write highly
scalable (non-HTML) web-based applications.

To keep the application simple, we chose only minimal features. Some features that you may like to add
to this application could include:

- An HTML interface to the same application. The HTML site should use the same back-end database. This will allow users to access the same site from their PC browsers as well.

- Business workflow logic in the application. For example, sending e-mail to the shipping department after a user has purchased items.

- An e-mail confirmation of the order.

## 17 PHP and MySQL

One huge benefit of using a scripting language like PHP is the ability to generate dynamic content. However, it is important to consider the source of that content. We have already seen how input can be received from the user – from session storage, and from flat text files. Now, we will learn how to use the power of a relational database to serve content for a PHP-driven application.

Truly sophisticated data-driven web applications use database management systems (DBMS) for a number of reasons. First, using the Structured Query Language (SQL), the web programmer can offload most of the data storage and management tasks to the database system. Second, databases are better at managing large amounts of data than we are, so we might as well let them do what they do best. Third, databases are persistent while variables and their data in PHP scripts generally only exist for the life of a given page request. Because of this persistence, databases can make more intelligent decisions on things such as disk performance and memory caching.

Using a database to store information also allows the PHP developer to write less code (being that data-handling tasks are being outsourced to the database management system) and abstract away the entire data management system.

This chapter will focus specifically on the MySQL interface. Some of the other PHP database interfaces, such as PostgreSQL, ODBC, and Oracle are covered in later chapters. In this chapter, we will cover the following topics:

- Relational database fundamentals
- The Structured Query Language (SQL)
- The PHP MySQL interface
- A simple data-driven PHP application
- A PHP database abstraction layer

If you are already familiar with relational database concepts and SQL, you may want to jump ahead to the PHP-specific section of this chapter, *PHP and Relational Databases*. If you are familiar with relational databases and SQL in general but not with MySQL specifically, you may want to browse this chapter, as the syntax tends to vary slightly between DBMSs. If you are *not* familiar with relational databases, keep in mind that this chapter provides only a cursory introduction to the topic. Many in-depth volumes have been written concerning relational database theory and best practices, such as:

- *Beginning SQL Programming* from Wrox Press (ISBN 1-861001-80-0)
- *Beginning Databases with PostgreSQL* from Wrox Press (ISBN 1-861005-15-6)

### Relational Databases

Technically speaking, a **database** is a collection of data organized for rapid search and retrieval. Databases come in many shapes and sizes:

- A **hierarchical** database is one in which data is stored in a tree-like structure, such as a computer's file system.

- A **relational** database management system (RDBMS) is one where data is organized into tables (also known as "entities"). Tables consist of fields (also known as "columns" or "attributes") and records (also known as "rows" or "instances" or "tuples").

- An **object-oriented** database is one in which data is stored in its natural structure, in the form of objects. Object-oriented databases offer a great deal of flexibility when using object-oriented programming. While a few object-oriented databases have emerged in recent years, they have yet to achieve the performance and widespread usage of relational databases, which are the main focus of this chapter. This is mainly due to the fact that relational algebra (the basis for relational database theory) is much more powerful and correct than any object query language can be.

- A **hybrid** DBMS is one that offers features of both object-oriented and relational databases.

While all of these different types of databases can be used with PHP, it is most common to use **relational** databases for web applications due to their speed, stability, and maturity. An application which implements an RDBMS almost always uses more than one table. The data in a table usually has a logical relationship with the data in other tables, hence the term relational database.

Let's now look into an example database that draws inspiration from an online library. The database will store information on the current books in the library, the books' authors, and the series to which each book belongs. Each book must belong to one and only one series, and may have multiple authors, and each author may have written multiple books. We also store the price, the quantity, and the number of books that are "booked" (reserved) for each book in the database.

We shall continue by demonstrating how this database will be organized into separate tables. The relationships between the tables, and the fields within the tables, will also be illustrated.

The table containing data describing book details would have a logical relationship with the table containing data about the different series of books like this:

| details |
|---|
| PK | ISBN |
| | price |
| | num_of_books |
| | num_booked |
| | series_ID |

### Indices

An **index** is a sorted list that speeds up data matching, and it is the most powerful tool for improving database performance. If computers were magically fast, we would have no need for indices, but they're not, and complex queries can sometimes take a very long time to process. Therefore, it is sometimes necessary to optimize a database to handle queries more quickly.

The index is a sorted list of the field's values. In addition to the values, it contains pointers to that value's location in the table. In MySQL, and many other database systems, indices are stored in their own files, separate from the table data.

A unique index is one in which each value in the index must be unique. Unique indices can be searched even more quickly than those that are not unique, but they are only applicable if the nature of the data in the field(s) being indexed is such that uniqueness makes sense.

For example, in the Periodic Table of elements, the element's symbol must always be unique; therefore, a unique index may be placed on the field "Symbol". The element's valence is not unique, so if an index were needed on the field "Valence", you may not use a unique index. For more information about indices, including unique indices, consult the documentation for your DBMS.

### Keys

A **primary key** is an example of a unique index. It is used to uniquely identify a single record in a table. No two records in a table can have the same value for their primary key. This is generally necessary in a relational database because it allows for the retrieval and manipulation of data in a logical, consistent, and unambiguous way. Primary keys are used to enforce this requirement.

> Primary keys may consist of one or more fields in the table.

In the above example, the `ISBN` field is the primary key of the `details` table. If the book has an ISBN of 1861003730, we can accurately match that ISBN, with the rest of the data pertaining to the book, since there can be only one 1861003730 in the `details` table. If a flaw in the application allowed us to enter a second record in the table with the ISBN 1861003730, the **referential integrity** of the database would be violated, since the primary key value no longer refers to just a single record.

Since each record has a unique identifier, we can now demonstrate the relationship between the `details` table data and the `series` table data, by referring to `series_ID` in `series`:

