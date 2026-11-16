+   1. Click **Edit** to the right of **Cluster size**.

+   2. Change the **Number of Worker** nodes to 2.

+   3. Click **Worker node size**, then **View all**, select **D3 v2** (this is the minimum CPU size for Hadoop nodes) and click **Select**.

+   4. Click **Head node size**, then **View all**, select **D3 v2** and click **Select**.

+   5. Click **Next** and click **Next** again to return to the **Cluster summary**. Microsoft will validate the new configuration.

+   6. When the **Create** button is enabled, click it to deploy the cluster.

It takes 20–30 minutes for Microsoft to “spin up” your cluster. During this time, Microsoft is allocating all the resources and software the cluster requires.

After the changes above, our estimated cost for the cluster was $1.18 per hour, based on _average_ use for similarly configured clusters. Our actual charges were less than that. If you encounter any problems configuring your cluster, Microsoft provides HDInsight chat-based support at:

```
https://azure.microsoft.com/en-us/resources/knowledge-center/technical--chat/
```

# 16.5.4 Hadoop Streaming

For languages like Python that are not natively supported in Hadoop, you must use **Hadoop streaming** to implement your tasks. In Hadoop streaming, the Python scripts that implement the mapping and reduction steps use the **standard input stream** and **standard output stream** to communicate with Hadoop. Usually, the standard input stream reads from the keyboard and the standard output stream writes to the command line. However, these can be _redirected_ (as Hadoop does) to read from other sources and write to other destinations. Hadoop uses the streams as follows:

+   • Hadoop supplies the input to the mapping script—called the **mapper**. This script reads its input from the standard input stream.

+   • The mapper writes its results to the standard output stream.

+   • Hadoop supplies the mapper’s output as the input to the reduction script—called the **reducer**—which reads from the standard input stream.

+   • The reducer writes its results to the standard output stream.

+   • Hadoop writes the reducer’s output to the Hadoop file system (HDFS).

The mapper and reducer terminology used above should sound familiar to you from our discussions of functional-style programming and filter, map and reduce in the “Sequences: Lists and Tuples” chapter.