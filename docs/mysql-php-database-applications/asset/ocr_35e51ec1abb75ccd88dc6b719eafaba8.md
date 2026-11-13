middleware applications. If MySQL accepted stored procedures (which it unfortunately does not – yet), a single PHP command could be sent to the database to query data, do some string manipulation, and then return a value ready to be displayed in your page.

The other major advantage comes when you are working in an environment in which more than one front-end is accessing the same database. Consider a situation in which there happens to be one front-end written for the Web and another, accessible on Windows machines, written in Visual C++. It would be a pain to write all the queries and transactions in two different places. You'd be much better off writing stored procedures and accessing those from your various applications. Stored procedures are planned for MySQL version 5.0.

# Summary

At this point you should have a pretty good idea of how relational databases work. The theory covered here is really important, as quality data design is one of the cornerstones of quality applications. If you fail in the normalization process, you could create difficulties that will haunt you for months or years.

In the applications in Parts III and IV of this book, you see how we approach and normalize several sets of data.

Now that you know how tables in a relational database work, move on to Chapter 2, where you see how to make these tables in MySQL.