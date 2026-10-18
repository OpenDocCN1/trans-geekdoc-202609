
# Typical Use Cases for Azure Table Storage

Typical use cases for Azure Table storage include caching user data for web applications, address books, device information, or other types of metadata. Applications written in .NET, Java, Python, Node.js, or Go can interact with Azure Table storage using the Azure SDK for those languages. Data can be accessed using OData for all languages and LINQ queries for applications written in .NET.

# Migration to Azure Cosmos DB Table API

The Table storage service in Azure is moving from Azure Storage to Azure Cosmos DB to overcome existing limitations with latency, scaling, throughput, availability, and query performance. Keep in mind that Azure Cosmos DB Table API and Azure Table storage share the same data model as Azure Table storage and expose the same query operations through their SDKs. For this reason, applications written for Azure Table storage can easily migrate to the Azure Cosmos DB Table API with minimum code changes.

[Table 3.3](#c03.xhtml#c03-tbl-0003) includes a list of some of the primary benefits that can be gained by migrating to the Azure Cosmos DB Table API from Azure Table storage.

[TABLE 3.3](#c03.xhtml#R_c03-tbl-0003) Azure Table storage vs. Azure Cosmos DB Table API

| Feature | Azure Table Storage | Azure Cosmos DB Table API |
| --- | --- | --- |
| Maximum Entity Size | 1 MB | 2 MB |
| Latency | Fast, but no upper bounds on latency. | Less than 10 ms latency for reads and writes at the 99th percentile, anywhere in the world. |
| Throughput | Variable throughput model. | Highly scalable with provisioned, autoscale, and serverless throughput options. |
| Global Distribution | Single region and one optional secondary read region. | Support for multi-region writes and reads with automatic and manual failovers at anytime, anywhere in the world. |
| Consistency | Strong within the primary region and eventual in the secondary. | Five well-defined consistency levels. |

More benefits can be found at `https://docs.microsoft.com/en-us/azure/cosmos-db/table/introduction#table-offerings`.

# Core (SQL) API

The Azure Cosmos DB Core (SQL) API is a document database service and is the default API for Azure Cosmos DB. As the name implies, the Core (SQL) API is the core, or native, API for working with NoSQL data in Azure Cosmos DB. This API is recommended for new applications that require high performance and global distribution and when migrating to Azure from other NoSQL database platforms. The Core (SQL) API is also the recommended migration option for relational databases that require the benefits of a NoSQL database.

The data model for the Core (SQL) API uses the default hierarchy of resources where an account hosts one or more databases, a database hosts a set of containers, and a container stores data as items. Items are formatted as JSON documents and can be interacted with using SQL.

SQL syntax used by the Core (SQL) API is very familiar to T-SQL with some additional functionality that is specialized for interacting with JSON data. For example, an application that is querying the Persons container of a database in an Azure Cosmos DB Core (SQL) API account might want to retrieve information about the user stored in the following JSON document:

```
{
    "firstname": "John",
    "lastname": "Smith",
    "age": 23,
    "favoriteSports": {
        "mostFavorite": "Basketball",
        "secondFavorite": "Baseball"
    },
    "id": "de5760d6-64fd-4dc3-8cb9-cc914ee860b0",
}
```

The application can use the following SQL query to return the user's first name and their most favorite sport:

```
SELECT p.firstname, p.favoriteSports.mostFavorite
FROM Persons AS p
WHERE p.id = 'de5760d6-64fd-4dc3-8cb9-cc914ee860b0'
```

The results from the query are:

```
[
    {
        "firstname": "John",
        "mostFavorite": "Basketball"
    }
]
```

Along with SQL, the Core (SQL) API supports user-defined functions and stored procedures written in JavaScript.

# API for MongoDB

MongoDB is a popular document database platform that stores data items as Binary JSON (BSON) documents. Organizations wanting to take advantage of the scalability, performance, high availability, and ease of maintenance that Azure Cosmos DB provides without changing any existing code can do so by migrating their MongoDB databases to the Azure Cosmos DB API for MongoDB.

Data can be migrated to the API for MongoDB using tools such as mongodump, mongorestore, or the Azure native Azure Database Migration Service. Once the data is in Azure, organizations can continue using their existing MongoDB applications by just changing the connection string. Tools that are native to MongoDB such as the MongoDB shell and MongoDB Compass can interact with databases hosted on the API for MongoDB just as they would with MongoDB hosted in an on-premises datacenter.

The Azure Cosmos DB API for MongoDB is compatible with MongoDB server versions 4.0, 3.6, and 3.2. More information about migrating to the Azure Cosmos DB API for MongoDB and estimating throughput can be found at `https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb/mongodb-introduction`.

# Cassandra API

Apache Cassandra is a popular columnar database that stores large volumes of data using a column-oriented schema. Just as with MongoDB and the Azure Cosmos DB API for MongoDB, organizations can migrate their existing Cassandra workloads to the Azure Cosmos DB Cassandra API to take advantage of the premium capabilities that Azure Cosmos DB provides.

Users can query data stored in the Cassandra API using the Cassandra Query Language (CQL) and tools like the CQL shell (cqlsh). Applications can also continue to use existing Cassandra client drivers to interact with Cassandra databases hosted on the Cassandra API.

# Gremlin API

The Azure Cosmos DB Gremlin API uses the Apache Tinkerpop graph framework to provide a graph database interface in Azure Cosmos DB. It allows organizations to manage existing and new graph database applications without needing to worry about overhead such as infrastructure, throughput, and availability.

While data is stored as JSON documents as they are with the Core (SQL) API, the Gremlin API enables the data to be queried with graph queries. Applications can query databases hosted on the Gremlin API using the Gremlin query language. More information on the Gremlin query language and using it to query data stored in the Azure Cosmos DB Gremlin API can be found at `https://docs.microsoft.com/en-us/azure/cosmos-db/graph/tutorial-query-graph`.

# Management Tasks for Azure Cosmos DB

Just as with relational PaaS databases in Azure, there are several management tasks that must be taken into consideration for Azure Cosmos DB. These include deploying instances of Azure Cosmos DB, configuring throughput and global distribution, migrating existing on-premises workloads to Azure Cosmos DB, and maintaining data security. The following sections will discuss these tasks in detail, as well as how to troubleshoot common connectivity issues when using Azure Cosmos DB.

## Deployment Options

Instances of Azure Cosmos DB can be deployed to an Azure subscription using several methods. Users can manually configure the necessary requirements for their Azure Cosmos DB environment through the Azure Portal or automate the deployment with different scripting languages. As discussed in [Chapter 2](#c02.xhtml), Azure PowerShell, Azure CLI, and ARM templates are some of the most common ways to automate Azure resource deployments. Let's discuss in the following sections how to use these different options to configure and deploy Azure Cosmos DB.

## Azure Portal

Use the following steps to create an Azure Cosmos DB account through the Azure Portal:

1. Log into `portal.azure.com` and search for `Azure Cosmos DB` in the search bar at the top of the page. Click `Azure Cosmos DB` to go to the Azure Cosmos DB page in the Azure Portal.
