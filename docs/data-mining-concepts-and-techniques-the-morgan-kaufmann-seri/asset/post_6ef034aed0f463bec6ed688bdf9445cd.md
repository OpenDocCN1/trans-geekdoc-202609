
Such partially materialized cubes are known as **iceberg cubes**. The minimum threshold is called the **minimum support threshold**, or **minimum support** (*min_sup*), for short. By materializing only a fraction of the cells in a data cube, the result is seen as the “tip of the iceberg,” where the “iceberg” is the potential full cube including all cells. An iceberg cube can be specified using an SQL query, as shown in Example 3.11.

### Example 3.11. Iceberg cube. Consider the following iceberg cube query.

```
compute cube sales_iceberg as
select month, city, customer_group, count(*)
from salesInfo
cube by month, city, customer_group
having count(*) >= min_sup
```

The compute cube statement specifies the precomputation of the iceberg cube, *sales_iceberg*, with three dimensions, *month*, *city*, and *customer_group*, and the aggregate measure count(). The input tuples are in the *salesInfo* relation. The cube by clause specifies that aggregates (group-by’s) are to be formed for each of the possible subsets of the given dimensions. If we were computing the full cube, each group-by would correspond to a cuboid in the data cube lattice. The constraint specified in the having clause is known as the **iceberg condition**. Here, the iceberg measure is count(). Note that the iceberg cube computed here can be used to answer group-by queries on any combination of the specified dimensions of the form having count(*) >= *v*, where *v* >= *min_sup*. Instead of count(), the iceberg condition may specify more complex measures, such as average().

If we were to omit the having clause, we would end up with the full cube. Let us call this cube *sales_cube*. The iceberg cube, *sales_iceberg*, excludes all the cells of *sales_cube* with a count that is less than *min_sup*. Obviously, if we were to set the minimum support to 1 in *sales_iceberg*, the resulting cube would be the full cube, *sales_cube*.

A naïve approach to computing an iceberg cube would be to first compute the full cube and then prune the cells that do not satisfy the iceberg condition. However, this is still prohibitively expensive. An efficient approach is to compute only the iceberg cube directly without computing the full cube. Section 3.5.2 discusses methods for efficient iceberg cube computation.

Introducing iceberg cubes lessens the burden of computing trivial aggregate cells in a data cube. However, we may still end up with a large number of uninteresting cells to compute. For example, suppose that there are 2 base cells for a database of 100 dimensions, denoted as {(*a1, *a2, *a3, ..., *a100) : 10, (*a1, *a2, *b3, ..., *b100) : 10}, where each has a cell count of 10. If the minimum support is set to 10, there are still a billion impermissible number of cells to compute and store, although most of them are not interesting. For example, there are 2^101 – 6 distinct aggregate cells like {(*a1, *a2, *a3, *a4, ..., *a99, *) : 10, ..., (*a1, *a2, *, *a4, ..., *a99, *a100) : 10, ..., (*a1, *a2, *a3, *, ..., *, *) : 10}, but most of them do not contain much new information. If we ignore all the aggregate cells that can be obtained by replacing some constants with *’s while keeping the same measure value, there are only three distinct cells left: {(*a1, *a2, *a3, ..., *a100) : 10, (*a1, *a2, *b3, ..., *b100) : 10, (*a1, *a2, *, ..., *) : 20}. That is, out of 2^101 – 4 distinct base and aggregate cells, only three really offer valuable information.

![](img/90c930779c8f928df6ff4481fc59f9a3_147_0.png)

To systematically compress a data cube, we need to introduce the concept of *closed coverage*. The **coverage** of a cell c is the set of base cells that are descendants of c. The measure of c is computed by the base cells that are descendants of c. In other words, the measure of c is determined by the coverage of c. Clearly, if two cells c1 and c2 have the same coverage, they have same measure no matter what aggregate functions are used. Based on this observation, a cell, c, is a *closed cell* if there exists no cell, d, such that d is a descendant of c (i.e., d is obtained by replacing at least one * in c with a non-* value, and d has the same coverage as c). A **quotient cube** is a data cube consisting of only closed cells. For example, the three cells derived in the preceding paragraph are the three closed cells of the data cube for the data set {(a1, a2, a3, ..., a100) : 10, (a1, a2, b3, ..., b100) : 10}. They form the lattice of a closed cube as shown in Fig. 3.19. Other nonclosed cells can be derived from their corresponding closed cells in this lattice. For example, "(a1, *, *, ..., *) : 20" can be derived from "(a1, a2, *, ..., *) : 20" because the former is a generalized nonclosed cell of the latter. Similarly, we have "(a1, a2, b3, *, ..., *) : 10."

