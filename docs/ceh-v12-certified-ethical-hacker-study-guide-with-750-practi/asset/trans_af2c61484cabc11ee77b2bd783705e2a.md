
正如我们在进行 DNS 劫持时所做的那样，`sslstrip` 需要我们在 `ARP` 劫持上就位。我们可以使用 `Ettercap` 来实现，方法与之前相同。我们需要像以前一样伪造 Internet 网关。我们在设置 `ARP` 劫持攻击时也需要监听远程连接。`sslstrip` 是 `Ettercap` 的一个插件，因此可以像启用 DNS 劫持插件一样启用该插件。这需要在 `Ettercap` 之前对其进行配置更改。`sslstrip` 需要知道所使用的防火墙命令，以便在防火墙上设置重定向。下面的行在 `/etc/ettercap/etter.conf` 文件中被注释掉了。如果你使用的是 `iptables`（这比 `ipchains` 更可能），则需要取消这些行的注释。

[`/etc/ettercap/etter.conf`]

```
# if you use iptables:
redir_command_on = "iptables -t nat -A PREROUTING -i %iface -p tcp --dport %port -j REDIRECT --to-port %rport"
redir_command_off = "iptables -t nat -D PREROUTING -i %iface -p tcp --dport %port -j REDIRECT --to-port %rport"
```

完成这些配置后，`sslstrip` 插件即可启用。它会执行 `iptables` 命令以启动重定向，从而让插件能够接收消息。下面是 `Ettercap` 内 `sslstrip` 开始运行的日志示例。

**在 `Ettercap` 中运行 `sslstrip`**

```
Host 192.168.86.1 added to TARGET1

ARP poisoning victims:

GROUP 1 : 192.168.86.1 18:D6:C7:7D:F4:8A

GROUP 2 : ANY (all the hosts in the list)

Activating sslstrip plugin…
SSLStrip plugin: bind 443 on 59273
SSLStrip Plugin version 1.1 is still under experimental mode. Please reports any issues to the development team.
DHCP: [192.168.86.1] ACK : 0.0.0.0 255.255.255.0 GW 192.168.86.1 DNS 192.168.86.1 "lan"
```

一旦 `iptables` 规则已就位，`sslstrip` 应该能够捕获所有 HTTPS 流量。不过，这前提是 HTTPS 连接使用的 SSL/TLS 版本易受 stripping 攻击影响；如果不是，则不会有任何流量。

### Spoofing Detection（欺骗检测）

网络运营商和安全专业人员需要能够检测欺骗攻击。一个优秀的欺骗攻击可能在用户层面不可见，这意味着必须在网络层面进行检测。这可能来自于使用网络入侵检测系统（IDS），但你仍需了解这些检测是如何工作的。首先，让我们从 ARP 欺骗入侵说起。正如你所见，ARP 欺骗依赖于攻击者发送大量 ARP 响应。用户看不到这些操作，但网络监控会显示大量的 gratuitous ARP 消息。这表明 ARP 欺骗正在发生，并提供攻击者的 MAC 地址。

仅凭二层地址（MAC 地址）并不能提供太多信息。大多数人无法仅凭 6 字节的 MAC 地址立即判断其所属系统。可以取前三个字节（OUI）进行查找，因为前三字节是组织唯一标识符。使用如 `wireshark.org` 所提供的 OUI 查找工具，可以得到网卡制造商的信息。例如，我的网络中某系统的 MAC 地址为 `70:4d:7b:6d:52:6a`，查询后发现制造商是 ASUSTek，因为网卡是由 ASUS 主板制造的。

MAC 地址本身并不足以定位，尤其是当网络中所有设备来自同一制造商时。你只知道制造商，而许多公司会从单一或少数制造商处采购全部或大部分计算机。此时你可能需要在网络中搜索该 MAC 地址。你的交换机始终维护 MAC 地址到端口号的映射。找到对应的交换机端口后，你可以确定该端口连接的是什么系统。如果端口连接的是非管理的端口或中间的交换机，则需要进一步追踪，最少可以沿着交换机端口或其连接的线缆进行追踪。

你可能需要在网络层（IP 地址欺骗）进行检测，尤其是在拒绝服务攻击（DoS）的情形下。这通常由路由器处理。如果路由器已配置逆向路径验证（reverse path verification），它可以通过在路由表中查找源地址来判断响应包应通过哪个接口发送。如果报文进入的接口与预期的出站接口不同，则有可能是欺骗包。

DNS 劫持检测相对困难，尤其是当攻击者使用其他方式捕获出站 DNS 请求时。若出站请求的 IP 地址与入站响应的 IP 地址一致，则可能安全；若不一致，则也可能安全——这听起来有点矛盾。DNS 的问题在于响应可能来自不同的地址，取决于 DNS 服务器的配置。更好的做法是使用本地 DNS 服务器，并将其配置为使用 TCP 而非 UDP。TCP 的三次握手能够更好地防止欺骗，或至少在防欺骗方面优于 UDP。你还可以确保本地 DNS 服务器启用 DNS 安全扩展（DNSSEC），通过对所通信服务器进行 cryptographic verification。

DHCP 星vation（DHCP starvation）攻击也可以被检测。如果突然出现来自意外 IP 地址的 DHCP 响应，这很可能是恶意活动。这可能是 DHCP 星vation 攻击的结果，也可能是攻击者在本地网络部署一个 DHCP 服务器，因为某些本地设备会充当 DHCP 代理，将请求转发到远程服务器。本地服务器响应更快，但如果大量的 `DHCPDISCOVER` 请求从未被接受，则可能是 DHCP 星vation 攻击的强烈迹象。

