# Role of Big Data in e-Healthcare

# Ambari

| Pig | Hive |
|---|---|
| MapReduce | HBase |
| HDFS(Hadoop Distributed File System) |
| YARN | Hadoop Common |

FIGURE 8.2 Hadoop architecture.

# 8.2.2 HADOOP

Hadoop is a framework written in Java language and is freely available online. It is founded by Doug Cutting and Mike Cafarella, who originated from a paper that was published in October 2003 "Google File System". It was named Hadoop by Cutting after his son's toy elephant. Initially, Hadoop contained only MapReduce for data processing. With the development of new modules, Hadoop has become an ecosystem of various data processing technologies like MapReduce, Pig, Hive, etc.

Figure 2.2 shows the architecture of Hadoop which is adequate for storing huge amounts of data in Hadoop Distributed File System (HDFS) and processing using various programming models like MapReduce, Pig, etc. [16].

The Apache framework modules are described below:

+   - **Hadoop Common**: Consists of all Java libraries and other functions required for the basic running of Hadoop and other Hadoop utilities. Hence, it is composed of various Java Archive (JAR) files.
- **YARN** Another Resource Negotiator: It is a cluster management technology in Hadoop. It has three components named Resource Manager, Node Manager and Application Manager.
- **HDFS**: It is the main storage in Hadoop. It ensures reliable storage of data by storing a copy of the data on top of HDFS. It is a column-oriented database which can be used to store and retrieve the data from HDFS.
- **HBase**: Compared to HDFS, it provides faster lookup and it provides random access to data.
- **MapReduce**: The main functionality of MapReduce is to process data in two ways (i.e., Map and Reduce), and it is developed by Google. Role of Map is to convert the data into intermediate pairs of values or keys, whereas Reduce uses this intermediate data to produce the final result.
- **Pig**: Pig is a tool used to analyse big data sets. Pig contains a programming language called Pig-Latin to access and manipulate data. Furthermore, User Defined Functions (UDFs) in Pig allow users to integrate function written in different languages like Java and Jython.