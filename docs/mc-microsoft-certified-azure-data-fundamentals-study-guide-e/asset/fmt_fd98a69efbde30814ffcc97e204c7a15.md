
## 4. Documents can easily be distributed across multiple storage devices.

## 33. You are designing a data storage solution that will store transactions made on an e-commerce site. The schema for these transactions is very fluid and is typically different for each transaction. There is also a requirement for the database to be able to scale globally, with some of the replicated regions being able to be written to. Which of the following is the most appropriate?

1. Azure SQL Database
2. Azure Cosmos DB API for MongoDB
3. Azure Cosmos DB Cassandra API
4. Azure Cosmos DB Core (SQL) API

## 34. Which of the following is a difference between Azure Table storage and the Azure Cosmos DB Table API?

1. Entities in Azure Table storage maintain a defined schema, while entities in the Azure Cosmos DB Table API have flexible schemas.
2. Azure Table storage offers single region replication, while the Azure Cosmos DB Table API offers multi-region replication.
3. Queries can only perform searches on keys when interacting with Azure Table storage, while the Azure Cosmos DB Table API allows queries to search on keys and values.
4. The maximum entity size in Azure Table storage is 2 MB, while the Azure Cosmos DB Table API has a maximum entity size of 4 MB.

## 35. What is the unit of measure used to represent the throughput required to read and write data stored in Azure Cosmos DB?

1. Database transaction units (DTUs)
2. Request Units (RUs)
3. Throughput units (TUs)
4. Cosmos DB transaction units (CDTUs)

## 36. What type of keys does an Azure Cosmos DB account generate to provide access to its resources? How many are created?

1. One read-write key and one read-only key
2. Two read-write keys and one read-only key
3. One read-write key and two read-only keys
4. Two read-write keys and two read-only keys

## 37. Which consistency level guarantees that all reads will return the most recent version of a document while potentially resulting in slower write performance due to application connections being paused while transactions are committed?

1. Session
2. Bounded staleness
3. Strong
4. Eventual

## 38. What is the name of the field that is used to distribute Azure Cosmos DB data across storage?

1. Partition key
2. Distribution key
3. Primary key
4. Foreign key

## 39. You have been asked to isolate an Azure Cosmos DB account by associating it with a subnet in a virtual network. Which of the following services can you use to attach a private IP address from the subnet to the account?

1. Private endpoint
2. Service endpoint
3. IP endpoint
4. Access endpoint

## 40. As the data architect for your company, you have been tasked with designing a storage solution that is optimized for storing videos, images, audio files, and each file's associated metadata. Which type of data store should you use?

1. Graph
2. Document
3. Object
4. Columnar

## 41. Which of the following storage services is used to replace existing on-premises file shares and is accessible via SMB or NFS protocols?

1. Azure Blob storage
2. Azure Files
3. Azure Data Lake Storage Gen2
4. Azure Cosmos DB File API

## 42. Which of the following access tiers is available for file shares that are hosted on a standard Azure storage account?

1. Transaction optimized
2. Hot
3. Cool
4. All of the above

## 43. What object is used to organize data in Azure Blob Storage?

1. Container
2. Directory
3. Blob
4. Table

## 44. What storage service is optimized to serve data to big data analytics environments such as Azure HDInsight, Azure Databricks, and Azure Synapse Analytics due to how it structures data and its integration with the Hadoop Distributed File System?

1. Azure Blob Storage
2. Azure Files
3. Azure Data Lake Storage Gen2
4. Azure Table storage

## 45. Is the italicized portion of the following statement true, or does it need to be replaced with one of the other fragments that appear below? `Azure Data Lake Storage Gen2` provides users with the ability to grant granular access to storage objects and data with the use of POSIX-like access control lists.

1. Azure Blob storage
2. Azure Files
3. Azure Table storage
4. No change needed

## 46. You are designing an Azure Storage solution that will be used to store log files. One of the solution requirements is that the data must be replicated to a secondary storage account in a different Azure region in case of a region outage. Which of the following options should you enable on the storage account?

1. Geo-redundant storage (GRS)
2. Geo-zone-redundant storage (GZRS)
3. Zone redundant storage (ZRS)
4. Both A and B

## 47. What is the minimum number of storage accounts you need to create to host two blob containers, one file share, and one table?

1. One
2. Two
3. Three
4. Four

## 48. Which of the following Azure RBAC roles will grant users read, write, and delete access to an Azure Blob Storage container but will not give them full management rights over the container?

1. Storage Blob Data Owner
2. Storage Blob Data Contributor
3. Storage Blob Data Reader
4. Storage Blob Data Writer

## 49. Is the italicized portion of the following statement true, or does it need to be replaced with one of the other fragments that appear below? `AzCopy` is a stand-alone desktop application that can be used to create and delete Azure Storage resources such as blob containers and file shares. Users can also upload, download, and delete Azure Storage data with `AzCopy`.

1. Azure Data Factory
2. Azure Data Box
3. Azure Storage Explorer
4. No change needed

## 50. Which of the following open-source frameworks can be deployed with Azure HDInsight?

1. Apache Hadoop
2. Apache Storm
3. Apache Kafka
4. All of the above

## 51. Is the italicized portion of the following statement true, or does it need to be replaced with one of the other fragments that appear below? `Spark drivers` are installed on every worker node in a Spark cluster and are used to execute job tasks.

1. Spark sessions
2. Spark executors
3. Cluster managers
4. No change needed

## 52. Which of the following statements regarding Azure Databricks is true?

1. Azure Databricks can be used for both batch and stream processing workflows.
2. The Databricks File System (DBFS) is a built-in distributed file system that Azure Databricks uses to persist data after a Databricks cluster is terminated so that it is not lost.
3. Azure Databricks provides an interactive development environment for data exploration.
4. All of the above.

## 53. The cost of an Azure Databricks cluster consists of what two components?

1. Azure VMs and Databricks Units (DBUs)
2. Azure Kubernetes Service (AKS) and Databricks Units (DBUs)
3. Azure Container Instance (ACI) and Databricks Units (DBUs)
4. Azure Kubernetes Service (AKS) and Databricks Cost Units (DCUs)

## 54. You are configuring a new Azure Databricks cluster that will be used for nightly batch processing jobs. The cluster will be responsible for processing very large datasets and will need to be able to scale out horizontally to finish processing data within a few hours. Which of the following cluster modes is the most optimal for this workload?

1. High concurrency
2. Standard
3. Single node
4. Compute

## 55. Which of the following is not a type of analytical pool that is available with Azure Synapse Analytics?

1. Serverless SQL pool
2. Dedicated SQL pool
3. Databricks pool
