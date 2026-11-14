


在 Linux 环境中要部署的蜜罐是 honeybits。13

## 部署注意事项

部署蜜罐时，应考虑几个事项。首先，蜜罐应尽可能逼真，从而对攻击者具有吸引力。真实程度——即看起来 _真实_ 的程度——将决定你是抓到攻击者，还是浪费时间，或者更糟。14 毕竟，如果攻击者发现你正在运行蜜罐，就不要指望他们会手下留情。最好的情况是，他们会直接离开；最坏的情况是，他们可能开始删除东西——而且不仅限于你的蜜罐。因此，应非常重视蜜罐的真实性，尤其是当它放置在生产环境中时。例如，如果蜜罐应该是一个 Linux 系统，那么不要运行 Windows 服务，反之亦然。此外，如果攻击者获得了系统访问权限，就给他们留些真实的东西可供发现，例如 honeytokens 或其他逼真的用户级文档和配置。

其次，你放置蜜罐的位置也会带来不同。在考虑面向互联网的蜜罐时，你可以问自己：SCADA（监控控制和数据采集）服务是否真的会托管在 Amazon AWS IP 地址空间中。在考虑内部蜜罐时，运行的配置和服务应与你放置蜜罐的环境融为一体。如果整个企业都在运行 Windows，只有一台主机除外，作为攻击者你会怀疑什么？另外，如果存在用户 VLAN 和服务器 VLAN，那么基于主机的蜜罐（服务很少甚至没有）应位于用户 VLAN，而具有多个但逼真服务的服务器类型配置应位于服务器 VLAN。

然而，对于安全研究人员来说，还有另一种选择。在非生产环境中使用蜜罐以进行研究时，你可以更自由地撒网（或者说搭建蜜网）。通过在云端运行一个开放多个端口（即使这些端口放在一起也不合理）的系统，你当然可以阻止高级攻击者，但蠕虫的最新变种会欣然连接并捐赠一个二进制样本供你分析。你看，这全部取决于你最初建立蜜罐的目的。

## 设置虚拟机

你可能决定将蜜罐安装在真正的完整操作系统上，但你可能希望从虚拟机提供的保护中受益，包括快照、与主机的显著隔离以及虚拟网络设置。在本章中，我们使用在虚拟机中运行的 64 位 Kali Linux 2017.1 来利用 Docker。然而，你也可以决定在云端（如 Amazon AWS、Digital Ocean 或类似平台）上运行蜜罐。

![](img/5f597c6a70133069118d9e804ace3775_586_0.png)

注意 请参阅“进一步阅读”部分，了解在 Amazon AWS 上设置 Ubuntu 16.04 的参考，但用户需自担风险：不要违反 Amazon 或你托管服务的任何用户协议。你已被警告。

## 开源蜜罐

在本节中，我们演示几个开源蜜罐。

### 实验 21-1：Dionaea

在本实验中，我们研究 Dionaea 蜜罐，这是一个模拟多个服务的轻量级蜜罐。15

![](img/5f597c6a70133069118d9e804ace3775_586_1.png)

注意 本章的实验需要 64 位 Linux，因为 Docker 不支持 32 位操作系统。我们使用 64 位 Kali 2017.1，如果你想跟进操作。

首先，设置一个文件夹以便从 Docker 中传输文件：

```
root@kali:~# mkdir data
```

拉取并运行 Dionaea Docker 镜像：

```
docker run -it -p 21:21 -p 42:42 -p 69:69/udp -p 80:80 -p 135:135 -p 443:443 -p 445:445 -p 1433:1433 -p 1723:1723 -p 1883:1883 -p 1900:1900/udp -p 3306:3306 -p 5060:5060 -p 5060:5060/udp -p 5061:5061 -p 11211:11211 -v `pwd`/data:/data dinotools/dionaea-docker:latest /bin/bash
```

现在，从容器的新 shell 中，让我们做一些更改并启用日志记录：

```
[container hash id]# sed -i 's/#default./default./' /opt/dionaea/etc/dionaea/dionaea.cfg
```

接下来，让我们在 dionaea.cfg 文件中启用会话的流捕获：

```
# cat <<EOF> /opt/dionaea/etc/dionaea/dionaea.cfg
[processor.filter_streamdumper]
name=filter
config.allow.0.types=accept
config.allow.1.types=connect
config.allow.1.protocols=ftpctrl
config.deny.0.protocols=ftpdata,ftpdatacon,xmppclient
next=streamdumper
[processor.streamdumper]
name=streamdumper
config.path=/opt/dionaea/var/dionaea/bistreams/%Y-%m-%d/
EOF
```

现在，启用处理器：

