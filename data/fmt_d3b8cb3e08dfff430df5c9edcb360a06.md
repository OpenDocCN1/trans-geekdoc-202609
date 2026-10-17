
# 附录 E：Cisco 防火墙命令

目前，防火墙是用于保护企业、军事或政府网络基础设施外部边界的主要设备。正确配置后，防火墙能有效防止公共互联网上的恶意用户访问私有数据，即使组织已连接互联网。Cisco 是互联网基础设施设备（如路由器、防火墙和虚拟专用网络 VPN）的主要供应商。鉴于大多数网络都会部署防火墙，且 Cisco 是网络基础设施组件的主要供应商，本文将介绍 Cisco PIX 防火墙使用的命令。

## PIX 命令参考

输入单独的问号（`?`）可列出所有命令；输入“`命令 空格 ?`”可获取特定命令的帮助信息。

在行首输入冒号（`:`）可向配置添加注释。使用注释可提高配置文件的可读性，或使配置文件中的命令不可执行。

**注意：** `cm` = 配置模式，`pm` = 特权模式，`um` = 非特权模式。

| 命令 | 说明 |
| :--- | :--- |
| `age 15` | 设置私有链路密钥的有效期为 15 分钟，`cm`。 |
| `apply` | 将出站访问控制列表应用于 IP 地址，`cm`。使用出站列表来允许或禁止访问系统端口。 |
| `arp` | `cm`。向 PIX 防火墙的 ARP 表添加条目。ARP 是一种低层 TCP/IP 协议，用于根据 IP 地址解析节点的物理地址。 |
| `arp timeout 42` | `cm`。修改 ARP 表条目的有效时间，条目在 ARP 表中存在 42 秒后被清除。默认是 4 小时。 |
| `auth` | 启用 PIX 用户认证，`cm`。最多 5 次登录机会。 |
| `auth-server` | 指定认证服务器的 IP 地址，`cm`。 |
| `auth-user` | 指定认证用户的 IP 地址，`cm`。允许为 IP 地址提供认证服务。 |
| `clear apply` | `cm`。清除对 IP 地址的之前的 outbound 访问控制列表应用。 |
| `clear arp` | `pm`。清除 PIX 的 ARP 表条目。可以通过 MAC 或 IP 地址清除。 |
| `clear auth-user` | `cm`。移除 IP 地址的认证访问权限。 |
| `clear auth-server` | `cm`。指定认证服务器不再处理认证请求。 |
| `clear http` | `cm`。移除对 IP 地址的 HTTP 访问。 |
| `clear outbound` | `cm`。清除出站访问列表。 |
| `clear route` | `cm`。清除内部或外部接口的路由表。 |
| `clear snmp-server` | `cm`。清除 SNMP 连接或位置，或停止发送 SNMP 事件数据。 |
| `clear syslog` | `cm`。停止记录 syslog 消息。 |
| `clear telnet` | `cm`。从用户中移除 PIX Telnet 访问权限。 |
| `conduit` | `cm`。为入站连接在防火墙上添加通道。 |
| `configure floppy` | `pm`。将当前配置与软盘上的配置合并。 |
| `configure memory` | `pm`。将配置与闪存中的配置合并。 |
| `configure terminal` | `pm`。启动配置模式。 |
| `disable` | `pm`。退出特权模式并返回到非特权模式。 |
| `enable` | `um`。启动特权模式。 |
| `enable password` | `pm`。设置特权模式密码。 |
| `failover` | `cm`。启用可选的故障转移功能的访问。 |
| `global` | `cm`。在全局池中定义 IP 地址。 |
| `help` | `um`。显示帮助信息。 |
| `hostname` | `cm`。在 PIX 命令行提示符中更改主机名。 |
| `http` | `cm`。允许内部 IP 地址访问 PIX HTML 管理界面。 |
| `interface ethernet` | `cm`。标识以太网板的速度和全双工模式。 |
| `interface token` | `cm`。标识令牌环板的速度。 |
| `ip address` | `cm`。标识 PIX 的 IP 地址。 |
| `kill telnet_id` | `pm`。终止一个 Telnet 会话。 |
| `link` | `cm`。指定到 PIX 的私有链接连接。 |
| `linkpath` | `cm`。定义私有链接的目标 IP 地址。 |
| `lnko` | `cm`。定义访问旧版本 2 私有链接 PIX 的访问权限。 |
| `lnkopath` | `cm`。指定到远程 PIX 的版本 2 私有链接路径。 |
| `nat` | `cm`。将网络与 IP 地址池关联。 |
| `no apply` | `cm`。取消之前使用 `apply` 命令的配置。 |
| `no arp` | `pm`。删除 PIX ARP 表中的内容。 |
| `no auth` | `cm`。暂停用户认证服务。 |
| `no auth-server` | `cm`。移除对认证服务器的访问权限。 |
| `no auth-user` | `cm`。禁用针对 IP 地址的用户认证。 |
| `no conduit` | `cm`。移除一个通道。 |
| `no failover` | `cm`。关闭故障转移或强制 PIX 进入待机模式。 |
| `no global` | `cm`。从全局池中移除 IP 地址。 |
| `no http` | `cm`。移除对 PIX HTML 管理界面的 IP 地址访问权限。 |
| `no link` | `cm`。禁用私有链接连接。 |
| `no linkpath` | `cm`。禁用私有链接的目标 IP 地址。 |

