# Diagnosing N+1 Problems

In the case of our posts-and-comments example, we might see something like this in the query logs:

# N Comment queries and 1 Post query

```
SELECT * FROM posts ORDER BY date DESC LIMIT 10;
SELECT * FROM comments WHERE comments.post_id = 936;
SELECT * FROM comments WHERE comments.post_id = 935;
SELECT * FROM comments WHERE comments.post_id = 934;
SELECT * FROM comments WHERE comments.post_id = 933;
SELECT * FROM comments WHERE comments.post_id = 932;
SELECT * FROM comments WHERE comments.post_id = 931;
SELECT * FROM comments WHERE comments.post_id = 929;
SELECT * FROM comments WHERE comments.post_id = 927;
```

If the application retrieves data for two or more relationships, the pattern might be less obvious. In the case of the Slow Reporting Script, where the application retrieved five associated entities for each root entity, the logs looked like this...

Queries batched per root entity

```
SELECT * FROM root_table WHERE;
SELECT * FROM rel1 WHERE rel1.root_id = 10324 ...;
SELECT * FROM rel2 WHERE rel2.root_id = 10324 ...;
SELECT * FROM rel3 WHERE rel3.root_id = 10324 ...;
SELECT * FROM rel4 WHERE rel4.root_id = 10324 ...;
SELECT * FROM rel5 WHERE rel5.root_id = 10324 ...;
SELECT * FROM rel1 WHERE rel1.root_id = 10325 ...;
SELECT * FROM rel2 WHERE rel2.root_id = 10325 ...;
SELECT * FROM rel3 WHERE rel3.root_id = 10325 ...;
SELECT * FROM rel4 WHERE rel4.root_id = 10325 ...;
SELECT * FROM rel5 WHERE rel5.root_id = 10325 ...;
SELECT * FROM rel1 WHERE rel1.root_id = 10326 ...;
SELECT * FROM rel2 WHERE rel2.root_id = 10326 ...;
SELECT * FROM rel3 WHERE rel3.root_id = 10326 ...;
SELECT * FROM rel4 WHERE rel4.root_id = 10326 ...;
SELECT * FROM rel5 WHERE rel5.root_id = 10326 ...;
```

... and so, with 5 related queries for each of the root entities. As you can see, the pattern repeats over groups of five lines, one for each rel1 through rel5.