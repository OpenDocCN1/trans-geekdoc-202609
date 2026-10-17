
`![Mathtype978-1-7998-2701-6.ch007.m97](img/ch007.m97.svg)` 的条目指向一个叶子节点，即节点 5。节点 5 未装满，有两个被索引对象 `![Mathtype978-1-7998-2701-6.ch007.m98](img/ch007.m98.svg)` 和 `![Mathtype978-1-7998-2701-6.ch007.m99](img/ch007.m99.svg)` 的条目。在节点 5 中，

`![Mathtype978-1-7998-2701-6.ch007.m100](img/ch007.m100.svg)`

`![Mathtype978-1-7998-2701-6.ch007.m101](img/ch007.m101.svg)`

和

`![Mathtype978-1-7998-2701-6.ch007.m102](img/ch007.m102.svg)`

其余节点与上述类似。

## 方法论

为了解决相似性搜索问题，我们可以计算查询向量与向量空间中所有其他向量之间的距离。然而，这种方法仅适用于小型向量空间。在大型向量空间中，我们必须寻找一种能够减少距离计算次数的方法。我们研究了许多方法，并意识到 M-Tree 可以帮助我们实现这一目标。因此，我们使用 Scala 语言实现了本地 M-Tree 结构（在单机上运行）。随后，我们在 Apache Spark 框架上使用 Scala 语言实现了分布式 M-Tree。我们还对本地和分布式 M-Tree 结构进行了大量实验。M-Tree 结构在单机上进行测试，DM-Tree 结构在 Spark 集群上进行测试，如图 8 所示。以下是我们解决方案的详细信息。

我们基于 (Ciaccia et al., 1997; Kouahla, 2011) 使用 Scala 语言创建了 `M-Tree` 类来表示本地 M-Tree 结构。`M-Tree` 类有两个用于搜索相似性的重要方法，如下所示：

*   `def kNNSearch(Q: Entry, k: Int): ListBuffer[(Long, Double)]`：执行 kNN 查询，并返回 Q 条目的 k 个最近邻条目的 k 对 (id, distance)。
*   `def rangeSearch(Q: Entry, rQ: Double): ListBuffer[(Long, Double)]`：执行范围查询，返回满足从 Q 到条目距离小于或等于 rQ 的条目对 (id, distance)。

我们不在此展示这些算法，因为它们已在 (Ciaccia et al., 1997) 中描述。

在大数据时代，我们拥有包含大量表示图像或视频片段向量的大型多媒体数据库。为了存储大型向量空间，我们使用 Hadoop 框架的 HDFS 分布式文件系统 (Zecevic & Bonaci, 2017)。除了 HDFS，我们还可以使用其他分布式文件系统，如 Amazon S3、Google File System 等。为了解决在大型向量空间中搜索相似性的问题，我们构建了一个分布式 M-Tree 结构并将其命名为 DM-Tree。

### 表 1. DM-Tree 类的属性

| Properties | Types | Descriptions |
| --- | --- | --- |
| CAPACITY | Int | DM-Tree 对象的容量。 |
| M-Trees | `RDD[(Int, M-Tree)]` | 存储 M-Tree 对象及其 id。 |

### 表 2. DM-Tree 类的方法

| Methods | Descriptions |
| --- | --- |
| `def createFrom(path: String, CAPACITY: Int): DM-Tree` | 从包含向量的 HDFS 文件创建 DM-Tree 对象。 |
| `def save(path: String, dmtree: DM-Tree): Unit` | 将 DM-Tree 对象存储到 HDFS 中。 |
| `def load(path: String): DM-Tree` | 从 HDFS 加载 DM-Tree 对象。 |
| `def rangeSearch(Q: String, rQ: Double): ListBuffer[(Long,Double)]` | 执行范围查询。 |
| `def kNNSearch(Q: String, k: Int): ListBuffer[(Long,Double)]` | 执行 kNN 查询。 |

