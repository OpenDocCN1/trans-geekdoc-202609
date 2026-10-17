
# Data Warehouses

Data warehouses are data management systems that support analytical workloads and business intelligence (BI) activities. Data managed by a data warehouse is derived from several sources, such as OLTP systems, web APIs, IoT devices, and social media networks. Unlike OLTP systems, data warehouses use data models that are read-optimized so analytical queries issued against them can efficiently return aggregated calculations to support business decisions.

As discussed in [Chapter 2](#c02.xhtml), data warehouses use denormalized data models that are optimized for analytical queries and read-heavy workloads. The most common design practice for this approach is the star schema. Star schemas denormalize business data to minimize the number of tables in the data model. Tables consist of business entities and measurable events that are related to those entities. This division of data categories is represented by the two types of tables defined in the star schema: dimension tables and fact tables.

Dimension tables contain information that describes a particular business entity. These tables are typically very wide, containing several descriptor columns and a key column that serves as a unique identifier. Some common entities that are stored as dimension tables include date, customer, product category, and product subcategory information. In all of these cases, there could be a relatively small number of rows but a large number of columns to provide as much descriptive information as possible.

Fact tables store quantifiable observations that are related to the dimension tables. These tables can grow to be very large, comprising several millions of rows related to specific measurable events. Some fact table examples include Internet sales, product inventory, and weather metrics. Fact tables also include foreign key columns that are used to establish relationships with dimension tables. These relationships determine the level of granularity that analytical queries can use when filtering fact table data. For example, a query that is filtering an Internet sales fact table by a date dimension can only return time slices for the level of detail contained in the date dimension.

## Azure Services for Modern Data Warehouses

In the Azure ecosystem there are several services that can be used to build a modern data warehouse solution. Depending on the scenario and the skillset of the engineers building the solution, most Azure services can be used to build different components of a data processing pipeline. However, there is a set of core Azure data services that are specifically designed to process big data workloads:

* Azure Data Factory
* Azure HDInsight
* Azure Databricks
* Azure Synapse Analytics

Each of these services can perform a variety of different functions in a data processing pipeline. This versatility allows them to be used in various stages of ETL or ELT pipelines. They have the flexibility to manage data in a variety of different formats and can scale horizontally as well as vertically to process very large volumes of data.

First, let's examine how Azure HDInsight, Azure Databricks, and ADF are used in modern data warehouse solutions. End-to-end data processing solutions with Azure Synapse Analytics will be described in the section “End-to-End Analytics with Azure Synapse Analytics” later in this chapter.

### Azure HDInsight

Azure HDInsight is a managed, open-source analytics service in Azure. With Azure HDInsight, you can deploy distributed clusters for Apache Hadoop, Apache Spark, Apache Interactive Query/LLAP (Live Long and Process), Apache Kafka, Apache Storm, and Apache HBase in Azure. Being able to quickly stand up these environments without having to procure and manage hardware reduces the barriers to entry for organizations who are beginning to build a modern data warehouse.

Open-source frameworks like Hadoop and Spark are designed to handle large-scale data processing activities by using a scale-out architecture. While they can be installed on a single server node for test purposes, most use cases leverage multiple server nodes that are clustered together to perform processing activities at scale. Clusters consist of a head/driver node that divides jobs into smaller tasks and one or more worker nodes that execute each task.

Distributed frameworks also rely on resource managers like Apache Hadoop YARN (Yet Another Resource Negotiator) to manage cluster resources and job scheduling. Resource managers designate compute resources (such as CPU, memory, IO) to cluster nodes and monitor the resource usage. Knowing details of how YARN and other resource managers are designed is beyond the scope of the DP-900 exam and this book, but you can find more information at the following link if you would like to learn more: `https://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html`.

Azure HDInsight makes it easy to manage distributed frameworks like Hadoop and Spark and offers the capability to customize a cluster deployment, such as adding new components and languages. Also, since Azure HDInsight is a PaaS service, you can easily scale the number of worker nodes allocated to cluster up or down to increase compute power or cut back on cost.

It is important to understand the different Azure HDInsight cluster types and when you should use them. Also, keep in mind that after you have deployed an Azure HDInsight cluster, you will not be able to change the cluster type. For this reason, it is critical that you understand the scenarios the cluster will be supporting. The following list describes each of the cluster types supported by Azure HDInsight:

* Apache Hadoop is an open-source technology for distributed data processing. It uses the MapReduce parallel processing framework to process data at scale and the Hadoop Distributed File System (HDFS) as a distributed storage system. MapReduce jobs divide compute jobs into smaller units of work to be run in parallel across the various nodes in a cluster. Users can also leverage Apache Hive with Hadoop to project a schema on data and query data using HiveQL. More information about Apache Hive can be found at `https://docs.microsoft.com/en-us/azure/hdinsight/hadoop/hdinsight-use-hive`.

One drawback to Hadoop is that it only supports batch processing, forcing users to leverage another service like Apache Storm or Apache Spark for distributed stream processing. Hadoop also reads and writes data from and to disk, potentially leading to poorer processing performance than Apache Spark, which supports in-memory processing.

* Apache Spark is an open-source, distributed processing framework that supports in-memory processing. Because of its speed, Spark has become the standard framework for batch and stream distributed processing activities over Hadoop. Apache Spark also supports interactive querying capabilities, allowing users to easily query data from distributed data stores like ADLS with popular development languages like Spark SQL. More Spark-specific features such as development languages, workflows, and best practices will be described in the section “Azure Databricks.”

* Apache Kafka is an open-source, distributed real-time data ingestion platform that is used to build stream processing data pipelines. It offers message broker functionality that allows users to publish and subscribe to data streams.

* Apache HBase is an open-source NoSQL database that is built on top of Apache Hadoop. It uses a columnar format to store rows of data as column families, similar to the Azure Cosmos DB Cassandra API. Developers can interact with HBase data using Hive queries.

* Apache Storm is an open-source, real-time processing system for processing large data streams very quickly. Similar to Hadoop and Spark, it uses a distributed framework to parallelize stream processing jobs.
