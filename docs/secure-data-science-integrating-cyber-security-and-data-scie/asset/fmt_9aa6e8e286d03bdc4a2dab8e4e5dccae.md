
# NoSQL Database

NoSQL database is a generic term for essentially a non-relational database design or scalability for the web. It is known as a non-relational high-performance database. The data models for NoSQL databases may include graphs, document structures, and key-value pairs. It can be argued that the databases that were developed in the 1960s such as IBM's IMS and those based on the network data model are NoSQL databases. However, other object-oriented data models that were developed in the 1990s led the way to develop NoSQL databases in the 2000s. What is different from the NoSQL databases and the older hierarchical, network, and object databases is that the NoSQL databases have been designed with the web in mind. That is, the goal is to access massive amounts of data on the web rapidly.

The most popular NoSQL database model is the key value pair. While relational databases consist of a collection of relations where each relation has a collection or attributes, these attributes are labeled and included in the schema. NoSQL databases have tables that have two columns: Key and Value. Key could be anything such as a person's name or the index of a stock. However, the value could be a collection of attributes such as the name of the stock, the value of the stock, and other information such as whether to buy the stock and if so, the quantity recommended. Therefore, all the information pertaining to a stock can be retrieved without having to perform many joins. Some of the popular NoSQL databases will be discussed in this section (e.g., MongoDB and HBase). For a detailed discussion of NoSQL databases, we refer the reader to `[[NOSQ](#ch04.xhtml#ref4_52)]`. More details are also given in `[[CATT2011](#ch04.xhtml#ref4_18)]`.

## 4.2.2.4 Google BigTable

BigTable is one of the early NoSQL databases running on top of the Google File System (GFS). It is now provided as a service in the cloud. BigTable maps the row key and the column together with a time stamp into a byte array. That is, it is essentially a NoSQL database that is based on the key value pair model. It was designed to handle petabyte-sized data. It uses compression algorithms when the data gets too large. Each table in BigTable has many dimensions and may be divided into what is called tablets to work with GFS. BigTable is used by many applications, including Google's YouTube, Google Maps, Google Earth, and Gmail. More details on BigTable can be found in `[[BIGT](#ch04.xhtml#ref4_14)]`.

## 4.2.2.5 Apache HBase

HBase is an open-source non-relational distributed database that was the first table developed for the Hadoop/MapReduce platform. That is, HBase is a NoSQL database that is based on a column-oriented key value data store model. It is implemented in Java. The queries are executed as MapReduce jobs. It is somewhat similar to Google's Big Table and uses compression for in-memory storage. HBase is scalable and handles billions of rows with millions of columns. It also integrates multiple data stores in different formats as well as facilitates the storage of sparse data. More details on HBase can be found in `[[HBAS](#ch04.xhtml#ref4_31)]`.

## 4.2.2.6 MongoDB

MongoDB is a NoSQL database. It is a cross-platform open-source distributed database. It has been used to store and manage documents. That is, it is mainly a document-oriented database. The documents are stored in a JSON-like format `[[CROC2006](#ch04.xhtml#ref4_24)]`. It supports both field and range queries as well as regular expression-based searches. It supports data replication and load balancing, which occurs through horizontal scaling. The batch processing of data as well as aggregation operations can be carried out through MapReduce. More details of MongoDB can be found at `[[MONG](#ch04.xhtml#ref4_50)]` and `[[CHOD2010](#ch04.xhtml#ref4_20)]`.

## 4.2.2.7 Apache Cassandra

Cassandra is a NoSQL distributed database `[[HEWI2010](#ch04.xhtml#ref4_32)]`. It was first developed at Facebook to power the Facebook applications and then became an Apache foundation open software initiative. It was designed with no single point of failure in mind. It supports clusters that span multiple data centers. All the nodes in a cluster perform the same function. As a result, there is virtually no single point of failure. It supports replication and is highly scalable. It is also fault tolerant and is integrated with Hadoop with support for MapReduce. The query language supported by Cassandra is Cassandra Query Language (CQL), which is an alternative to SQL. It can also be accessed from programs such as Java, C++, and Python. More details of Cassandra can be found at `[[CASS](#ch04.xhtml#ref4_17)]`.

## 4.2.2.8 Apache CouchDB

As stated in `[[COUC](#ch04.xhtml#ref4_23)]`, CouchDB enables one to access data by implementing the Couch Replication Protocol. This protocol has been implemented by numerous platforms from clusters to the web to mobile phones. It is a NoSQL database and implemented in a concurrent language called Erlang. It uses javaScript object notation (JSON) to store the data and JavaScript for the query language. More details on CouchDB can be found in `[[COUC](#ch04.xhtml#ref4_23)]` and `[[ANDE2010](#ch04.xhtml#ref4_7)]`.

## 4.2.2.9 Oracle NoSQL Database

Oracle is one of the premier relational database vendors and they have marketed relational database products since the late 1970s. They offered object-relational database products in the 1990s and more recently the NoSQL database. The NoSQL database is based on the key value paid model. Each row has a unique key and has a value that is of arbitrary length and interpreted by the applicant. Oracle NoSQL database is a shared-nothing system and is distributed across what are called multiple shards in a cluster. The data is replicated in the storage nodes within a shard for availability. The data can be accessed via programs such as those written in Java, C, Python as well as RESTful web services. More details on the Oracle NoSQL database can be found at `[[ORAC](#ch04.xhtml#ref4_53)]`.

## 4.2.2.10 Weka

Weka is an open-source software product that implements a collection of data mining techniques from association rule mining to classification to clustering. It has been designed, developed, and maintained by Mankato University in New Zealand. Weka 3, a version of Weka, operated on big datasets. While earlier versions of Weka required the entire datasets to be loaded into memory to carry out say classification, the big data version carried out incremental loading and classification. Weka 3 also supports distributed data mining with Map and Reduce tasks. It also provides wrappers for Hadoop and Spark. More details on Weka can be found at `[[WEKA](#ch04.xhtml#ref4_72)]`.

## 4.2.2.11 Apache Mahout

The Apache Mahout provides an environment to implement a collection of machine learning systems. These systems are scalable and implemented on top of Hadoop. The machine learning algorithms include classification and clustering. The instructions of the machine learning algorithms are transformed into MapReduce jobs and executed on Hadoop. Mahout provides Java libraries to implement the mathematics and statistical techniques involved in machine learning algorithms. The goal is for the machine learning algorithms to operate on very large datasets. In summary, as stated in `[[MAHO](#ch04.xhtml#ref4_47)]`, Mahout provides the following three features: “(i) a simple and extensible programming environment and framework for building scalable algorithms, (ii) a wide variety of premade algorithms for Scala + Apache Spark, H2O, and Apache Flink, and (iii) Samsara, a vector math experimentation environment with R-like syntax which works at scale.” More details on Mahout can be found at `[[MAHO](#ch04.xhtml#ref4_47)]`.

# 4.3 Cloud Computing

## 4.3.1 Cloud Computing Models
