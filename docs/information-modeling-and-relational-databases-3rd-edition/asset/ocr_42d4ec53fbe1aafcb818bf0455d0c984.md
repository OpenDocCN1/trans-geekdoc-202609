It’s important to remember that the distinctive feature of a column-oriented database
is the way that the information is stored physically. From a conceptual viewpoint, we
could still think of the database in the traditional manner, but we would find some types
of operation more efficient and others less efficient than in a standard normalized relational
database. In some cases, column-oriented databases can be queried using standard
SQL, making the “NoSQL” label a little bit pointless.

The advantages of column orientation are only valid if queries operate on one column
or a small number of columns. Queries involving several columns get less benefit from the
localization of information from a single column. If multiple columns are frequently used
together, it’s possible to add another level of organization by grouping columns into col-
umn families. For example, columns related to individual customer details (such as name,
address, date of birth, etc.) could be grouped into a “Personal” column family. This can be
used to ensure that the relevant columns are colocated in the database.

Column orientation provides additional opportunities for efficient storage of informa-
tion. All the data from one row-oriented column (visualized as a row in a column-
oriented database) is of the same type, opening possibilities for applying various types
of compression to the values. An obvious instance of this is when the column contains
many duplicate entries such as URLs or product names. In some cases, it may be possible
to compress a column sufficiently to fit in memory for direct access, dramatically impro-
ing response time. Compression is useful because column-oriented databases are
often used with very large datasets. There is also no need to allow for NULLs. An empty
cell in a row-oriented database simply does not need to exist in its column-oriented
equivalent.

The design of a column-oriented schema needs to consider not only the information to
be stored but also how the database will be used and how it might evolve in the future.
Adding a new column to the database is very easy—it can just be appended to the existing
columns without impacting any existing queries. Other types of schema changes may be
more problematic. Changes to query patterns can also reduce the effectiveness of the
database if its design has been optimized for an anticipated scenario that no longer
applies. It is also more difficult to design effective indexing schemes in the column-
oriented case.

Column-oriented databases are very much skewed toward improving the efficiency of
read operations (select in SQL). Operations such as insert (a new entity), update (an attri-
bute of an existing entity), and delete (an existing entity) are generally slower because of
the way the information is spread in physical storage. Also, read operations are improved
only for certain types of queries. Consider the following two SQL queries:

```
**select avg(weight) from Person**
**select * from Person**
```

In a column-oriented database, the first of these will be faster but the second will be
slower than the row-oriented equivalent (obviously, the differences will only be meaning-
ful in large datasets). Generally, row-oriented operations or those involving many columns