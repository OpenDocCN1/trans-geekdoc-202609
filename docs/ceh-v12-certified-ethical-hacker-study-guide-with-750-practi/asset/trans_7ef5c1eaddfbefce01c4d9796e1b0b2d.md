
-   [hping](https://wiki.example.org/hping)是开发者认为的TCP/IP数据包的“瑞士军刀”。你可以将其用作普通的ping程序，发送ICMP回显请求。由于`hping`主要是一个数据包构造程序，它允许你使用你想要的头部设置通过不同协议发起连接，默认模式可能对你并不理想。默认情况下，如果你只指定目标主机或IP地址而不做其他设置，`hping`会向目标的端口0发送带有变化源地址的数据包。地址0本质上是无效的目标，因为它被视为保留且没有用途。你不应该收到你正在发送流量的目标系统的任何响应。如果收到响应，说明目标主机真的在违反协议。虽然`hping`使用TCP实现这一点，但端口0对UDP和TCP都是无效的。

-   虽然你可以使用`hping`替代ping程序，通过使用`‑1`参数（即启用ICMP模式）来建立对特定端口的连接。你将获得与ping程序相同的行为，即获取系统的“存活”状态和往返时间。此外，你还能获得更详细的信息，因为你可以知道特定服务是否正在运行。这在对应用进行测试时可能很有用，帮助你发现服务何时失败。除了往返时间外，响应中会包含大量细节。

-   下面的代码片段展示了对目标系统上Web服务器进行`hping3`的运行示例。

**发送SYN消息到目标系统**

```
kilroy@quiche:~$ sudo hping3 -S -p 80 192.168.86.1
HPING 192.168.86.1 (eth0 192.168.86.1): S set, 40 headers + 0 data bytes
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=0 win=29200 rtt=7.9 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=1 win=29200 rtt=7.9 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=2 win=29200 rtt=7.6 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=3 win=29200 rtt=7.5 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=4 win=29200 rtt=7.3 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=5 win=29200 rtt=3.0 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=6 win=29200 rtt=2.8 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=7 win=29200 rtt=2.7 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=8 win=29200 rtt=2.5 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=9 win=29200 rtt=2.4 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=10 win=29200 rtt=2.2 ms
```

-   `hping`会返回所有已设置的标志，包括SYN和ACK以及不分片位（DF）。此外，你还能看到IP标识、相对序号以及目标主机提供的窗口大小等信息。对于没有监听的端口，`hping`不会像标准ping程序那样提示主机不可达或超时，而是返回与开放端口相同的响应。标志会显示为RA（表示RST和ACK），说明远程系统重置了端口，表明没有应用程序在该端口上。

-   除了ICMP和TCP，你还可以发送UDP消息。由于UDP头部选项有限，发送UDP消息的参数较少。`hping`可以通过`‑‑scan`（或`‑8`）参数进行端口扫描。下面的示例展示了扫描1‑1023端口的过程，针对管理端口范围。输出中被截断的部分是未监听的端口号及其服务名称。

**使用hping进行UDP端口扫描**

```
root@quiche:~# hping3 --scan 1-1023 –a 10.15.24.5  -2 192.168.86.1
Scanning 192.168.86.1 (192.168.86.1), port 1-1024
1024 ports to scan, use -V to see all the replies
+----+-----------+---------+---+-----+-----+-----+
|port| serv name |  flags  |ttl| id  | win | len |
+----+-----------+---------+---+-----+-----+-----+
All replies received. Done.
Not responding ports: (1 tcpmux) (2 nbp) (3 ) (4 echo) (5 ) (6 zip) (7 echo) (8 ) (9 discard) (10 ) (11 systat) (12 ) (13 daytime) (14 ) (16 netstat) (17 ) (18 qotd) (19 msp) (20 chargen) (21 ftp-data) (22 ftp) (23 ssh) (24 )
```

-   `hping`还能够发送任意大小的数据包。使用`‑d`后跟字节计数可以设置数据包的体积。你还可以通过`‑‑file`参数指定文件，让`hping`读取文件内容并用于填充数据包的数据部分，这可能会导致应用因违反协议规范而崩溃。

-   `packETH`与`hping`不同，它采用图形用户界面（GUI）来设置所有参数。所选协议的头部集合会根据协议而变化，每个低层头部指示下一个协议，即下一组头部。选择协议后，`packETH`会自动提供该协议所需的所有头部字段。图5.25展示了IP头和TCP头的字段，同时也指示在层2头部中选择IP作为下一层协议。虽然此截图看不到层2头部，但你可以在`packETH`中设置地址、选择层2协议版本、添加802.1q虚拟局域网（VLAN）标签，以指定帧所属的VLAN。

