
# more /opt/dionaea/var/dionaea/dionaea.log

二进制文件可在以下位置找到
# ls /opt/dionaea/var/dionaea/binaries/
和会话数据流可在以下位置找到
# ls /opt/dionaea/var/dionaea/bitstreams/

![](img/5f597c6a70133069118d9e804ace3775_590_0.png)

注意 由于我们的蜜罐在 Docker 中运行，文件不具备持久性。因此，如果您想进一步检查某个文件，需要将其移动到我们设置的共享文件夹。在 Docker 容器内，使用 tar 将文件复制到 /data 文件夹，该文件夹映射到我们在 Kali 上的工作目录，如下所示：

```
# tar -cvf /data/dionaea.tar /opt/dionaea/var/dionaea/
```

## 实验 21-2：ConPot

在本实验中，我们将研究 ConPot 蜜罐，它模拟了一个 ICS/SCADA 设备。16

再次创建一个目录，这次用于存放日志（另一种常见用例）：

```
root@kali:~# mkdir -p var/log/conpot
```

现在拉取并运行 ConPot 蜜罐：

```
root@kali:~# docker run -it -p 80:80 -p 102:102 -p 502:502 -p 161:161/udp -v $(pwd)/var/log/conpot:/var/log/conpot --network=bridge honeynet/conpot:latest
```

现在，从另一个 Linux 或 Mac shell 中，针对主机运行 snmpwalk：

```
$ snmpwalk -c public 192.168.80.231
SNMPv2-MIB::sysDescr.0 = STRING: Siemens, SIMATIC, S7-200
SNMPv2-MIB::sysObjectID.0 = OID: SNMPv2-SMI::enterprises.20408
DISMAN-EVENT-MIB::sysUpTimeInstance = Timeticks: (415) 0:00:04.15
SNMPv2-MIB::sysContact.0 = STRING: Siemens AG
SNMPv2-MIB::sysName.0 = STRING: CP 443-1 EX40
SNMPv2-MIB::sysLocation.0 = STRING: Venus
SNMPv2-MIB::sysServices.0 = INTEGER: 72
SNMPv2-MIB::sysORLastChange.0 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::snmpInPkts.0 = Counter32: 9
SNMPv2-MIB::snmpOutPkts.0 = Counter32: 0
SNMPv2-MIB::snmpInBadVersions.0 = Counter32: 0
SNMPv2-MIB::snmpInBadCommunityNames.0 = Counter32: 0
SNMPv2-MIB::snmpInBadCommunityUses.0 = Counter32: 0
SNMPv2-MIB::snmpInASNParseErrs.0 = Counter32: 0
...<truncated for brevity>...
```

打开网页并查看下一张截图所示的 Web 界面。请务必点击几次 Refresh 以查看变化。

![](img/5f597c6a70133069118d9e804ace3775_591_0.png)

![](img/5f597c6a70133069118d9e804ace3775_591_1.png)

注意 系统名称和其他指纹项可在源文件的 templates 目录中调整。强烈建议您修改这些内容；否则，您将不会拥有一个非常活跃的 ConPot。

日志可在共享文件夹中找到：

```
root@kali:~# less var/log/conpot/conpot.log
```

## 实验 21-3：Cowrie

在本实验中，我们将拉取并使用 Cowrie 蜜罐，正如作者所描述的那样，它是一个中交互蜜罐，17 能够模拟 SSH 和 Telnet，最重要的是，能够捕获每个命令。它还能重播按键序列，以便有趣地查看黑客活动。

克隆蜜罐 GitHub 仓库，然后配置、构建并运行蜜罐：

```
root@kali:~# git clone https://github.com/micheloosterhof/docker-cowrie.git
```

```
root@kali:~# cd docker-cowrie
root@kali:~/docker-cowrie# mkdir -p var/log/cowrie var/run etc
root@kali:~/docker-cowrie# cat <<EOF> etc/cowrie.cfg
[telnet]
enabled = yes
EOF
```

由于此特定 Docker 镜像将用户名设置为 "cowrie"，并且我们不想设置一个全局可写的共享文件夹（以便用户可以写入日志），因此这次我们将使用 Docker 卷功能。按如下方式设置 Docker 卷：

```
root@kali:~/docker-cowrie# docker volume create cowrie
```

现在，确认卷的创建并检查其位置（稍后将使用）：

```
root@kali:~/docker-cowrie# docker volume inspect cowrie
[
 {
 "Driver": "local",
 "Labels": {},
 "Mountpoint": "/var/lib/docker/volumes/cowrie/_data",
 "Name": "cowrie",
 "Options": {},
 "Scope": "local"
 }
]
```

