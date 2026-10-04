
# 8. Common Questions

## Can I Combine Single-Query With Query-And-Stitch?

It might be reasonable in some cases to combine the single-query approach with the query-and-stitch approach. You might handle all the "to-one" relationships with the single-query approach, and follow by handling all the "to-many" relationships using query-and-stitch. Doing so would reduce the number of queries in total by consolidating all the "to-one" queries into the root query. In our earlier examples, that would mean the three Post, Author, and Summary queries would become one query, leaving only the Comment and Tag queries.

I am in favor of combining the approaches when performance is of the utmost concern. However, my guess is that by eliminating N+1 problems in the codebase, we have increased performance so dramatically that the greater concern is one of consistency. Mixing approaches, or using one approach in some cases and the other in different cases, means inconsistency in the codebase. That, in turn, can reduce developer comprehension and confuse expectations.

Thus, I prefer using the query-and-stitch method throughout a codebase, even when it means one or two extra queries here and there. Of course, once those extra queries change from an imagined or predicted performance concern into an actual and measured performance concern, I am happy to use the single-query solution to resolve those concerns.

As usual, your own needs and preferences should be the final determinant of which approaches to use, and when.

## Can I Use-Selects Instead Of The IN() Operator?

In the query-and-stitch solution, we create a list of quoted comma-separated values indicating the identity or foreign key to retrieve from the database. We then use the list of values with an IN() operator to get the necessary rows for building our associations.

While it is easy to imagine problems with the IN() operator, I myself have rarely run into a situation where using IN() was actually a problem. Some databases may restrict the number or length of IN() elements, or restrict the length of the query string overall, but in practice I have found these restrictions of little importance. As long as the IN() condition referred to an indexed column, I found few or no performance-related problems.

However, there are still cases where the IN() operator is a measurable problem. You will only be able to tell this by running EXPLAIN (or the equivalent) on your slower queries, and discovering that the query plan is sub-optimal to the IN().

In such cases, replace the IN() with a JOIN on a sub-select to provide the related values for retrieval. For example, fetching a root collection of Post entities and an associated collection of Comment entities might look like this

```php
<?php
// fetch the sequentially-indexed post entities
$stmt = 'SELECT *
FROM posts
ORDER BY datetime DESC
LIMIT 10';
$sth = $pdo->prepare($stmt);
$sth->execute();
$post_entities = $sth->fetchAll(PDO::FETCH_CLASS, 'Post');

// fetch all the comments for all the posts
$stm = "SELECT *
FROM comments
JOIN (
SELECT post_id
FROM posts
ORDER BY datetime DESC
LIMIT 10
) AS posts ON posts.post_id = comments.post_id";
$sth = $pdo->prepare($stmt);
$sth->execute();
$comment_entities = $sth->fetchAll(PDO::FETCH_CLASS, 'Comment');
?>
```

In this case, we remove the WHERE ... IN() and literal list of post_id values. We then replace it with JOIN against a sub-select that is identical to the SELECT we used to create the root collection (with the exception that the sub-select returns only the primary key).

If we really want to get clever, we can create a temporary table with the post_id values from the root collection. We can then JOIN against the temporary table instead of the sub-select. This is probably most useful when we need to use the same sub-select multiple times within a transaction.

## Should I Use a Transaction With Query-And-Stitch?

With query-and-stitch, we make multiple calls to the database. However, the data in the database may change between those calls. For example, let's say we fetch the rows for a Post collection, and immediately after that one of the posts row values is changed (say the author_id). Any query after that, where we JOIN posts or otherwise provide the same list of author_id values to available, may be inconsistent and lead to unexpected results.

For this reason, it may be wise in some cases to perform query-and-stitch inside a transaction. Doing so will help to maintain a consistent state across the several queries whose results will be stitched together.

There are differing levels of transaction isolation, and different databases have their defaults. I suggest using the READ COMMITTED level and moving up to REPEATABLE READ if you notice errors or inconsistencies from insufficient isolation.

> Transactions and transaction isolation carry performance considerations related to table and row locking. Be sure to consult your database documentation for specifics. You may need to choose a tradeoff between consistency and performance.

For example, with PDO and either MySQL or PostgreSQL, the code might look like the following:

```php
<?php
// begin the transaction in
$pdo->exec('SET TRANSACTION ISOLATION LEVEL REPEATABLE READ');
$pdo->beginTransaction();
// select all the data ...
// end the transaction
$pdo->commit();
// stitch the data together into entities
?>
```

Notice that we do all our data selection in a single block, then end the transaction, and only afterwards do we stitch our entities. This is because we want to keep the time spent in the transaction as short as possible. In general, longer transactions mean slower performance.

> http://en.wikipedia.org/wiki/Isolation_(database_systems)

## Can I Just Use ORM?

At this point, some readers are wondering if it would be wise to incorporate ORM system such as Doctrine, Propel, or one of the others available in PHP. After all, ORMs use the single-query and query-and-stitch techniques themselves, and thus using an ORM would automate away a lot of the code we have to write for ourselves when solving the N+1 problem.

I have mixed feelings about ORMs. After developing a robust ORM system for Solar with Jeff Moore, I am fully acquainted with the tradeoffs in using them. They are often a great boon in the early development of an application. But later they are revealed as opaque, ineffective, or unpredictable in edge cases, and so require that you have good knowledge of their idiosyncrasies in different situations.

ORMs almost always require you to learn special idioms to build your queries. These idioms can be tied to a SQL-lookalike language, or to a particular set of methods and informational properties on various classes, or even of the two. I feel this modified way-of-working presents a significant impediment to incorporating an ORM into an existing application. Even if your database logic is well separated, you will have to rewrite every database interaction to conform to the ORM query idioms. This will take time and effort that might be better spent elsewhere.

Even after incorporating an ORM, you may not be fully insulated from the N+1 problem. This is especially case if the ORM lazy-loads records in a loop where you did not eager-fetch the necessary data. You will need to pay attention to how your ORM works internally so that you do not end up with the very problem you were trying to solve.

Overall, I think the tradeoffs of an ORM are highly context-dependent. I cannot offer general-purpose advice regarding them without knowing your particular situation, other than to say “Proceed with caution.”

http://solarphp.com
http://www.procata.com

# Appendix

## SQL Schema

The following SQLite tables represent the data structures for a naive blogging application.
The tables are named for plural entities: posts, comments, and so on. Each primary key column is auto-incremented, and is named for the singular entity suffixed with *_id: post_id, comment_id, and so on.

The summaries table does not have a summary_id column, since each row is one-to-one with posts directly. The posts_tags table is an association table, mapping a many-to-many relationship between posts and tags.

The tables are stripped to reveal the core substance of the data, and should not be used as the basis for a real application.

```
CREATE TABLE authors (
    author_id INTEGER PRIMARY KEY AUTOINCREMENT,
    name VARCHAR(255)
);
CREATE TABLE comments (
    comment_id INTEGER PRIMARY KEY AUTOINCREMENT,
    post_id INTEGER,
    datetime DATETIME,
    name VARCHAR(255),
    email VARCHAR(255),
    website VARCHAR(255),
    body TEXT
);
CREATE TABLE posts (
    post_id INTEGER PRIMARY KEY AUTOINCREMENT,
    author_id INTEGER,
    datetime DATETIME,
    title VARCHAR(255),
    body TEXT
);
CREATE TABLE posts_tags (
```
