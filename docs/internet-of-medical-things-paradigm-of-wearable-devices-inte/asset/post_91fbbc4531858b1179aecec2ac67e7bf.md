MapReduce research trends were proposed in a study [11] in which the authors concluded that the direction of research in MapReduce concerned either enhancing its programming model or deploying existing algorithm to run on this model.

## Disadvantages of Using MapReduce

- MapReduce is designed for Online Analytical Processing (OLAP) systems only. It cannot be used in Online Transaction Processing (OLTP) systems.
- Since MapReduce processes the data on multiple systems simultaneously, the entire system needs to be set up prior to processing data.
- The MapReduce code is written in Java or Python. Hence, working knowledge of one of these languages is a must for MapReduce.
- It is only useful in applications where the task can be divided amongst multiple nodes.

An application [30] was proposed based on MapReduce where image file-books are converted into text e-books to enable searching for words in e-books.

## 2.2.6 KAFKA

Most of the technologies that were developed before the introduction of Kafka undreamed and static data. There existed technologies that worked upon streaming data [41], but their efficiency and performance was not up to the mark as required with the current technology advancements. Also not all data is fit to be streamed, but trends are shifting towards streaming data analysis. Today-one of the Fortune 500 Companies use Kafka whether they are from the telecom, travel, and banking sectors, or more. Kafka has its roots everywhere with the real-time analytics supported by powerful architecture of HDFS which is a distributed file system that allows storing static data, and batch processing can be done on a database. This type of architecture provides analysis results on historical data or any past data is required. While this approach fails processing of future messages is required as well Kafka cannot process past data, what it does goes up to the last record in the database and keeps processing the future data is an extension to previously designed technologies providing extensive functionality over them. Originally developed at LinkedIn, Kafka steadily made its presence in markets among various enterprises.

Using Apache Kafka [4], the authors proposed a system for forecasting of electricity that can predict the required power generation (i.e. close to 99% of the actual usage) using Big Data Analytics. It is often compared to other technologies like ActiveMQ or RabbitMQ for implementation in enterprises, but with its ability to handle high velocity data streams, other technologies have away. Since being developed at LinkedIn, it has a high-profile support from big companies like Netflix, Uber and others. It was written in Scala and Java originally by its developers. It has a built-in partitioning system, offers high throughput, better fault-tolerance in case system failure occurs and a great large-scale messaging system. It can be integrated with Apache Spark and Apache Storm for real-time analysis. aggregation solution is another area where Kafka is useful. It collects logs from various services across organizations and makes them available in required format for consumers. In Kafka, data is stored in the form of topics which is nothing but a stream of messages belong together. These topics are broken down into partitions, and each partition contains a subset of the original topic. Creation of partitions eases out the processing, and a larger amount of data can be handled using this approach. Kafka architecture has four core APIs:

- **Producer API**: Producers are the publishers who send data to Kafka brokers. When a producer sends a message to a broker, the simply appends the data at the end of the partition. Producer has a choice between either to send data to partition of its own choice or broker append to the last partition or any default one.

- **Consumer API**: Consumers consume data from brokers or in simple words they access the data from brokers. They subscribe the topics according to their requirements and pull the data from brokers for further processing. Data can be easily accessed in Kafka cluster due to its policy of partition creation.

- **Stream API**: Stream API takes input from various topics, processes them and generates outputs to be presented to one or more topics. These APIs are useful if data items need to be accessed from one topic to another.

- **Connector API**: Connector APIs connect the topics to applications. Also, they identify the reusable producers and consumers who can link the topics with applications. These APIs are necessary from both the user as well as system point of view.

Because of its rich set of features, various companies hire Kafka experts. The salary trends for this domain have increased significantly over the years providing more and opportunities in this sector as well. Figure 8.14 shows the cluster diagram of a Kafka ecosystem.

![](img/2dc9e3a88134e2acf1f9a7c9853b0c7c_169_0.png)

FIGURE 8.14 Kafka ecosystem [40].

## Internet of Medical Things

There are four major components shown in this diagram:

- **Brokers**: These are the load balancers of a Kafka cluster. There are multiple brokers inside a cluster to handle large amounts of data. Each broker can handle thousands of reads and writes per second which in turn contain terabytes of messages without any impact on performance. They are stateless and a leader is selected among all the brokers by ZooKeeper.
- **ZooKeepers**: These are the managers of all the brokers present in the system. They provide information to producers and consumers if any new broker is added in the system or when there is failure of any present broker. All broker activities are coordinated by ZooKeeper. Depending upon the information provided by ZooKeeper to consumers and producers, necessary action is taken by them, whether to work with a new broker or any other thing.
- **Producers**: As the data arrives to a Kafka cluster, producers seamlessly push the data to brokers irrespective of any acknowledgement. New data is appended at the end of brokers. From there on, processing of data takes place.
- **Consumers**: Data stored inside brokers are used by consumers. They issue pull requests of push requests made by producers. Every partition has offset value attached to itself.

Offset values of a message are maintained by ZooKeeper. After the producer pushes the data into cluster, an offset value is assigned to every message by ZooKeeper. The Consumer issues the pull request to ZooKeeper, accesses the data, processes it and sends an acknowledgement to ZooKeeper after completion of task. Upon receiving the acknowledgement, the offset values of the accessed messages are updated with the new values. ZooKeeper can be thought of as a synchronization mechanism between consumers and brokers to provide smooth functionality across the system. In case of system failure, a new leader among all the brokers needs to be selected which is done by the ZooKeeper. From time to time, the ZooKeeper replicates the data stored inside Kafka brokers to handle the system failure which in turn is one of the major strengths of Kafka. Kafka can be set up in two configurations depending upon requirements. One is a single broker cluster and the other is a multi-broker cluster

Figure 8.15 shows the setup of Apache Kafka with single node-broker and single ZooKeeper configuration. There are multiple producers and consumers present in the system. Figure 8.16 shows an overview of a Kafka system with single-multiple brokers and single ZooKeeper configuration. Here also there are multiple producers and consumers. Four major benefits of Kafka are Scalability, Reliability, Durability, and Performance.
