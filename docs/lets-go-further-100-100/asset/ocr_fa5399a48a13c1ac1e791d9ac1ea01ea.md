> instead... either will work in the context of a query string.

# Dynamic filtering in the SQL query

The hardest part of building a dynamic filtering feature like this is the SQL query to retrieve the data — we need it to work with no filters, filters on both `title` and `genres`, or a filter on only one of them.

To deal with this, one option is to build up the SQL query dynamically at runtime... with the necessary SQL for each filter concatenated or interpolated into the `WHERE` clause. But this approach can make your code messy and difficult to understand, especially for large queries which need to support lots of filter options.

In this book we’ll opt for a different technique and use a fixed SQL query which looks like this:

```
```sql
SELECT id, created_at, title, year, runtime, genres, version
FROM movies
WHERE (LOWER(title) = LOWER($1) OR $1 = '')
AND (genres @> $2 OR $2 = '{}')
ORDER BY id
```
```

This SQL query is designed so that each of the filters behaves like it is ‘optional’. For example, the condition `(LOWER(title) = LOWER($1) OR $1 = '')` will evaluate as `true` if the placeholder parameter `$1` is a case-insensitive match for the movie