构建 Docker 镜像并运行它：

```
root@kali:~/docker-cowrie# ./.build.sh
root@kali:~/docker-cowrie# docker run -it -p 2222:2222 -p 2223:2223 -v etc:/cowrie/cowrie-git/etc -v cowrie:/cowrie/cowrie-git/log cowrie
b4de1484e3c86c2c9b0649920765785d3702530b51c8380cf10585911747c94f
```

如您所见，./run.sh 脚本在端口 2222（SSH）和 2223（Telnet）上运行蜜罐。您可以选择在正常端口 22 和 23 上运行它们，但您需要移除那里运行的任何实际服务。例如，要将 SSH 更改为其他端口，请编辑 /etc/ssh/sshd_config，更改端口设置，并发出以下命令以重启服务：

```
# service ssh restart
```

从另一个 Linux 或 Mac shell 中与蜜罐交互。您可以使用 root 以及除 root 或 123456 之外的任何密码登录：

```
$ ssh -p 2222 root@192.168.80.231
The authenticity of host '[192.168.80.231]:2222 ([192.168.80.231]:2222)' can't be established.
RSA key fingerprint is
SHA256:/rjInNCAgF5SFRbyMxppF0gVniQGX7nN6rTp6x1hNm4.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '[192.168.80.231]:2222' (RSA) to the list of known hosts.
Password:

The programs included with the Debian GNU/Linux system are free software; the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

root@svr04:~# ls
root@svr04:~# pwd
/root
root@svr04:~# id
uid=0(root) gid=0(root) groups=0(root)
root@svr04:~# wget www.google.com
--2017-08-19 00:53:19--  http://www.google.com
Connecting to www.google.com:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html; charset=ISO-8859-1]
Saving to: ‘/root/index.html’

100%[===============================>] 0           --
eta 0s

2017-08-19 00:53:20 (9 KB/s) - ‘/root/index.html’ saved [10457/0]

root@svr04:~# cat index.html
cat: /root/index.html: No such file or directory
root@svr04:~# ls -l
-rw-r--r-- 1 root root 0 2017-08-19 00:53 index.html
root@svr04:~#
```

请注意，系统似乎只下载了一个文件（实际上文件并不存在，文件大小为零）。在 Docker 实例上按 ctrl-c 停止容器。

现在，Cowrie 的一个巧妙之处在于能够按照黑客的时间序列重放攻击。使用前述卷位置，下载 Cowrie playlog 脚本并针对 tty 日志运行它：

```
root@kali:~/docker-cowrie# wget https://github.com/micheloosterhof/cowrie/raw/master/bin/playlog
--2017-08-18 23:10:24--
...<truncated for brevity>...
(raw.githubusercontent.com) |151.101.56.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3853 (3.8K) [text/plain]
Saving to: 'playlog'

playlog
100%[================================================================================================================>] 3.76K --.-KB/s    in 0s
==============================================================================================>]  3.76K --.-KB/s    in 0s

2017-08-18 23:10:24 (37.8 MB/s) - 'playlog' saved [3853/3853]
```

```
root@kali:~/docker-cowrie# chmod 755 playlog
root@kali:~/docker-cowrie# ./playlog /var/lib/docker/volumes/cowrie/_data/tty/*
```

Debian GNU/Linux 系统中包含的程序是自由软件；每个程序的确切发行条款在 /usr/share/doc/*/copyright 中的单独文件中说明。

Debian GNU/Linux 在适用法律允许的范围内不提供任何担保。

```
root@svr04:~# ls
root@svr04:~# id
uid=0(root) gid=0(root) groups=0(root)
root@svr04:~# pwd
/root
root@svr04:~# exit
root@kali:~/docker-cowrie#
```

这太酷了：我们可以实时查看自动化机器人输入或运行的内容。playlog 脚本还带有减慢或加快播放速度的选项。

## 实验 21-4：T-Pot

在本实验中，我们将汇总所有内容并下载安装 T-Pot 蜜罐，它是对多种其他蜜罐的自动化安装，包括我们在之前实验中使用的那些。此外，T-Pot 包含一个基于 Elasticsearch、Logstash 和 Kibana（ELK）堆栈的用户界面。18 本实验中测试的 T-Pot 版本可从本书网站下载。最新版本可从 T-Pot GitHub 下载（请参阅“进一步阅读”部分）。

T-Pot 蜜罐的最低系统要求是标准蜜罐的 4GB 内存和 64GB 硬盘空间（它可能在更少的资源下运行，但这些是公布的