---

# 常用 UNIX/Linux 命令参考

## 文件压缩与解压

| 命令 | 说明 | 示例 | 解释 |
| :--- | :--- | :--- | :--- |
| `Compress filename` | 通过节省磁盘空间对文件进行压缩 | | |
| `Uncompress filename` | 解压缩文件 | | |

## 表达式求值

| 命令 | 说明 | 示例 | 解释 |
| :--- | :--- | :--- | :--- |
| `Eval "resize"` | 告诉目标计算机窗口在 telnet 期间已被调整 | | |

## 文件过期控制 (Chexp)

| 命令 | 说明 | 示例 | 解释 |
| :--- | :--- | :--- | :--- |
| `Chexp #` | 防止文件在目标计算机上过期（被擦除）# 天 | `Chexp 365 nr*` | 防止目标计算机删除所有以 `nr` 开头的文件长达 1 年（365 天） |
| | | `Chexp 4095 nr*` | 使所有以 `nr` 开头的文件永不过期或被删除（无限） |

## 队列状态查看 (Qstat)

| 命令 | 说明 | 示例 | 解释 |
| :--- | :--- | :--- | :--- |
| `Qstat` | 显示已提交到网络排队系统（本质上是批处理作业）的进程状态 | `Qstat` | 显示提交者的请求状态，包括请求名称、请求 ID、所有者、相对优先级和状态（是否已运行） |
| | | `Qstat -a` | 显示所有请求 |
| | | `Qstat -l` | 显示长格式请求 |
| | | `Qstat -m` | 显示中等长度格式请求 |
| | | `Qstat -u bob` | 仅显示属于用户 `bob` 的请求 |
| | | `Qstat -x` | 显示扩展格式的请求头 |

## 终端窗口管理 (Xterm)

| 命令 | 说明 | 示例 | 解释 |
| :--- | :--- | :--- | :--- |
| `Xterm` | 打开新窗口 | `Xterm` | 这将打开一个类似当前窗口的新窗口 |
| | | | 供你工作 |
| | | | 供你当前正在工作的窗口 |
| `Xterm -option` | `-option` 设置选项 | | |
| `Xterm +option` | `+option` 将选项重置为默认值 | | |
| `Xterm -help` | 显示 xterm 选项 | `Xterm -help` | 显示可用的选项 |
| `Xterm -e program` | 在新 xterm 窗口中执行指定程序；程序执行完毕后，新窗口关闭 | `Xterm -e myprog.exe` | 在 xterm 窗口中执行 `myprog.exe` 程序，以便你仍可在当前窗口工作 |
| `Xterm -sb` | 打开一个 xterm，当输出超出页面顶部时保存指定行数并通过滚动条访问，使其可滚动回顾过去的行 | `Xterm -sb` | 在页面右侧添加滚动条，用于查看过去的行 |
| `Xterm -sl number` | 指定保存的行数，一旦滚动到屏幕顶部之外，Xterm 会保存这些行（默认是 64） | `Xterm -sl 1000` | Xterm 会保存 1000 行工作，直到滚动到即视区之外；可以通过滚动条访问 |
| `Xterm -geom WxH+X+Y` | 该选项允许指定新窗口的大小 `W x H`（像素/字符），以及在窗口打开时的位置 `X, Y` | `xterm -geom 80x80+0+50` | 打开一个 80x80 的窗口，并将其左上角放在屏幕左侧 0 处、顶部 50 处 |
| | | `xterm -geom 10x35+300+500` | 10x35 的窗口，窗口左上角距左侧 300、距顶部 500 |
| | | `xterm -geom 5x5+0+0` | 创建一个 5x5 的窗口，窗口左上角位于屏幕左上角 |
| `Xterm -title Label` | 允许为窗口的标题栏设置标签 | `Xterm -title SCRIPTS` | 打开一个标题为 `SCRIPTS` 的 xterm 窗口（默认标题为 `-e` 选项后的内容） |
| `Xterm -area Color` | 允许修改 xterm 窗口中不同区域的颜色 | `Xterm -bg white` | 将背景颜色设置为 `white` |
| | | `Xterm -bd huntergreen` | 将窗口边框颜色设置为 `huntergreen` |
| | | `Xterm -fg red` | 将文本颜色设置为 `red` |
| `Xterm -fn font` | 设置新 xterm 窗口的字体 | `Xterm -fn courr18` | 设置字体为 `courr18`（默认是 `fixed`） |
| `Xterm -iconic` | 以图标化（最小化）方式启动新 xterm 窗口（双击可最大化） | `Xterm -iconic -title xyz` | 打开一个图标化的 xterm，标题为 `xyz` |

