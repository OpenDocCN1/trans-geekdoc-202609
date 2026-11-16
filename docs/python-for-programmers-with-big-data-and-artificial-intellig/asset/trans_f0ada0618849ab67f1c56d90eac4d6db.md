
sys.argv[1] 转换为整数。回顾，元素 0 表示脚本的名称。

单击此处查看代码图像

```python
50 if __name__ == '__main__':
51     tweet_limit = int(sys.argv[1]) # get maximum number of tweets
```

第 52 行调用 socket 模块的 socket 函数，该函数返回一个套接字对象，我们将使用它来等待 Spark 应用程序的连接。

单击此处查看代码图像

```python
52 client_socket = socket.socket() # create a socket
53
```

第 55 行调用套接字对象的 bind 方法，传递一个包含计算机主机名或 IP 地址以及该计算机端口号的元组。它们共同表示此脚本将等待来自另一个应用的初始连接的位置：

单击此处查看代码图像

```python
54 # app will use localhost (this computer) port 9876
55 client_socket.bind(('localhost', 9876))
56
```

第 58 行调用套接字的 listen 方法，这会导致脚本等待直到接收到连接。此语句阻止 Twitter 流在 Spark 应用程序连接之前启动。

单击此处查看代码图像

```python
57 print('Waiting for connection')
58 client_socket.listen() # wait for client to connect
59
```

一旦 Spark 应用程序连接，第 61 行调用套接字方法 accept，该方法接受连接。该方法返回一个元组，包含脚本将用于与 Spark 应用程序通信的新套接字对象以及 Spark 应用程序所在计算机的 IP 地址。

单击此处查看代码图像

```python
60 # when connection received, get connection/client address
61 connection, address = client_socket.accept()
62 print(f'Connection received from {address}')
63
```

接下来，我们对 Twitter 进行身份验证并启动流。第 73–74 行设置流，将套接字对象 connection 传递给 TweetListener，以便它可以使用套接字将标签发送到 Spark 应用程序。

单击此处查看代码图像

```python
# configure Twitter access
auth = tweepy.OAuthHandler(keys.consumer_key, keys.consumer_secret)
auth.set_access_token(keys.access_token, keys.access_token_secret)

# configure Tweepy to wait if Twitter rate limits are reached
api = tweepy.API(auth, wait_on_rate_limit=True,
                 wait_on_rate_limit_notify=True)

# create the Stream
twitter_stream = tweepy.Stream(api.auth,
                               TweetListener(api, connection, tweet_limit))

# sys.argv[2] is the first search term
twitter_stream.filter(track=sys.argv[2:])
```

最后，第 79–80 行在套接字对象上调用 close 方法以释放其资源。

单击此处查看代码图像

```python
connection.close()
client_socket.close()
```

## 16.7.2 汇总推特标签；介绍 Spark SQL

在本节中，您将使用 Spark 流式处理读取通过套接字由脚本 starttweetstream.py 发送的标签并汇总结果。您可以创建新笔记本并输入此处显示的代码，也可以加载我们在 ch16 示例文件夹的 SparkHashtagSummarizer 子文件夹中提供的 hashtagsummarizer.ipynb 笔记本。

## 导入库

首先，让我们导入此笔记本中使用的库。我们将在使用 pyspark 类时对其进行说明。从 IPython 中，我们导入了 display 模块，该模块包含可在 Jupyter 中使用的类和实用函数。特别是，我们将使用 clear_output 函数在显示新图表之前删除现有图表：

单击此处查看代码图像

```python
[1]: from pyspark import SparkContext
from pyspark.streaming import StreamingContext
from pyspark.sql import Row, SparkSession
from IPython import display
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline
```

此 Spark 应用程序以 10 秒批次汇总标签。处理每个批次后，它会显示一个 Seaborn 柱状图。IPython 魔法命令

```python
%matplotlib inline
```

表示基于 Matplotlib 的图形应在笔记本中显示，而不是在各自的窗口中。回顾一下，Seaborn 使用 Matplotlib。

我们在本书中使用了多个 IPython 魔法命令。有许多专门用于 Jupyter 笔记本的魔法命令。要查看完整的魔法命令列表，请参阅：

https://ipython.readthedocs.io/en/stable/interactive/magics.html

## 获取 SparkSession 的实用函数