Another strategy for partial materialization is to precompute only the cuboids involving a small number of dimensions such as three to five. These cuboids form a **cube shell** for the corresponding data cube. Queries on additional combinations of the dimensions will have to be computed on-the-fly. For example, we could compute all cuboids with three dimensions or less in an n-dimensional data cube, resulting in a cube shell of size 3. This, however, can still result in a large number of cuboids to compute, particularly when n is large. Alternatively, we can choose to precompute only portions or *fragments* of the cube shell based on cuboids of interest. Section 3.5.3 discusses a method for computing **shell fragments** and explores how they can be used for efficient OLAP query processing.

## 3.4.3 OLAP server architectures: ROLAP vs. MOLAP vs. HOLAP

There are many methods for efficient data cube computation, based on the various kinds of cubes described earlier in this section. In general, there are two basic data structures used for storing cuboids. The implementation of relational OLAP (ROLAP) uses relational tables, whereas multidimensional arrays are used in multidimensional OLAP (MOLAP). In some situations, we may also combine ROLAP and MOLAP to obtain the hybrid OLAP (HOLAP) approach. Let us look at the details here.

Logically, OLAP servers present business users with multidimensional data from data warehouses or data marts, without concerns regarding how or where the data are stored. However, the physical architecture and implementation of OLAP servers must consider data storage issues. Implementations of a data warehouse server for OLAP processing may have the following options.

### Relational OLAP (ROLAP) servers

These are the intermediate servers that stand in between a relational back-end server and client front-end tools. They use a *relational* or *extended-relational DBMS* to store and manage warehouse data, and OLAP middleware to support missing pieces. ROLAP servers include optimization for each DBMS back end, implementation of aggregation navigation logic, and additional tools and services. ROLAP technology tends to have greater scalability than MOLAP technology.

### Multidimensional OLAP (MOLAP) servers

These servers support multidimensional data views through *array-based multidimensional storage engines*. They map multidimensional views directly to data cube array structures. The advantage of using a data cube is that it allows fast indexing to precomputed summarized data. Notice that with multidimensional data stores, the storage utilization may be low if the data set is sparse. In such cases, sparse matrix compression techniques should be explored.

Many MOLAP servers adopt a two-level storage representation to handle dense and sparse data sets: Denser subcubes are identified and stored as array structures, whereas sparse subcubes employ compression technology for efficient storage utilization.

### Hybrid OLAP (HOLAP) servers

The hybrid OLAP approach combines ROLAP and MOLAP technology, benefiting from the greater scalability of ROLAP and the faster computation of MOLAP. For example, a HOLAP server may allow large volumes of detailed data to be stored in a relational database, whereas aggregations are kept in a separate MOLAP store.

### Specialized SQL servers

To meet the growing demand of OLAP processing in relational databases, some database system vendors implement specialized SQL servers that provide advanced query language and query processing support for SQL queries over star and snowflake schemas in a read-only environment.

“How are data actually stored in ROLAP and MOLAP architectures?” Let’s first look at ROLAP. As its name implies, ROLAP uses relational tables to store data for online analytical processing. Recall that the fact table associated with a base cuboid is referred to as a *base fact table*. The base fact table stores data at the abstraction level indicated by the join keys in the schema for the given data cube. Aggregated data can also be stored in fact tables, referred to as **summary fact tables**. Some summary fact tables store both base fact table data and aggregated data. Alternatively, separate summary fact tables can be used for each abstraction level to store only aggregated data.

### Example 3.12. A ROLAP data store

Table 3.3 shows a summary fact table that contains both base fact data and aggregated data. The schema is “⟨*record_identifier (RID), item, ..., day, month, quarter, year, dollars_sold⟩,” where *day, month, quarter,* and *year* define the sales date, and *dollars_sold* is the sales amount. Consider the tuples with an *RID* of 1001 and 1002, respectively. The data of these tuples are at the base fact level, where the sales dates are October 15, 2010, and October 23, 2010, respectively. Consider the tuple with an *RID* of 5001. This tuple is at a more general level of abstraction than the tuples 1001 and 1002. The *day* value has been generalized to `all`, so that the corresponding *time* value is October 2010. That is, the *dollars_sold* amount shown is an aggregation representing the entire month of October 2010, rather than just October 15 or 23, 2010. The special value `all` is used to represent subtotals in summarized data.
