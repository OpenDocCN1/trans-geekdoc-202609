
7. Which of the following is the most optimal solution for storing images, telemetry data, and data that is used for distributed analytics solutions?

1. `Azure SQL Database`
2. `Azure Blob Storage`
3. `Azure Cosmos DB Gremlin API`
4. `Azure Files`

8. What data processing approach is typically used to process data for traditional business intelligence solutions?

1. `ELT`
2. `Batch`
3. `Streaming`
4. `ETL`

9. Data that is transformed so that it meets the schema requirements of a destination table is an example of what type of data processing strategy?

1. `Schema-on-upload`
2. `Schema-on-read`
3. `Schema-on-write`
4. `Analytical processing`

10. What technology in Azure allows data engineers to build data processing pipelines with a graphical user interface?

1. `Azure Data Factory mapping data flows`
2. `SSIS`
3. `Azure Databricks`
4. `Azure Logic Apps`

11. Which of the following methods is used to manage the order in which data processing activities are executed?

1. `Data flow`
2. `Management flow`
3. `Control flow`
4. `Orchestration flow`

12. You have been tasked with taking data stored as parquet files in Azure Data Lake Storage Gen2 and loading the most recent three years of data into an Azure Synapse Analytics data warehouse. However, you must first query the parquet data to determine which rows fall within the last three years. Which of the following options will allow you to query the parquet data without requiring you to physically store the data in the data warehouse first?

1. `Azure Synapse Analytic serverless SQL pools`
2. `Synapse Pipelines`
3. `Synapse Link`
4. `Linked Service`

13. Is the italicized portion of the following statement true, or does it need to be replaced with one of the other fragments that appear below? *Prescriptive* analytics involves examining historical data to determine why certain events happened.

1. `Predictive`
2. `Diagnostic`
3. `Cognitive`
4. `No change needed`

14. You are a data analyst for a company that sells different types of bicycles. For an upcoming review of this past quarter's sales, you would like to build a report that shows how well different types of bikes have done in the company's various sales territories. One requirement for this report is that it includes a visualization that displays total sales for each bike subcategory. Which of the following visuals best serves this requirement?

1. `Line chart`
2. `Column chart`
3. `Scatter plot`
4. `Map`

15. What type of index is optimal for database tables that are used in queries that perform large aggregations of data?

1. `Columnstore`
2. `Clustered`
3. `Nonclustered`
4. `Unique`

16. Which Azure SQL option is an example of an IaaS offering?

1. `Azure SQL Database`
2. `Azure SQL Managed Instance`
3. `SQL Server on an Azure Virtual Machine`
4. `Azure Synapse Analytics dedicated SQL pools`

17. Which Azure SQL option requires the least amount of administrative effort and is typically used when building modern cloud applications?

1. `Azure SQL Managed Instance`
2. `Azure SQL Database`
3. `Azure Synapse Analytics Serverless SQL Pools`
4. `SQL Server on an Azure Virtual Machine`

18. You are developing a database platform that will serve an OLTP system and will need to store more than 10 TB of data. The database platform will need to minimize administrative effort as much as possible. Which of the following database and service tier options is the most appropriate for this use case?

1. `Azure SQL Database Hyperscale`
2. `Azure SQL Database Elastic Pool`
3. `Azure SQL MI, Business Critical`
4. `Azure Synapse Analytics dedicated SQL pools`

19. Which of the following options will give specific IP addresses access to an Azure SQL Database's logical server?

1. `Virtual network firewall rules`
2. `Private Link`
3. `Server-level IP firewall rules`
4. `Database-level IP firewall rules`

20. What free tool can be used to determine potential compatibility issues when planning a SQL Server database upgrade or a migration to Azure SQL?

1. `Data Migration Planner`
2. `Data Migration Assistant`
3. `Database Migration Recommender`
4. `Database Migration Service`

21. Which of the following tools can be used to automate Azure resource deployments?

1. `Azure PowerShell`
2. `Azure CLI`
3. `Azure Resource Manager templates`
4. `All of the above`

22. How often does Azure perform a full database backup of an Azure SQL Database?

1. `Once a month`
2. `Once a week`
3. `Once a day`
4. `Once an hour`

23. Which of the following commands is an example of a DML command?

1. `SELECT`
2. `CREATE`
3. `ALTER`
4. `DROP`

24. Which SQL Server feature can be used to obfuscate sensitive data in different columns?

1. `Always Encrypted`
2. `Transparent Data Encryption`
3. `Dynamic data masking`
4. `Column-Level Security`

25. Which of the following open-source databases is available as a PaaS offering in Azure?

1. `PostgreSQL`
2. `MySQL`
3. `MariaDB`
4. `All of the above`

26. Which of the following describes Read Committed isolation for SQL Server?

1. `Transactions running with Read Committed isolation issue locks on involved data at the time of data modification to prevent other transactions from reading dirty data. This is the default isolation level for SQL Server–based database engines.`
2. `Transactions running with Read Committed isolation issue read and write locks on involved data until the end of the transaction.`
3. `Read Committed isolation is the lowest isolation level, only guaranteeing that physically corrupt data is not read.`
4. `Read Committed isolation is the highest isolation level, completely isolating transactions from one another.`

27. When following a star schema design pattern for a data warehouse, which of the following table types is used to store metrics?

1. `Measure table`
2. `Dimension table`
3. `Materialized table`
4. `Fact table`

28. When configuring a SQL Server instance on an Azure VM, what is the recommended storage configuration for the disk, log, and tempdb files?

1. `Place data and log files on the same disk and tempdb on a separate disk.`
2. `Place data, log, and tempdb files on separate disks.`
3. `Place log and tempdb files on the same disk and data files on a different disk.`
4. `Place data and tempdb files on the same disk and log files on a separate disk.`

29. Is the italicized portion of the following statement true, or does it need to be replaced with one of the other fragments that appear below? *Nonrepeatable* reads occur when a transaction reads the same row several times and returns different data each time.

1. `Phantom`
2. `Dirty`
3. `Inconsistent`
4. `No change needed`

30. What type of join will retrieve all data from the left table of a join condition and only data that meets the join condition from the table on the right?

1. `Full inner join`
2. `Left inner join`
3. `Left outer join`
4. `Right outer join`

31. Which of the following nonrelational database types is optimal for storing the relationships between multiple entities?

1. `Graph database`
2. `Document database`
3. `Key-value store`
4. `Columnar database`

32. Which of the following statements is not true about a document in a document database?

1. `Different schemas can be used across multiple documents.`
2. `Documents are typically stored as semi-structured data formats, such as JSON, BSON, and XML.`
3. `Queries performing specific lookups or filters can only search by a document's key and not by one of the data values.`