以下是应用于 DM-Tree 类中的算法详情。

## 创建 DM-Tree 结构

### 图 3. 从向量集创建 DM-Tree 结构的过程

![Figure978-1-7998-2701-6.ch007.f03](img/ch007.f03.png)

创建 DM-Tree 结构的过程如图 3 所示。首先，我们将向量集从 Hadoop 框架的 HDFS 分布式文件系统加载到 Apache Spark 集群的 RDD 结构中 (Zecevic & Bonaci, 2017)。然后，在 RDD 结构的每个分区上，我们通过使用 Map 转换创建一个 M-Tree 结构。Map 转换类似于 forEach 循环，但它并行执行任务。由 RDD 结构的分区创建的一组 M-Tree 结构即为 DM-Tree 结构。因为我们可以配置 RDD 结构的分区数量，所以 DM-Tree 结构的 M-Tree 结构数量也可以配置。算法 1 详述了创建 DM-Tree 结构的算法。

### 算法 1. 从向量集创建 DM-Tree 对象的算法

**输入**：

1. `path`：包含向量集的 HDFS 文件路径。
2. `CAPACITY`：DM-Tree 对象中 M-Tree 对象的容量。

**输出**：一个 DM-Tree 对象。

1. 将向量集的 HDFS 文件加载到 Spark 集群的 RDD 对象中。
2. 使用 `CAPACITY` 作为 DM-Tree 对象中 M-Tree 对象的容量，创建一个新的 DM-Tree 对象。
3. 将 RDD 对象的每个分区映射到 DM-Tree 对象中的一个 M-Tree 对象（即并行地从 RDD 对象的每个分区创建一个 M-Tree 对象）。
4. 返回 DM-Tree 对象。

## 存储 DM-Tree 结构

由于创建 DM-Tree 结构耗时，我们需要存储 DM-Tree 结构以便后续复用。此外，向量空间可能非常大，因此 DM-Tree 结构也可能非常大。我们无法将 DM-Tree 结构存储在本地文件系统中，而必须存储在像 HDFS 这样的分布式文件系统中。算法 2 详述了将 DM-Tree 结构存储到 HDFS 的算法。

### 算法 2. 将 DM-Tree 对象存储到 HDFS 的算法

**输入**：

1. `path`：将存储 DM-Tree 对象的 HDFS 中目录的路径。
2. `dmtree`：将被存储到 HDFS 的 DM-Tree 对象。

**输出**：无。

1. 存储 DM-Tree 对象的信息，如：DM-Tree 对象的容量、DM-Tree 对象中 M-Tree 对象的数量。
2. 映射 DM-Tree 对象中的每个 M-Tree 对象 {
3. 将 M-Tree 对象存储到由 `path` 指定的 HDFS 目录中。
4. }
5. 返回。

## 加载 DM-Tree 结构

当我们需要在向量空间中有效地搜索相似性时，我们需要将 DM-Tree 结构从 HDFS 加载到 Spark 集群中。因为 DM-Tree 结构由一组 M-Tree 结构组成，每个执行器应该加载一个 M-Tree 结构以有效处理。因此，执行器的数量应等于 M-Tree 结构的数量。算法 3 详述了从 HDFS 加载 DM-Tree 对象的算法。

### 算法 3. 从 HDFS 加载 DM-Tree 对象的算法

**输入**：

1. `path`：存储 DM-Tree 对象的 HDFS 中目录的路径。

**输出**：一个 DM-Tree 对象。

1. 加载 DM-Tree 对象的信息，如：DM-Tree 对象的容量、DM-Tree 对象中 M-Tree 对象的数量。
2. 使用加载的容量创建一个新的 DM-Tree 对象。
3. 从每个执行器并行加载由 `path` 指定目录中文件中的 DM-Tree 对象的 M-Tree 对象。
4. 返回 DM-Tree 对象。

## 执行分布式 kNN 查询