```
# sed -i 's/processors=filter_emu/processors=filter_emu,filter_streamdumper/' /opt/dionaea/etc/dionaea/dionaea.cfg
```

现在，让我们启动它：

```
# /opt/dionaea/bin/dionaea -u dionaea -g dionaea -c /opt/dionaea/etc/dionaea/dionaea.cfg
```

打开另一个 Kali 终端会话，并从该新 shell 中使用 Metasploit 攻击蜜罐：

```
root@kali:~/dionaea# msfconsole -x "use exploit/windows/smb/ms10_061_spoolss; set PNAME HPPrinter; set RHOST 127.0.0.1; set LHOST 127.0.0.1; set LPORT 4444; exploit; exit"
```

### Metasploit

数据管理麻烦？在 Metasploit Pro 中列出、排序、分组、标记和搜索你的渗透测试数据 -- 了解更多信息请访问 http://rapid7.com/metasploit

```
= [ metasploit v4.14.10-dev                             ]
+ -- --=[ 1639 exploits - 944 auxiliary - 289 post        ]
+ -- --=[ 472 payloads - 40 encoders - 9 nops             ]
+ -- --=[ Free Metasploit Pro trial: http://r-7.co/try_msp ]
```

```
PNAME => HPPrinter
RHOST => 127.0.0.1
LHOST => 127.0.0.1
LPORT => 4444
```

```
[!] You are binding to a loopback address by setting LHOST to
127.0.0.1. Did you want ReverseListenerBindAddress?
[*] Started reverse TCP handler on 127.0.0.1:4444
[*] 127.0.0.1:445 - Trying target Windows Universal...
[*] 127.0.0.1:445 - Binding to 12345678-1234-abcd-EF00
0123456789ab:1.0@ncacn_np:127.0.0.1[\spoolss] ...
[*] 127.0.0.1:445 - Bound to 12345678-1234-abcd-EF00
0123456789ab:1.0@ncacn_np:127.0.0.1[\spoolss] ...
[*] 127.0.0.1:445 - Attempting to exploit MS10-061 via
\\127.0.0.1\HPPrinter ...
[*] 127.0.0.1:445 - Printer handle:
00000000000000000000000000000000000000000000000000
[*] 127.0.0.1:445 - Job started: 0x3
[*] 127.0.0.1:445 - Wrote 73802 bytes to
%SystemRoot%\system32\VKurZGLb7Kudrj.exe
[*] 127.0.0.1:445 - Job started: 0x3
[*] 127.0.0.1:445 - Wrote 2241 bytes to
%SystemRoot%\system32\wbem\mof\RN21znSEgz7T0S.mof
[-] 127.0.0.1:445 - Exploit failed: NoMethodError undefined
method `unpack' for nil:NilClass
[*] Exploit completed, but no session was created.
```

请注意，来自 Metasploit 的攻击失败了。然而，这是预料之中的，因为我们运行的是低交互式蜜罐。不过，有效载荷已被传输和捕获，这也是本实验的目的。

现在，从第二个 Kali shell 中，像下面所示那样使用 FTP 连接到你的蜜罐。如果你是全新安装的 Kali，则需要先安装 FTP。

```
root@kali:~/dionaea# apt-get install ftp
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  ftp
0 upgraded, 1 newly installed, 0 to remove and 1220 not upgraded.
Need to get 58.7 kB of archives.
After this operation, 135 kB of additional disk space will be
used.
```

```
root@kali:~# ftp 127.0.0.1
Connected to 127.0.0.1.
220 DiskStation FTP server ready.
Name (127.0.0.1:root): foo
331 Password required for foo.
Password:
230 User logged in, proceed
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> help
Commands may be abbreviated.  Commands are:
```

| ! | dir | mdelete | qc | site |
|---|---|---|---|---|
| $ | disconnect | mkdir | sendport | size |
| account | exit | mget | put | status |
| append | form | mget | pwd | struct |
| ascii | get | mls | quit | system |
| bell | glob | mode | quote | sunique |
| binary | hash | modtime | recv | enex |
| bye | help | mput | reget | tick |
| case | idle | newer | rstatus | trace |
| cd | image | nmap | rhelp | type |
| cdup | ipany | nlist | rename | user |
| chmod | ipv4 | trans | reset | umask |
| close | ipv6 | open | restart | verbose |
| cr | lcd | prompt | rmdir | ? |
| delete | ls | passive | runique | |
| debug | macdef | proxy | send | |

```
ftp> bye
root@kali:~#
```

现在，让我们查看日志。从蜜罐 shell 中，按 ctrl-c 停止蜜罐，然后按如下方式查看日志：


