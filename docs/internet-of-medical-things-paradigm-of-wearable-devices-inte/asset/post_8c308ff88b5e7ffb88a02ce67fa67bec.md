
## Role of Big Data in e-Healthcare

In Big Data is not left behind. Most of the Cloud service providers use Big Data with the NoSql for maintaining their databases.

In one study, the author described [6] data management challenges for Big Data and Cloud such as Approximate Results, Data Privacy, Enterprise Data Enrichment with Data exploration to enable Deep Analytics, and social media. Organizations across the world strive to save big on every transaction they are involved in and to maximize profits. So, does it mean that introduction of this dynamic approach towards the past technology will shift the market towards the newly introduced? The answer is simple, in the long term, and in the short term not so much. People who have invested a lot of money in building up the infrastructure based upon previous technologies might not have to suffer losses, as these structures are literally the backbone of their organizations, and completely shutting down the whole system to a new one is not a beneficial option at the present time. One of the critical situations that users face is this database approach to, i.e. SQL or NoSql so that their needs are completely fulfilled. The SQL approach has ruled the past decades providing uniformity and functionality, as the advancements in other domains are happening. Big Data is not left behind in this race. Before NoSql came into the picture, huge databases needed to be maintained were difficult to maintain. Inducing intelligence to gain importance, MapReduce is used to implement large amounts of data. A study [9], concluded that in the four years Google implemented (>10 thousand) MapReduce which is executed on Google clusters to process data (>20 petabytes) per day.

In [31], the authors discussed the use of Big Data and utilization of its methods in the business (i.e., at the global level)! With this small application, people can share their information any time and place. Revolution come into the industry with the development of Hadoop, and with this revolution older technologies starting fast. The biggest advantage in Hadoop was that it was based on distributed computing. Networks were divided into master and slave nodes which enhanced the computing power of a system. By similarity of Hadoop and NoSql, a buzz was created in the tech industry as both can hand-in-hand provide extensive features with each. NoSql databases can be of different forms like graph, object databases, XML databases, Grid and Cloud, document database, key-value pairs or wide-column stores. These databases do not follow any strict schema design and are suitable for Big Data. One more thing emerges when someone deals with Big Data, i.e., how to scale up the processing to data arriving at faster rates. If someone goes with the relational database concept to manage this much data and that too with many variations, then in some way or another results that will be generated is either erroneous or incomplete, or any unwanted situation may arise as system failure, data corruption, etc. NoSql does not follow Atomicity, Consistency, Isolation and Durability (ACID) properties as seen in the case of an SQL approach. When a user submits a query to be operated upon a database, priority is to get the result as soon as possible putting aside the importance of getting the right answer. Therefore, NoSql possesses a weak consistency.

## Internet of Medical Things

Privacy is also a major factor which decides the performance of any technology. In [22], the authors discussed the need for privacy integration and awareness about security in Big Data platforms. Further, they discussed issues related to the framework which supports privacy access control features in Big Data platforms. There are numerous applications developed using NoSQL approach. The role of Big Data in road transport policies (i.e., Europe) is further discussed [13]. Next, a Cloud computing technique with Big Data was used to analyse the performance of Smart Grids so that customer cost could be reduced in managing data over network [15]. Recommendation and prediction systems are also mostly based on the NoSQL approach. In [17] the authors proposed a personalized contents recommendation service using Big Data with a small sample so that it accurately predicts the user's performance. It predicts using Big Data with a variety of user information. In another work [18], a model was proposed for analysing and monitoring traffic over the Internet to enhance the quality which is used to promote online investments. Sensor devices are frequently used these days. Data is generated from these devices as well. In [20], the authors summarised the expansion of sensors in Big Data systems (in urban environments), including for assisted living, air pollution monitoring, intelligent transportation, and disaster management systems. With the rapid expansion of fully sequenced and animated plant genomes, plant science has benefited from next sequencing. Authors proposed [26] mechanisms for studying the transcription control of various species using Big Data. Dynamics of life is also studied of various genomes. With a powerful tool (Big Data) in hand, the future can also be predicted. In another application [29], the authors proposed a wind turbine conditioning monitoring system in increasing volumes of data are being captured and stored as Big Data. The system's capability of capturing huge amounts of data led to the necessity of using enhanced data handling techniques.

It can be clearly observed that for the big techniques like Microsoft, IBM, SAP and others, the trend has shifted towards the NoSQL approach.

## Advantages of NoSQL

- Economical
- Big Data applications
- Less support required from database administrator
- Scalable and reliable
- Flexible data models

## Disadvantages of NoSQL

- Less measure
- Less support
- Analytics and business intelligence issues
- Administration is difficult
- Fewer expert people

This does not mean that using an SQL approach will lead to losses, but the ball is definitely in NoSql's court, proving its edge over the RDBMS approach.

## Role of Big Data in e-Healthcare

### Ambari

| Pig | Hive |
|---|---|
| MapReduce | HBase |
| HDFS(Hadoop Distributed File System) | |
| YARN | Hadoop Common |

FIGURE 8.2 Hadoop architecture.

### 8.2.2 HADOOP

Hadoop is a framework written in Java language and is freely available online. It is founded by Doug Cutting and Mike Cafarella, who originated from a paper that was published in 2003 "Google File System". It was named Hadoop after his son's toy. Initially, Hadoop contained only MapReduce for data processing. With the development of new modules, Hadoop has become an ecosystem of various data processing technologies like MapReduce, Pig, etc.

Figure 2.2 shows the architecture of Hadoop which is adequate for storing huge amounts of data in Hadoop Distributed File System (HDFS) and processing using various programming models like MapReduce, Pig, etc. [16].

The Apache framework modules are described below:

- **Hadoop Common**: Consists of all Java libraries and other functions required for the basic running of Hadoop and other Hadoop utilities. Hence, it is composed of various Java Archive (JAR) files.
- **YARN** Another Resource Negotiator: It is a cluster management technology in Hadoop. It has three components named Resource Manager, Node Manager and Application Manager.
- **HDFS**: It is the main storage in Hadoop. It ensures reliable storage of data by storing a copy of the data on top of HDFS. It is a column-oriented database which can be used to store and retrieve the data from HDFS.
- **HBase**: Compared to HDFS, it provides faster lookup and it provides random access to data.
- **MapReduce**: The main functionality of MapReduce is to process data in two ways (i.e., Map and Reduce), and it is developed by Google. Role of Map is to convert the data into intermediate pairs of values or keys, whereas Reduce uses this intermediate data to produce the final result.
- **Pig**: Pig is a tool used to analyse big data sets. Pig contains a programming language called Pig-Latin to access and manipulate data. Furthermore, User Defined Functions (UDFs) in Pig allow users to integrate function written in different languages like Java and Jython.
