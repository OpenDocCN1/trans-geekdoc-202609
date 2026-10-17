
# Nmap 扫描日志

## 端口发现阶段

Discovered open port `21/tcp` on `192.168.56.102`
Discovered open port `29/tcp` on `192.168.56.102`
Discovered open port `80/tcp` on `192.168.56.102`
Discovered open port `143/tcp` on `192.168.56.102`
Discovered open port `443/tcp` on `192.168.56.102`
Discovered open port `993/tcp` on `192.168.56.102`

... (truncated)

## Nmap 扫描详细输出

```
Starting Nmap 7.70 (https://nmap.org ) at 2019-01-15 13:43 GMT
NSE: 148 scripts for pre-scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 13:43
Completed NSE at 13:43, 0.00s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 13:43
Completed NSE at 13:43, 0.00s elapsed
Initiating ARP Ping Scan at 13:43
Scanning 192.168.56.102 [1 port]
Completed ARP Ping Scan at 13:43, 0.04s elapsed (1 hosts)
Initiating Connect Scan at 13:43
Scanning 192.168.56.102 [65535 ports]
Discovered open port 21/tcp on 192.168.56.102
Discovered open port 143/tcp on 192.168.56.102
Discovered open port 80/tcp on 192.168.56.102
Discovered open port 29/tcp on 192.168.56.102
Discovered open port 993/tcp on 192.168.56.102
Discovered open port 443/tcp on 192.168.56.102
...
```

# Nmap 扫描结果 (TCP)

扫描完成后，将提供一个扫描报告，并输出到通过 `-oN` 指定的文本文件中。在 `192.168.56.102` 上发现了开放端口 `21/tcp`、`143/tcp`、`80/tcp`、`29/tcp`、`993/tcp`、`443/tcp`...

| 端口 | 状态 | 服务 | 版本 |
| :--- | :--- | :--- | :--- |
| 21/tcp | open | ftp | ProFTPD 3.3 |
| 25/tcp | open | smtp | Exim smtp 4.6 |
| 80/tcp | open | http | nginx 1.4.0 |
| 110/tcp | open | pop | Cyrus popd 2.3.2 |
| 143/tcp | open | imap | Cyrus imad 2.3.2 |
| 443/tcp | open | ssl/http | nginx 1.4.0 |
| 995/tcp | open | pop3/pop3 | Cyrus popd 2.3.2 |
| 4190/tcp | open | sieve | Cyrus timmsied 2.3.2 |

服务信息：主机：`localhost`, `mailserver01`；操作系统：`Unix`, `Linux`； CPE: `cpe:/o:linux:linux_kernel`

Nmap 完成：在 172.77 秒内扫描了 1 个 IP 地址（1主机在线）
发送的原始数据包：26 (1.986KB) | 接收：14 (1.238KB)

这次扫描的结果与你初始扫描的结果会有很大不同。这一次，由于你启用了额外的 Nmap 选项，你可以看到更多关于主机上运行服务的信息，并且识别出了一个额外的开放端口 (`4190`)。注意报告顶部的表头：

| 端口 | 状态 | 服务 | 原因 | 版本 |
| :--- | :--- | :--- | :--- | :--- |

开放的端口将用如下行标出：

| 25/tcp | open | smtp | syn-ack | Exim smptd 4.68 |

在此示例中，端口是 TCP 端口 `25`，状态为 `open`（开放），在该端口上运行的服务是 SMTP 服务器。Nmap 确定该端口开放的原因是它接收到了 `SYN-ACK` TCP 数据包。这是之前提到的三次握手的一部分，`R` 表示该服务已开放并正在等待远端的 `ACK`（确认）响应。Nmap 还检测到了该端口上的软件响应（`Exim smptd 4.68`）。Exim 是软件的名称，`smptd` 中的 `d` 代表 `daemon`（守护进程）。*守护进程*是一个作为后台进程运行的程序，在系统启动时自动启动。`4.68` 是 Exim 软件的版本号。

这些是你在扫描真实服务器时可能预期看到的内容。在这一组结果中，有几个服务特别值得关注，因为它们与电子邮件直接相关。这些是我们在本章将重点关注的服务。其他服务将在未来章节的相关部分进行介绍。

当你进行渗透测试时，你很可能想按顺序遍历端口，通过探测每个端口获取信息并移动到下一个端口。现在，我们将跳过文件传输协议（FTP）服务（将在第 9 章“文件和文件共享”中探索）以及丢弃服务（discard service），并转向运行在端口 `25` 上的 SMTP 服务。这前三个开放端口的结果如下：

| 端口 | 状态 | 服务 | 原因 | 版本 |
| :--- | :--- | :--- | :--- | :--- |
| 9/tcp | open | discard? | syn-ack | |
| 21/tcp | open | ftp | syn-ack | ProFTPD 1.3.3a |
| | | auth-owners: nobody | | |
| 25/tcp | open | smtp | syn-ack | Exim smptd 4.68 |

# 探测 SMTP 服务

```
| auth-owners: Debian-exim
| smtp-commands: localhost Hello nmap.scan.me [192.168.56.103], SIZE 5242800, EXPN, PIPELINING, HELP,
| 支持的命令: AUTH HELLO EHLO MAIL RCPT DATA NOOP QUIT RSET HELP EXPN VRFY
```
