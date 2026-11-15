
her name to make the necessary changes. If this is not done rigorously, the result is an unreliable data store that is very difficult to manage. If, instead, we had embedded Courses into Students, an update to the Course details would entail accessing all Student documents.

The alternative approach to *embedding* is *referencing*. This concept is much closer to the way that foreign key references are used in a relational database. Using the same example as above, we could put Course documents and Student documents into different collections, as in the following example.

```
{
  "Courses": [
    {"_id": "DB102",
    "courseName": "Databases",
    "creditValue": 15},
    {"_id": "SW101",
    "courseName": "Python",
    "creditValue": 10}
  ]
}
{
  "Students": [
    {"_id": "12345",
    "name": "Abby Akbar",
    "courses": [ {"courseId": "DB102", "grade": 3.4},
                 {"courseId": "SW101", "grade": 3.8} ] },
    {"_id": "67890",
    "name": "Bill Briggs",
    "courses": [ {"courseId": "DB102", "grade": 3.2} ] }
  ]
}
```

Here, the two collections contain a list of Course documents and a list of Student documents, respectively. The relationships between students and courses are recorded by references from Student documents to the identifiers of Course documents. This avoids the data redundancy of the previous example, but introduces other issues. For instance, if we want to obtain the total value of credits gained by a student, we have to read additional Course documents to get the necessary information. This is roughly the equivalent of a join in a relational system.

The relationship between Courses and Students is many-to-many (so in the example above, a Student document needs to contain references to multiple Course documents). We could resolve this by inventing a new Course-Student document, equivalent to a linking table in a relational system. However, this could be rejected as an unnatural artifact. Thinking of a paper-based equivalent in the real world, it's quite plausible that there could be Course documents and Student documents, but a Course-Student document would be unlikely.

In designing a document database, the choice between embedding and referencing depends on finding the right balance between several competing factors.

First, we need to identify the significant document types. If we are starting from scratch, we can develop an object-role model (ORM) to clarify the information structure relevant to our concerns. From this, we can use relational mapping (as discussed in *Chapter 11*) to derive a set of candidate document types that could be represented in the appropriate JSON format. Alternatively, we may want to base our design on preexisting documents, respecifying these in JSON format if they have some other form (CSV, XML, ...).

The next set of decisions is highly dependent on the expected usage of the documents. Broadly speaking, we want a document to be as big as it needs to be but not bigger. This may indicate that some candidate documents should be split to improve performance (there may be a database-imposed size limit on individual documents, but this is usually large enough not to be a concern). In thinking about relationships between documents, we need to know the relative frequency of the usual Create, Read, Update, Delete (CRUD) operations on the data. It's quite common for Read operations to dominate, but that's not always the case.

If we consider two document types, A and B, that are related in some way, here are some of the kinds of scenarios that might be relevant.

- If A and B are often queried together, consider embedding A in B, or B in A (whichever gives the optimum performance).
- Long lists are inefficient, so if embedding B in A results in long lists of Bs, consider referencing instead.
- If B is rarely queried in isolation, consider embedding B in A.
- If B is embedded in A, but B is associated with many other document types, consider referencing instead.
- If B is embedded in A, and B is updated much more frequently than A, consider referencing instead.

## Partitioning

Partitioning in a document database usually refers to horizontal partitioning. Something akin to vertical partitioning could be achieved by splitting a document type to make two new document types, each containing a different subset of the original document fields, but this is an intrinsic part of the original database design. Horizontal partitioning can be based on any part of a document, but the choice is determined by the way that the database is expected to be used. Each partition, or "shard", can hold a subset of the documents in a collection and is physically distinct from other shards. A crucial decision is the selection of the field or fields to be used as the basis for distribution. As with other aspects, this will depend on the expected pattern of usage of the database. For example, if queries often focus on data within a given year, it may be appropriate to assign a separate shard for each year and use a relevant date field as the basis for distribution.

Each document in a collection is assigned a *shard key* value based on the relevant field(s). The shard key should be chosen to distribute data evenly across the shards to prevent hotspots and ensure balanced performance. Each shard in the database maintains metadata that maps ranges of shard key values to specific shards. When an operation is performed, the database client includes the shard key value in the query or command sent to the cluster. This is handled by a specialized router that examines the shard key, determines which shards need to be involved in executing the operation, and then formulates a plan for executing the query across the relevant shards.

Assuming a query involving several shards, the router sends the parts of the query to the appropriate shards based on the shard key range for which the shard is responsible. Each shard locally executes its part of the query and returns partial results to the router containing the subset of the overall results specific to that particular shard. Once the router receives results from all shards, it combines them to form a complete result set. This may involve sorting, merging, and applying any additional query operations (e.g., filtering) to match the original query criteria. Finally, the router sends the merged result set back to the client application, providing a unified view of the query results as if it had been executed on a single nonsharded database.

The collection and merging of distributed results obviously impose a performance penalty, so the choice of shard key needs to be considered carefully. Ideally, the partitioning should be designed so that most queries can be addressed to a single shard within the cluster.

## Indexing

As with Relational databases, document databases can use indexing to improve the performance of queries by creating data structures that allow for efficient data retrieval. As with other aspects of schema design, it's important to have a clear strategy for indexing. Although indexing can improve query performance, it will also have an impact on write performance and will increase storage requirements.

The application(s) using the database should be examined for the type of queries used and their relative frequency. Based on the number and type of operations, the appropriate index types can be identified. Several types are available, including:

- Single Field Index: The most basic type of index where queries are based on a single field.
- Compound Index: Created on multiple fields, combining them into a single index.
- Multikey Index: Separately indexes elements of an array.

There are also other types of indexes for more specialized applications, such as Text, Geospatial, and Hashed indexes.

Indexes are created using an operation to specify the collection and fields to be indexed, along with any additional options that might be required, such as creating the index in the background to minimize disruption. For example, we could create a Single Field index on a courseName field in a Courses collection as follows:

```
db.Courses.createIndex( { courseName: 1 } )
```

Here, the digit 1 indicates that the index should be in ascending order; descending order would be indicated by a –1 parameter.

It's also important to handle updates and deletes carefully in document databases. Unlike relational databases, document databases do not enforce referential integrity or cascading deletes. It's up to the developer to ensure that updates and deletes are performed correctly, without leaving orphaned data or breaking relationships.

Referential integrity is a concept commonly associated with relational databases, where relationships among tables are maintained and enforced using foreign keys. In a document database, which follows a NoSQL data model, referential integrity is not natively provided in the same way. However, referential integrity-like patterns and mechanisms can be employed to ensure data consistency and relationships among documents. Embedding and Referencing can provide some degree of integrity, as described above. Additional measures can include:

- Transactions, allowing multiple operations on different documents atomically to ensure data consistency across the affected documents. While transactions do not enforce referential integrity, they can help maintain data consistency among related documents.
- Triggers and Hooks, which allow custom logic to run before or after specific database operations, such as insert, update, or delete. These can be used to implement custom referential integrity checks and ensure that related documents remain consistent during data modification operations.
- Application code, external to the database, can be augmented with additional functionality to ensure that data modifications conform to the desired relationships and integrity constraints before persisting them to the database.

## Database Queries

Because of their NoSQL status, document databases do not include the familiar select statement from SQL. However, they do provide equivalent facilities in their own query language. We will use MongoDB as an example (https://www.mongodb.com) and its MQL query language. The language allows similar functionality through functions that allow operations such as selection, projection, filtering, sorting and aggregation. Here, we will look at a few simple examples to give an impression of the scope available.
