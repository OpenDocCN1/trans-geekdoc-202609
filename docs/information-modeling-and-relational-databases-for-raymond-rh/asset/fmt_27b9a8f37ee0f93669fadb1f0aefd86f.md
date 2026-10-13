
# Column-Oriented Database Systems

Several column-oriented database systems are available, including the following:

- **Amazon Redshift** has excellent integration with other AWS products. It provides dynamic scaling and automates many system management activities.
- Several open-source systems are available.
- **PostgreSQL** is a well-known row-based database, but it also has a column store option that is useful when you want to use only one database for both column and row store.
- **MariaDB** is another popular open-source database that supports both row and column storage.
- **Apache Cassandra** is a column-oriented database designed to handle large amounts of data across many commodity servers.

[Fig. 17.6](#Ch017_875-933_B9780443237904000050.xhtml#f0035) shows a simple example. This does not represent any specific database product; it’s intended only to illustrate the concept. Assume that we have information about individuals and their dietary preferences. A relational table might look something like the following (with empty cells corresponding to `NULL` in relational terminology).

![Fig. 17.6 Dietary data.](images/B9780443237904000050/f17-06-9780443237904.jpg)

[Fig. 17.6](#Ch017_875-933_B9780443237904000050.xhtml#B-f0035) Dietary data.

If we imagine this serialized into physical storage, it might look something like the following:

```
1, Alice, glutenfree, 68, 2, Bob, NULL, 92, 3, Clare, NULL, NULL, 4, Dave, vegan, 66, 5, Edna, NULL, 78
```

[Fig. 17.7](#Ch017_875-933_B9780443237904000050.xhtml#f0040) shows how the same information might look in a column-oriented database, assuming explicit identifiers.

![Fig. 17.7 Column-oriented dietary data.](images/B9780443237904000050/f17-07-9780443237904.jpg)

[Fig. 17.7](#Ch017_875-933_B9780443237904000050.xhtml#B-f0040) Column-oriented dietary data.

The example in [Fig. 17.7](#Ch017_875-933_B9780443237904000050.xhtml#f0040) is laid out in separate tabular form for comparison with the relational version, but it is also possible to visualize the name, diet, and weight “tables” as rows in a column-oriented database, as shown in [Fig. 17.8](#Ch017_875-933_B9780443237904000050.xhtml#f0045). From this perspective, it’s possible to see that rows in this representation can contain a variable number of columns.

![Fig. 17.8 Dietary data expressed in row form.](images/B9780443237904000050/f17-08-9780443237904.jpg)

[Fig. 17.8](#Ch017_875-933_B9780443237904000050.xhtml#B-f0045) Dietary data expressed in row form.

In this case, serializing the data into physical storage might look something like the following:

```
1, Alice, 2, Bob, 3, Clare, 4, Dave, 5, Edna, 1, glutenfree, 4, vegan, 1, 68, 2, 92, 4, 66, 5, 78
```

At this simple level, we can’t see the specific detail of the data layout in persistent storage. This depends very much on the specific database being considered. Even so, it’s obvious that in one case, a retrieval will find colocated information for an entity and the other will find colocated information for an attribute. Another way of saying this might be that row-oriented retrieval gets values for the attributes of an entity, but column-oriented retrieval gets values for the entities of an attribute.

Consider a query to find the average person’s weight from this information. The relational case would require the retrieval of each row and the weight column value within the row before calculating the average value. In the column-oriented case, we simply need to retrieve the weight row in the table shown in [Fig. 17.8](#Ch017_875-933_B9780443237904000050.xhtml#f0045) to get all the necessary values for the calculation. Because data retrieval from persistent storage is the most time-consuming part of the operation, this shows that the column-oriented approach has the potential for much better performance on certain types of queries. Performance is probably the greatest single motivator for this type of database, especially as the database becomes larger. In a column-oriented database, increasing amounts of data result in rows becoming bigger, not a bigger number of rows, so these are sometimes referred to as “wide tables”.

It’s important to remember that the distinctive feature of a column-oriented database is the way that the information is stored physically. From a conceptual viewpoint, we could still think of the database in the traditional manner, but we would find some types of operation more efficient and others less efficient than in a standard normalized relational database. In some cases, column-oriented databases can be queried using standard `SQL`, making the “NoSQL” label a little bit pointless.

The advantages of column orientation are only valid if queries operate on one column or a small number of columns. Queries involving several columns get less benefit from the localization of information from a single column. If multiple columns are frequently used together, it’s possible to add another level of organization by grouping columns into **column families**. For example, columns related to individual customer details (such as name, address, date of birth, etc.) could be grouped into a “Personal” column family. This can be used to ensure that the relevant columns are colocated in the database.

Column orientation provides additional opportunities for efficient storage of information. All the data from one row-oriented column (visualized as a row in a column-oriented database) is of the same type, opening possibilities for applying various types of compression to the values. An obvious instance of this is when the column contains many duplicate entries such as URLs or product names. In some cases, it may be possible to compress a column sufficiently to fit in memory for direct access, dramatically improving response time. Compression is useful because column-oriented databases are often used with very large datasets. There is also no need to allow for `NULL`s. An empty cell in a row-oriented database simply does not need to exist in its column-oriented equivalent.

The design of a column-oriented schema needs to consider not only the information to be stored but also how the database will be used and how it might evolve in the future. Adding a new column to the database is very easy–it can just be appended to the existing columns without impacting any existing queries. Other types of schema changes may be more problematic. Changes to query patterns can also reduce the effectiveness of the database if its design has been optimized for an anticipated scenario that no longer applies. It is also more difficult to design effective indexing schemes in the column-oriented case.

Column-oriented databases are very much skewed toward improving the efficiency of read operations (`select` in `SQL`). Operations such as `insert` (a new entity), `update` (an attribute of an existing entity), and `delete` (an existing entity) are generally slower because of the way the information is spread in physical storage. Also, read operations are improved only for certain types of queries. Consider the following two `SQL` queries:

```
select avg(weight) from Person
select * from Person
```

In a column-oriented database, the first of these will be faster but the second will be slower than the row-oriented equivalent (obviously, the differences will only be meaningful in large datasets). Generally, row-oriented operations or those involving many columns will be slower in a column-oriented database, making them unattractive for transactional applications.
