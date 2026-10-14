
`ip_local_port_range` 定义系统上可用端口的范围。在我的 Ubuntu 标准安装中，它的值设置为 `32768-61000`。增大范围以允许更多连接。可用端口的数量限制了同时打开的连接数。记住，即使连接已关闭，它仍然会在 `TIME_WAIT` 状态中占用端口（不过我们可以通过下面的设置来缓解）。

```
1 > sysctl -w net.ipv4.ip_local_port_range="10000 65535"
2 > vi /etc/sysctl.d/haproxy-tuning.conf
3     net.ipv4.ip_local_port_range=10000 65535
```

#### `net.ipv4.tcp_tw_reuse`

TCP 协议的一部分是 `TIME_WAIT` 状态，它会在连接关闭后保持 socket 打开最多 4 分钟。在繁忙服务器上，这可能导致端口/套接字耗尽。`net.ipv4.tcp_tw_reuse` 告诉内核在确认安全的情况下，可以在不等待完整超时的情况下重用 TCP 套接字。此外，`net.ipv4.tcp_recycle` 和 `net.ipv4.tcp_fin_timeout` 也可以调整，但请谨慎操作这两项。

```
1 > sysctl -w net.ipv4.tcp_tw_reuse=1
2 > sysctl -w net.ipv4.netfilter.ip_conntrack_tcp_timeout_time_wait=1
3 > vi /etc/sysctl.d/haproxy-tuning.conf
4     net.ipv4.tcp_tw_reuse=1
5     net.ipv4.netfilter.ip_conntrack_tcp_timeout_time_wait=1
```

#### `ulimit -n 999999`

在标准 Linux 配置中，每个进程允许打开的最大文件数（即套接字）设置得很低（1024）。因为套接字在 Linux 系统中被视为文件，这个限制也直接决定了并发连接数。记住，负载均衡器的每个连接需要两个套接字——一个用于客户端的入站连接，另一个用于到后端的出站连接，因此初始上限最多只能有 512 个并发连接。幸运的是，修改这个设置很简单。

```
1 > vi /etc/security/limits.conf
2     * soft  nofile  999999
3     * hard  nofile  999999
4 > ulimit -n 999999
```

> 注意：可能需要重启 HAProxy 使该设置生效。

### 扩展问题

调试负载均衡器问题时，尤其是在高负载环境下，会感到沮丧。如果负载均衡器变慢或无响应，请关注以下几个常见问题。

#### 饱和网络

这似乎不言自明，但我曾为此困扰过。记得曾花费超过一小时才弄清为什么我们的 Twitpic 负载均衡器运行像蜗牛一样且持续丢失连接。原因是网卡被配置为 100 Mbps，而我们试图通过它推送 150 Mbps。使用 `vnstat` 可以查看网卡当前的带宽使用情况。请务必检查**公网**和**私网**两个网络，因为负载均衡器通常会同时使用这两者。

```
1 > vnstat -i eth1 -l
```

![](images/04----vnstat.png)

#### 运行出内存

尽管 HAProxy 的内存占用很低，但在大量入站连接且后端服务器慢或过载的情况下，仍可能耗尽内存。使用 `free` 命令检查内存使用情况。

#### 大量 `TIME_WAIT` 连接

如前所述，大量处于 `TIME_WAIT` 状态的连接会导致服务器资源耗尽。可以通过前文提到的配置选项进行缓解。使用 `netstat -n | grep TIME_WAIT | wc -l` 可以查看当前处于 `TIME_WAIT` 状态的套接字数量。

## 应用服务器：使用 Nginx 和 PHP-FPM 实现水平扩展

应用服务器集群是应用的核心，负责运行 PHP 代码并提供图片、CSS、JavaScript 等静态资源。幸运的是，应用服务器通常是栈中最容易扩展的部分，因为前文提到的负载均衡器配置中，只需将新的应用服务器加入池中即可水平扩展，提高容量。即使服务器失败（它们会失败），HAProxy 也会自动将其从池中移除，无需报警，也无需在夜间被叫醒——它们能够轻松扩展。

### 选择正确的 PHP 版本

PHP 社区在更新方面表现得非常保守，甚至可以说是“年岁如旧”。因此，务必确保运行的是最新的 PHP 版本，即 **PHP 5.4.4**（截至撰写时）。

> 2014 年更新——使用 PHP 5.5！这里的所有描述依然适用，只是 Dotdeb 仓库的路径改为 `deb http://packages.dotdeb.org wheezy-php55 all` 和 `deb-src http://packages.dotdeb.org wheezy-php55 all`。

PHP 的主版本每次迭代都在速度和内存使用上得到提升，因此运行最新版本可以最大化硬件性能。5.4 相比 5.3 在功能和速度上显著更好，同样 5.3 也优于 5.2。

在 Debian 或 Ubuntu 系统上，可以使用 **Dotdeb** 仓库来获取几乎即时、无痛的 PHP 更新，同时也能获得 Ubuntu 官方仓库中滞后的软件（如 Redis 与 Nginx）。这省去了等待发行版维护者更新的时间，往往需要数周甚至更久。

如果你使用的是 Ubuntu Quantal（12.10），PHP 5.4 已经在 apt 仓库中，无需额外添加 Dotdeb 的 php54 行。

设置 Dotdeb 与添加另一个 apt 源同等简单：

```
 1 > vi /etc/apt/sources.list.d/dotdeb.list
 2 
 3 deb http://packages.dotdeb.org squeeze all
 4 deb-src http://packages.dotdeb.org squeeze all
 5 
 6 # 仅在使用 Ubuntu 12.04（Precise）时包含以下行
 7 deb http://packages.dotdeb.org squeeze-php54 all
 8 deb-src http://packages.dotdeb.org squeeze-php54 all
 9 
10 > wget http://www.dotdeb.org/dotdeb.gpg
11 > cat dotdeb.gpg | sudo apt-key add -
12 > apt-get update
```

#### 基准测试：PHP 5.3 与 PHP 5.4

在所有可测试的场景中，PHP 5.4 在每秒请求数（RPS）和内存占用方面均优于 PHP 5.3。下面的图表展示了我的测试结果，供您参考：

![](images/05----chart_1.png)![](images/05----chart_2.png)![](images/05----chart_3.png)

### Nginx 与 PHP-FPM

正如第 2 章所讨论，我们将用 **nginx + PHP-FPM** 替代传统的 Apache + mod_php 组合。虽然可以保留 Apache 并通过 HAProxy 水平扩展，但 nginx + PHP-FPM 的组合更为优雅。Trust me，摒弃 Apache，改用 nginx。

我们在 2010 年将 Twitpic 迁移到此架构，当时我对 nginx 并不熟悉，担心配置会很复杂。结果发现，nginx 的配置文件简洁易读，管理起来比 Apache 更轻松。而且 nginx 官方 Wiki（[http://wiki.nginx.org/Main](http://wiki.nginx.org/Main)）提供了完整的每项配置选项文档。

同样，PHP-FPM 也是可靠的软件，和使用 mod_php 一样可靠。PHP 5.3 之前它是以补丁形式开发，由与 nginx 同一团队维护，而自 PHP 5.3 起已被整合进 PHP 官方发行版，得到整个 PHP 社区的全力支持，经过充分测试，完全可靠。

假设您的 PHP 应用位于 `/u/apps/my_app`，入口脚本为 `/u/apps/my_app/www/index.php`。大多数框架（如 Zend、Kohana、Cake）都兼容此配置。

下面是我们的部署步骤：

