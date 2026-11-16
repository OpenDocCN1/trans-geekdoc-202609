
## 16. Big Data: Hadoop, Spark, NoSQL and IoT

### Objectives

- Understand what big data is and how quickly it’s getting bigger.
- Manipulate a SQLite relational database using Structured Query Language (SQL).
- Understand the four major types of NoSQL databases.
- Store tweets in a MongoDB NoSQL JSON document database and visualize them on a Folium map.
- Understand Apache Hadoop and how it’s used in big-data batch-processing applications.
- Build a Hadoop MapReduce application on Microsoft’s Azure HDInsight cloud service.
- Understand Apache Spark and how it’s used in high-performance, real-time big-data applications.
- Use Spark streaming to process data in mini-batches.
- Understand the Internet of Things (IoT) and the publish/subscribe model.
- Publish messages from a simulated Internet-connected device and visualize its messages in a dashboard.
- Subscribe to PubNub’s live Twitter and IoT streams and visualize the data.

### Outline

- 16.1 Introduction
- 16.2 Relational Databases and Structured Query Language (SQL)
- 16.2.1 A books Database
- 16.2.2 SELECT Queries
- 16.2.3 WHERE Clause
- 16.2.4 ORDER BY Clause
- 16.2.5 Merging Data from Multiple Tables: INNER JOIN
- 16.2.6 INSERT INTO Statement
- 16.2.7 UPDATE Statement
- 16.2.8 DELETE FROM Statement
- 16.3 NoSQL and NewSQL Big-Data Databases: A Brief Tour
- 16.3.1 NoSQL Key–Value Databases
- 16.3.2 NoSQL Document Databases
- 16.3.3 NoSQL Columnar Databases
- 16.3.4 NoSQL Graph Databases
- 16.3.5 NewSQL Databases
- 16.4 Case Study: A MongoDB JSON Document Database
- 16.4.1 Creating the MongoDB Atlas Cluster
- 16.4.2 Streaming Tweets into MongoDB
- 16.5 Hadoop
- 16.5.1 Hadoop Overview
- 16.5.2 Summarizing Word Lengths in Romeo and Juliet via MapReduce
- 16.5.3 Creating an Apache Hadoop Cluster in Microsoft Azure HDInsight
- 16.5.4 Hadoop Streaming
- 16.5.5 Implementing the Mapper
- 16.5.6 Implementing the Reducer
- 16.5.7 Preparing to Run the MapReduce Example
- 16.5.8 Running the MapReduce Job
- 16.6 Spark
- 16.6.1 Spark Overview
- 16.6.2 Docker and the Jupyter Docker Stacks
- 16.6.3 Word Count with Spark
- 16.6.4 Spark Word Count on Microsoft Azure
- 16.7 Spark Streaming: Counting Twitter Hashtags Using the pyspark-notebook Docker stack
- 16.7.1 Streaming Tweets to a Socket
- 16.7.2 Summarizing Tweet Hashtags; Introducing Spark SQL
- 16.8 Internet of Things and Dashboards
- 16.8.1 Publish and Subscribe
- 16.8.2 Visualizing a PubNub Sample Live Stream with a Freeboard Dashboard
- 16.8.3 Simulating an Internet-Connected Thermostat in Python
- 16.8.4 Creating the Dashboard with Freeboard.io
- 16.8.5 Creating a Python PubNub Subscriber
- 16.9 Wrap-Up

### 16.1 INTRODUCTION

In Section 1.7, we introduced big data. In this capstone chapter, we discuss popular hardware and software infrastructure for working with big data, and we develop complete applications on several desktop and cloud-based big-data platforms.

### Databases

Databases are critical big-data infrastructure for storing and manipulating the massive amounts of data we’re creating. They’re also critical for securely and confidentially maintaining that data, especially in the context of ever-stricter privacy laws such as HIPAA (Health Insurance Portability and Accountability Act) in the United States and GDPR (General Data Protection Regulation) for the European Union.

First, we’ll present relational databases, which store structured data in tables with a fixed-size number of columns per row. You’ll manipulate relational databases via Structured Query Language (SQL).

Most data produced today is unstructured data, like the content of Facebook posts and Twitter tweets, or semi-structured data like JSON and XML documents. Twitter processes each tweet’s contents into a semi-structured JSON document with lots of metadata, as you saw in the “Data Mining Twitter” chapter. Relational databases are not geared to the unstructured and semi-structured data in big-data applications. So, as big data evolved, new kinds of databases were created to handle such data efficiently. We’ll discuss the four major types of these NoSQL databases—key-value, document, columnar and graph databases. Also, we’ll overview NewSQL databases, which blend the benefits of relational and NoSQL databases. Many NoSQL and NewSQL vendors make it easy to get started with their products through free tiers and free trials, and typically in cloud-based environments that require minimal installation and setup. This makes it practical for you to gain big-data experience before “diving in.”

### Apache Hadoop

Much of today’s data is so large that it cannot fit on one system. As big data grew, we needed distributed data storage and parallel processing capabilities to process the data more efficiently. This led to complex technologies like Apache Hadoop for distributed data processing with massive parallelism among clusters of computers where the intricate details are handled for you automatically and correctly. We'll discuss Hadoop, its architecture and how it's used in big-data applications. We'll guide you through configuring a multi-node Hadoop cluster using the Microsoft Azure HDInsight cloud service, then use it to execute a Hadoop MapReduce job that you'll implement in Python. Though HDInsight is not free, Microsoft gives you a generous new-account credit that should enable you to run the chapter's code examples without incurring additional charges.

### Apache Spark

As big-data processing needs grow, the information-technology community is continually looking for ways to increase performance. Hadoop executes tasks by breaking them into pieces that do lots of disk I/O across many computers. Spark was developed as a way to perform certain big-data tasks *in memory* for better performance.

We'll discuss Apache Spark, its architecture and how it's used in high-performance, real-time big-data applications. You'll implement a Spark application using functional-style filter/map/reduce programming capabilities. First, you'll build this example using a Jupyter Docker stack that runs locally on your desktop computer, then you'll implement it using a cloud-based Microsoft Azure HDInsight multi-node Spark cluster.

We'll introduce Spark streaming for processing streaming data in mini-batches. Spark streaming gathers data for a short time interval you specify, then gives you that batch of data to process. You'll implement a Spark streaming application that processes tweets. In that example, you'll use Spark SQL to query data stored in a Spark `DataFrame` which, unlike pandas `DataFrames`, may contain data distributed over many computers in a cluster.

### Internet of Things

We'll conclude with an introduction to the Internet of Things (IoT)—billions of devices that are continuously producing data worldwide. We'll introduce the *publish/subscribe model* that IoT and other types of applications use to connect data users with data providers. First, without writing any code, you'll build a web-based dashboard using Freeboard.io and a sample live stream from the PubNub messaging service. Next, you'll simulate an Internet-connected thermostat which publishes messages to the free Dweet.io messaging service using the Python module Dweepy, then create a dashboard visualization of the data with Freeboard.io. Finally, you'll build a Python client that *subscribes* to a sample live stream from the PubNub service and dynamically visualizes the stream with Seaborn and a Matplotlib `FuncAnimation`.

### Experience Cloud and Desktop Big-Data Software

Cloud vendors focus on **service-oriented architecture (SOA)** technology in which they provide “as-a-Service” capabilities that applications connect to and use in the cloud. Common services provided by cloud vendors include: 1

1 For more as-a-Service acronyms, see https://en.wikipedia.org/wiki/Cloud_computing and https://en.wikipedia.org/wiki/As_a_service.
