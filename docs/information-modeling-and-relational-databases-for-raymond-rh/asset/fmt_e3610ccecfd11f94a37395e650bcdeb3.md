
## 17.2 Key-Value Stores

Key-value data stores are a type of NoSQL database that is becoming increasingly popular due to flexibility and scalability. Unlike traditional relational databases, key-value stores do not use a fixed schema for most of the data. Instead, data is stored as a collection of key-value pairs, where the key is used to uniquely identify the data and the value is the actual data. This type of data store is particularly useful for applications that require fast, efficient data access and retrieval.

There are many commercial key-value data stores available in the market today, in addition to others that are not promoted as key-value stores but offer similar capabilities. `Redis` is an in-memory data structure store that is used for database caching, message brokering, and real-time analytics. It is known for its speed and versatility and is often used as a distributed cache. `RiakKV` is a high-availability distributed key-value data store that is designed to be fault-tolerant and scalable. `Apache HBase` is an open-source, distributed key-value store built on top of the Hadoop Distributed File System (`HDFS`). It is designed for large-scale, random read/write access to Big Data and is modeled after Google’s BigTable approach. `Amazon DynamoDB` is a fully managed key-value data store offered by Amazon Web Services (`AWS`). It offers features such as data replication, encryption at rest, and flexible indexing options.

The main feature of key-value stores is their conceptual simplicity. They build on the well-known technique of `hashing` to provide a consistent way of accessing data values that may not necessarily have a regular format. The values are held in a specialized structure, the internal details of which can be temporarily ignored by users. Values are associated with a unique key that provides a means of locating the values within the structure. A hash function is used that, given a key, provides access to the related value(s), either directly or indirectly using some form of pointer.

Such structures are supported in many programming languages. The terminology varies across different languages and such structures may be described as Hash Maps, Hash Tables, Dictionaries, Associative Arrays, and so on. The terminology is also not used consistently, so a precise definition is only relevant in the context of a specific language. For example, `Python` uses the term `dictionary` to refer to a structure containing key-value pairs. The items are ordered by key value in more recent versions of `Python`, but that’s not necessarily true of equivalent structures in other languages. `JavaScript` can simply use JSON-style Objects for the same purpose. Despite differences in syntax, all these programmatic approaches support a broadly equivalent range of operations, such as:

*   Insert item (`key`, `value`)
*   Update value (`key`, `new value`)
*   Delete item (`key`)
*   Retrieve value (`key`)
*   Test for existence (`key`)

Most languages allow the types of values that can be stored to be anything expressible in that language, ranging from simple types (number, string, etc.) to items that may have their own internal structure, such as objects, lists, and perhaps even further dictionaries. Although such structures can be used within a program, they can’t be directly accessed from outside the program and must be exported in some form, such as `JSON`, if required externally.

Data within a program will obviously disappear when it terminates, and so key-value stores provide equivalent functionality in persistent storage. This also makes the data accessible from many different programs (assuming suitable language bindings).

We can approximate a key-value database using a relational database with a single table defined in a similar way to the following SQL fragment:

```
create table myKV (  theKey varchar(20) primary key,  theValue BLOB )
```

Here, the key is assumed to be a string of up to 20 characters, but any SQL data type could be used. The value here is a `BLOB` datatype that is used to contain undifferentiated binary data that is not parsed by the database. `BLOB` may be replaced by other types such as `varbinary()` in some SQL dialects.

Key-value stores differ from relational databases by focusing solely on the efficient storage and retrieval of complete units of data. The internal structure of a data unit can be ignored by the data store so it can be treated as a single item. This removes the need to support complex queries, as the only essential operations needed are writing and reading individual data units. The data store is no longer responsible for understanding the internal values, data types, and structure of the information. That responsibility is now devolved to applications that use it. Any changes to the internal data structure, adding or removing values, have no impact on the data store, though they obviously will within any associated application.

In addition to making storage and retrieval more efficient, this flat structure also greatly simplifies the design and implementation of a data store because its schema can be trivially simple. However, it’s important to remember that the need for a detailed schema has not gone away completely–it has simply been moved from the data store to the application.

Although key-value stores excel at rapid retrieval of data units, some also offer specific ways of operating on data values inside a unit, such as appending to a string, pushing an element to a list, and getting the member with the highest ranking in a sorted set. If the content of the data unit is encoded in some structured form such as `JSON` or `XML`, then facilities can be provided to query the content in the appropriate way.

Key-value stores are well suited to being distributed, and it’s probably not a coincidence that their rise in popularity has occurred alongside the emergence of cloud computing as a viable platform. A data store can be scaled almost indefinitely by partitioning horizontally across many servers, each of which handles its own subset of the keys and values. Resilience and performance can be improved by replication so that multiple copies can be held on different servers and accessed through an appropriate load-balancing mechanism.

Distribution does not apply in all situations; some key-value stores are designed to be held in memory to provide the fastest possible speed of retrieval. Solid-state disks are about 100 times faster than older hard disks, but `RAM` is orders of magnitude faster still. Distribution is much more problematic for an in-memory store, but hybrid solutions can be found. For example, an in-memory store can be used to provide a lookup between an application-based key and a server-based key that can then be used to access a distributed key-value store.