分布式 kNN 查询是在 DM-Tree 结构上进行的 kNN 查询。图 4 展示了执行分布式 kNN 查询的过程。首先，主节点中的驱动程序通过使用 Map 转换向工作节点中的 M-Tree 对象发送执行 kNN 查询的请求。然后，驱动程序将结果从工作节点收集到主节点，并通过使用 Reduce 动作将它们合并为单个结果。结果按距离升序排序，然后从排序后的结果中提取前 k 个条目。算法 4 详述了执行分布式 kNN 查询的算法。

### 图 4. 执行分布式 kNNSearch(Q, k) 的过程

![Figure978-1-7998-2701-6.ch007.f04](img/ch007.f04.png)

### 算法 4. 在 DM-Tree 对象上执行分布式 kNN 查询的算法

**输入**：

1. `Q`：一个查询向量。
2. `k`：查询向量的最近邻数量。

**输出**：一个包含 (id, distance) 对的列表，其中 id 是向量的 id，distance 是从 Q 到该向量的距离。

```
1. 映射 DM-Tree 对象的 M-Tree 对象 RDD 中的每个 `mtree` 对象 {
2.   设置 `result = mtree.kNNSearch(Q, k)`
3. }
4. 将结果从工作节点收集到主节点。
5. 设置 `unionResult = union` 收集到的结果。
6. 设置 `sortedResult = unionResult.sortBy("distance", "ascending")`。
7. 返回 `sortedResult.top(k)`。
```

算法 4 成功解决了 kNN 搜索问题。然而，该算法仍有一个需要改进的缺点。即每个工作节点向主节点发送 k 个向量，然后主节点排序并仅选择最接近查询向量的 k 个向量。因此，存在发送到主节点但从未被使用的向量。这增加了从工作节点无谓传输到主节点的数据量，降低了算法的效率。然而，改进这一缺点并不简单。我们需要做更多研究。

## 执行分布式范围查询

### 图 5. 执行分布式 RangeSearch(Q, rQ) 的过程

![Figure978-1-7998-2701-6.ch007.f05](img/ch007.f05.png)

### 分布式范围查询

分布式范围查询是针对 `DM-Tree` 结构的范围查询。图 5 展示了执行分布式范围查询的过程。首先，驱动程序通过 `Map` 变换向工作节点中的 `M-Tree` 对象发送执行范围查询的请求。然后，驱动程序将结果从工作节点收集到主节点，并通过 `Reduce` 动作将它们合并为单个结果。为了便于观察，结果按距离升序排序。算法 5 详细描述了在 `DM-Tree` 结构上执行范围查询的算法。

### 算法 5. 执行分布式范围查询的算法

**输入：**

1. `Q`：查询向量。
2. `rQ`：最大距离。

**输出：** 一组键值对列表 `(id, distance)`，其中 `id` 是向量的 ID，`distance` 是从 `Q` 到该向量的距离。

```
1. Map each mtree object in the RDD of M-Tree objects of the DM-Tree object {
2.   Set result = mtree.rangeSearch(Q, rQ)
3. }
4. Collect the results from the worker nodes to the master node
5. Set unionResult = union the collected results
6. Set sortedResult = unionResult.sortBy("distance", "ascending")
7. Return sortedResult
```

## 实验

本节展示了在 `M-Tree` 和 `DM-Tree` 结构上的实验。我们使用的数据是从马克斯·普朗克信息学研究所网站下载的 Yago 知识库（“YAGO (database) Wikipedia,” n.d.; “YAGO Homepage,” n.d.）合成的。我们还使用 Scala 语言构建了一个应用程序来实现 `M-Tree` 和 `DM-Tree` 结构以进行实验。以下是实验的详细信息。

### M-Tree 结构实验

为了对 `M-Tree` 结构（“M-Tree Wikipedia,” n.d.）进行实验，我们使用了一台配置如下的计算机：

