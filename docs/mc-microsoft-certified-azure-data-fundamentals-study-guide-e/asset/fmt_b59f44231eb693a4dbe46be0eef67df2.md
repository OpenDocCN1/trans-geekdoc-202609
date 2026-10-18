
## 2. Which of the following data storage options are appropriate for data scientists and analysts to use when analyzing business data?

1. Data warehouses
2. OLAP models
3. Enterprise data lakes
4. All of the above

## 3. What open-source technology provides ACID properties on data stored in ADLS?

1. Delta Lake
2. Parquet
3. Apache Spark
4. Hadoop

## 4. Which of the following services is not used in a batch processing workflow?

1. Azure Databricks
2. Azure Stream Analytics
3. Azure Synapse Analytics
4. Azure Data Factory

## 5. You are designing a data warehouse that will serve as the single source of truth for a venue management company. The data warehouse's data model will use a star schema so that it is optimized for reporting tools and analytical queries. Using this design pattern, what type of tables will store concession and retail sales metrics?

1. Dimension tables
2. Materialized views
3. Fact tables
4. Composite tables

## 6. You are designing a stream processing pipeline for an IoT workflow. The solution will use Apache Spark structured streaming to process the data, but it requires a highly scalable service to act as the real-time message ingestion engine. Which of the following Azure HDInsight cluster types is a viable option to ingest large volumes of streaming data?

1. Apache Hadoop
2. Apache Spark
3. Apache Kafka
4. Apache Storm

## 7. Which of the following statements about Azure Databricks is false?

1. Azure Databricks cannot read data from a real-time ingestion engine like Azure Event Hubs or Apache Kafka.
2. Administrators can leverage their existing Azure Active Directory infrastructure to manage user access control for Databricks-specific objects such as notebooks, clusters, and jobs.
3. Azure Databricks can read and write data from Azure data stores such as Azure Blob Storage, ADLS, Azure SQL Database, and Azure Synapse Analytics dedicated SQL pools.
4. When creating a Spark cluster in Azure Databricks, users can set a time period that Azure Databricks will use to automatically terminate the cluster when idle.

## 8. Which of the following components is not used when calculating the cost of an Azure Databricks cluster?

1. Azure VM price
2. Price of DBUs consumed
3. Azure Databricks workspace price
4. None of the above

## 9. You are deploying a new Azure Databricks workspace that will be used by data engineers and data scientists at your company. Clusters deployed to the workspace will need to be able to connect to Azure services that are assigned private endpoints. You are also required to configure Azure Databricks so that cluster nodes do not have public IP addresses. Which of the following options is the recommended solution for meeting the listed requirements?

1. Enable VNet injection on the workspace so that all cluster nodes run on one of your VNets. This will allow you to easily connect clusters to services using private endpoints. VNet injection uses all private IP addresses by default.
2. Enable VNet injection on the workspace so that all cluster nodes run on one of your VNets. This will allow you to easily connect clusters to services using private endpoints. Enable secure cluster connectivity to change the public subnet to private.
3. Enable VNet injection on the workspace so that all cluster nodes run on one of your VNets. This will allow you to easily connect clusters to services using private endpoints. Enable private link to change the public subnet to private.
4. Use VNet peering to peer the Databricks-managed VNet with the VNet that hosts the private endpoints you are connecting to. VVet injection uses all private IP addresses by default. Enable secure cluster connectivity to ensure that only private IP addresses are used.

## 10. Which of the following Git providers are supported by Azure Databricks?

1. Bitbucket
2. GitHub
3. Azure DevOps
4. All of the above

## 11. You are configuring an Azure Databricks cluster that will be used by several analysts and data scientists. Because users will be running interactive workloads sporadically, the cluster must be able to support concurrent requests. Which cluster mode should you define for this cluster?

1. Standard
2. High Concurrency
3. Single User
4. Interactive

## 12. Which of the following is not a component that can be manually created after an Azure Synapse Analytics workspace is deployed?

1. Serverless SQL pool
2. Dedicated SQL pool
3. Data Explorer pool
4. Apache Spark pool

## 13. You are designing a solution that will analyze operational data that is stored in an Azure Cosmos DB Core (SQL) API database. The solution must be near real time, but it must also minimize the impact on the performance of the operational data store. Which of the following options is the most appropriate for this scenario?

1. Enable Azure Synapse Link to synchronize your transactional data from Azure Cosmos DB to a column-oriented analytical data store and use an Azure Synapse Analytics serverless SQL pool to analyze the data.
2. Create an Azure Data Factory copy activity to copy the data from Azure Cosmos DB to an Azure Synapse Analytics dedicated SQL pool.
3. Create an Azure Data Factory copy activity to copy the data from Azure Cosmos DB to an Azure Synapse Analytics serverless SQL pool.
4. Enable Azure Synapse Link to synchronize your transactional data from Azure Cosmos DB to a column-oriented analytical data store and use an Azure Synapse Analytics data explorer pool to analyze the data.

## 14. How many additional Azure Synapse Analytics serverless SQL pools can be added to a single workspace?

1. 1
2. 10
3. 0
4. 5

## 15. You are the administrator for an Azure Synapse Analytics dedicated SQL pool. Table distribution and index design are optimized to meet the workload needs of the queries that are frequently executed against the database. You have recently been asked to improve the performance of a query that is run regularly. When enabled, which of the following features will immediately improve the query's performance by caching the results for later use?

1. Result set caching
2. Query store
3. Extended events
4. Clustered columnstore index

## 16. Which of the following is a common use case for an Azure Synapse Analytics serverless SQL pool?

1. Performing exploratory analysis of Azure Storage data with T-SQL queries
2. Creating a logical data warehouse that maintains an up-to-date view of data by providing a relational schema on top of raw data stored in Azure Storage without moving data
3. Transforming ADLS data with T-SQL and serving the transformed data to Power BI or a persistent data store like Azure SQL Database
4. All of the above

## 17. What T-SQL function allows you to read the content of files stored in Azure Storage with a serverless SQL pool?

1. OPENQUERY
2. OPENROWSET
3. OPENDATASOURCE
4. OPENEXTERNALDATA

## 18. Is the italicized portion of the following statement true, or does it need to be replaced with one of the other fragments that appear below? A *Serverless SQL pool* is an analytical data store that uses a scale-out architecture to distribute data processing across multiple nodes. It is optimized to serve large amounts of historical data very quickly to data analysts and BI applications and is typically used as the single source of truth for business insights.

1. Dedicated SQL pool
2. Data Explorer pool
3. Apache Spark pool
4. No change needed

## 19. What type of Azure Data Factory activity is used to manage the flow of a pipeline?

1. Data movement activity
2. Control activity
3. Data transformation activity
