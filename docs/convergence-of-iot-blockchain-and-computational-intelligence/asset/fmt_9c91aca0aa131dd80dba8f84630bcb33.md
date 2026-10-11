
The data ingestion layer is the fourth layer that includes large data, cleaning, streaming, and data management. `Apache flume` and `Apache Nifi` are examples of big data ingestion tools. `Apache flume` provides distributed service. A large amount of data is collected, aggregated, and transferred preserving reliability. A stream of data collected from multiple sources is stored and analyzed in `Hadoop`. Based on the flow of data streaming, its architecture is made simple. It is robust and tolerant of flaws with many failures and recovery mechanisms. `Apache Nifi` is an easy-to-use, reliable system, and prevailing for data distribution and processing. It enables tracking data flow, provides seamless service for monitoring and controlling. The data is encrypted by `SSL`, `HTTPS`, `SSH` so it is secure.

### 3.3.4.1 Storage Tools

#### 3.3.4.1.1 Hadoop Distributed File System

A Java-based file system is used for the secure storage of large data called the `Hadoop Distributed File System (HDFS)`. It is scalable to serve large customers and allows easy access from a large repository. Redundancy is preserved as multiple copies of data are stored on different machines. It is a master/slave architecture model, that allows parallel processing by dividing the data and placing it in different clusters ([Nazini and Sasikala, 2019](#chapter3.xhtml#ref3_11)).

#### 3.3.4.1.2 Gluster File System

A `Gluster file system (Gluster FS)` is an open-source, dependable distributed file system that provides linear scale performance in storage. It can be deployed for unstructured data. It is scalable and allows distributed storage. `Gluster FS` can be used in cloud computing, media streaming, and content delivery.

#### 3.3.4.1.3 Amazon Simple Storage Service

`Amazon simple storage service (Amazon S3)` is a simple, object storage web service. It provides maximum durability and is scalable on widespread. Cloud applications use `S3` service. It allows a large data repository with fault recovery. The migration of data is easier than other services. The cost is comparatively reduced when stored on `S3`.

### 3.3.5 Data Analysis

Data analysis is the fifth layer that relates to data investigation, extraction, and machine processing. Most companies use big data analytics to improve productivity, revenue, and lower cost. `Apache Hive`, `Apache Spark SQL`, `Amazon Redshift`, `Presto SQL Query Engine` are examples of big data query tools ([Kamilaris et al., 2017](#chapter3.xhtml#ref3_8); [Samanta et al., 2021](#chapter3.xhtml#ref3_15); [Vinodhini et al., 2020](#chapter3.xhtml#ref3_34); [Karthiprem et al., 2016](#chapter3.xhtml#ref3_9)).

#### 3.3.5.1 Apache Hive

`Apache Hive` works on `Apache Hadoop`. It provides a large dataset for analysis, and summarization with an ad-hoc query. The `SQL` query is used on hive called `HiveQL`. It is scalable; as data grows many machines are added to enhance the performance.

#### 3.3.5.2 Apache Spark SQL

`Apache spark SQL` has a spark model for structured data processing. It has a cost-based optimizer. It provides a code generator for fast queries. The scalability is surprisingly high with fault tolerance.

#### 3.3.5.3 Amazon Redshift

`Amazon Redshift` works on petabytes on cloud. It is used in the processing of data on a query. The database can be created on-demand when an `SQL` is running. Insight of customers and business is acquired. The overall management is coordinated by `redshift`. These tasks include the provision of cluster power, monitoring and backup, and the deployment of updates and improvements to the `Amazon Redshift` system.

#### 3.3.5.4 Presto – SQL Query Engine

`Presto` is an open-source `SQL` database engine. It is distributed to run interactive analytical queries of all volumes of a data source. It is designed for commercial use and scales to large extent. It queries data from a relational database. It aims at the analyst who operates the response for each minute. `Facebook` uses `presto` against many internal data stores. The employees execute queries greater than 40,000 and scan numerous data. `Dropbox` and `Airbnb` are examples of companies using `presto`.

### 3.3.6 Application Layer

Layer 6 is the base for `IoT` applications. This layer offers the service needed by the client. The client can use any smart app, such as smartphones, smartwatches, etc. The service rendered by this layer is identity-related service, aggregation service, and collaborative service. The identity-related support offered to the system is constantly monitored and updated. For example, consider the digitization of the medical record. The `RFID` tag has a patient identity. The data from the tag is gathered and stored in the database. On each visit, the record is updated. The stored information is extracted by web-based or mobile applications. Load delivery between smart grids is an example of data aggregation service. It reviews the information obtained from various sensors. The networks analyze the information and fed the data to the `IoT` application. Smart home automation requires data to be shared among various smart devices at home. This is an example of a collaborative service. It offers complete control and access at any point in time ([Perez et al., 2019](#chapter3.xhtml#ref3_13)).

### 3.3.7 People and Process Layer

People and process layers also involve business interaction and decision-making based on `IoT` computing. Security and data integrity are concerns while implementing `IoT` on a large scale. [Figure 3.8](#chapter3.xhtml#fig3_8) shows the deployment of security in all technology. Security breaches should be prevented, to reduce the risk of vulnerability. `International electrotechnical commission (IEC)` is an International Standard. It gives a conformity assessment for all electrical, and electronic technologies. `IoT` devices should abide by the standards and guidelines of `IEC` (Ahmed et al., 2018).

![FIGURE 3.8 IoT security.](images/fig3_8.jpg)

[FIGURE 3.8](#chapter3.xhtml#b3fig3_8) IoT security.

#### 3.3.7.1 People

The `National Institute of Standard and Technology (NIST)` continuously monitors and promotes a new standard to enhance security. A security team is a set of professionals closely working for security. When the vulnerability is detected the security team identifies the impact of severity. It debugs updates and deploys to the customer immediately.

#### 3.3.7.2 Process

There should be a strong security process before deploying a device in real time. The security process should be put into action once a device is discovered with vulnerabilities. In any device deployment, the following [Table 3.3](#chapter3.xhtml#tbl3_3) process should be considered to handle the security issues.

[TABLE 3.3](#chapter3.xhtml#b3tbl3_3) Security Process

| Process | Description |
| --- | --- |
| **Identifying** | Identify the vulnerability |
| **Isolating** | Separating it from the network of devices |
| **Validating** | Ensuring authenticity |
| **Handling** | Handling the vulnerability |

#### 3.3.7.3 Technology

Business vendors need trustworthy devices and authentic software. The chain of trust begins at the root and extends to the application layer. Data security plays a vital role. The vendors ensure data security in three forms as shown in [Figure 3.9](#chapter3.xhtml#fig3_9). The securities of data at rest, in use, in motion, are termed as secure storage, secure processing, and secure networking.

![FIGURE 3.9 Data security.](images/fig3_9.jpg)

[FIGURE 3.9](#chapter3.xhtml#b3fig3_9) Data security.
