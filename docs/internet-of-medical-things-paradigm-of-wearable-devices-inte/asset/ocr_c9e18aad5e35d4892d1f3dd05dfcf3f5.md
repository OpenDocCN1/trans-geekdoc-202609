# Internet of Medical Things

+   - Apache Kafka is installed
  i. Download Kafka
  ii. Extract tar file
  iii. Start Kafka Server

After installation of ZooKeeper and Kafka, single node-single broker can be implemented using the following steps:

+   - Start ZooKeeper
- Configure Single Node-Single Broker
  i. Get List of Topics
    Command: bin/kafka-topics.sh -list -zookeeper localhost:2181
  ii. Send Message
    Command: bin/kafka-console-producer.sh -broker-list localhost:9092 -topic topic-name
  iii. Receive Message
    Command: bin/kafka-console-consumer.sh -zookeeper localhost:2181 -topic topic-name -from-beginning
- Single Node-Multiple Broker system can be configured similarly
- Some topic options:
  i. Modify Topic
    Command: bin/kafka-topics.sh -zookeeper localhost:2181 -alter -topic name -partitions count
    Example: bin/kafka-topics.sh -zookeeper localhost:2181 -alter -topic Hello-kafka -partitions 2
  ii. Delete Topic
    Command: bin/kafka-topics.sh -zookeeper localhost:2181 -delete -topic _name
    Example: bin/kafka-topics.sh -zookeeper localhost:2181 -delete -topic Hello-kafka

User interact with Kafka by writing interactive queries and generating results thereby. This system analysed possible data-analytics assignment strategies with an I/O path and was able to overcome data movement in a given situation.

A Flex Analytics [24] system improves the flexibility and scalability of project platforms and is valid for data pre-processing, runtime data analysis as well as transfer of data at a large scale. Kafka can be downloaded from kafka.apache.org, and its setup generally includes some nowadays like Java which should be installed in systems and others. With the current advancements in technology and enterprises looking for best systems in the market, Kafka has proved its presence from time to time. The overview of Kafka is shown in Figure 8.17.