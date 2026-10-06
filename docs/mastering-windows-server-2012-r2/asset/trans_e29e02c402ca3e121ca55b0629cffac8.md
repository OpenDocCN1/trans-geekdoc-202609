

# 使用 DNS 工具进行去注册与故障排除

当然，`nsLookup` 提供了我们需要访问的网站的 IP 地址。但是——“噢，不”——微软的网站并不仅仅在 URL 中使用 IP 地址。因此，尝试使用 IP 地址也是行不通的。

我们通过 Microsoft Windows 恶意软件删除工具 (MSRT) 找到了解决方案。它必须在另一台计算机上下载，然后使用 Sneaker 将 MSRT 程序包传输到受感染的计算机上。它识别并删除了病毒。幸运的是，现如今 Conficker 病毒仅局限于其他具有过时或缺失杀毒软件和 Windows Update 定义更新的操作系统上。不过，这是一个很好的例子，说明了如何利用名称解析修改来制造混乱，然后像 `nsLookup` 这样的工具可以用于故障排除并识别它的存在。

当应用程序无法访问服务器时，在检查 TCP/IP 连通性后，我们开始使用 `nsLookup` 命令进行尝试。以下是我们要寻找的内容：

- DNS 服务器是否有响应？命令将直接告诉你是否可以连接到 DNS 服务器。如果存在延迟或超时，则无需继续。你遇到了连通性问题。
- 默认服务器未知？这表明 `nsLookup` 执行的反向查找失败了。当处于这种状态时，我们发现 `nsLookup` 的其他测试都会变得异常。
- 你是否可以解析本地 FQDN（完全限定域名）？这跳过了客户端的部分处理过程。客户端将附加主 DNS 后缀来搜索主机名。
- 你是否可以在没有 DNS 后缀的情况下解析主机名？这是客户端的操作方式，你可以通过此进行测试。
- 你是否可以解析外部 FQDN？这将验证默认 DNS 服务器是否访问互联网。

`nsLookup` 有两种模式：单查询模式和交互模式。交互模式要强大得多，因此我们在开始时使用它。这种模式提供了对不同类型的资源记录进行查询的能力，并允许你切换服务器。以下是我们经常执行的查询示例（添加了注释以供清晰）：

```
C:\Users\Administrator.BF1>nslookup
Default Server: BF1.bigfirm.com
Address: 192.168.0.10
```

```
rem 查询一个主机记录
> BF1.bigfirm.com
Server BF1.bigfirm.com
Address: 192.168.0.10

Name: BF1.bigfirm.com
Address: 192.168.0.10
```

```
rem 查询一个反向 "ptr" 记录
> set q-ptr
> 192.168.0.10
Server: BF1.bigfirm.com
Address: 192.168.0.10

10.168.192.in-addr.arpa    name = BF1.bigfirm.com
```

```
rem 查询一个区域起始记录 (SOA)
> set q-soa
> bigfirm.com
Server: BF1.bigfirm.com
Address: 192.168.0.10
```

```
bigfirm.com
primary name server = BF1.bigfirm.com
responsible mail addr = hostmaster.bigfirm.com
serial = 124
refresh = 900 (15 mins)
retry = 600 (10 mins)
expire = 86400 (1 day)
default TTL = 3600 (1 hour)
BF1.bigfirm.com    internet address = 192.168.0.10
```

```
rem 查询一个名称服务器记录 (NS)
> set q-ns
> bigfirm.com
Server: BF1.bigfirm.com
Address: 192.168.0.10
```

```
bigfirm.com    nameserver = BF1.bigfirm.com
BF1.bigfirm.com    internet address = 192.168.0.10
```

```
rem 查询一个资源记录
> set q-rvs
> _ldap.tcp.bigfirm.com
Server: BF1.bigfirm.com
Address: 192.168.0.10
```

```
_ldap_tcp.bigfirm.com  SRV service location:
    priority = 0
    weight = 100
    port = 389
    svr hostname = BF1.bigfirm.com
```

```
BF1.bigfirm.com    internet address = 192.168.0.10
```

# DCDAG

`DcDiag` 最初是 Windows Server 早期版本管理员支持工具（需要单独安装）的一部分，但现在默认作为 Windows Server 2012 R2 安装的一部分包含。它是我们对 DNS 结构进行快速健康检查的首选工具。因为它运行在许多域控制器上。

