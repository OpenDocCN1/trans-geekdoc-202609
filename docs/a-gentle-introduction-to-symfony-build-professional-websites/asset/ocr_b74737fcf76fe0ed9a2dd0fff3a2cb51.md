be used for each query based on internal heuristics. Adding an index can sometimes be disappointing in terms of performance boost, so make sure you measure the improvements.

Unless specified otherwise, each request uses a single database connection in symfony, and the connection is closed at the end of the request. You can enable persistent database connections to use a pool of database connections that remain open between queries, by setting persistent: true in the databases.yml file, as shown in Listing 18-11.

# Listing 18-11 - Enabling Persistent Database Connection Support, in config/databases.yml

```
prod:
  propel:
    class: sfPropelDatabase
    param:
      dsn: mysql:dbname=example;host=localhost
      username: username
      password: password
      persistent: true # Use persistent connections
```

This may or may not improve the overall database performance, depending on numerous factors. The documentation on the subject is abundant on the Internet. Make sure you benchmark your application performance before and after changing this setting to validate its interest.

# MySQL-specific tips

Many settings of the MySQL configuration, found in the my.cnf file, may alter database performance. Make sure you read the online documentation 65 on this subject.

One of the tools provided by MySQL is the slow queries log. All SQL statements that take more than long_query_time seconds to execute (this is a setting that can be changed in the my.cnf) are logged in a file that is quite difficult to construe by hand, but that the mysqldumpslow command summarizes usefully. This is a great tool to detect the queries that require optimizations.

# Tweaking the View

According to how you design and implement the view layer, you may notice small slowdowns or speedups. This section describes the alternatives and their tradeoffs.

# Using the Fastest Code Fragment

If you don't use the caching system, you have to be aware that an include_component() is slightly slower than an include_partial(), which itself is slightly slower than a simple PHP include. This is because symfony instantiates a view to include a partial and an object of class sfComponent to include a component, which collectively add some minor overhead beyond what's required to include the file.

However, this overhead is insignificant, unless you include a lot of partials or components in a template. This may happen in lists or tables, and every time you call an include_partial() helper inside a foreach statement. When you notice that a large number of partial or component inclusions have a significant impact on your performance, you may consider

65. http://dev.mysql.com/doc/refman/5.0/en/option-files.html