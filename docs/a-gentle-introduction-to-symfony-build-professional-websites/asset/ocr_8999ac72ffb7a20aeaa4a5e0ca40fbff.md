+   - pgsql
+   - sqlite
+   - oracle

hostspec, database, username, and password are the usual database connection settings.

To override the configuration per application, you need to edit an application-specific file,
such as apps/frontend/config/databases.yml.

If you use a SQLite database, the hostspec parameter must be set to the path of the
database file. For instance, if you keep your blog database in data/blog.db, the
databases.yml file will look like Listing 8-19.

# Listing 8-19 - Database Connection Settings for SQLite Use a File Path As Host

```
all:
  propel:
    class:  sfPropelDatabase
    param:
      phptype:  sqlite
      database: %SF_DATA_DIR%/blog.db
```

# Extending the Model

The generated model methods are great but often not sufficient. As soon as you implement
your own business logic, you need to extend it, either by adding new methods or by
overriding existing ones.

# Adding New Methods

You can add new methods to the empty model classes generated in the lib/model/
directory. Use $this to call methods of the current object, and use self:: to call static
methods of the current class. Remember that the custom classes inherit methods from the
Base classes located in the lib/model/om/ directory.

For instance, for the Article object generated based on Listing 8-3, you can add a magic
__toString() method so that echoing an object of class Article displays its title, as
shown in Listing 8-20.

# Listing 8-20 - Customizing the Model, in lib/model/Article.php

```
class Article extends BaseArticle
{
    public function __toString()
    {
        return $this->getTitle(); // getTitle() is inherited from BaseArticle
    }
}
```

You can also extend the peer classes—for instance, to add a method to retrieve all articles
ordered by creation date, as shown in Listing 8-21.

# Listing 8-21 - Customizing the Model, in lib/model/ArticlePeer.php

```
class ArticlePeer extends BaseArticlePeer
{
    public static function getAllOrderedByDate()
    {
        $c = new Criteria();
```