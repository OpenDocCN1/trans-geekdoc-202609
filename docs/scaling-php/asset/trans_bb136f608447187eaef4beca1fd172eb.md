
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

![](images/06----fio.png)

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

| ![information](images/leanpub_information.png) || **MySQL 使用哪些不同类型的 I/O？** |
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

