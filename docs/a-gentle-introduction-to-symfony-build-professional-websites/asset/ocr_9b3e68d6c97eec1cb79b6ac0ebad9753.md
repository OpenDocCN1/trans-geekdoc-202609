Even after calling the delete() method, an object remains available until the end of the request. To determine if an object is deleted in the database, call the isDeleted() method.

# ## Retrieving Records by Primary Key

If you know the primary key of a particular record, use the retrieveByPk() class method of the peer class to get the related object.

```
$article = ArticlePeer::retrieveByPk(7);
```

The schema.yml file defines the id field as the primary key of the blog_article table, so this statement will actually return the article that has id 7. As you used the primary key, you know that only one record will be returned; the $article variable contains an object of class Article.

In some cases, a primary key may consist of more than one column. In those cases, the retrieveByPk() method accepts multiple parameters, one for each primary key column.

You can also select multiple objects based on their primary keys, by calling the generated retrieveByPks() method, which expects an array of primary keys as a parameter.

# ## Retrieving Records with Criteria

When you want to retrieve more than one record, you need to call the doSelect() method of the peer class corresponding to the objects you want to retrieve. For instance, to retrieve objects of class Article, call ArticlePeer::doSelect().

The first parameter of the doSelect() method is an object of class Criteria, which is a simple query definition class defined without SQL for the sake of database abstraction.

An empty Criteria returns all the objects of the class. For instance, the code shown in Listing 8-12 retrieves all the articles.

# Listing 8-12 - Retrieving Records by Criteria with doSelect()—Empty Criteria

```
$c = new Criteria();
$articles = ArticlePeer::doSelect($c);
```

```
// Will result in the following SQL query
SELECT blog_article.ID, blog_article.TITLE, blog_article.CONTENT,
       blog_article.CREATED_AT
FROM   blog_article;
```

### Hydrating

The call to ::doSelect() is actually much more powerful than a simple SQL query. First, the SQL is optimized for the DBMS you choose. Second, any value passed to the Criteria is escaped before being integrated into the SQL code, which prevents SQL injection risks. Third, the method returns an array of objects, rather than a result set. The ORM automatically creates and populates objects based on the database result set. This process is called hydrating.

For a more complex object selection, you need an equivalent of the WHERE, ORDER BY, GROUP BY, and other SQL statements. The Criteria object has methods and parameters for all these conditions. For example, to get all comments written by Steve, ordered by date, build a Criteria as shown in Listing 8-13.