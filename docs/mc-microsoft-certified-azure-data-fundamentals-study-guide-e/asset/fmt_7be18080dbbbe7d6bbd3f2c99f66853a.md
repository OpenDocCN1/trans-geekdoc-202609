
### Data

The `Data` button opens a page that allows you to link external and integrated datasets to the Azure Synapse Analytics workspace. It has two tabs, the `Workspace` tab to organize any analytics pools that are associated with the workspace and the `Linked` tab to organize external storage such as ADLS or Azure Blob Storage. From this page, you can create new blank script pages or predefined scripts that run bulk load operations or select the top 100 rows of a table. [Figure 5.39](#c05.xhtml#c05-fig-0039) is an example of the Workspace tab and the external data source options that can be added by clicking the `+` button.

### Develop

The `Develop` button opens a page that organizes all SQL scripts, KQL scripts, notebooks, mapping data flows, and Apache Spark jobs. [Figure 5.40](#c05.xhtml#c05-fig-0040) is an example of the Develop page and the various objects that can be added by clicking the `+` button.

### Integrate

The `Integrate` button opens a page that allows you to build data orchestration and movement pipelines. You can create new pipelines or use the Copy Data tool to perform a one-time or scheduled data load from over 90 data sources. The functionality is similar to ADF, with some additional activities that are specific to Azure Synapse Analytics. [Figure 5.41](#c05.xhtml#c05-fig-0041) is an example of the Integrate page and the Synapse-specific activities.

![FIGURE 5.39 Synapse Studio Data page](images/c05f039.png)

[FIGURE 5.39](#c05.xhtml#R_c05-fig-0039) Synapse Studio Data page

![FIGURE 5.40 Synapse Studio Develop page](images/c05f040.png)

[FIGURE 5.40](#c05.xhtml#R_c05-fig-0040) Synapse Studio Develop page

![FIGURE 5.41 Synapse Studio Integrate page](images/c05f041.png)

[FIGURE 5.41](#c05.xhtml#R_c05-fig-0041) Synapse Studio Integrate page

### Monitor

The `Monitor` button opens a page that provides a comprehensive view of the performance details and statuses for the different analytics pools, activities, and integration pipelines. [Figure 5.42](#c05.xhtml#c05-fig-0042) is an example of the Monitor page with a focus on the SQL pools section.

![FIGURE 5.42 Synapse Studio Monitor page](images/c05f042.png)

[FIGURE 5.42](#c05.xhtml#R_c05-fig-0042) Synapse Studio Monitor page

### Manage

The `Manage` button opens the Manage page (see [Figure 5.43](#c05.xhtml#c05-fig-0043)). This page allows you to perform several management tasks:

* Create, configure, pause, and resume analytics pools.
* Create and delete linked services. Linked services provide the connection information to external data sources that are used in Synapse pipelines.
* Link an Azure Purview account to catalog metadata and data lineage.
* Create and delete triggers. A trigger is used to automate when a Synapse pipeline is executed. Types of triggers include schedules, storage events, and custom events.
* Create and delete integration runtimes. An integration runtime (`IR`) is the compute infrastructure used by Synapse pipelines.
* Manage all security access controls and credentials.
* Link a Git repository to your Azure Synapse Analytics workspace.

![FIGURE 5.43 Synapse Studio Manage page](images/c05f043.png)

[FIGURE 5.43](#c05.xhtml#R_c05-fig-0043) Synapse Studio Manage page

### Dedicated SQL Pools

Azure Synapse Analytics dedicated SQL pools (formerly Azure SQL Data Warehouse) are relational data stores that use a massively parallel processing (`MPP`) architecture to optimally manage large datasets. This can be done by separating compute and storage by using a SQL engine to perform computations and Azure Storage to store the data. Dedicated SQL pools use a relational schema, typically a star schema, to serve data to users as tables or views for business intelligence applications.

In a modern data warehouse architecture, a dedicated SQL pool is at the end of an ETL/ELT process, serving as the `single source of truth` for data analysts and BI applications. Tables using columnstore compression can store an unlimited amount of data, making dedicated SQL pools the ideal destination data store for big data workloads that process several terabytes or even petabytes worth of data. Additional processes can also extract subsets of data that represent specific business segments from a dedicated SQL pool and load them into Azure Analysis Services or Power BI OLAP models for self-service BI scenarios.

As mentioned in [Chapter 2](#c02.xhtml), dedicated SQL pools shard data into 60 distributions across one or more compute nodes depending on the dedicated SQL pool's service level objective (`SLO`). Tables can be defined with one of three distribution patterns to optimize how data is sharded throughout the distributions. The following list is a quick reminder of the three distribution patterns and when to use each one:

* `Hash distribution` uses a hash function to deterministically assign each row to a distribution. When defining a table with this distribution type, one of the columns is designated as the distribution column. This distribution type offers the most optimal query performance for joins and aggregations on large tables. For this reason, large fact tables are typically defined as hash distributed tables. However, keep in mind that the values of a column designated as the distribution column cannot be updated. The column must also have a high number of unique values and a low number of null values. Poorly chosen distribution columns can lead to unacceptable query response times that cannot be resolved without re-creating the table. Use round robin distribution instead of hash distribution if there are no suitable distribution columns for a large fact table.

* `Round robin distribution` evenly and randomly distributes rows across all 60 distributions. Staging tables and fact tables without a good distribution column candidate are typically defined as round robin tables.

* `Replicated tables` cache a full copy of a table on the first distribution of each compute node. This removes the need to shuffle data when querying data from multiple distributions. However, replicated tables can require extra storage, making them impractical for large tables or tables that are frequently written to. For this reason, only small tables (less than 2 GB) or tables that store static data (such as reference data) are defined as replicated tables.

Along with classic relational database features such as partitioning, row-store indexes, and statistics, dedicated SQL pools include several features that optimize the performance of analytical queries that aggregate large numbers of rows. These features are especially useful for querying historical data from fact tables, which can quickly become very large. Some of the most important features are as follows:

* `Clustered columnstore indexes` (`CCIs`) physically organize tables into a columnstore format. With a columnstore format, rows of data are compressed into `rowgroups`, optimizing how large tables are stored (up to 10X data compression versus uncompressed data) and the processing time for queries that perform table scans (up to 10X times the query performance over traditional row-oriented indexes). This is ideal for data warehouses, especially for large fact tables that are subject to analytical queries that scan large amounts of data.
