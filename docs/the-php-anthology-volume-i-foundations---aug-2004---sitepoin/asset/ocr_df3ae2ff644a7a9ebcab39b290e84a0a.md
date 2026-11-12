MySQL. Although PostgreSQL is arguably the better database, in that it supports more of the features that are common to relational databases, MySQL is better supported on Windows, and is a popular choice among Web hosts that provide support for PHP. These factors combine to make PHP and MySQL a very popular combination. This book is geared to the use of MySQL with PHP but it's important to remember that there are alternatives with full support for features such as stored procedures, triggers and constraints, many of which become important for applications with complex data structures.

This chapter covers all the common operations PHP developers have to perform when working with MySQL, from retrieving and modifying data, to searching and backing up a database. The examples focus on using a single table, so no discussion is made of table relationships here. For a full discussion of table relationships, see Kevin Yank's Build Your Own Database Driven Website Using PHP & MySQL (ISBN 0-9579218-1-0), or see an example of them in practice when we deal with user groups in Volume II, Chapter 1.

The examples used here work with a sample database called sitepoint, which contains the following single table:

```
File: articles.sql

CREATE TABLE articles (
    article_id INT(11) NOT NULL AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL DEFAULT '',
    intro TEXT NOT NULL,
    body TEXT NOT NULL,
    author VARCHAR(255) NOT NULL DEFAULT '',
    published VARCHAR(11) DEFAULT NULL,
    public ENUM('0','1') NOT NULL DEFAULT '0',
    PRIMARY KEY (article_id),
    FULLTEXT KEY art_search (title, body, author)
)
```

A query to construct this table along with some sample data is available in the code archive, contained in the file sql/articles.sql. The table will be used for examples in later chapters of the book.

# How do I access a MySQL database?

Connecting to MySQL with PHP couldn't be easier. It's essentially a two-step process; first connect to the MySQL database server itself, then inform MySQL of the database you want to connect to.