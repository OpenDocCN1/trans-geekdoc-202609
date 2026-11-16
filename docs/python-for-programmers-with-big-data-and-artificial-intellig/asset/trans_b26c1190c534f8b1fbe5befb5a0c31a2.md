

## 修改笔记本以适用于 Azure

执行以下步骤，在完成每个步骤时执行每个单元格：

- 1. HDInsight 群集不允许 NLTK 将下载的停用词存储在 NLTK 的默认文件夹中，因为它是系统受保护文件夹的一部分。在第一个单元格中，按如下修改调用 `nltk.download('stopwords')`，以将停用词存储在当前文件夹 (`'.'`) 中：

```
nltk.download('stopwords', download_dir='.')
```

执行第一个单元格时，HDInsight 为你设置名为 sc 的 SparkContext 对象，下方会显示“正在启动 Spark 应用程序”。任务完成后，单元格的代码将执行并下载停用词。

- 2. 在第二个单元格中，在加载停用词之前，必须告诉 NLTK 它们位于当前文件夹。在 import 语句之后添加以下语句，以告诉 NLTK 在当前文件夹中搜索其数据：

```
nltk.data.path.append('.')
```

- 3. 由于 HDInsight 为你设置了 SparkContext 对象，原始笔记本的第三个和第四个单元格不再需要，因此你可以删除它们。要执行此操作，请单击单元格内部并从 Jupyter 的 **编辑** 菜单中选择 **删除单元格**，或者单击单元格左侧的空白边距并键入 dd。

- 4. 在下一个单元格中，指定底层 Hadoop 文件系统中 RomeoAndJuliet.txt 的位置。将字符串 'RomeoAndJuliet.txt' 替换为字符串

```
'wasb://example/data/RomeoAndJuliet.txt'
```

记法 `wasb://` 表示 RomeoAndJuliet.txt 存储在 Windows Azure 存储 Blob (WASB) 中——即 Azure 对 HDFS 文件系统的接口。

- 5. 因为 Azure 当前使用 Python 3.5.x，不支持 f-string。因此，在最后一个单元格中，使用字符串方法 `format` 的旧式 Python 字符串格式化替换 f-string：

```
print('{:>{width}}: {}'.format(word, count, width=max_len))
```

你将看到与上一部分相同的最终结果。

**注意：** 使用完群集和其他资源后，请务必将其删除，以免产生费用。有关详细信息，请参阅：

```
https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-po
```

请注意，删除 Azure 资源时，你的笔记本也会被删除。你可以在 Jupyter 中选择“文件” > “下载为” > “笔记本 (.ipynb)”来下载刚才执行的笔记本。

## 16.7 Spark 流式处理：使用 PySpark-Notebook Docker 堆栈统计 Twitter 标签

在本节中，你将创建并运行一个 Spark 流式处理应用程序，用于接收你指定主题的推文流，并在每 10 秒更新一次的条形图中汇总前 20 个标签。为此示例，你将使用第一个 Spark 示例中的 Jupyter Docker 容器。

此示例包含两部分。首先，使用“Twitter 数据挖掘”章节中的技术，你将创建一个从 Twitter 流式传输推文的脚本。然后，我们将在 Jupyter Notebook 中使用 Spark 流式处理来读取推文并汇总标签。

这两个部分将通过网络套接字相互通信——这是客户端/服务器网络的低级视图，其中客户端应用程序通过网络使用类似于文件 I/O 的技术与服务器应用程序进行通信。程序可以从套接字读取或向套接字写入，类似于从文件读取或向文件写入。套接字表示连接的一端。在此示例中，客户端将是 Spark 应用程序，服务器将是接收流式推文并将其发送到 Spark 应用的脚本。

### 启动 Docker 容器并安装 Tweepy

为此示例，你将 Tweepy 库安装到 Jupyter Docker 容器中。按照第 16.6.2 节的说明启动容器并向其中安装 Python 库。使用以下命令安装 Tweepy：

```
pip install tweepy
```

### 16.7.1 将推文流式传输到套接字

脚本 `starttweetstream.py` 包含“Twitter 数据挖掘”章节中 `TweetListener` 类的修改版本。它流式传输指定数量的推文，并将其发送到本地计算机上的套接字。达到推文限制后，脚本会关闭套接字。你以前已使用过 Twitter 流式处理，因此我们将仅关注此处的新内容。请确保文件 `keys.py`（位于 `ch16` 文件夹的 `SparkHashtagSummarizer` 子文件夹中）包含你的 Twitter 凭据。

### 在 Docker 容器中执行脚本

