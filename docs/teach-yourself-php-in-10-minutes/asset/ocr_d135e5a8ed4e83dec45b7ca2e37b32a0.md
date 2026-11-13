# # Database Portability Issues

By using database abstraction, you can write database-driven code that should be able to work with a multitude of back ends, simply by changing the DSN used to connect to the database.

However, not all database systems are the same, so you need to consider the design of database tables and SQL statements in order to make sure that your code is as widely supported as possible.

The most important consideration is to make sure that your SQL is written for the lowest common subset of the SQL language available to all the database back ends you want to be compatible with. For example, SQL that contains subqueries will not work with MySQL 4.0 or earlier. Similarly, you should avoid SQL commands that are specific to certain database systems, such as LIMIT or CREATE SEQUENCE .

# # Portability Modes

The DB class includes some portability mode settings that can ease the transition from one database back end to another. These modes are indicated by a series of constants, shown in Table 20.3 , that you can set by using the setOption method with the required options, combined with a logical OR operator. The following statement shows an example:

```
```php
$db->setOption('portability',
   DB_PORTABILITY_ERRORS | DB_PORTABILITY_NUMROWS );
```
```

# ## Table 20.3. Portability Mode Constants

| Constant | Mode |
| :--- | :--- |
| DB_PORTABILITY_ALL | Turns on all portability features |
| DB_PORTABILITY_NONE | Turns off all portability features |
| DB_PORTABILITY_DELETE_COUNT | Forces a count to take place in a DELETE statement with no WHERE clause, with WHERE 1=1 appended to the statement |
| DB_PORTABILITY_ERRORS | Increases consistency of error reporting between different database systems |
| DB_PORTABILITY_LOWERCASE | Forces conversion of names of tables and columns to lowercase |
| DB_PORTABILITY_NULL_TO_EMPTY | Converts fetched NULL values to empty strings; some databases do not distinguish these |