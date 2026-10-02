
然后请确保在 /etc/php5/conf.d/gearman.ini 中指定加载共享库 gearman.so（这是 Ubuntu 中的做法。其他 Linux 发行版或 UNIX 变体可能有不同的设置。）：
```
extension="gearman.so"
```

根据操作系统，这可能已为您完成。另一种选择是将此行添加到您的 php.ini 中。请参考您的操作系统手册。

## Gearman MySQL UDF 安装

也可以与 Gearman 一起使用的还有 Gearman MySQL 用户定义函数，或 UDF。除了新的基于 C 的 Gearman 之外，Eric Day 还编写了这些 UDF。这些 UDF 在使用 Gearman 时比仅使用外部程序提供更大的功能。UDF 本身就是客户端程序，并在 MySQL 服务器内部运行。有了这些 UDF，您可以像使用常规客户端程序一样向 Gearman 作业服务器添加作业，但是在 MySQL 内部而不是使用外部程序或在应用程序代码中。这乍一看可能令人困惑——在服务器内运行客户端。然而，如果您回想起前面的章节，示例 Curl UDF http_get() 和 memcached UDF 也都是客户端。

Gearman MySQL UDF 使您能够从 MySQL 内部请求 Gearman 作业服务器的作业。这意味着您可以在表上设置触发器，以便在发生 UPDATE、DELETE 或 INSERT 时也可以添加作业。想想这为您带来的强大功能！

要开始安装 Gearman MySQL UDF，请按照以下步骤操作：

- 1. 下载最新的 UDF 源代码，您可以在 Launchpad 上找到它 https://launchpad.net/gearman-mysql-udf，将其下载到与您下载 Gearman 作业服务器源代码相同的目录中并解压/gzip 分发文件：
- 2. 进入 Gearman MySQL UDF 源代码目录：
- 3. 为编译配置软件包。您使用的路径取决于您拥有的 MySQL 发行版，是源代码还是二进制等。您需要找到 mysql_config 存在的路径。您可能需要安装所需的 MySQL 开发或社区开发包（yum search mysql、apt-cache search mysql、yast 等）。

```
wget http://launchpad.net/gearman-mysql-udf/trunk/0.4/+download/gearman-mysql-udf-0.4.tar.gz
tar xzvf gearman-mysql-udf-0.4.tar.gz
```

```
cd gearman-mysql-udf-0.4
```

在 Ubuntu 系统上，它将是：

```
./configure --with-mysql=/usr/bin/mysql_config --libdir=/usr/lib/mysql/lib
```

--with-mysql 是告诉配置程序在哪里找到 mysql_config 的参数。--libdir 是共享 UDF 库将被安装的位置，并且该目录必须是 MySQL 可以从中加载库的目录。您可能需要添加或编辑 /etc/ld.so.conf.d/mysql.conf 以确保列出了该路径，然后运行 ldconfig。

- 4. 接下来，构建并安装 UDF 源代码：

```
make
make install
```

- 5. 要加载 UDF，您需要在 MySQL 内部执行此操作：

```
CREATE FUNCTION gman_do RETURNS STRING SONAME "libgearman_mysql_udf.so";
CREATE FUNCTION gman_do_low RETURNS STRING SONAME "libgearman_mysql_udf.so";
CREATE FUNCTION gman_do_high RETURNS STRING SONAME "libgearman_mysql_udf.so";
CREATE FUNCTION gman_do_background RETURNS STRING SONAME "libgearman_mysql_udf.so";
CREATE FUNCTION gman_do_low_background RETURNS STRING SONAME "libgearman_mysql_udf.so";
CREATE FUNCTION gman_do_high_background RETURNS STRING SONAME "libgearman_mysql_udf.so";
CREATE AGGREGATE FUNCTION gman_sum RETURNS INTEGER SONAME "libgearman_mysql_udf.so";
CREATE FUNCTION gman_servers_set RETURNS STRING SONAME "libgearman_mysql_udf.so";
```

此时，Gearman MySQL UDF 已安装。

## 运行 Gearman 作业服务器

运行 gearmand，即 Gearman 作业服务器，是您使用它的下一步。

要启动 gearmand：

- 1. 运行（无论安装在什么路径）：

```
/usr/local/bin/gearmand -d
```

这告诉 gearmand 在后台分离运行。

- 2. 现在，运行一个 worker。gearmand 在源代码目录的 examples/ 目录中包含一些示例 worker 和客户端程序。要真正做点什么，您需要运行一个 worker 程序。为了测试 gearmand（以及 worker 和客户端，以了解 Gearman 的整体工作原理），请使用两个窗口来查看它到底做了什么。在一个窗口中启动 reverse worker。不要使用 & 将其放到后台：

