| Advantages | Disadvantages |
|---|---|
| **Promotes data consistency**<br>Eliminating data redundancy and defining clear relationships promotes data consistency. | **Difficulty in balancing normalization**<br>When normalizing a database, you need to aim for a balance between reducing data redundancy and maintaining performance. Over-normalization (too many tables and relationships) or under-normalization (failing to separate data appropriately) may lead to maintenance issues and low performance. |
| **Simplifies database maintenance**<br>Changes can be made to a single table without affecting other tables. | **Overheads in updates**<br>Updating records may require changing data in different places, which can reduce performance or increase the complexity of update operations. |

Denormalization: deliberately allowing for data redundancy in a database design to improve the performance of queries.

# Denormalization

Denormalization refers to deliberately allowing for data redundancy in a database design to improve the performance of queries.

| Advantages | Disadvantages |
|---|---|
| **Improved query performance**<br>There is less need for joins; the simpler structure of the tables improves the performance of read-heavy queries. | **Data redundancy**<br>There is the possibility of inconsistencies if updates are not properly managed; it is more challenging to synchronize and maintain the data. |
| **Simplified data retrieval**<br>Data is stored closer to the way it is accessed by applications so it allows for faster retrieval of data as there are less complex joins between tables. | **Increased storage overhead**<br>Redundant data requires additional storage space, which can become significant in large or evolving systems. |
| **Enhanced scalability**<br>This reduces the overhead of maintaining complex relationships, so it supports larger data sets and higher transaction volumes without sacrificing performance. | **Maintenance challenges**<br>Managing denormalized databases requires careful planning and maintenance to ensure data integrity and consistency. |

There are situations where denormalization can enhance performance, especially when read performance is crucial and outweighs concerns about data redundancy and updates complexity. Some specific scenarios are as follows:

# Read-intensive applications

Read-intensive applications refer to applications in which the focus is on retrieving data, rather than updating it. By reducing the number of tables, relationships and joins, data can be accessed faster, improving query performance and response time.

# Reporting and analytics

Reporting and analytics are used when generating complex reports or analysing large sets of data. Reducing the number of tables, simplifying relationships and decreasing the need for joins speeds up reporting and analytics queries.

# Data warehousing

In data warehousing, the focus is on storing and analysing historical data from different sources. Simplifying complex queries across different data sources and using fewer tables to organize related data improves query performance and response time.

Denormalization simplifies query structures by reducing the need for joins between tables. Simpler queries are easier to write, faster to execute, easier to understand and easier to maintain. On the other side, allowing for data redundancy means increased storage