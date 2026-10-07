

![](img/ceaab52f5a948b18995b8efe89758781_122_0.png)

图 5.21

NMAP 扫描看起来很有趣。如果我们点击它，我们不仅能看到发现的端口列表，还能看到可以进一步探索的额外实体列表，如下代码和图 5.23 所示：

- - [] 选项：
- [] 2018-12-18 03:52:02 UTC 开始运行：
- [] 扫描列表为: ["185.165.169.124", ports: 10
- [] 正在扫描 185.165.169.124 并存储在 /tmp/nmap_scan_47907309.xml
- [] Nmap 选项:
- [] Nmap 输出:

```
Nmap 7.01 ( https://nmap.org ) at 2018-12-18 03:52:02
Nmap scan report for 185.165.169.124
Host is up.
PORT    STATE   SERVICE   VERSION
21/tcp  filtered  ftp
22/tcp  filtered  ssh
23/tcp  filtered  telnet
25/tcp  filtered  smtp
80/tcp  filtered  http
110/tcp filtered  pop3
```

# 第 5 章 网络发现自动化工具入门 101

```
139/tcp filtered netbios-ssn
443/tcp filtered https
445/tcp filtered microsoft-ds
3389/tcp filtered ms-wbt-server
53/udp filtered domain
67/udp filtered dhcp
123/udp filtered ntp
135/udp filtered msrpc
137/udp filtered netbios-ns
138/udp filtered netbios-dgm
161/udp filtered smp
445/udp filtered microsoft-ds
631/udp filtered ipp
1434/udp filtered ms-sql-m
```

匹配此主机的指纹太多，无法提供特定的操作系统详情。发现 Intrigue 的真正迷人之处不仅是因为你所使用的任务/模块的能力，还因为你可以通过这些模块扩展的范围之广。例如，从图 5.24 所示的结果中，我们可以看到 websocket .uberpepe.net 和 ftp.uberpepe.net。

| | | |
|---|---|---|
| dns_bute on DnsRecord: uberpepe.net | D | complete |
| enrich_dns_record on DnsRecord: uberpepe.net | D | complete |
| dns_bute on DnsRecord: uberpepe.net | D | complete |
| enrich_dns_record on DnsRecord: uberpepe.net | D | complete |
| dns_bute on DnsRecord: cpanel.uberpepe.net | D | complete |
| enrich_dns_record on DnsRecord: cpanel.uberpepe.net | D | complete |
| dns_bute on DnsRecord: mokotoldband.uberpepe.net | 3 | complete |
| enrich_dns_record on DnsRecord: mokotoldband.uberpepe.net | 3 | complete |
| dns_bute on DnsRecord: microsoft.uberpepe.net | 3 | complete |
| enrich_dns_record on DnsRecord: microsoft.uberpepe.net | 3 | complete |
| dns_bute on DnsRecord: uberpepe.net | 2 | complete |
| enrich_dns_record on DnsRecord: uberpepe.net | 2 | complete |
| dns_bute on DnsRecord: mokotoldband.uberpepe.net | 3 | complete |
| enrich_dns_record on DnsRecord: mokotoldband.uberpepe.net | 3 | complete |
| dns_bute on DnsRecord: bedmaybreakfast.uberpepe.net | 3 | complete |
| enrich_dns_record on DnsRecord: bedmaybreakfast.uberpepe.net | 3 | complete |
| dns_bute on DnsRecord: ns2.uberpepe.net | 3 | complete |
| enrich_dns_record on DnsRecord: ns2.uberpepe.net | 3 | complete |
| enrich_nameerver on DnsRecord: ns1.uberpepe.net | D | complete |
| enrich_nameerver on DnsRecord: ns1.uberpepe.net | D | complete |
| dns_bute on DnsRecord: uberpepe.net | D | complete |
| enrich_dns_record on DnsRecord: uberpepe.net | D | complete |
| public_groups, check on DnsRecord: uberpepe.net | 13 | complete |
| dns_bute on DnsRecord: uberpepe.net | 4 | complete |
| search_ct on DnsRecord: uberpepe.net | 4 | complete |
| enumerate, namervers on DnsRecord: uberpepe.net | 2 | complete |
| dns_bute on DnsRecord: uberpepe.net | D | complete |
| enrich_net, block on NetBlock: 184.154.0.16 | D | complete |
| hmap_scan on ipAddress: 184.154.76.235 | 39 | complete |
| whoislookup on ipAddress: 184.154.76.235 | 1 | complete |
| enrich_dns_record on DnsRecord: uberpepe.net | 1 | complete |
| enrich/domain on DnsRecord: uberpepe.net | 1 | complete |
| enrich/p_address on ipAddress: 184.154.76.235 | 2 | complete |
| create_entity on DnsRecord: uberpepe.net | 1 | complete |

图 5.22

实体：

- FtpService: 184.154.76.235:21 [链接]
- SshService: 184.154.76.235:22 [链接]
- SmtpService: 184.154.76.235:25 [链接]
- Url: 184.154.76.235:80 [链接]
- Url: http://bedmaybebreakfast.fast.uberpepe.net:80 [链接]
- Url: http://cdn.uberpepe.net:80 [链接]
- Url: http://ftp.uberpepe.net:80 [链接]
- Url: http://mail.uberpepe.net:80 [链接]
- Url: http://motocall.uberpepe.net:80 [链接]
- Url: http://ms2.uberpepe.net:80 [链接]
- Url: http://test.uberpepe.net:80 [链接]
- Url: http://uberpepe.net:80 [链接]
- Url: http://webdisk.uberpepe.net:80 [链接]
- Url: http://webmail.uberpepe.net:80 [链接]
- Url: http://www.uberpepe.net:80 [链接]
- Url: http://bedmaybebreakfast.fast.uberpepe.net:80 [链接]
- Url: http://mokototand.uberpepe.net:80 [链接]
- Url: http://uberpepe.net:80 [链接]
- NetworkService: network://184.154.76.235:10 [链接]
- Url: 184.154.76.235:443 [链接]
- Url: http://bedmaybebreakfast.fast.uberpepe.net:443 [链接]
- Url: http://cdn.uberpepe.net:443 [链接]
- Url: http://ftp.uberpepe.net:443 [链接]
- Url: http://mail.uberpepe.net:443 [链接]
- Url: http://mokofoband.uberpepe.net:443 [链接]
- Url: http://ms1.uberpepe.net:443 [链接]
- Url: http://ms2.uberpepe.net:443 [链接]
- Url: http://test.uberpepe.net:443 [链接]
- Url: http://uberpepe.net:443 [链接]
- Url: http://vps.uberpepe.net:443 [链接]
- Url: http://webdisk.uberpepe.net:443 [链接]
- Url: http://webmail.uberpepe.net:443 [链接]
- Url: http://www.uberpepe.net:443 [链接]
- Url: http://bedmaybebreakfast.fast.uberpepe.net:443 [链接]
- Url: http://mokofotand.uberpepe.net:443 [链接]
- Url: http://www.uberpepe.net:443 [链接]
- DnsService: dns://184.154.76.235:53 [链接]

图 5.23

探索 webdisk.uberpepe.net 的结果，我们可以发现任务选项已经变化，并且针对新目标。这次，我们可以运行漏洞检查、探测主机（当显示 RDP 或 VNC 端口时很有用），甚至使用“URI 破解”和“凭据破解”命令对目标进行破解。

> **警告** 破解凭据不在本书的范围内，如果你没有权限，这是非法的。如果使用这些工具，请合法且负责任。

# 第 5 章 网络发现自动化工具 103

Uri: http://webdisk.uberpepe.net:80

| 任务 | 值 |
| ------|
| 在此工作节点上运行任务 | 破解 |
| 详情 | 破解 |
| 丰富表格 | 示例 |
| 实体类型 | 导入 AS444 范围 |
| | 导入检查 |
| | 导入顶级域名 |
| | 搜索 Phishtank |
| | 检查安全头部 |
| | 收集并分析链接 |
| | 收集 SSL路径 |
| | 扫描元数据 |
| | 检查 SQLi 参数 |
| | 漏洞 HTTP 头部 |
| 漏洞检查 - 攻击处理程序 |

图 5.24

# 分析结果

Intrigue 的搜索引擎令人印象深刻。一旦扫描完成，点击“实体”查看它收集的所有内容。

对于 people.net，我们可以看到以下发现的实体，如图 5.25 所示：

- 实体总量：58
- DnsService: 1
- SshService: 1
- FtpService: 1
- SmtpService: 1
- Url: 34
- IpAddress: 1
- NetBlock: 1

| people | 开始 | 实体 | 分析 | 导出 | 系统 |
| --- | --- | --- | --- | --- | --- |
| | | | | | |
| | | | | | |
| | | | 下一页: 0 ... 99 | | |
| | | | name | | |
| 搜索: | | | | | |
| 提示：使用“name”和“details”搜索特定字段。用逗号隔开项。[DnsRecord: test.uberpepe.net] | | | | |
| | | [DnsRecord: www.uberpepe.net] | | | |
| | | [DnsRecord: people.net] | | | |
| | | [DnsRecord: whrm.uberpepe.net] | | | |
| | | [DnsRecord: grpe.uberpepe.net] | | | |
| | | [DnsRecord: webisk.uberpepe.net] | | | |
| | | [DnsRecord: net2.uberpepe.net] | | | |
| | | [DnsRecord: webmail.uberpepe.net] | | | |
| | | [DnsRecord: rest.uberpepe.net] | | | |
| | | [DnsRecord: mobile.uberpepe.net] | | | |
| | | [DnsRecord: mokobard.uberpepe.net] | | | |
| | | [DnsRecord: bemaybreakfast.uberpepe.net] | | | |
| | | [DnsRecord: bemaybreakfastfast.uberpepe.net] | | | |
| | | [DnsRecord: google.uberpepe.net] | | | |
| | | [DnsRecord: mail.uberpepe.net] | | | |
| | | |DnsRecord: ftp.uberpepe.net] | | | |

图 5.25

* 注意：

