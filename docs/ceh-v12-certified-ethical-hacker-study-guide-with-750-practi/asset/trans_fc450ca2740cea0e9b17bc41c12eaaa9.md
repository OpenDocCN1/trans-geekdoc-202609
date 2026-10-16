
因为 syslog 支持远程日志记录，它可以作为集中化的日志主机使用。这一点在为应急响应做准备时，可能显得尤为重要。常见的隐藏痕迹的做法是清除日志。任何获得系统访问权限的攻击者可能会擦除本地日志，但如果他们正在将日志流传到外部，则日志会保留供以后使用，除非攻击者能够入侵集中日志主机。

下面的代码块展示了 syslog 消息的示例。每条消息以日期开头，随后是发出消息的主机名。接着是产生日志的进程（包括进程 ID）。最后是进程生成的消息内容。

```
[syslog Messages]
Jun 26 10:27:16 boardinghouse kernel: [923361.001444] vmbr0: port 3(tap210i0) entered forwarding state
Jun 26 10:27:17 boardinghouse pvedaemon[10864]: <root@pam> end task
UPID:boardinghouse:000034F1:0580EE23:5B326963:qmstart:210:root@pam: OK
Jun 26 10:27:42 boardinghouse pvedaemon[9338]: <root@pam> starting task
UPID:boardinghouse:00003552:0580F8B5:5B32697E:vncproxy:210:root@pam:
Jun 26 10:32:09 boardinghouse pvedaemon[9338]: <root@pam> end task
UPID:boardinghouse:00003552:0580F8B5:5B32697E:vncproxy:210:root@pam: OK  
```
