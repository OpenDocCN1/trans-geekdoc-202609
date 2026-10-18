
## 4. D. Azure Databricks Structured Streaming and Azure Stream Analytics can be used to create live and on-demand stream processing solutions. Both technologies can use data stored in Azure Blob Storage as reference data.

## 5. D. All of these options are nonrelational data stores. While Azure Blob Storage is not a database, it is still a nonrelational data store because of its ability to store nonrelational data such as binary, JSON, and Parquet files.

## 6. A. Azure Cosmos DB’s Gremlin API is the best choice for storing relationships between different department entities. While this can be accomplished with a relational model, graph databases such as the Azure Cosmos DB’s Gremlin API are better options since they do not require applications to perform complex queries with several join operations.

## 7. B. Azure Blob Storage is optimized for storing massive amounts of binary data such as images and can be accessed by several machine learning development platforms.

## 8. C. The `COPY` statement provides the most flexibility for high-throughput data loading from external storage accounts into Azure Synapse Analytics.

## 9. B. Azure Synapse Analytics dedicated SQL pool leverages scale-out architecture by distributing data and data processing to multiple nodes.

## 10. D. Batch processing is the practice of transforming groups of data at scheduled periods of time.

## 11. A. Azure Data Factory mapping data flows is a tool that allows data engineers to build data processing pipelines with a graphical user interface. Because there isn't any code involved, this solution is the easiest to maintain and has the least amount of operational overhead.

## 12. C. Diagnostic analytics answer questions about why things happened, and descriptive analytics answer questions about what has happened.

## 13. D. Matrices are useful infographics for clearly displaying numerical totals and subtotals over different groups of categories.

## 14. A. Analysts will need to be able to create and interact with reports as well as be able to pin the most relevant visualizations from those reports to dashboards for executives.

## 15. B. Line charts are useful for displaying how data has changed over time.

## 16. A. Cognitive analytics techniques can be used to build machine learning or deep learning models that power conversational bots. Each time they are queried, they become more accurate as these models are designed to learn from each interaction with data.

# Chapter 2: Relational Databases in Azure

## 1. B. While transactions with Read Committed isolation prevent other transactions from reading dirty data, they do not stop other transactions from modifying or inserting data. This can result in nonrepeatable or phantom reads.

## 2. C. The optimal method for storing data in an analytical system is to flatten data into a star schema. This allows business users to easily write queries that can read data without requiring complex joins.

## 3. A. Creating a nonclustered index on the column or columns that are included in the filter criteria for commonly used queries will increase their performance.

## 4. D. No change is needed as Azure SQL Managed Instance falls under the PaaS database options.

## 5. A. Azure SQL MI is ideal for lift-and-shift scenarios that require a quick migration time to Azure. SQL MI provides nearly 100 percent feature compatibility with SQL Server, all the while providing users with the benefits of a PaaS database.

## 6. B. Memory optimized virtual machines offer stronger memory-to-CPU ratios that are ideal for SQL Server workloads.

## 7. B. SQL Server Always On availability groups replicate specific user databases to other SQL Server instances for HADR purposes.

## 8. D. Virtual networks, or VNets for short, are fundamental building blocks to building an isolated network in Azure. Services such as SQL Server on Azure VM and Azure SQL MI can be added to VNets to limit application connectivity to applications that can connect to the VNet.

## 9. A. A network security group, or NSG for short, controls access to the SQL Managed Instance data endpoint by filtering traffic on port 1433 and ports 11000–11999 when SQL Managed Instance is configured for redirect connections. The NSG is associated to the subnet hosting the Azure SQL MI once it is created.

## 10. B. The Business Critical tier of Azure SQL MI automatically creates a SQL Server Always On availability group and multiple secondary nodes for HADR purposes. While these nodes are abstracted from the user, one of them is enabled to serve read-only workloads. This allows users to read data from the database without affecting the performance of the write operations.

## 11. C. The maximum number of user databases that can be deployed to a single Azure SQL MI is 100.

## 12. C. Private Link is a service in Azure that allow users to attach a private endpoint to PaaS offerings such as Azure SQL Database. A private endpoint is a private IP address in a specific subnet in a VNet.

## 13. B. Materialized views consist of aggregations performed on multiple tables, allowing analysts to use simple queries to build reports. Materialized views also compile and store aggregations as data is updated in the underlying tables, making them much faster than traditional views.

## 14. D. To take advantage of Azure Synapse Analytics dedicated SQL pool's scale-out design, data is sharded 60 distributions across one or more compute nodes.

## 15. B. Azure SQL MI manages database backups by taking full, differential, and transaction log backups at scheduled time periods. Database backups can be restored to another Azure SQL MI by using a point-in-time restore to specify what version of the database should be restored.

## 16. A. The vCore-based purchasing model for Azure SQL Database includes the following service tiers: General Purpose, Business Critical, Hyperscale. This purchasing model gives users the ability to choose the number of vCores, the amount of memory, and storage speed.

## 17. B. Azure Database for PostgreSQL is the only open-source PaaS database option that offers a Hyperscale deployment model for large OLTP workloads.

## 18. B. `Connect-AzAccount` is required to establish a connection with an Azure environment before resources can be managed.

## 19. C. Hash distribution is the best option for large fact tables and provides the best performance for joins and aggregations. This type of distribution distributes data by running a hash function on a column in a table that will deterministically assign each row of a table to a distribution.

## 20. D. `Microsoft.Sql/servers` manages the deployment configuration of a logical servers, while `Microsoft.Sql/servers/databases` manages the deployment configuration for each database associated with a logical server.

## 21. A. `New-AzSqlDatabase` is the Azure PowerShell command used to create a new Azure SQL Database.

## 22. B. The SQL DB Contributor role gives a user the ability to create and manage databases in Azure. While the Contributor role also allows the user to perform the same task, it grants more privileges than what are needed.

## 23. C. Always Encrypted is a feature in SQL Server and Azure SQL that encrypts sensitive table columns. It allows the client application to manage the encryption and decryption keys, ensuring that only the client app can decrypt the sensitive data.

## 24. D. SQL Server Management Studio (SSMS) provides tools for configuring, monitoring, and administering instances of SQL Server and Azure SQL.

## 25. A. Database contained users only have access to the databases they are hosted in. Change the database context in the SSMS Connect To Server screen from `default` to the database the user is contained in to successfully establish the connection.

## 26. B. `CREATE TABLE` statements fall under the Data Definition Language, or DDL, category of SQL statements.
