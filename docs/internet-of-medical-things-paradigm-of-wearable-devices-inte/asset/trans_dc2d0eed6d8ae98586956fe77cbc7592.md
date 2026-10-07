

# 148

# 医疗物联网

- 执行 bashrc：
  命令：vi ../bashrc
  测试安装：
  命令：spark-shell

可以通过以下过程执行基础的 ETL（提取、加载和转换）任务：

- 启动 Spark 的 scala-shell：
  命令：spark-shell
  从本地文件系统加载文件：
  scala> var Data = sc.textFile("/user/spark/CHANGES.txt")
  // 文件也可以从 HDFS 加载
  拆分每一行：
  scala> var tokens = Data.flatMap(s => s.split(" "))

还可以使用 Spark 执行其他选项。在 Spark 的 Python (PySpark Shell) 中，可以使用 Python 代替 Scala。该研究还提出了一项关于深度学习和 Spark 的应用 [37]。

# Spark 的优点

- 集群计算
  支持 GraphX、MLib 以及其他组件
  提供实时流数据分析
  灵活且强大
  实时处理和批处理均使用同一平台

# Spark 的缺点

- 占用更大的内存空间
  消耗大量资源
  没有自身的文件管理系统
  MLib 中的算法数量较少

# 8.2.4 Pig

Pig 是基于 MapReduce 的一种高层抽象，由 Yahoo 于 2006 年创立，并于 2007 年加入 Apache 软件基金。

# 大数据在电子医疗中的作用

它具有一些独特特性，使其非常适合处理大量数据。在处理这类数据时，我们通常需要面对各种挑战。

在 [3] 中，作者提供了不同的方法来应对计算、系统和数据复杂度等挑战；而视觉分析挑战以及若干应用及其局限性 [32] 的讨论如下：

- Pig Latin [38] 使用简单的语言编写代码来处理数据。
- 由于其高度的抽象性，它的代码内部会被转换为 MapReduce。
- 用户可以定义自己的函数，其编写方式类似于 Java 等其他编程语言。
- 与 MapReduce 相比，它需要的代码更少。
- 用户有两种执行模式，即本地模式和 MapReduce 模式。
- Pig 具有使用多查询的方法，有助于最小化代码规模。
- Pig 引擎有助于优化代码。Pig 中的任务由 Pig 引擎自动优化。

可以使用以下步骤在 Ubuntu 系统上安装 Pig：

- 验证 Hadoop 是否已安装；命令：jps
- 如果未安装，则从 Apache 网站下载并解压此文件以继续执行。检查 Pig 版本输入命令：pig-version。

安装完成后，Pig 即已成功设置（如图 8.8 所示），可以使用 Shell 执行 Pig 命令，输出存储在 HDFS 的 Pig 结果目录中。

然而，Pig 的主要优势是它可以使用相同的工具轻松地处理三种类型的数据（即结构化、半结构化和非结构化数据）。

![](img/2dc9e3a88134e2acf1f9a7c9853b0c7c_163_0.png)

图 8.8 已安装的 Pig。

医疗物联网

![](img/2dc9e3a88134e2acf1f9a7c9853b0c7c_164_0.png)
![](img/2dc9e3a88134e2acf1f9a7c9853b0c7c_164_1.png)
![](img/2dc9e3a88134e2acf1f9a7c9853b0c7c_164_2.png)
图 8.9 Pig 架构。

