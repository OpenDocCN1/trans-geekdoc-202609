

server`172.20.0.5`

victim`172.20.0.6`

attacker`172.20.0.7` 对于本实验，我们的 IP 地址是静态配置的，且攻击者已知这些地址。还假设攻击者位于本地网络中。最后，victim 被错误配置为忽略主机密钥的变化。这并不完全不合理，因为许多用户在提示时都会忽略警告并清空 known\_hosts 文件。首先下载 [scapy.zip](https://github.com/rxt1077/it230/raw/main/labs/scapy.zip) 文件，该文件包含我们将使用的 Docker Compose 配置。将其解压到你有写权限的目录中。本实验需要我们使用三个终端窗口/选项卡：一个用于 `docker-compose up` 命令，它将显示后台运行的所有内容的输出；一个用于 victim，它将显示与 server 的 SSH 会话；还有一个用于 attacker，我们将使用它来发起攻击。

![](images/scapy.svg "fig:")

打开三个终端，并在每个终端中 `cd` 进入你解压实验 zip 文件的目录。你所在的目录中应该有一个 `docker-compose.yml` 文件以及 `server`、`victim` 和 `attacker` 目录。

在第一个终端中运行 `docker-compose up` 命令来构建镜像并运行容器：

Listing 1. docker-compose up

```
PS C:\Users\rxt1077\it230\labs\scapy> docker-compose up
Creating network "scapy_testnet" with the default driver
Creating scapy_server_1 ... done
Creating scapy_victim_1 ... done
Creating scapy_attacker_1 ... done
Attaching to scapy_victim_1, scapy_server_1, scapy_attacker_1
server_1 | > Starting SSHD
server_1 | >> Generating new host keys
scapy_victim_1 exited with code 0
attacker_1 | INFO 2021/10/07 13:56:45 No host keys configured, using keys at "/root/.local/share/sshesame"
attacker_1 | INFO 2021/10/07 13:56:45 Host key "/root/.local/share/sshesame/host_rsa_key" not found, generating it
attacker_1 | INFO 2021/10/07 13:56:45 Host key "/root/.local/share/sshesame/host_ecdsa_key" not found, generating it
attacker_1 | INFO 2021/10/07 13:56:45 Host key "/root/.local/share/sshesame/host_ed25519_key" not found, generating it
attacker_1 | INFO 2021/10/07 13:56:45 Listening on [::]:22
server_1 | ssh-keygen: generating new host keys: RSA DSA ECDSA ED25519
server_1 | >>> Fingerprints for dsa host key
server_1 | 1024 MD5:a5:e6:e9:38:d2:2e:88:fd:f0:aa:a8:05:07:35:5f:18 root@a010fe3c2f3c (DSA)
server_1 | 1024 SHA256:NM7DONpt1doZp4e6WV+6WVVr+KUrh9luUSRcAhnzdyw root@a010fe3c2f3c (DSA)
server_1 | 1024 SHA512:LHfFdSk1XiAKQArH0CW+RkaKv5GgovPCH7UIQ+P4T2LbgGpCBP5aGA1V3oriYbTZWuS9TlUgDbEfTBq19AV/cA root@a010fe3c2f3c (DSA)
server_1 | >>> Fingerprints for rsa host key
server_1 | 3072 MD5:74:44:b6:a2:74:b9:7e:1b:ba:3d:27:b8:19:3a:48:df root@a010fe3c2f3c (RSA)
server_1 | 3072 SHA256:mubm9mLNrdNDk5fyj0dghDBIbbwcVKXo23Qdv61/S/c root@a010fe3c2f3c (RSA)
server_1 | 3072 SHA512:JFQhS6trY7sNqRSwZ+t0uyBb5ddNh9qSLtBrMaa5G7xWzKHpxCuKBSDbvLk4W9JKeQftTU4293UDV9vqCcf/6w root@a010fe3c2f3c (RSA)
server_1 | >>> Fingerprints for ecdsa host key
server_1 | 256 MD5:15:75:5f:9b:72:7c:f0:13:ea:0d:b4:47:b7:62:69:63 root@a010fe3c2f3c (ECDSA)
server_1 | 256 SHA256:4p/Afp/8C2tHn7AePdS7OHCgPxfBamdaLIUg4IJ7xx4 root@a010fe3c2f3c (ECDSA)
server_1 | 256 SHA512:NnbevqBXFkGQWIirdFsLPnX85q7q/1Y7E4i+BLHLqE3cg2aqkduBJsssyr9+G7bSvq7txvjl9SRmyRAzuDT7DQ root@a010fe3c2f3c (ECDSA)
server_1 | >>> Fingerprints for ed25519 host key
server_1 | 256 MD5:ad:00:61:26:4d:a0:07:be:6b:8e:91:bd:f0:65:e6:14 root@a010fe3c2f3c (ED25519)
server_1 | 256 SHA256:Vl7jQulDsONglP1xbSN+J8nSfCaIER40rHhgy7z/BYg root@a010fe3c2f3c (ED25519)
server_1 | 256 SHA512:WkmvOWe6oaZ/qE1ZiA0rZAjn9H+hCDxI8NHpsjRNCalK/CgVV9+VhkzHgRTKfKTqQeE0y/Zz2GaEJGv/sapCHg root@a010fe3c2f3c (ED25519)
server_1 | WARNING: No SSH authorized_keys found!
server_1 | >> Unlocking root account
server_1 | WARNING: password authentication enabled.
server_1 | WARNING: password authentication for root user enabled.
server_1 | >> Running: /etc/entrypoint.d/changepw.sh
server_1 | Running /usr/sbin/sshd -D -e -f /etc/ssh/sshd_config
server_1 | Server listening on 0.0.0.0 port 22.
server_1 | Server listening on :: port 22.
```

① 注意 attacker 在后台运行着一个伪造的 SSH 服务器
② 注意 server 在后台运行着一个合法的 SSH 服务器

在第二个终端中运行 `docker-compose run victim bash`，然后从提示符处使用密码 "password" SSH 连接到 server：

Listing 2. victim

```
PS C:\Users\rxt1077\it230\labs\scapy> docker-compose run victim bash
Creating scapy_victim_run ... done
bash-5.0# ssh server
Warning: Permanently added 'server,172.20.0.5' (ECDSA) to the list of known hosts.
root@server's password:
You are now logged into 'server' (presumably from 'victim') via SSH for this assignment. Leave this connection open while you experiment with scapy from 'attacker'.
bf9ebe42a108:~#
```

① 密码是 "password"。输入时不会在屏幕上显示。

在第三个终端中，我们首先执行（回顾此时 sshesame 已经在后台运行）在 attacker 上启动一个 BASH shell，并将其配置为不仅接受其自身 IP 地址的数据包，还接受 server 的 IP 地址的数据包。一旦流量被路由到我们这里，这将允许 attacker 也响应发往 172.20.0.5 的数据包。

Listing 3. attacker

```
PS C:\Users\rxt1077\it230\labs\scapy> docker-compose exec attacker bash
root@5195de3d330c:/# ip addr add 172.20.0.5 dev eth0
root@5195de3d330c:/# ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: tunl0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN group default qlen 1000
    link/ipip 0.0.0.0 brd 0.0.0.0
3: sit0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN group default qlen 1000
    link/sit 0.0.0.0 brd 0.0.0.0
347: eth0@if348: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default
    link/ether 02:42:ac:14:00:07 brd ff:ff:ff:ff:ff:ff
    link-netnsid 0
    inet 172.20.0.7/24 brd 172.20.0.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet 172.20.0.5/32 scope global eth0
       valid_lft forever preferred_lft forever
```

① 这是我们开始时的 IP
② 这是 attacker 认为自己拥有的附加 IP

现在 attacker 系统已配置完成，我们将交互式启动 `scapy`：

Listing 4. attacker

```
root@5195de3d330c:/# scapy
INFO: Can't import matplotlib. Won't be able to plot.
INFO: Can't import PyX. Won't be able to use psdump() or pdfdump().
INFO: No IPv6 support in kernel
INFO: Can't import python-cryptography v1.7+. Disabled WEP decryption/encryption. (Dot11)
INFO: Can't import python-cryptography v1.7+. Disabled IPsec encryption/authentication.
WARNING: IPython not available. Using standard Python shell instead.
AutoCompletion, History are disabled.
aSPY//YASa apyyyyCY//////////YCa | sY//////YSpcs scpCY//Pp | Welcome to Scapy
ayp ayyyyyyySCP//Pp syY//C | Version 2.4.5
AYAsAYYYYYYYY///Ps cY//S | pCCCCY//p cSSps y//Y | https://github.com/secdev/scapy
SPPPP///a pP///AC//Y | A//A cyP////C | Have fun!
p///Ac sC///a | P////YCpc A//A | To craft a packet, you have to be a scccccp///pSP///p p//Y | packet, and learn how to swim in sY/////////y caa S//P | the wires and in the waves.
cayCyayP//Ya pY/Ya | -- Jean-Claude Van Damme
sY/PsY////YCc aC//Yp | sc sccaCY//PCypaapyCP//YSs spCPY//////YPSps ccaacs
>>>
```

你会注意到 scapy 的提示符是 `>>>`, 就像 python 一样，因为它 *就是* python。由于我们在使用 python，让我们通过定义一些简单的变量来让生活更轻松：

Listing 5. attacker