```
./reverse_worker
```

- 3. 运行一个客户端程序。使用 Gearman 作业服务器，您有两种请求作业的方式：
- Attached/callback，这将等待服务器委派的作业完成并返回该 worker 的返回值。
- Detached/backgrounded，这允许进程自行运行，不等待 worker 的返回值。

对于本示例，将运行 callback/attached 客户端。

- 4. 在另一个窗口中，运行 reverse_client_cb 程序：

```
./reverse_client_cb "This is a test"

Created: H:hanuman:929
```

```
Created: H:hanuman:930
Created: H:hanuman:931
Created: H:hanuman:932
Created: H:hanuman:933
Created: H:hanuman:934
Created: H:hanuman:935
Created: H:hanuman:936
Created: H:hanuman:937
Created: H:hanuman:938
Completed: H:hanuman:929 tset a si sihT
Completed: H:hanuman:930 tset a si sihT
Completed: H:hanuman:931 tset a si sihT
Completed: H:hanuman:932 tset a si sihT
Completed: H:hanuman:933 tset a si sihT
Completed: H:hanuman:934 tset a si sihT
Completed: H:hanuman:935 tset a si sihT
Completed: H:hanuman:936 tset a si sihT
Completed: H:hanuman:937 tset a si sihT
Completed: H:hanuman:938 tset a si sihT
```

如果您查看 worker 运行的窗口：

```
Job=H:hanuman:929 Workload=This is a test Result=tset a si sihT
Job=H:hanuman:930 Workload=This is a test Result=tset a si sihT
Job=H:hanuman:931 Workload=This is a test Result=tset a si sihT
Job=H:hanuman:932 Workload=This is a test Result=tset a si sihT
Job=H:hanuman:933 Workload=This is a test Result=tset a si sihT
Job=H:hanuman:934 Workload=This is a test Result=tset a si sihT
Job=H:hanuman:935 Workload=This is a test Result=tset a si sihT
Job=H:hanuman:936 Workload=This is a test Result=tset a si sihT
Job=H:hanuman:937 Workload=This is a test Result=tset a si sihT
Job=H:hanuman:938 Workload=This is a test Result=tset a si sihT
```

正如您所见，客户端从作业服务器 gearmand 请求作业到 reverse worker，该作业通过作业服务器分派给 worker，然后 worker 反转文本并返回反转结果。

## 使用 Gearman MySQL UDF

另一种向 Gearman 作业服务器发出作业请求的方式是使用 Gearman MySQL UDF。
提供的 UDF 在以下各节中详细讨论。

### gman_servers_set()

此 UDF，您必须在调用任何其他 Gearman MySQL UDF 之前调用它，设置将在客户端会话中用于任何 UDF 调用的服务器池。它以一个或多个逗号分隔的服务器作为第一个参数，端口可选——默认为端口 4730。第二个参数可用于设置特定服务器运行特定作业！

```
gman_servers_set("<server list>", "<optional: job>")
```

单个服务器的示例为：

```
SELECT gman_servers_set("192.168.1.33:7004")
```

以下是将 192.168.1.33 分配给运行 reverse worker 的示例：

```
SELECT gman_servers_set("192.168.1.33:4730", "reverse");
```

以下是将两个服务器分配给运行 indexer worker 的示例：

```
SELECT gman_servers_set("192.168.1.88:4730,192.168.1.99:7004", "indexer");
```

设置好服务器后，您就可以使用 Gearman MySQL UDF 从 UDF 查询中请求作业。

### gman_do()

这些 UDF 向 Gearman 作业服务器 gearmand 发送作业请求：

```
gman_do("<function name>", "<input value>")
gman_do_low("<function name>", "<input value>")
gman_do_high("<function name>", "<input value>")
gman_do_background("<function name>", "<input value>")
gman_do_low_background("<function name>", "<input value>")
gman_do_high_background("<function name>", "<input value>")
<job name> should be <function name>
```

gman_do() 运行一个普通作业，在返回结果之前等待作业完成。如果有，gman_do_low|high() 是低/高优先级作业，也会等待，而 gman_do_background() 和 gman_do_background_low|high() 以正常、低或高优先级在后台（异步）运行作业，仅返回主机和作业编号（作业句柄），您稍后可以查询其结果。

> 如果您想通过使用触发器的 Gearman MySQL UDF 发出作业请求，则需要调用 gman_do_background()。否则，插入到表中的数据的 INSERT 语句将不会在作业完成之前完成。

### gman_sum()

这是一个聚合函数，用于并行运行作业。它比使用 sum(gman_do(...)) 快得多，因为它同时运行作业。

```
SELECT gman_sum("wc", Host) AS test FROM mysql.user;
```
