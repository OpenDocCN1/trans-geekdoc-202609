Hardware is rarely the problem. Except in extreme cases (such as intense usage of Gd for graphics rendering, intense number crunching, or large reporting applications), the overhead imposed by PHP itself does not require significant system resources.

# # Tracking Down the Bottleneck

There are straightforward steps to resolving each different variety of identifiable bottleneck, as discussed in the remainder of this appendix. However, your first task is to determine where the bottleneck can be found and into which of the three categories described previously it falls.

# # Database Queries

The easiest offenders to track down are slow database queries. Almost all enterprise-class PHP applications depend on a database of some kind. This book has heavily advocated PostgreSQL, but many applications (particularly those you will encounter that are written by third parties) will make use of the more popular MySQL.

You must eliminate database bottlenecks before attempting to optimize code. Because most code is dependent on the database in some respect (even if only for the supply of data), looking at code before its data source is optimized is not time well spent.

The simplest way to determine whether database bottlenecks exist in a script is to temporarily adapt your database interaction code to add a timer method.

Consider the query method of your abstraction layer for PostgreSQL. By adding error log stamps before and after each query, you can show how long each query took and easily produce an analyzable log for your page. The following excerpt shows an example, demonstrating how you might measure the time taken to perform a query in the database abstraction layer by sandwiching the `execute query` statement as follows:

```
```php
$intTimeNow = microtime();
$q_handle = pg_exec($this->link_ident, $sql);
$intTimeTaken = microtime() - $intTimeNow;
error_log("DEBUG: QUERY: $sql\n");
error_log("DEBUG: TIME TAKEN: $intTimeTaken\n");
```
```

This will yield error log output similar to the following:

```
```
[Sun May 16 22:10:19 2004] [error] DEBUG: QUERY: SELECT id, logged_in, user_id FROM "user_sessions" WHERE session_id='98ce552be0a2ea6b6f69fbebcd14997c' AND user_agent='Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)' AND ip_address='192.168.4.3'
[Sun May 16 22:10:19 2004] [error] DEBUG: TIME TAKEN: 0.003752
```
```

Executing a typical PHP script with your database abstraction layer doctored as shown in the preceding example will then yield a series of `DEBUG: QUERY xx` and `DEBUG: TIME TAKEN` statements as shown.

The pattern of queries will be easier to analyze if you can ensure that no other warnings, error messages, or code-initiated debug statements are writing to the error log, and that the analysis of the time being taken by your query has exclusivity for now.