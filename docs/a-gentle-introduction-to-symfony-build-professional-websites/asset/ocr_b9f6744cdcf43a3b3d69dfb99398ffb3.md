# Listing 8-13 - Retrieving Records by Criteria with doSelect()—Criteria with Conditions

```
```php
$c = new Criteria();
$c->add(CommentPeer::AUTHOR, 'Steve');
$c->addAscendingOrderByColumn(CommentPeer::CREATED_AT);
$comments = CommentPeer::doSelect($c);

// Will result in the following SQL query
SELECT blog_comment.ARTICLE_ID, blog_comment.AUTHOR, blog_comment.CONTENT,
    blog_comment.CREATED_AT
FROM   blog_comment
WHERE  blog_comment.author = 'Steve'
ORDER BY blog_comment.CREATED_AT ASC;
```
```

The class constants passed as parameters to the add() methods refer to the property names. They are named after the capitalized version of the column names. For instance, to address the content column of the blog_article table, use the ArticlePeer::CONTENT class constant.

> > Why use CommentPeer::AUTHOR instead of blog_comment.AUTHOR, which is the way it will be output in the SQL query anyway? Suppose that you need to change the name of the author field to contributor in the database. If you used blog_comment.AUTHOR, you would have to change it in every call to the model. On the other hand, by using CommentPeer::AUTHOR, you simply need to change the column name in the schema.yml file, keep phpName as AUTHOR, and rebuild the model.

Table 8-1 compares the SQL syntax with the Criteria object syntax.

# Table 8-1 - SQL and Criteria Object Syntax

| SQL | Criteria |
| --- | --- |
| WHERE column = value | ->add(column, value); |
| WHERE column <> value | ->add(column, value, Criteria::NOT_EQUAL); |
| **Other Comparison Operators** | |
| > , < | Criteria::GREATER_THAN, Criteria::LESS_THAN |
| >=, <= | Criteria::GREATER_EQUAL, Criteria::LESS_EQUAL |
| IS NULL, IS NOT NULL | Criteria::ISNULL, Criteria::ISNOTNULL |
| LIKE, ILIKE | Criteria::LIKE, Criteria::ILIKE |
| IN, NOT IN | Criteria::IN, Criteria::NOT_IN |
| **Other SQL Keywords** | |
| ORDER BY column ASC | ->addAscendingOrderByColumn(column); |
| ORDER BY column DESC | - |
| | ->addDescendingOrderByColumn(column); |
| LIMIT limit | ->setLimit(limit) |
| OFFSET offset | ->setOffset(offset) |
| FROM table1, table2 WHERE table1.coll = table2.col2 | ->addJoin(coll, col2) |