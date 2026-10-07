# Role of Big Data in e-Healthcare

![](bbox=[0.118, 0.093, 0.881, 0.279])

FIGURE 8.17 Kafka overview [24].

#  8.2.7 Hive

Hive is used in Hadoop as a data warehouse infrastructure which processes structured data. It exists on top of Hadoop to digest Big Data, and makes querying and analyzing easy. Facebook (a company) was the one that developed Hive at the initial stage; the Apache Software Foundation it it declared it as an open source, and named it Apache Hive. A detailed study was discussed in [34] on Hive and HiveQL. Hive was designed for Online Analytical Processing (OLAP). It stores schema in a database as an SQL query (i.e., HiveQL, or HQL) and processes data into HDFS. Hive's features are fast, scalable, familiar, and extensible.
The working of Hive is as follows:

+   - **Execute Query:** It consists of Hive interface as Command Line or make Web UI for querying to Driver (any database driver such as JDBC, ODBC, etc.) for execution.
- **Get Metadata:** The compiler transmits metadata request to any Metastore (database).
- **Get Plan:** The driver takes advantage of the query compiler that parses the same query to the query's syntax, plan and requirement.
- **Send Plan:** Further, the compiler checks the requirement then retransmits the plan to the driver for completing and parsing the query.
- **Send Metadata:** It is responsible to transmit metadata as a response to the compiler.
- **Execute Plan:** The driver transmits the execute plan to the execution engine.
- **Metadata Ops:** During execution, the execution engine executes metadata operations with Metastore.
- **Execute Job:** Internally, the execution job process is a MapReduce job. The execution engine transmits the job to JobTracker, which is in Name Node and assigns it.
- **Fetch and send Result:** The execution engine receives the results from Data Nodes. The execution engine sends those resultant values to the driver; the driver sends the results to Hive Interfaces.