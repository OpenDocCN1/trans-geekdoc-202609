
-   默认情况下，查询会跳过查询缓存。如果你想让特定查询使用缓存，需要将 `SELECT` 改为 `SELECT SQL_CACHE`。例如-

``` 
1 mysql> SELECT SQL_CACHE FROM foobar WHERE id = 123456
```

然而，按需查询缓存仍然受全局写入的影响，因此它并不是完美的解决方案。

##### XtraDB/InnoDB vs MyISAM

你会发现我在这一章没有提及任何 MyISAM 相关的性能设置。原因是你在生产环境中绝对不应该使用 MyISAM。为什么不能使用 MyISAM？

**它不支持行级锁**

这意味着每次向 MyISAM 表中插入数据时，整个表都会被锁定，其他并发连接在查询完成前无法从该表读取或写入。这是一个巨大的限制。InnoDB 支持行级锁，只有参与插入或更新的行在修改时才会被锁定。

如果你在低负载环境下使用，这可能影响不大，但 MyISAM 绝对不适合高负载工作负载，且在扩展时没有位置。将所有表切换到 InnoDB，然后不要回头。

###### 如何判断表是 MyISAM 还是 InnoDB？

```
1 mysql> SHOW TABLE STATUS WHERE 'Name' = 'foobar'\G
2 *************************** 1. row ***************************
3            Name: foobar
4          Engine: InnoDB
5         Version: 10
6      Row_format: Compact
```

###### 如何将表从 MyISAM 切换到 InnoDB？

```
1 mysql> ALTER TABLE foobar ENGINE = INNODB;
```

警告：`ALTER TABLE` 操作可能耗时较长，并会对表加写锁，从而阻止数据写入。

###### 关于搜索呢？

确实，InnoDB 不支持像 MyISAM 那样的全文搜索。事实上，搜索方面有更好的替代方案。请查看：

*   [ElasticSearch](http://www.elasticsearch.org/)

*   [Sphinx](http://sphinxsearch.com/)

*   [Solr](http://lucene.apache.org/solr/)

据说 MySQL 5.6 将为 InnoDB 添加全文搜索功能。我尚未测试，无法评估性能，但它可能会取代或至少大幅减少对独立搜索服务的需求。

### 调优 Linux 以应对高强度数据库

Linux 和 MySQL 是天作之合。默认情况下，MySQL 在 Linux 系统上运行得相当不错，但通过调整一些设置并做出正确的初始决策，我们可以在 I/O 方面（作为性能弱点）提升 30-40% 的性能。

#### 更改 I/O 调度器

Linux 内核默认包含三种 I/O 调度器：`cfq`、`deadline` 和 `noop`。可以通过以下命令查看当前使用的调度器（这里 `sda` 是磁盘设备 ID）：

```
1 cat /sys/block/sda/queue/scheduler
2 noop deadline [cfq]
```

大多数发行版默认使用 `cfq`，它旨在在整个系统间公平分配 I/O 资源，非常适合桌面环境中多个程序争夺 I/O 的场景。但对于单一数据库服务器，你希望数据库拥有**所有** I/O 资源。

选择哪个调度器并不重要，`deadline` 和 `noop` 都表现良好，关键是**不要选择 `cfq`**。`cfq` 速度极慢，切换到 `deadline` 或 `noop` 能带来巨大收益。`noop` 适合 SSD 和硬件 RAID，但在我测试中，`deadline` 和 `noop` 的表现相似。

![](images/06----cfq_benchmark.png)

如上图所示，上方窗口运行 `iostat -x 1` 命令，显示每秒 I/O 使用情况。在白色横线上方，使用的是 `cfq` 调度器，可以看到红色列标记的 I/O 使用率约为 100%。2 秒后切换到 `noop` 调度器，**I/O 利用率立即减半**，稳定在 20% 左右。

黄色方框标记的部分表明，读/写操作速率在整个测试过程中保持不变，因此 I/O 利用率的下降是由于调度器切换导致的。

切换 I/O 调度器非常简单，是提升数据库写入性能的低挂果实，只需几秒钟。

> 我的数据库所在磁盘是 `/dev/sda`，示例中针对该磁盘修改 I/O 调度器。如果你的磁盘标识不同，请将 `sda` 替换为对应的标识。`sda` 是大多数人的正确选择。

```
1 > echo noop > /sys/block/sda/queue/scheduler
2 > vi /etc/rc.local
3   # 在 rc.local 文件中添加此行，因为系统重启后 I/O 调度器会恢复默认
4   echo "noop" > /sys/block/sda/queue/scheduler
```

#### 调整 swappiness

交换通常会导致 MySQL 服务器崩溃。由于 MySQL 有自己的内部缓存，它依赖内存缓冲池始终保持快速。当 Linux 将缓冲池的部分数据交换到磁盘时，会让 MySQL 突然失去支撑，甚至在内存不足时导致服务器崩溃。因此，必须配置 MySQL 以最大化内存使用，同时避免过高导致系统交换。

我们可以通过配置 `vm.swappiness` 让内核更倾向于保留内存中的非活动数据，而不将其写入磁盘。但需注意，如果完全禁用交换，当系统内存不足时，服务器会因无法使用磁盘交换空间而直接崩溃。

```
1 > sysctl -w vm.swappiness=0
2 > vi /etc/sysctl.conf
3   vm.swappiness=0
```

#### 增加打开文件数

如前 Load Balancer 章节所述，标准 Linux 配置下，进程最大打开文件数设置得很低（1024）。MySQL 需要增加打开文件数的原因有两点：第一，`max_connections` 设置需要为每个连接分配文件描述符；第二，每个打开的表也需要一个文件描述符。例如，10 个表和 100 个连接，至少需要 1000 个打开文件，因为每个连接线程维护自己的文件句柄。

修改方法很简单：

```
1 > vi /etc/security/limits.conf
2     * soft  nofile  999999
3     * hard  nofile  999999
4 > ulimit -<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk>
