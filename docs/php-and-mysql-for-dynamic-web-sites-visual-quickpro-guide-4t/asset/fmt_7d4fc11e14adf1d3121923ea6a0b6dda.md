
• How do you fix the problem of a many-to-many relationship between two tables?

• What are the four types of indexes? What general types of columns *should be* indexed? What general types of columns *should not* be indexed?

• What are the two most common MySQL table types? What is the default table type for your MySQL installation?

• What is a *character set*? What is a *collation*? What impact does the character set have on the database? What impact does the collation have? What character set and collation are you using?

• What is *UTC*? How do you find the UTC time in MySQL? How do you convert from UTC to another time zone’s time?

• What are *foreign key constraints*? What table type supports foreign key constraints?

#### Pursue

• You may want to consider downloading, installing, and learning to use the MySQL Workbench application. It can be quite useful.

• If you don’t fully grasp the process of normalization—and that’s perfectly understandable—search for additional tutorials online or ask a question in my support forums.

• Design your own database using the information presented here.

## 7. Advanced SQL and MySQL

### In This Chapter

- [Performing Joins](#ch07.html#ch07lev1sec1) [204](#ch07.html#ch07lev1sec1)
- [Grouping Selected Results](#ch07.html#ch07lev1sec2) [214](#ch07.html#ch07lev1sec2)
- [Advanced Selections](#ch07.html#ch07lev1sec3) [218](#ch07.html#ch07lev1sec3)
- [Performing FULLTEXT Searches](#ch07.html#ch07lev1sec4) [222](#ch07.html#ch07lev1sec4)
- [Optimizing Queries](#ch07.html#ch07lev1sec5) [230](#ch07.html#ch07lev1sec5)
- [Performing Transactions](#ch07.html#ch07lev1sec6) [234](#ch07.html#ch07lev1sec6)
- [Database Encryption](#ch07.html#ch07lev1sec7) [237](#ch07.html#ch07lev1sec7)
- [Review and Pursue](#ch07.html#ch07lev1sec8) [240](#ch07.html#ch07lev1sec8)

This, the last chapter dedicated to SQL and MySQL (although most of the rest of the book will use these technologies in some form or another), discusses the higher-end concepts often needed to work with more complicated databases, like those created in the previous chapter. The first such topic is the `JOIN`, a critical SQL term for querying normalized databases with multiple tables. From there, the chapter introduces a category of functions that are specifically used when grouping query results, followed by more complex ways to select values from a table.

In the middle of the chapter, you’ll learn how to perform `FULLTEXT` searches, which can add search engine-like functionality to any site. Next up is the `EXPLAIN` command: it provides a way to test the efficiency of your database schema and your queries. The chapter concludes with coverage of transactions and database encryption.

### Performing Joins

Because relational databases are more complexly structured, they sometimes require special query statements to retrieve the information you need most. For example, if you wanted to know what messages are in the *MySQL* forum (using the *forum* database created in the previous chapter), you would need to first find the `forum_id` for *MySQL*:

```
SELECT forum_id FROM forums WHERE name='MySQL'
```

Then you would use that number to retrieve all the records from the *messages* table that have that `forum_id`:

```
SELECT * FROM messages WHERE forum_id=1
```

This one simple (and, in a forum, often necessary) task would require two separate queries. By using a *join,* you can accomplish all of that in one fell swoop.

A join is an SQL query that uses two or more tables, and produces a virtual table of results. Any time you need to simultaneously retrieve information from more than one table, a join is what you’ll probably use.

Joins can be written in many different ways, but the basic syntax is:

```
SELECT what_columns FROM tableA JOIN_TYPE tableB JOIN_CLAUSE
```

Because joins involve multiple tables, the `what_columns` can include columns in any named table. And as joins often return so much information, it’s normally best to specify exactly what columns you want returned, instead of selecting them all.

When selecting from multiple tables, you must use the dot syntax (`table.column`) if the tables named in the query have columns with the same name. This is often the case when dealing with relational databases because a primary key from one table may have the same name as a foreign key in another. If you are not explicit when referencing your columns, you’ll get an error:

```
SELECT forum_id FROM messages INNER JOIN  
forums ON messages.forum_id=forums.forum_id
```

The two main types of joins are *inner* and *outer* (there are subtypes within both). As you’ll see with outer joins, the order in which you reference the tables does matter.

The join clause is where you indicate the relationship between the joined tables. For example, `forums.forum_id` should equal `messages.forum_id` (as in the above).

You can also use `WHERE` and `ORDER BY` clauses with a join, as you would with any `SELECT` query.

As a last note, before getting into joins more specifically, the SQL concept of an *alias*—introduced in [Chapter 5](#ch05.html#ch05), “[Introduction to SQL](#ch05.html#ch05)”—will come in handy when writing joins. Often an alias will just be used as a shorthand way of referencing the same table multiple times within the same query. If you don’t recall the syntax for creating aliases, or how they’re used, revisit that part of [Chapter 5](#ch05.html#ch05).

(As in the previous two chapters, this chapter will use the command-line mysql client to execute queries, but you can also use phpMyAdmin or another tool. The chapter assumes you know how to connect to the MySQL server and declare the character set to use, if necessary.)

#### Inner Joins

An inner join returns all of the records from the named tables wherever a match is made. For example, to find every message posted in the *MySQL* forum, the inner join would be written as:

```
SELECT m.message_id, m.subject, f.name  
FROM messages AS m INNER JOIN forums AS f  
ON m.forum_id = f.forum_id  
WHERE f.name = 'MySQL'
```

This join is selecting three columns from the *messages* table (aliased as *m*) and one column from the *forums* table (aliased as *f*) under two conditions. First, the `f.name` column must have a value of *MySQL* (this will return the `forum_id` of 1). Second, the `forum_id` value in the *forums* table must match the `forum_id` value in the *messages* table. Because of the equality comparison being made across both tables (`m.forum_id = f.forum_id`), this is known as an *equijoin*.

As an alternative syntax, if the column in both tables being used in the equality comparison has the same name, you can simplify your query with `USING`:

```
SELECT m.message_id, m.subject, f.name  
FROM messages AS m INNER JOIN forums AS f  
USING (forum_id)  
WHERE f.name = 'MySQL'
```

#### To use inner joins

**1.** Connect to MySQL and select the *forum* database.

**2.** Retrieve the forum name and message subject for every record in the *messages* table:

```
SELECT f.name, m.subject FROM forums  
AS f INNER JOIN messages AS m  
USING (forum_id) ORDER BY f.name;
```

This query will effectively replace the `forum_id` value in the *messages* table with the corresponding `name` value from the *forums* table for each of the records in the *messages* table. The end result is that it displays the textual version of the forum name for each message subject.
