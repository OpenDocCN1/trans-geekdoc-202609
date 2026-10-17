
`2408960` 字节为每分钟写入日志的字节数。[Google 2408960 bytes to megabytes](https://www.google.com/?q=2408960+bytes+to+megabytes#hl=en&safe=off&output=search&sclient=psy-ab&q=2408960+bytes+to+megabytes&gs_l=hp.12...0.0.0.1163.0.0.0.0.0.0.0.0.0..0.0.0.0.0.0.0.0.0.0.0.0.0.0.0..0.0.0..0.0.0...0.0.0..0.0.les%3B..0.0.0.1c.ONtw7scylt0&pbx=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.&fp=19fc9cab2f77850f&bpcl=35440803&biw=1129&bih=999)，显示 MySQL 每分钟向日志写入 2.29MB 数据。

Multiply the megabytes per minute times 60 minutes to determine how much data would be written out in one hour.

```
1 2.29MB * 60 minutes = 137.4MB
```

Since InnoDB keeps two individual log files, divide 137.4MB by 2 and we get about 69MB, so `innodb_log_file_size` should be around 70MB in this scenario. We can go higher, even up to 100MB or 200MB, but as you can see, for most cases, setting it very high is unnecessary.

(*Calculation method adopted from the [MySQL Performance Blog](http://www.mysqlperformanceblog.com/2008/11/21/how-to-calculate-a-good-innodb-log-file-size)*)

在现有 MySQL 数据库上生效的改动，需要干净地关闭 MySQL，删除 InnoDB 日志文件，然后重新启动 MySQL。如果不这样做，MySQL 会报错说现有的日志文件大小与 `innodb_log_file_size` 的值不匹配。

需要删除的文件位于 MySQL 数据目录，文件名为 `ib_logfile0` 和 `ib_logfile1`。请记住，这些文件仅在崩溃时才必要，因此在使用 `mysqladmin shutdown` 干净关闭 MySQL 后，你可以自由删除它们。MySQL 启动后会根据新指定的大小重新创建这些文件。

**注意**：如果不使用 `innodb_file_per_table`，请不要删除 `ibdata1` 文件，因为它包含所有 InnoDB 数据。使用 `rm -rf ib*` 这类命令时很容易误删此文件。

### max_connections

`max_connections` 需要设置为应用程序可能出现的理论最大连接数。由于每个 PHP-FPM 进程通常只使用一个连接，你应使用 PHP-FPM 配置文件中的 `pm.max_children` 设置来进行计算。

**设置 `max_connections` 的公式：**

```
1 max_connections = pm.max_children * number of application servers
```

默认值 100 连接远远不足，务必将其调高。还需确保有足够的内存来处理理论最大连接数。MySQL 是多线程服务器，为每个连接创建一个线程，每个线程约需要 192KB 内存。例如，192KB * 2000 连接 ≈ 400MB，因此在扣除 `innodb_buffer_pool_size` 后，确保系统有足够的空闲内存来容纳这些连接。

### innodb_io_capacity

`innodb_io_capacity` 设置告诉 InnoDB 你的系统能提供多少 IOPS，从而设定上限，防止磁盘被饱和。因此，需要根据 MySQL 系统中磁盘的性能来设置该值。默认值 100 在当今硬件中远远不足，必须进行调优。以下为一些推荐的起始值：

| 驱动类型 || 值 |
| --- | --- |
| Enterprise SSD || 50,000 |
| Single Consumer SSD || 10,000 |
| 4 Drives in a RAID-10 || 5000 |
| Single 7200RPM Drive || 200 |

在我们的从服务器上，我们使用 Enterprise-Level Micron SSD 驱动器并配置 RAID-0，能够将其设置为 `150,000`。

不确定系统性能如何？可以使用 `fio` 快速测试系统的随机 IOPS 能力。假设你想测试挂载为 `/mysql` 的磁盘 `/dev/sdb1`。

首先需要安装 `fio` 并创建作业文件。我们定义的作业会测试 128MB 文件上的随机读写性能。如果系统拥有更快的驱动器，建议将文件大小至少调整到 5GB，因为测试会几乎瞬间完成。在单个 7200RPM 驱动器系统上，测试约需 30 秒。

```
1 > apt-get instal fio
2 > cd /mysql
3 > mkdir /mysql/fio
4 > vi random-rw.fio
5     [random_rw]
6     rw=randrw
7     size=128M
8     directory=/mysql/fio
```

运行刚才创建的作业文件：

```
1 > fio random-rw.fio
```

![](img/06----fio.png)

作业运行结束后，你会看到类似上述输出。黄色下划线标示的数值是平均随机读 IOPS（此例为 285），红色下划线标示的数值是平均写入 IOPS（282）。这来自一个单个 7200RPM 驱动器系统。

`fio` 支持多种配置选项和测试类型。通过修改 `rw=randrw` 变量，可更改基准测试类型。可用的测试类型如下：

| 名称 || 测试类型 |
| --- | --- |
| read || 仅测试顺序读取 |
| write || 仅测试顺序写入 |
| randread || 仅测试随机读取 |
| randwrite || 仅测试随机写入 |
| rw || 测试顺序读取+写入 |
| randrw || 测试随机读取+写入 |

随机 I/O 是最差情况且最慢的场景，因此使用 `randrw` 测试的值作为 `innodb_io_capacity` 的保守起点是合理的，但它能让你了解系统性能。你可以尝试使用 `rw=rw` 运行作业，观察系统在 100% 顺序、最佳情况下的表现。

| ![information](img/leanpub_information.png) || **MySQL 使用哪些不同类型的 I/O？** |
| --- | --- |
| 写入 InnoDB 日志文件使用顺序 I/O。 |
| 写入 InnoDB 数据文件主要使用随机 I/O。 |
| 从 InnoDB 数据文件读取主要使用随机 I/O。 |

### innodb_read_io_threads & innodb_write_io_threads

InnoDB 使用后台线程管理读写任务。默认值为 4，对于现代系统而言过低。应将其设置为 CPU 核心数的 4 倍。

### query_cache_size

MySQL 查询缓存乍看之下似乎是个好主意。它会将每条查询的结果缓存到内存中，当再次发送相同查询时，可直接返回结果，无需再次解析。对于读取密集型表，它能显著加速查询响应，甚至可以替代 Memcached 等独立缓存层。

但在写入操作上存在问题。由于查询缓存设计为始终提供最新数据，需要智能地更新缓存。然而，它并未如此处理。相反，每次发生数据写入时，查询缓存会**完全清空并重置整个表的缓存**。**每一次写入（INSERT、UPDATE、DELETE）都会导致缓存被清除**。想象一下，如果每秒有 100 条写入操作，查询缓存需要每秒刷新 100 次，几乎完全失去作用。

不仅如此，它还会损害性能。缓存越大，清空所需时间越长，导致每条 INSERT 查询变慢。此外，查询缓存使用全局锁，同一时间只能被单个线程访问——这意味着其他线程在等待清空缓存时会被阻塞。

**结论**：**如果工作负载包含显著的写入量，请彻底禁用查询缓存**。因为 InnoDB 已拥有其内部缓存，查询仍能保持高速。 **如果你有读取密集且极少写入的表，查询缓存是合理的**，它可以让你免于额外实现缓存层，简化应用复杂度。

由于 MySQL 存在一个 bug，需要同时将 `query_cache_size` 和 `query_cache_type` 设置为 0。

但如果我的应用既有读取密集型表，也有写入密集型表呢？由于查询缓存是全局设置而非按表设置，你应该**禁用查询缓存**，因为它通常弊大于利。你可以开启**按需缓存**，如果正确使用，它仍能提供一定收益。

为此，首先需要将配置值设置为开启按需缓存：

```
1 query_cache_type=2
2 query_cache_size=16M
```

16MB 是查询缓存的良好起点。请记住，缓存需要在每次写入时被清除，因此应保持尽可能小。它只存储查询语句和结果，通常每条只有几 KB。

- 默认情况下，查询会跳过查询缓存。如果你想让特定查询使用缓存，需要将 `SELECT` 改为 `SELECT SQL_CACHE`。例如-

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

* [ElasticSearch](http://www.elasticsearch.org/)
* [Sphinx](http://sphinxsearch.com/)
* [Solr](http://lucene.apache.org/solr/)

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

![](img/06----cfq_benchmark.png)

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
```