在此示例中，你将使用 JupyterLab 的 Terminal 窗口在一个选项卡中执行 `starttweetstream.py`，然后在另一个选项卡中使用笔记本执行 Spark 任务。在 Jupyter `pyspark-notebook` Docker 容器运行时，在 Web 浏览器中打开

```
http://localhost:8888/lab
```

。在 JupyterLab 中，选择 **文件 > 新建 > 终端** 以打开包含 **终端** 的新选项卡。这是基于 Linux 的命令行。键入 `ls` 命令并按 `Enter` 键会列出当前文件夹的内容。默认情况下，你将看到容器的 `work` 文件夹。

要执行 `starttweetstream.py`，必须首先使用以下命令导航到 SparkHashtagSummarizer 文件夹：

Windows 用户应注意，Linux 使用 / 而不是 \ 分隔文件夹，且文件和文件夹名称区分大小写。

```
cd work/SparkHashtagSummarizer
```

现在可以使用以下形式的命令执行脚本：

```
ipython starttweetstream.py number_of_tweets search_terms
```

其中 `number_of_tweets` 指定要处理的推文总数，而 `search_terms` 是一个或多个用空格分隔的字符串，用于筛选推文。例如，以下命令将流式传输 1000 条关于 football 的推文：

```
ipython starttweetstream.py 1000 football
```

此时，脚本将显示“等待连接”，并等待 Spark 连接以开始流式传输推文。

### starttweetstream.py import 语句

出于讨论目的，我们已将 `starttweetstream.py` 分成几个部分。首先，我们导入脚本中使用的模块。Python 标准库的 `socket module` 提供了使 Python 应用程序能够通过套接字进行通信的功能。

单击此处查看代码图像

```
1 # starttweetstream.py
2 """Script to get tweets on topic(s) specified as script argument(s)
3   and send tweet text to a socket for processing by   Spark."""
4 import keys
5 import socket
6 import sys
7 import tweepy
8
```

### 类 TweetListener

再次，你已经看到类 TweetListener 中的大部分代码，因此我们仅在此关注新内容：

- 方法 `__init__`（第 12–17 行）现在接收一个 `connection` 参数，表示套接字，并将其存储在 `self.connection` 属性中。我们使用此套接字将标签发送到 Spark 应用程序。

- 在方法 `on_status`（第 24–44 行）中，第 27–32 行从 Tweepy Status 对象提取标签，将其转换为小写，并创建一个空格分隔的标签字符串以发送到 Spark。关键语句是第 39 行：

```
self.connection.send(hashtags_string.encode('utf-8'))
```

这使用连接对象的 send 方法将推文文本发送到正在从该套接字读取的任何应用程序。send 方法期望其参数为字节序列。字符串方法调用 encode('utf-8') 将字符串转换为字节。Spark 将自动读取字节并重建字符串。

单击此处查看代码图像

```
9 class TweetListener(tweepy.StreamListener):
10 """Handles incoming Tweet stream."""
11
12 def __init__(self, api, connection, limit=10000):
13 """Create instance variables for tracking number of tweets."""
14 self.connection = connection
15 self.tweet_count = 0
16 self.TWEET_LIMIT = limit # 10,000 by default
17 super().__init__(api) # call superclass's init
18
19 def on_connect(self):
20 """Called when your connection attempt is successful, enabling
21 you to perform appropriate application tasks at that point."""
22 print('Successfully connected to Twitter\n')
23
24 def on_status(self, status):
25 """Called when Twitter pushes a new tweet to you."""
26 # get the hashtags
27 hashtags = []
28
29 for hashtag_dict in status.entities['hashtags']:
30 hashtags.append(hashtag_dict['text'].lower())
31
32 hashtags_string = ' '.join(hashtags) + '\n'
33 print(f'Screen name: {status.user.screen_name}:')
34 print(f' Hashtags: {hashtags_string}')
35 self.tweet_count += 1 # track number of tweets processed
36
37 try:
38 # send requires bytes, so encode the string in utf-8 format
39 self.connection.send(hashtags_string.encode('utf-8'))
40 except Exception as e:
41 print(f'Error: {e}')
42
43 # if TWEET_LIMIT is reached, return False to terminate streaming
44 return self.tweet_count != self.TWEET_LIMIT
45
46 def on_error(self, status):
47 print(status)
48 return True
49
```

### 主应用程序

运行脚本时，第 50–80 行将执行。你以前已连接到 Twitter 以流式传输推文，因此此处仅讨论此示例中的新内容。

第 51 行通过转换命令行参数来获取要处理的推文数量

