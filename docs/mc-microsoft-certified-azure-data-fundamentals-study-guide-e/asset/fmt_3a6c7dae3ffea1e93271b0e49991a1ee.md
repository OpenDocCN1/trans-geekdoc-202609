
[FIGURE 3.4](#c03.xhtml#R_c03-fig-0004) Graph database

Graph databases are optimal for solutions that ask questions such as “Find all employees that report directly to the CEO.” Applications querying large graphs with lots of nodes and edges, such as social media networks, can perform complex analyses very quickly. While relational databases can be used to store the same data as a graph database, queries written for the graph database circumvent any join operations or subqueries that would need to be considered for the relational database.

Graph databases can be implemented in Azure using the Azure Cosmos DB Gremlin API.

## Azure Cosmos DB

`Azure Cosmos DB` is a multi-model PaaS NoSQL database management system. `Multi-model` means that organizations can use Azure Cosmos DB to build key-value, document, columnar, and graph data stores. The different categories are made available as database APIs, including the Table API, Core (SQL) API, API for MongoDB, Cassandra API, and Gremlin API. Users will have the option of choosing one of these APIs when deploying an instance of Azure Cosmos DB.

The highest level of management for Azure Cosmos DB is a database account. Currently, you are allowed to have up to 50 Azure Cosmos DB accounts in an Azure subscription, but that can be increased by submitting a support ticket in the Azure Portal. Each database account can have one or more databases (referred to as a keyspace when using the Azure Cosmos DB Cassandra API), that serve as the unit of management for a set of containers.

Containers are the fundamental unit of scalability for throughput and storage. It is at this level that data is partitioned and replicated across multiple regions. Users can also register stored procedures, user-defined functions, triggers, and merge procedures within a container. Containers are identified by different names depending on which type of NoSQL database is deployed. [Table 3.1](#c03.xhtml#c03-tbl-0001) lists the naming convention used by each Azure Cosmos DB API.

[TABLE 3.1](#c03.xhtml#R_c03-tbl-0001) Azure Cosmos DB API-specific names for containers

| API || Container Naming Convention |

| --- | --- |

| Table API || Table |

| --- | --- |

| Core (SQL) API || Container |

| Cassandra API || Table |

| API for MongoDB || Collection |

| Gremlin API || Graph |

Data stored in containers is automatically grouped into logical partitions based on a partition key and is distributed across physical partitions. A `partition key` is a designated data field that is used to efficiently group throughput and related data. Other than choosing an appropriate partition key, partition administration is handled internally by Azure Cosmos DB.

Individual data records stored in a database container are referred to as `items`. When Azure Cosmos DB partitions data, it groups items with the same partition key value into the same logical partition. Items are automatically indexed as they are added to a container. Indexing behavior can also be customized by configuring the indexing policy on the container. Like containers, items are referred to by different names depending on which type of NoSQL database is deployed. [Table 3.2](#c03.xhtml#c03-tbl-0002) lists the naming convention used by each Azure Cosmos DB API.

[TABLE 3.2](#c03.xhtml#R_c03-tbl-0002) Azure Cosmos DB API-specific names for items

| API || Item Naming Convention |

| --- | --- |

| Table API || Entity |

| --- | --- |

| Core (SQL) API || Item |

| Cassandra API || Row |

| API for MongoDB || Document |

| Gremlin API || Node or edge |

Azure Cosmos DB ensures that data is highly available, regardless of which API is being used. As a matter of fact, Azure Cosmos DB guarantees 99.99 percent high availability when deployed to a single region and 99.999 percent high availability when deployed to multiple regions. Reads and writes are also guaranteed within 10 milliseconds across regions wherever the data is being replicated to. The following sections focus on how to optimize performance and availability for Azure Cosmos DB before finishing with an overview of the different database APIs.

### High Availability

High availability is a foundational component of Azure Cosmos DB. `Global distribution` in Azure Cosmos DB allows users to easily replicate data to multiple regions by associating one or more additional regions to an Azure Cosmos DB account. Adding new regions can be done through the Azure Portal or programmatically.

New regions can be configured to be read-only or to allow both reads and writes. Read-only workloads such as those produced from reporting applications can be offloaded to the read-only replicas, resulting in better performance for these workloads and those performing write operations. It is recommended to configure at least two different regions to allow writes in case of regional failure. This guarantees that if the primary region goes down, then write operations will automatically be routed to another region.

In addition to global distribution, Azure Cosmos DB maintains four replicas of the data within each region. For example, if you define an Azure Cosmos DB account to use two regions, then eight copies of the data will be maintained. Data resiliency within regions can also be guaranteed by enabling availability zone support. Availability zones ensure that replicas are placed in different zones of a given region, protecting data from in-region zonal failures.

#### Consistency Levels

Distributed databases such as Azure Cosmos DB that manage multiple write copies across different regions requires a trade-off between data consistency, availability, and performance. Using a strong consistency model results in the most updated data being read by applications but can result in slower performance since data has to replicate and be committed to each associated region before an application is allowed to read data. While eventual consistency offers better performance, applications reading data are at risk of returning dirty data.

Azure Cosmos DB offers five well-defined `consistency levels` to balance the trade-off between consistency, availability, and performance. The following list describes each consistency level, starting with the strictest level of consistency and finishing with the most relaxed:

*   `Strong`—This consistency level guarantees that reads return the most recent version of data, regardless of what region an application is reading data from. There is a possibility of slower performance as application connections may experience delays until transactions are committed across every associated region.

*   `Bounded staleness`—With this consistency level, applications reading data from the same region that it was written to use strong consistency. For applications reading data from regions outside of where data was written, there is a set “staleness window” for data. This means that data is committed asynchronously to other associated regions in the Azure Cosmos DB account. The staleness window can be configured one of two ways: 

    *   The number of versions of a record

    *   A set time interval between writes Whenever either of these two limits is reached, connections are paused, and data is committed to the outside regions. Bounded staleness is a good choice for applications that require low write latency and guaranteed local consistency.

*   `Session`—This is the most widely used consistency level for single region and globally distributed accounts. It grants a session token to the application writing data and guarantees that it and any other application sharing the same session token see the most recent version of data. All other reads use eventual consistency.