> **注意：**
> *   使用 xterm 可以消除桌面杂乱。强烈建议在脚本中学习使用它。
> *   当在滚动条上点击时，左键向下滚动，右键向上滚动，中键将滚动条定位到鼠标位置以便上下拖动。
> *   窗口的大小优先于位置，所以如果你将其定位得太靠近屏幕边缘，它将会在保持正确大小的前提下贴边定位。
> *   Position `+0+0` 是屏幕左上角；右下角大约是 `+1200+1000`，取决于分辨率。
> *   选项可以组合使用。

## 别名与归档管理

| 命令 | 说明 |
| :--- | :--- |
| `alias dir ls` | 允许将 `dir` 或 `ls` 打印为目录列表。（注：可以将任何单词替换 `dir`，甚至使用 `mouse`。因此，当我在命令行输入 `mouse` 时，它会执行 `ls` 命令的功能。） |
| `alias` | 显示所有已定义的别名。 |
| `unalias dir` | 现在 `dir` 不再作为替代 `ls` 的命令使用。 |
| `alias h history` | 我现在只需输入 `h` 即可代替完整的 `history` 命令。 |
| `history` | `history` 命令会列出系统中已输入的命令列表（数量取决于 history 的配置）。 |
| `tar -cvf a:archive .` | 备份当前目录（`.`），并将生成的归档存储在磁盘的软盘上： |
| `tar -cvf a:archive *.doc` | 备份所有带 `.doc` 后缀的文件 |
| `tar -cvf a:archive -` | 当需要从键盘输入文件名（标准输入）时使用。每行输入一个文件名。`^Z` 表示列表结束 |
| `tar -tf a:archive \| more` | 列出 archive 中当前包含的所有文件 |
| `find / -ctime -7 > weeklist` | 查找最近 7 天内修改的文件，并将文件名写入 weeklist |
| `tar -cvf a:archive - < weeklist` | 备份 weeklist 中的所有文件 |
| `find / -ctime -7 \| tar -cvf a:archive -` | 使用管道（`|`）实现上述两条命令的相同功能 |
| `df` | 显示文件系统的磁盘空间使用情况 |
| `du` | 显示目录的磁盘空间使用量 |
| `grep -i '^Aftp' /etc/inetd.conf` | 检查是否在运行 ftp 服务： |
| `find / -name '*s' -print` | 从根目录（`/`）开始查找以 `s` 结尾的文件并打印到屏幕 |
| `find / -name core -atime +7 -exec rm -f {} \;` | 查找 7 天以上未访问的 core 文件并强制删除它们。core 文件记录系统或应用程序故障的信息 |
| `find / -ctime -2 -print` | 列出 2 天内修改的文件 |
| `find /users/jake -exec chown jake {} \;` | 将 `/users/jake` 目录及其下所有文件的所有者改为 jake |
| `find / -nogroup -print` | 查找无属组的文件 |
| `find / -nouser -print` | 查找无属主的文件 |
| `fsck` | 文件系统检查与修复 |
| `ftp` | 文件传输协议客户端 |

