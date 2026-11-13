
3. ROLLBACK: Used to undo all changes made during the current transaction. It reverts the database to the state it was in before the transaction began.

In the example below, the two UPDATE statements are reversed, and so the table would reach its state prior to the updates being made.

```
BEGIN TRANSACTION;
UPDATE Employees SET Salary = Salary + 100 WHERE EmployeeID = 1;
UPDATE Employees SET Salary = Salary - 100 WHERE EmployeeID = 5;
ROLLBACK;
```

## TOK

## How has the development of database technology influenced the way we acquire and process knowledge?

The development of database technology has profoundly influenced the ways in which we acquire and process knowledge, touching on key areas such as the nature of knowledge, how it is shared and the ethical considerations involved.

Databases store vast amounts of data, but this raw data only becomes useful when it is processed into information and then interpreted as knowledge. This raises questions about the nature of knowledge itself. How do we distinguish between data, information and knowledge? How does the structure of a database influence what we consider to be true or valuable knowledge?

Databases rely on structured query languages (SQL) and other forms of data communication. The precision and clarity required in database queries contrast with the ambiguity and richness of natural language. This might lead to a more structured, but potentially limited, way of knowing. How does the structured nature of database queries influence our understanding of complex or ambiguous information?

## REVIEW QUESTIONS

- 1. Discuss whether a view is physically stored in a database.
- 2. Define the term “database transaction”.
- 3. Identify a reason a transaction may need to be rolled back by giving an example.
- 4. State the effect of rolling back a transaction.
- 5. Describe the four properties that describe a transaction.

## SYLLABUS CONTENT

By the end of this chapter, you should be able to:

- 3.4.1 Outline the different types of databases as approaches to storing data
- 3.4.2 Explain the primary objectives of data warehouses in data management and business intelligence
- 3.4.3 Explain the role of online analytical processing (OLAP) and data mining for business
- 3.4.4 Describe the features of distributed databases

## A3.4.1 Types of databases as approaches to storing data

Database models represent frameworks that determine the logical structure of a database and influence how data is stored, organized and manipulated. Different database models cater to different types of applications and requirements.

### NoSQL databases

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_204_0.png)

NoSQL databases are designed to handle large volumes of data and diverse data types. They offer flexibility and scalability, making them suitable for modern web applications, such as e-commerce platforms, big data and real-time analytics.

NoSQL databases store data differently from relational databases. There are four main types of NoSQL databases: document databases, key-value databases, wide-column store databases and graph databases.

### Document databases

In document databases, data is stored in documents like JSON (JavaScript Object Notation) objects. The documents contain pairs of fields and values, and document databases are used for content management systems and e-commerce platforms. They offer a flexible data model, suitable for semi-structured and unstructured data sets. They provide an easy way to represent hierarchical data, but a disadvantage is that they pose a risk of data redundancy and inconsistency. An example of such a database is MongoDB. Here is an example:

```
{
 "_id": "12345",
 "name": "blabla",
 "email": "blabla@car.com",
 "address": {
 "street": "bloblo street",
 "city": "omega city",
 },
 "services": ["transport", "tourism"]
}
```

### Key-value databases

In key-value databases, data is stored as key-value pairs. Key-value databases are used for real-time analytics, caching and session management. They are simple databases that allow for fast read and write operations, however, they have limited querying capabilities. An example of a key-value database is Redis. Here is an example:

```
Key: user:12345
Value: {"name": "blabla", "email": "blabla@car.com", "job": "transporter"}
```

### Wide-column store databases

In wide-column store databases, data is stored in tables, rows and dynamic columns. Different rows can have different sets of columns. They enable efficient retrieval of sparse and wide data and are used in big-data applications or real-time analytics. They are proven to be efficient for read and write operations on large data sets and are easy to scale horizontally; however, this is a complex model to implement. An example of a wide-column store database is Cassandra.

Here is an example:

| name | id | email | dateOfBirth |
|---|---|---|---|
| blabla | 12345 | blabla@car.com | |
| nathan | 1234 | | 12-12-2000 |

### Graph databases

In graph databases, data is stored as nodes and edges in a graph structure. Nodes usually store data about people, places or things, and edges store data about the relationships between nodes. They are used for social-media platforms or recommendation engines. Graph databases are great for representing and querying complex relationships, but they use a specialized query language, and it is more complex to maintain and optimize them. An example of a graph database is OrientDB. Here are two examples of graph databases:

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_205_0.png)

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_205_1.png)

- Cloud database: a database that runs on cloud computing platforms, providing scalability, high availability and flexible resource management.
- Spatial database: a database optimized to store and query data related to objects in space, including points, lines and polygons.
- In-memory database: a database that stores data entirely in the main memory (RAM) rather than on disk, providing extremely fast read and write operations.

### Cloud databases

Cloud databases are databases that run on cloud computing platforms, providing scalability, high availability and flexible resource management. They can be NoSQL or SQL databases.

In cloud databases, pricing is based on the use of system resources, which can be provisioned on demand as needed to meet processing workloads. Organizations can choose between two models when they opt for cloud databases:

- **Self-managed database**: An infrastructure as a service (IaaS) environment, in which the database runs on a virtual machine on a system operated by a cloud provider. The provider manages and supports the cloud infrastructure, including servers, operating systems and storage devices. But the organization is responsible for database deployment, administration and maintenance, so it has full control over the database.

- **Managed database services**: Fully managed by the vendor, both the system infrastructure and the database platform are managed for the customer, the vendor handles provisioning, backups, scaling, patching, upgrades and other basic database administration functions; organizations monitor the database, and they can collaborate with the vendor on some administrative functions.

Examples of database-as-a-service (DBaaS) are Amazon DynamoDB and Azure Cosmos DB. They are used for startups, IoT or web-scale applications; they are fully managed, offer pay-as-you-go pricing and the organization has limited control over the infrastructure.

Examples of managed databases are Amazon RDS, Google Cloud SQL and Azure SQL database. They are used for web and enterprise applications, and they depend on cloud providers and potentially have higher costs.

### Spatial databases

Spatial databases are optimized to store and query data related to objects in space, including points, lines, polygons, 3D shapes and coordinates. They support spatial data types and spatial indexes to access the data, and they support geometric functions. They are used for Geographic Information Systems (GIS), location-based services and mapping applications. Examples are: Oracle Spatial, PostGis and MongoDB with Geospatial Indexes. Such models efficiently store and query spatial data, but they use complex data types and queries that require specialized knowledge or experts.

### In-memory databases

In-memory databases store data entirely in the main memory (RAM) rather than on disk, providing extremely fast read and write operations. They are used for real-time analytics, caching and gaming applications. They allow for extremely fast data access and transaction processing, but they have low latency for read and write operations. Examples are Redis and Oracle TimesTen.

## A3.4.2 Primary objectives of data warehouses in data management and business intelligence

- Data warehouse: a specialized type of database designed for analytical purposes rather than transactional processing.

A data warehouse is a specialized type of database designed for analytical purposes rather than transactional processing. It is used to store and analyse large volumes of historical data from various sources to support decision-making processes within organizations. A data warehouse represents a repository of stored data related to a specific subject. It includes tools to extract, transform and load data into the repository and tools to manage and retrieve the metadata.
