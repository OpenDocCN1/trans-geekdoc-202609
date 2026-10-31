
![](img/de0823012275cf4ceebdb822a56e6b71_53_0.png)

By the time you read this book, there is a very good chance that MySQL will support transactions. The developers have been working with transaction-safe tables for some time. Check mysql.com to see if the current release can use transactions. We did not use transactions in any of the applications in this book.

When you're working with a series of steps like this, there is potential for serious problems. If the operating system crashes or power goes out between steps two and three, the database will contain bad data.

To prevent such a state, most sophisticated database systems make use of *transactions*. With transactions, the developer can identify a group of commands. If any one of these commands fails to go through, the whole group of commands is nixed and the database returns to the state it was in before the first command was attempted. This is known as a COMMIT/ROLLBACK approach. Either all of the requests are committed to the database, or the database is rolled back to the state it was in prior to the transactions.

In Section 5.4.3 of the MySQL Reference Manual, there is a lengthy defense of MySQL's choice not to include transactions. It also includes techniques for achieving the same effect with logging and table locks. You can decide for yourself whether this argument makes sense. Many people feel that the lack of transactions makes MySQL a poor choice in certain environments. If you're the IT manager at a bank looking for a relational database management system (RDBMS), MySQL probably isn't the way to go.

## Stored procedures

The big fancy database systems allow for procedural code (something very much like PHP or Perl) to be placed within the database. There are a couple of key advantages to using stored procedures. First, it can reduce the amount of code needed in middleware applications. If MySQL accepted stored procedures, a single PHP command can be sent to the database to query data, do some string manipulation, and then return a value ready to be displayed in your page.

The other major advantage comes from working in an environment where more than one front-end is accessing the same database. Consider a situation where there happens to be a front-end written for the Web and another in Visual C++ accessible on Windows machines. It would be a pain to write all the queries and transactions in two different places. You'd be much better off writing stored procedures and accessing those from your various applications.

![](img/de0823012275cf4ceebdb822a56e6b71_53_1.png)

MySQL also does not support sub-selects. We will discuss how to work around this limitation in Chapter 3.

## Summary

At this point you should have a pretty good idea of how relational databases work. The theory covered here is really important, as quality data design is one of the cornerstones of quality applications. If you fail in the normalization process, you could leave yourself with difficulties that will haunt you for months or years.

In the applications in Parts 3 and 4 of this book, you will see how we approached and normalized several sets of data.

Now that you know how tables in a relational database work, move on to Chapter 2, where you will see how to make these tables in MySQL.

## Chapter 2

### The Structured Query Language for Creating and Altering Tables

### IN THIS CHAPTER

- Creating tables and databases in MySQL
- Choosing the proper column type and column attributes for tables
- Maintaining databases and tables

In Chapter 1 you learned that tables are the basis of all the good things that come from working with relational databases. There's a fair amount you can do with these tables, as you'll see throughout this book. So it should come as no surprise that the process of creating and maintaining the tables requires some knowledge. As Mom used to say, nothing good comes easy.

If you're coming to MySQL from Microsoft's SQL Server or a desktop package like Access, you may be used to creating tables with a slick WYSIWYG (what you see is what you get) interface. In fact, there is a package called phpMyadmin that will give you many of the niceties you're used to working with. We use this tool and love it. We'll discuss it in further detail at the end of this chapter. There's no doubt that working with a graphical interface can be a lot more pleasant than figuring out the syntax of a language—any language.

![](img/de0823012275cf4ceebdb822a56e6b71_55_0.png)

> In fact, there are many GUI tools you can use when working with MySQL. See http://www.mysql.com/downloads/contrib.html for a listing. The MySQL development team is working on an Access-like interface to MySQL. Check the mysql.com site for availability.

However, even if you plan on installing and using this tool, you should take some time to learn how to create and maintain tables using the Data Definition Language (DDL), which is part of SQL. Specifically, it will be a great help to you to know the create and alter commands. Before too long you will have to use these commands within your scripts. There also may be an occasion when you don't have access to the graphical interface, and you'll need this knowledge to fall back on.

## Definitions

Before we get to creating tables and databases in MySQL, there are a couple of items you'll need to understand. The concepts I'm about to present are very important—make sure you understand how to deal with these before you move forward in your database design.

### Null

One of the first decisions you will have to make for every column in your tables is whether or not you are going to allow null values. If you remember back to your ninth grade math, you may recall the null set, which is a grouping that contains nothing. In relational databases, null has the same meaning: a null field contains nothing.

Keep in mind that a null field is distinctly different from a text string with no characters (a zero-length string) or the numerical value of zero. The difference is that empty strings and zeros are values. In your programming you most likely have had an occasion where you have had to check whether a string contained any value, perhaps as part of an if... statement. In PHP, it would look like this:

```
$var //this is a variable used in the test
if ($var == "")
{
    echo "Var is an empty string";
} else {
    echo $var;
}
```

The same syntax would work for comparing zero against another value.

These sorts of comparisons will not work with null. Since null is the absence of value, any comparison with any value (including another null) is meaningless. In Chapter 3 you will see that null values require the application developer to be very careful when writing table joins. To give you a quick preview, consider what would happen if we wanted to join Table 2-1 and Table 2-2:

![](img/de0823012275cf4ceebdb822a56e6b71_57_0.png)

In your SQL select statements (covered in Chapter 3), there are a couple of ways you can check if a field contains a null value. First, you can use MySQL's isnull() function. For example to find rows in a table where the middle_name column contains null values, you could run the following query:

```
select * from names where isnull(middle_name);
```

Or, to exclude null values in the query result:

```
select * from names where !isnull(middle_name);
```

The exclamation point means "not."

You can also use the is null and is not null statements. For example:

```
select * from users where addr2 is null;
select * from users where addr2 is not null;
```

### TABLE 2-1 CONTACTS

| first_name | last_name | spouse_id |
|---|---|---|
| Jay | Greenspan | 1 |
| Brad | Bulger | NULL |

### TABLE 2-2 SPOUSES

| spouse_id | first_name | last_name |
|---|---|---|
| 1 | Melissa | Ramirez |

If you wanted to find the authors of a great book on MySQL and PHP and their associated spouses, you would have to join these tables on the spouse_id field. (Don't worry if you don't understand the exact syntax, it will be covered in the next chapter.)

```
SELECT * FROM Contacts, Spouses
WHERE Contacts.spouse_id = Spouses.spouse_id
```