*   **处理器：** Intel(R) Core™ i5-6500 CPU @ 3.20GHz 3.20GHz
*   **安装内存 (RAM)：** 16.0 GB

我们在 64 维向量集上进行了实验。从这些向量集中，我们创建了 `CAPACITY` 为 1,000 个条目的 `M-Tree` 结构。表 3 显示了创建和存储、加载 `M-Tree` 结构；在 `M-Tree` 结构上执行 kNN 和范围查询的实验结果（单位：毫秒）。这里我们仅测试最多 2,000,000 个向量。如果向量数量更多，将超出我们计算机的容量。

图 6 展示了创建+存储和加载 `M-Tree` 结构时间（单位：毫秒）的对比图表。该图表表明，创建并存储 `M-Tree` 结构到本地文件非常耗时。然而，从本地文件加载 `M-Tree` 结构则更快。例如，创建并存储 200 万向量的 `M-Tree` 耗时 128,099 毫秒（约 128 秒），而加载 `M-Tree` 耗时 76,859 毫秒（约 77 秒）。

图 7 展示了在 `M-Tree` 结构上执行 kNN 和范围查询时间的对比图表。该图表表明，执行查询非常快，且 kNN 查询总是比范围查询耗时更长。例如，在 200 万向量的 `M-Tree` 上执行 kNN 查询耗时 7,823 毫秒（约 8 秒），而执行范围查询耗时 5,649 毫秒（约 6 秒）。

### 表 3. 创建和存储、加载 M-Tree 结构；在 M-Tree 结构上执行 kNN 和范围查询的实验结果（单位：毫秒）

| Number of Vectors | Creating & Storing | Loading | kNN Query | Range Query |
| :--- | :--- | :--- | :--- | :--- |
| 0.1m | 56,680 | 34,008 | 259 | 276 |
| 0.2m | 58,093 | 34,856 | 527 | 481 |
| 0.3m | 60,523 | 36,314 | 990 | 761 |
| 0.4m | 65,132 | 40,679 | 1,341 | 1,022 |
| 0.5m | 69,979 | 44,387 | 1,711 | 1,340 |
| 0.6m | 75,091 | 45,055 | 1,882 | 1,628 |
| 0.7m | 77,783 | 46,670 | 2,366 | 1,876 |
| 0.8m | 81,062 | 48,637 | 2,503 | 2,165 |
| 0.9m | 86,910 | 52,146 | 2,850 | 2,466 |
| 1.0m | 91,837 | 55,102 | 3,190 | 2,814 |
| 1.1m | 97,354 | 58,412 | 3,846 | 2,997 |
| 1.2m | 102,286 | 61,372 | 3,861 | 3,289 |
| 1.3m | 104,049 | 63,829 | 4,574 | 3,635 |
| 1.4m | 110,409 | 66,245 | 4,620 | 3,903 |
| 1.5m | 112,596 | 67,558 | 5,615 | 4,190 |
| 1.6m | 114,304 | 68,582 | 5,567 | 4,620 |
| 1.7m | 116,533 | 69,920 | 5,760 | 4,836 |
| 1.8m | 118,344 | 71,006 | 6,220 | 5,233 |
| 1.9m | 123,269 | 73,961 | 6,617 | 5,545 |
| 2.0m | 128,099 | 76,859 | 7,823 | 5,649 |

**图 6.** 创建+存储和加载 M-Tree 结构的时间对比（单位：毫秒）

![Figure978-1-7998-2701-6.ch007.f06](img/ch007.f06.png)

**图 7.** 在 M-Tree 结构上执行 kNN 和范围查询的时间对比（单位：毫秒）

![Figure978-1-7998-2701-6.ch007.f07](img/ch007.f07.png)

### DM-Tree 结构实验

为了对多媒体数据库的 `DM-Tree` 结构进行实验，我们构建了一个包含 16 台计算机的 Spark 集群，配置如下：
