
- Pass the buffer content to the ob_gzhandler() function
- ob_gzhandler() will try to determine if the browser accepts gzip encoding by looking at the headers the browser has sent with its request
- If gzip data is accepted then the buffer is compressed and a content type gzip header is generated to be outputted to the browser
- The compressed data and the header are sent to the browser

You can find a really huge improvement in performance, and a reduction in bandwidth costs by using compressed output. To use compressed output:

```
ob_start('ob_gzhandler');
```

The browser will receive gzip compressed output.

We can also set the ob_gzhandler() function as the default callback function for ob_start() by setting the following in the php.ini file:

```
output_handler = 'ob_gzhandler'
```

> The ob_gzhandler() callback function can be used only with PHP 4.0.5 or later. Previous PHP versions have a huge memory leak bug in the ob_gzhandler() function.

If you experience problems outputting gzipped content, use the vary HTTP header. Also, avoid using gzipped content for the output of a POST request, as some browsers are known to have problems with this.

## Database Optimizations

This is probably the main source of optimization problems. As scripts normally use most of their execution time doing database operations, we'll look at several ways to improve database performance, and examine and evaluate how well our scripts query the database.

We'll use MySQL as our sample database but the concepts can be extended easily to PostgreSQL, Oracle, and other databases.

### Analyzing Queries

Once we find the queries responsible for the lack of speed we'll have to analyze each query to see what's wrong. First, check if we are attempting a very big join operation that is not necessary, and check if there's some other way to write the query faster. Two queries are usually faster than a join of two big tables.

### How to Evaluate a Query

When a well written query is taking a lot of time, use the MySQL EXPLAIN command to check how MySQL is processing the query. The syntax is:

```
EXPLAIN SELECT ..... FROM ..... WHERE.....
```

In short, just add EXPLAIN before the SELECT statement. MySQL will evaluate the query and return a table with columns indicating how the query would be processed, the returned information is:

- **table**
  The table to which the row of output refers.

- **type**
  The join type being used. Information about different join types is covered in the *Join Types* section.

- **possible_keys**
  This column indicates which indices could be used by MySQL to perform the query. If this column is empty then there're no relevant indices. In this case we can usually improve the query performance by taking a look at the WHERE clause and see if there are columns that can be indexed.

- **key**
  This column indicates the index that MySQL has selected to be used in this query, if *key* is *NULL* then no index will be used. If MySQL chooses the wrong index we'll have to force the use of an index by using the *USE INDEX/IGNORE INDEX* syntax in our query.

- **key_len**
  *key_len* indicates the length of the key that MySQL has decided to use.

- **ref**
  This indicates which columns or constants are used with the key to select rows from the table.

- **rows**
  This shows the number of rows MySQL believes must be examined to select rows from the table.

- **Extra**
  Additional information about the way in which the MySQL engine will resolve the query. Text in this column can be as follows:

- **Distinct**
  MySQL will not continue searching for the current row combination after it has found the first matching row.

- **Not exists**
  MySQL was able to do a *LEFT JOIN* optimization on the query, and will not examine more rows in this table for a row combination after it finds one row that matches the *LEFT JOIN* criteria.

- **Using filesort**
  MySQL will need to do an extra pass to find out how to retrieve the rows in sorted order. The sort is done by going through all rows according to the join type and storing the "sort key + pointer" to the row for all rows that match the *WHERE* clause. The keys are then sorted, before the rows are retrieved in sorted order.

- **Using index**
  The column information is retrieved from the table using only information in the index tree, without having to do an additional seek to read the actual row. This can be done when all the used columns for the table are part of the same index.

- **Using temporary**
  MySQL will need to create a temporary table to hold the result. This happens when we use an ORDER BY clause on a different column to that set by a GROUP BY being used in the same query.

To get our queries as fast as possible, look out for Using filesort and Using temporary. If we find one of these then we will need to optimize our query.

### JOIN Types

The different join types are listed below ordered from best to worst type:

- **system**
  The table has only one row. System joins are uncommon (tables usually have more than one row) and are the fastest since there is only one row to examine.

- **eq_ref**
  One row will be read from this table for each combination of rows from the previous tables. This is the best possible join type other than the system type. It is used when all parts of an index are used by the join and the index is UNIQUE or a primary key.

- **ref**
  All rows with matching index values will be read from this table for each combination of rows from the previous tables. ref is set if the join uses only a leftmost prefix of the key, or if the key is not a UNIQUE or PRIMARY KEY. If the key that is used matches only a few rows, this join type is good.

- **range**
  Only rows that are in a given range will be retrieved using an index to select the rows. The key column indicates which index is used.

- **ALL**
  A full table scan will be done for each combination of rows from the previous tables. This is normally not good if the table is the first table and usually very bad in all other cases. Normally we can avoid ALL by adding more indices so that the row can be retrieved based on constant values or column values from earlier tables.

- **index**
  This is the same as ALL except that only the index tree is scanned. This is usually faster than ALL, as the index file is usually smaller than the data file.

We can get a good indication of how good a join is by multiplying all values in the rows column of the EXPLAIN output. This should tell us roughly how many rows MySQL must examine to execute the query.

The following example from the MySQL documentation shows how a join can be optimized progressively using the information provided by the EXPLAIN command. Here we use an imaginary database with some sample fields, so we can ignore the name of tables, databases, and fields. The purpose of the sample is to analyze how to read the output of EXPLAIN.

We use EXPLAIN to examine the SELECT statement:

```
EXPLAIN SELECT tt.TicketNumber, tt.TimeIn,
tt.ProjectReference, tt.EstimatedShipDate,
tt.ActualShipDate, tt.ClientID,
tt.ServiceCodes, tt.RepetitiveID,
tt.CurrentPProcess, tt.CurrentDPPerson,
tt.RecordVolume, tt.DPPrinted, et.COUNTRY,
et_1.COUNTRY, do.CUSTNAME
FROM tt,et,et AS et_1
WHERE
tt.SubmitTime IS NULL
AND tt.ActualPC = et.EMPLOYID
AND tt.AssignedPC = et_1.EMPLOYID
AND tt.ClientID = do.CUSTNMBR;
```

Assume that the columns being compared have been declared as follows:

| Table | Column | Column Type |
| --- | --- | --- |
| tt | ActualPC | CHAR(10) |
| tt | AssignedPC | CHAR(10) |
| tt | ClientID | CHAR(10) |
| et | EMPLOYID | CHAR(15) |
| do | CUSTNMBR | CHAR(15) |

and that the tables have the indices shown below:

| Table | Index |
| --- | --- |
| tt | ActualPC |
| tt | AssignedPC |
| tt | ClientID |
| et | EMPLOYID (primary key) |
| do | CUSTNMBR (primary key) |

The tt.ActualPC values aren’t evenly distributed.

Initially, before any optimizations have been performed, the EXPLAIN statement produces the following information:

| Table | Type | Possible Keys | Key | Key Length | Ref | Rows |
| --- | --- | --- | --- | --- | --- | --- |
| et | ALL | PRIMARY | NULL | NULL | NULL | 74 |
| do | ALL | PRIMARY | NULL | NULL | NULL | 2135 |
| et_1 | ALL | PRIMARY | NULL | NULL | NULL | 74 |
| tt | ALL | AssignedPC, ClientID, ActualPC | NULL | NULL | NULL | 3872 |
