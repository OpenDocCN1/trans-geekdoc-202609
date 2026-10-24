
spans multiple versions of a database schema, due to the evolutionary process of an organization. OLAP systems also deal with information that originates from different organizations, integrating information from many data stores.

- Access patterns: The access patterns of an OLTP system consist mainly of short, atomic transactions, such as transferring an amount from one account to another. Such a system requires concurrency control and recovery mechanisms. However, accesses to OLAP systems are mostly read-only operations (because most data warehouses store historic rather than up-to-date information). Many accesses may be complex queries.

"Why not perform OLAP directly on operational databases instead of constructing a separate data warehouse?" A major reason for a separation is to ensure the high performance of both systems. An operational database is designed and tuned from known tasks and workloads like indexing and hashing using primary keys, searching for particular records, and optimizing "canned" queries, which are pre-programmed and frequently used queries in business. OLAP queries, however, are often complex. They involve the computation of large data groups at summarized levels and may require the use of special data organization, access, and implementation methods based on multidimensional views. Processing OLAP queries directly in operational databases may substantially jeopardize the performance of operational tasks. An operational database supports the concurrent processing of multiple transactions. Concurrency control and recovery mechanisms (e.g., locking and logging) are required to ensure the consistency and robustness of transactions. An OLAP query often needs read-only access of massive data records for summarization and aggregation. Concurrency control and recovery mechanisms, if applied for such OLAP operations, may seriously delay the execution of concurrent transactions and thus substantially reduce the throughput of an OLTP system.

Finally, the separation of operational databases from data warehouses is based on the different structures, contents, and uses of the data in these two kinds of systems. Decision support requires historic data, whereas operational databases do not typically maintain historic data. In this context, the data in operational databases is usually far from complete for decision making. Decision support requires consolidation (e.g., aggregation and summarization) of data from heterogeneous sources, resulting in high-quality, clean, and integrated data. In contrast, operational databases contain only detailed raw data, such as transactions, which need to be consolidated before analysis. Because the two systems provide quite different functionalities and require different kinds of data, it is presently necessary to maintain separate databases.

## 3.1.2 Architecture of data warehouses: enterprise data warehouses and data marts

"What does the architecture of a data warehouse look like?" To answer this question, we first introduce the general three-tier architecture of data warehouses and then discuss two major data warehouse models: the enterprise warehouse and the data mart.

### The three-tier architecture

Data warehouses often adopt a three-tier architecture, as shown in Fig. 3.1.

The bottom level is a warehouse database server that is typically a main-stream database system, such as a relational database or a key-value store. Back-end tools and data extraction/transformation/loading (ETL) utilities are used to feed data into the bottom tier from operational databases or

![](img/90c930779c8f928df6ff4481fc59f9a3_119_0.png)

FIGURE 3.1
A three-tier data warehousing architecture.

other external sources (e.g., customer profile information provided by external partners). These tools and utilities perform data extraction, cleaning, and transformation, as well as load and refresh functions to update the data warehouse. This tier also contains a metadata repository, which stores information about the data warehouse and its contents.

The middle tier is an OLAP server that is typically implemented using either a relational OLAP (ROLAP) model (i.e., an extended relational DBMS that maps operations on multidimensional data to standard relational operations) or a multidimensional OLAP (MOLAP) model (i.e., a special-purpose server that directly implements multidimensional data and operations). We will discuss OLAP servers in detail soon.

The top tier is a **front-end client layer**, which contains tools for querying, reporting, visualization, analysis, and/or data mining, such as trend analysis and prediction.

"What are metadata in a warehouse database server?" **Metadata** are data about data. When used in a data warehouse, metadata are the data that defines warehouse objects. Metadata are created for the data names and definitions of the given warehouse. Additional metadata may be created and captured for timestamping any extracted data, the source of the extracted data, and missing fields that have been added by data cleaning or integration processes.

In addition, a metadata repository may contain a description of the *data warehouse structure* (e.g., the schema, view, dimensions, derived data definition, etc.), *operational metadata* (e.g., data transformation lineage, freshness of data), definitions of data summarization, mapping from operational data to the data warehouse, system information, and related business information.

Metadata play a very different role than other data warehouse data and are important for many reasons. For example, metadata are used as a directory to help analysts locate the contents of a data warehouse and as a guide to data mapping when data are transformed from the operational environment to the data warehouse environment. Metadata also serve as a guide to the algorithms used for summarization between the current detailed data and the lightly summarized data and between the lightly summarized data and the highly summarized data. Metadata should be stored and managed persistently (i.e., on disk).

Data warehouse systems use back-end tools and utilities to populate and refresh their data (Fig. 3.1). These tools and utilities include the functions of **data extraction** (gathering data from multiple, heterogeneous, and external sources), **data cleaning** (detecting errors in data and rectifying them when possible), **data transformation** (converting data from legacy or host format to warehouse format), **loading** (sorting, summarizing, consolidating, computing views, checking integrity, and building indices and partitions), and **refreshing** (propagating the updates from the data sources to the warehouse). In addition, data warehouse systems usually provide a good set of data warehouse management tools.

### ETL for data warehouses

In order to load and periodically refresh contents in data warehouses, typically data warehousing systems implement some ETL modules. We discuss the essential techniques and methods for data extraction, transformation, and loading in Chapter 2, which serve data warehousing, too. Here, we briefly introduce some major tasks of ETL for data warehouses.

### Data extraction

A data extraction process extracts data from external sources and is often the most important aspect of ETL. For example, a data warehouse may need to extract transaction data from an OLTP database and also user review data from social media repository. To encapsulate the details of various data sources, *wrappers* are often developed and deployed, which interact with data sources and supply extracted data to the ETL module. Due to the diversity and dynamics of data sources, manually developing wrappers is often inefficient and ineffective in quality. Recently, more and more wrappers are data driven and can automatically adapt to changes of data sources, such as changes in schema, update frequency, layout, and encoding. For example, a wrapper for an OLTP database can monitor and adapt to schema updates. A wrapper for a social media can crawl data from the social media and extract key fields from text, such as product name and sentiment of user review. Moreover, the wrapper may also be able to adapt to changes in social media layouts and remain robust against spamming.
