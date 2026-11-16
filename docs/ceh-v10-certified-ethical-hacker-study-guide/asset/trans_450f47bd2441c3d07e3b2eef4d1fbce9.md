

## 日志记录

在此过程中，在多个地方出现过一个想法，即日志记录。这不仅是系统日志记录，也是应用程序日志记录。不仅如此，它不仅仅是桌面或服务器等系统上的日志记录，还包括路由器和交换机等网络设备，当然还有防火墙上的日志记录。即使在网络中运行了 IDS 的情况下，你也不一定总是想要发出警报，因为可能有一些你不觉得有必要跟进的事件。但是，一旦发生安全漏洞，了解事件发生的事实可能很有用。拥有历史数据的重要性无论如何强调都不为过。

许多系统，包括类 Unix 系统以及网络设备，都支持 syslog 协议。这是一种日志记录协议，最初是作为 Simple Mail Transfer Protocol (SMTP) 服务器 sendmail 的日志机制而出现的。多年来，自 20 世纪 80 年代 syslog 首次在 sendmail 中实现以来，它已成为类 Unix 系统上的标准日志解决方案，该协议已在 RFC 3164 中记录，后来在 RFC 5424 中标准化。Syslog 不仅在消息的创建和读取中具有易于理解的语法，还可以用于远程日志记录和本地日志记录。

由于 syslog 可以支持远程日志记录，它可以用作集中式日志主机。这一事实在准备事件响应时也许尤其重要。清除痕迹的常见方法是清除日志。任何获得系统访问权限的攻击者都可能擦除本地日志，但如果日志正在从系统流出，它们将被保留以供日后使用，除非攻击者能够攻破集中式日志主机。

你可以在下面的代码清单中看到 syslog 消息的示例。每条消息都以日期开头，后跟来源主机名。然后是创建日志的进程，包括进程识别号。最后，显示进程生成的消息。

### syslog 消息

```
Jun 26 10:27:16 boardinghouse kernel: [923361.001444] vmbr0: port 3(tap210i0) entered forwarding state
Jun 26 10:27:17 boardinghouse pvdaemon[10864]: <root@pam> end task
UPID:boardinghouse:000034F1:0580EE23:5B326963:qmstart:210:root@pam: OK
Jun 26 10:27:42 boardinghouse pvdaemon[9338]: <root@pam> starting task
UPID:boardinghouse:00003552:0580F885:5B32697E:vncproxy:210:root@pam:
Jun 26 10:32:09 boardinghouse pvdaemon[9338]: <root@pam> end task
UPID:boardinghouse:00003552:0580F885:5B32697E:vncproxy:210:root@pam: OK
```

syslog 标准定义了设施来对消息进行分类，以便它们可以被路由到不同的位置。例如，与身份验证相关的任何消息都可以放入单个文件中，远离其他类型的消息。每个设施可以路由到不同的文件，甚至不同的系统，如果你希望某些日志消息存储在本地，而其他消息存储在集中位置。在某些 syslog 实现中，你可以同时本地和远程存储。这提供了本地日志以及充当备份的远程日志。

除了设施之外，syslog 还定义了严重性。这意味着应用程序可以确定事件的级别，包括信息性、调试、警告和错误。与设施一样，严重性也可以重定向到不同的位置。

当然，并非每个系统都是类 Unix 系统。Windows 系统在桌面和服务器上都非常常见。在 Windows 系统上，日志消息会发送到事件子系统。与 syslog 使用的基于文本的消息不同，事件子系统使用二进制存储系统。当然，事件子系统存储数据的方式的一个优势是，可以像查询数据库一样对其进行查询。虽然解析消息不那么容易，但你可以查询消息的事实意味着你可以通过单个查询轻松返回相关消息。

Windows 的事件子系统也拥有大量数据。除了系统、安全和应用程序等不同类别之外，还有事件 ID。事件 ID 可以识别所有相同的条目。搜索事件 ID 可以为你提供特定事件的每个实例，该事件可能跨多个进程发生。图 3.7 显示了 Windows 事件查看器中的单个事件，你可以在其中看到事件 ID。你还可以在事件查看器中看到随每个事件提供的其他信息。

### 图 3.7 事件查看器

![](img/421171b17a0c0dfae0aacde15d9831c1_107_0.png)

在两种情况下，应用程序开发人员都可以利用系统提供的日志功能。在 Unix 端，任何开发人员都可以写入 syslog，syslog 服务将根据配置文件中的定义处理写入日志的操作。这使开发人员免于开发日志方案的负担，并确保查找日志消息的单一位置。Windows 系统也是如此。任何应用程序开发人员都可以利用事件子系统，使用它来写入日志消息。应用程序甚至可以有自己的日志文件，Windows 会将日志拆分到不同的位置。如果你进入事件查看器应用程序，你将能够查看所有事件日志条目以及事件日志所属的不同类别。你通常会看到 Windows 正在记录的所有应用程序列表。任何应用程序都可以在该列表中拥有自己的条目，以使日志与系统分开，同时仍然记录到与其他所有日志相同的位置。