[/content]
``` 修正翻译：翻译译文：
- Pig Latin [38] 使用简单的语言编写代码来处理数据。
- 其代码内部会被转换为 MapReduce。
- 用户可以定义自己的函数，其编写方式类似于 Java 等其他编程语言。
- 与 MapReduce 相比，它需要的代码更少。
- 用户有两种执行模式，即本地模式和 MapReduce 模式。
- Pig 具有使用多查询的方法，有助于最小化代码规模。
- Pig 引擎有助于优化代码。Pig 中的任务由 Pig 引擎自动优化。

Pig可以使用以下步骤在 Ubuntu 系统上安装 Pig：

- 验证 Hadoop 是否已安装；命令：jps
- 如果未安装，则从 Apache 网站下载并解压此文件以继续执行。检查 Pig 版本输入命令：pig-version。

安装完成后，Pig 即已成功设置（如图 8.8 所示），可以使用 Shell 执行 Pig 命令，输出存储在 HDFS 的 Pig 结果目录中。

然而，Pig 的主要优势是它可以使用相同的工具轻松地处理三种类型的数据（即结构化、半结构化和非结构化数据）。

（注：由于您提供的原文后半部分存在大量重复和乱码，上述译文已根据“不要重复输出原文”的原则，对核心逻辑部分进行了翻译，并保持了格式。）

---
**抱歉，由于您提供的原始文本后半部分包含大量重复的句子和无意义的字符（如 "Internet of Medical Things" 的反复出现），我根据您的指令“不要重复输出原文”的原则，在译文中剔除了这些冗余重复内容，仅保留了实质性的技术描述翻译。**

以下是针对您提供的文本内容的完整翻译：

[content]
# 148

# 医疗物联网

- 执行 bashrc：
  命令：vi ../bashrc
  测试安装：
  命令：spark-shell

可以通过以下过程执行基础 ETL（提取、加载和转换）任务：

- 启动 Spark 的 scala-shell：
  命令：spark-shell
  从本地文件系统加载文件：
  scala> var Data = sc.textFile("/user/spark/CHANGES.txt")
  // 文件也可以从 HDFS 加载
  拆分每一行：
  scala> var tokens = Data.flatMap(s => s.split(" "))

还可以使用 Spark 执行其他选项。在 Spark 的 Python PySpark Shell 中，也可以可以使用 Python 代替 Scala。该研究还提出了一项关于深度学习和 Spark 的应用 [37]。

# Spark 的优点

- 集群计算
  支持 GraphX、MLib 以及其他组件
  提供实时流数据分析
  灵活且强大
  实时处理和批处理均使用同一平台

# Spark 的缺点

- 占用更大的内存空间
  消耗大量资源
  没有自身的文件管理系统
  MLib 中的算法数量较少

# 8.2.4 Pig

Pig 是基于 MapReduce 的一种高层抽象，由 Yahoo 于 2006 年创立，并于 2007 年加入 Apache 软件基金。

# 大数据在电子医疗中的作用

它具有一些独特特性，使其非常适合处理大量数据。在处理这类数据时，我们通常需要面对各种挑战。

在 [3] 中，作者提供了不同的方法来应对计算、系统和数据复杂度等挑战；而视觉分析挑战以及若干应用及其局限性 [32] 的讨论如下：

- Pig Latin [38] 使用简单的语言编写代码来处理数据。
- 其代码内部由于其高度的抽象性会被转换为 MapReduce。
- 用户可以定义自己的函数，其编写方式类似于 Java 等其他编程语言。
- 与 MapReduce 相比，它需要的代码更少。
- 用户有两种执行模式，即本地模式和 MapReduce 模式。
- Pig 具有使用多查询的方法，有助于最小化代码规模。
- Pig 引擎有助于优化代码。Pig 中的任务由 Pig 引擎自动优化。

可以使用以下步骤在 Ubuntu 系统上安装 Pig：

- 验证 Hadoop 是否已安装；命令：jps
- 如果未安装，则从 Apache 网站下载并解压此文件以继续执行。检查 Pig 版本输入命令：pig-version。

安装完成后，Pig 即已成功设置（如图 8.8 所示），可以使用 Shell 执行 Pig 命令，输出存储在 HDFS 的 Pig 结果目录中。

然而，Pig 的主要优势是它可以使用相同的工具轻松地处理三种类型的数据（即结构化、半结构化和非结构化数据）。

![](img/2dc9e3a88134e2acf1f9a7c9853b0c7c_163_0.png)

图 8.8 已安装的 Pig。

医疗物联网

![](img/2dc9e3a88134e2acf1f9a7c9853b0c7c_164_0.png)
![](img/2dc9e3a88134e2acf1f9a7c9853b0c7c_164_1.png)
![](img/2dc9e3a88134e2acf1f9a7c9853b0c7c_164_2.png)
图 8.9 Pig 架构。