如您将很快看到，可以使用 Spark SQL 查询弹性分布式数据集（RDD）中的数据。Spark SQL 使用 Spark DataFrame 来获取底层 RDD 的表格视图。SparkSession（模块 pyspark.sql）用于从 RDD 创建 DataFrame。

每个 Spark 应用程序只能有一个 SparkSession 对象。以下函数（我们从 Spark 流式处理编程指南9中借用）定义了如果 SparkSession 实例已存在则获取它，如果尚不存在则创建一个的正确方法：0

9 https://spark.apache.org/docs/latest/streaming-programming-guide.html#dataframe-and-sql-operations.

0 由于此函数是从 Spark 流式处理编程指南的 DataFrame 和 SQL 操作部分（https://spark.apache.org/docs/latest/streaming-programming-guide.html#dataframe-and-sql-operations）借用的，我们没有将其重命名为使用 Python 的标准函数命名样式，也没有使用单引号来定界字符串。

单击此处查看代码图像

```python
[2]: def getSparkSessionInstance(sparkConf):
    """Spark Streaming Programming Guide's recommended method
    for getting an existing SparkSession or creating a new one."""
    if ("sparkSessionSingletonInstance" not in globals()):
        globals()["sparkSessionSingletonInstance"] = SparkSession \
            .builder \
            .config(conf=sparkConf) \
            .getOrCreate()
    return globals()["sparkSessionSingletonInstance"]
```

## 基于 Spark DataFrame 显示柱状图的实用函数

我们在 Spark 处理每个标签批次后调用函数 display_barplot。每次调用都会清除之前的 Seaborn 柱状图，然后根据其接收到的 Spark DataFrame 显示一个新图表。首先，我们调用 Spark DataFrame 的 toPandas 方法将其转换为 pandas DataFrame 以便与 Seaborn 一起使用。接下来，我们调用 IPython.display 模块中的 clear_output 函数。关键字参数 wait=True 表示该函数应删除之前的图表（如果有），但仅在新图表准备好显示时才执行。函数中的其余代码使用我们之前展示过的标准 Seaborn 技术。函数调用 sns.color_palette( 'cool', 20 ) 从 Matplotlib 库的 'cool' 调色板中选择二十种颜色：

单击此处查看代码图像

```python
[3]: def display_barplot(spark_df, x, y, time, scale=2.0, size=(16, 9)):
    """Displays a Spark DataFrame's contents as a bar plot."""
    df = spark_df.toPandas()

    # remove prior graph when new one is ready to display
    display.clear_output(wait=True)
    print(f'TIME: {time}')

    # create and configure a Figure containing a Seaborn barplot
    plt.figure(figsize=size)
    sns.set(font_scale=scale)
    barplot = sns.barplot(data=df, x=x, y=y
                        palette=sns.color_palette('cool', 20))

    # rotate the x-axis labels 90 degrees for readability
    for item in barplot.get_xticklabels():
        item.set_rotation(90)

    plt.tight_layout()
    plt.show()
```

## 到目前为止汇总前 20 个标签的实用函数

在 Spark 流式处理中，DStream 是 RDD 的序列，每个 RDD 表示要处理的数据的一个小型批次。如您将很快看到，您可以指定一个函数，该函数用于对流中的每个 RDD 执行任务。在此应用中，函数 count_tags 将汇总给定 RDD 中的标签计数，将其添加到当前总数（由 SparkSession 维护），然后显示更新的前 20 个标签柱状图，以便我们可以查看前 20 个标签随时间的变化情况。1 为方便讨论，我们将此函数分解为更小的部分。首先，通过使用 SparkContext 的配置信息调用实用函数 getSparkSessionInstance 来获取 SparkSession。每个 RDD 都可以通过 context 属性访问 SparkContext：

1 当此函数第一次被调用时，如果尚未接收到带标签的推文，您可能会看到异常错误消息显示。这是因为我们只是在标准输出中显示错误消息。一旦有带标签的推文，该消息就会消失。

单击此处查看代码图像

```python
[4]: def count_tags(time, rdd):
    """Count hashtags and display top-20 in descending order."""
    try:
        # get SparkSession
        spark = getSparkSessionInstance(rdd.context.getConf())
```

接下来，我们调用 RDD 的 map 方法