## 审计

日志很重要，我们通常依赖应用程序开发人员来实现日志记录，理想情况下是可配置的日志记录，意味着不同级别的日志消息。能够将日志记录调整到详细级别可以使故障排除容易得多。操作系统也是如此。这时审计就可以派上用场了。类 Unix 系统和 Windows 系统都提供启用和配置审计的功能。当然，两种系统对审计的定义不同。

在 Windows 系统上，审计是一种安全功能。它涉及系统事件的成功或失败。例如，这可以包括登录的成功或失败，或者对系统文件的访问。图 3.8 显示了本地安全策略应用程序中的审计策略设置。策略中的每个类别都可以记录成功或失败。但这并不是二选一的关系。你可以同时记录成功和失败。如果审计事件被触发，它们将出现在 Windows 事件查看器的安全日志中。

### 图 3.8 Windows 中的审计策略

![](img/421171b17a0c0dfae0aacde15d9831c1_108_0.png)

在 Linux 端，存在完全不同的审计基础架构。使用 auditctl 程序，可以在 Linux 系统上管理审计策略。Linux 内核中的审计子系统可用于监视文件和目录的活动。它可以用于监视应用程序执行。也许最重要的是，它还可以用于监视系统调用。系统上任何程序使用的任何系统调用都可以被监视和记录。审计子系统通常有自己的日志集。下面的代码清单显示了 CentOS Linux 系统 audit.log 中一些日志条目的示例。

### audit.log 示例输出

```
type=USER_LOGIN msg=audit(1530130008.763:341): pid=9711 uid=0 auid=0 ses=30
msg='op=login id=0 exe="/usr/sbin/sshd" hostname=binkley.lan addr=192.168.86.49
terminal=dev/pts/0 res=success'
type=USER_START msg=audit(1530130008.765:342): pid=9711 uid=0 auid=0 ses=30
msg='op=login id=0 exe="/usr/sbin/sshd" hostname=binkley.lan addr=192.168.86.49
terminal=dev/pts/0 res=success'
type=CONFIG_CHANGE msg=audit(1530130271.424:353): auid=4294967295 ses=4294967295
op=add_rule key=(null) list=4 res=1
type=SERVICE_START msg=audit(1530130271.424:354): pid=1 uid=0 auid=4294967295
ses=4294967295 msg='unit=auditd comm="systemd" exe="/usr/lib/systemd/systemd"
hostname=? addr=? terminal=? res=success'
type=SYSCALL msg=audit(1530130283.962:355): arch=c000003e syscall=59 success=yes
exit=0 a0=106e000 a1=1063a90 a2=10637e0 a3=7ffec3721e70 items=2 ppid=9711
pid=9908 auid=0 uid=0 gid=0 euid=0 suid=0 fsuid=0 egid=0 sgid=0 fsgid=0 tty=pts0
ses=30 comm="cat" exe="/usr/bin/cat" key=(null)
type=EXECVE msg=audit(1530130283.962:355): argc=2 a0="cat" a1="audit.log"
type=CWD msg=audit(1530130283.962:355): cwd="/var/log/audit"
type=PATH msg=audit(1530130283.962:355): item=0 name="/usr/bin/cat" inode=2799
dev=fd:00 mode=0100755 ouid=0 ogid=0 rdev=00:00 objtype=NORMAL cap_fp=0000000000000000 cap_fi=0000000000000000 cap_fe=0 cap_fver=0
type=PATH msg=audit(1530130283.962:355): item=1 name="/lib64/ld-linux-x86-64.so.2" inode=33559249 dev=fd:00 mode=0100755 ouid=0 ogid=0 rdev=00:00 objtype=NORMAL cap_fp=0000000000000000 cap_fi=0000000000000000 cap_fe=0 cap_fver=0
type=PROCTITLE msg=audit(1530130283.962:355): proctitle=6361740061756469742e6C6F6767
```

每个条目都提供关于条目类型的详细信息，这指示了审计子系统检测到的内容。例如，第一个条目表示用户已登录。你可以从详细信息中看到，连接来自的地址是 192.168.86.49，可执行文件是 /usr/sbin/sshd，结果是成功。其他条目指示文件操作、程序执行和配置更改。

与 Windows 下的审计一样，Linux 下的审计也需要配置。你可以通过创建 auditd 守护进程使用的规则来完成此操作。你可以直接在配置文件中进行更改，也可以使用 auditctl 命令在命令行中添加规则。这直接实施更改，也是审计系统启动时调用的内容。放入配置文件的是将传递给 auditctl 的命令行参数。

