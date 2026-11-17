Symfony’s syntax for schemas uses the YAML format. The schema.yml files must be located in the myproject/config/ directory.

> Symfony also understands the Propel native XML schema format, as described in the “Beyond the schema.yml: The schema.xml” section later in this chapter.

# Schema Example

How do you translate a database structure into a schema? An example is the best way to understand it. Imagine that you have a blog database with two tables: blog_article and blog_comment, with the structure shown in Figure 8-1.

# Figure 8-1 - A blog database table structure

![](bbox=[0.114, 0.282, 0.462, 0.394])

The related schema.yml file should look like Listing 8-3.

# Listing 8-3 - Sample schema.yml

```
propel:
  blog_article:
    _attributes: { phpName: Article }
    id:
    title: varchar(255)
    content: longvarchar
    created_at: ~
  blog_comment:
    _attributes: { phpName: Comment }
    id: ~
    blog_article_id: ~
    author: varchar(255)
    content: longvarchar
    created_at: ~
```

Notice that the name of the database itself (blog) doesn’t appear in the schema.yml file. Instead, the database is described under a connection name (propel in this example). This is because the actual connection settings can depend on the environment in which your application runs. For instance, when you run your application in the development environment, you will access a development database (maybe blog_dev), but with the same schema as the production database. The connection settings will be specified in the databases.yml file, described in the “Database Connections” section later in this chapter. The schema doesn’t contain any detailed connection to settings, only a connection name, to maintain database abstraction.

# Basic Schema Syntax

In a schema.yml file, the first key represents a connection name. It can contain several tables, each having a set of columns. According to the YAML syntax, the keys end with a colon, and the structure is shown through indentation (one or more spaces, but no tabulations).