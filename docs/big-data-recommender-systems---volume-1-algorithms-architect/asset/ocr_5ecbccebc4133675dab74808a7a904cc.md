# 236 Big data recommender systems, volume 1

user-based and item-based algorithms may present higher stability. Also, we studynthe basics of relevant research and advanced schemas, and discuss future thoughts.

#  11.2 Security issues and approaches in HDFS architecture

A big data recommender system gathers and analyzes a large amount of raw data. Hadoop is used to store and manage a large amount of data and distribute data analysis between a number of servers. HDFS is the file system for Hadoop architecture and has security problems. In this section, we present security problems in HDFS. The HDFS will become more secure by using some algorithms such as Kerberos.

HDFS is the Hadoop file system that is scalable and reliable and as its name shows, it is distributed. A cluster of HDFS consists of a node name and a number of nodes. By using special hardware, you can store a large amount of data in lower latency and do some operations as Write Once and Read several times. In these special hardware devices, you can store in blocks of 64 MB, which is the default size. Different nodes communicate with each other using remote procedure calls (RPCs). Name nodes reserve special data such as file name, copies of file, properties and block addresses. These data can be stored in random access memory (RAM), for retrieving so fast. Also, this leads to loss of data and helps stop system correction. Moreover, name nodes enumerate blocks and if they find out any block is absent or is not copied successfully, they create a right copy of that failed or lost block. A timestamp is attached to any block to recognize its current situation. It is not necessary to repair a failed node immediately, but failed nodes can be repaired in scheduled times. An operator supports more than 1,000 nodes in HDFS [1]. Blocks are copied, and sent and received between nodes. In Hadoop, original node that copies a block is called rack 1 and the other node is known as rack 2. This framework does not support caching data [2–4] because of large amount of data. Figure 11.1 shows HDFS architecture.

![](bbox=[0.198, 0.646, 0.803, 0.856])

Figure 11.1 HDFS architecture [5]