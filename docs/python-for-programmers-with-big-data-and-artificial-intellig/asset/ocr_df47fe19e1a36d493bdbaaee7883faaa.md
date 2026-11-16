# Getting the SparkContext

The rest of the code in this notebook sets up Spark streaming to read text from the starttweetstream.py script and specifies how to process the tweets. First, we create the SparkContext for connecting to the Spark cluster:

```
[5]: sc = SparkContext()
```

# Getting the StreamingContext

For Spark streaming, you must create a StreamingContext (module pyspark.streaming), providing as arguments the SparkContext and how often in seconds to process batches of streaming data. In this app, we'll process batches every 10 seconds—this is the batch interval:

lick here to view code image

```
[6]: ssc = StreamingContext(sc, 10)
```

Depending on how fast data is arriving, you may wish to shorten or lengthen your batch intervals. For a discussion of this and other performance-related issues, see the Performance Tuning section of the Spark Streaming Programming Guide:

```
https://spark.apache.org/docs/latest/streaming-programming-guide.html#performan
```

# etting Up a Checkpoint for Maintaining State

By default, Spark streaming does not maintain state information as you process the stream of RDDs. However, you can use Spark checkpointing to keep track of the streaming state. Checkpointing enables:

+   • fault-tolerance for restarting a stream in cases of cluster node or Spark application failures, and
+   • stateful transformations, such as summarizing the data received so far—as we're doing in this example.

StreamingContext method checkpoint sets up the checkpointing folder:

lick here to view code image

```
[7]: ssc.checkpoint('hashtagsummarizer_checkpoint')
```

For a Spark streaming application in a cloud-based cluster, you'd specify a location within HDFS to store the checkpoint folder. We're running this example in the local Jupyter Docker image, so we simply specified the name of a folder, which Spark will create in the current folder (in our case, the ch16 folder's SparkHashtagSummarizer). For more details on checkpointing, see