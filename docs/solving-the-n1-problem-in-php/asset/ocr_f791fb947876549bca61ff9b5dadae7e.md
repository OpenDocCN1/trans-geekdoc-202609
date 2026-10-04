# Diagning N+1 Problems

If the queries are batched per-relationship, instead of per-root-entity, the log might look more like this:

Queries batched per relationship

```
SELECT * FROM root_table WHERE ... ;
SELECT * FROM rell1.root_id = 10324 ...;
SELECT * FROM rell1.root_id = 10325 ...;
SELECT * FROM rell1.root_id = 10326 ...;

SELECT * FROM rell2.root_id = 10324 ...;
SELECT * FROM rell2.root_id = 10325 ...;
SELECT * FROM rell2.root_id = 10326 ...;

SELECT * FROM rell3.root_id = 10324 ...;
SELECT * FROM rell3.root_id = 10325 ...;
SELECT * FROM rell3.root_id = 10326 ...;

SELECT * FROM rell4.root_id = 10324 ...;
SELECT * FROM rell4.root_id = 10325 ...;
SELECT * FROM rell4.root_id = 10326 ...;

SELECT * FROM rel4.root_id = 10324 ...;
SELECT * FROM rell4.root_id = 10325 ...;
SELECT * FROM rell4.root_id = 10326 ...;

SELECT * FROM rell5.root_id = 10324 ...;
SELECT * FROM rell5.root_id = 10325 ...;
SELECT * FROM rell5.root_id = 10326 ...
```

Unfortunately, even when we recognize a pattern, it may be difficult to discover what part of the codebase is causing the problem. We will need to search the codebase for SQL strings similar to the ones showing up in the logs.

> If your database abstraction layer has a query profiler that retains a backtrack, so that you can tell where the query originates, so much the better (Aura.Sql¹ is one package). Even if it does not, you can narrow down the possible locations by starting the profiler at a point of your choosing, then stopping the profiler (and logging or dumping its output) at a later point.

¹https://github.com/auraph/Aura.Sql