

## 对于指定为路由器和防火墙的树莓派：

- 1. 确保树莓派从 DHCP 服务器获取 IP 地址。此树莓派需要静态 IP（以便其他树莓派可以找到它来请求互联网流量），因此 DHCP 服务器需要此树莓派的 MAC 地址，以便每次分配相同的 IP 地址。要从控制台查看 IP 地址，请使用命令 `ip a`。

- 2. 要直接设置静态 IP（无需 DHCP 服务器），请按以下方式编辑文件 `/etc/dhcpcd.conf`：

```
interface eth0
static ip_address=192.168.1.1/24
static routers=192.168.1.254
static domain_name_servers=192.168.1.254
```

- 3. 通过编辑 `/etc/sysctl.conf` 启用 IP 转发。

- 4. 通过运行 `sudo raspi-config` 设置与学校 WiFi 网络（或提供外出互联网访问的其他网络）的 WiFi 连接。

- 5. 使用 nftables 配置 NAT 和防火墙。主配置文件将是 `/etc/nftables.conf`。基本模板配置可能类似于：

```
table inet filter {
    chain input {
        type filter hook input priority 0;
        # Accept any localhost traffic
        iif lo accept
        # Accept traffic already established
        ct state established,related accept
        # Enable HTTP and HTTPS
        tcp dport { http, https } accept
        # Drop everything else
        counter drop
    }
}
```

- 6. 要应用规则更改，请运行此命令：`sudo nft -f /etc/nftables.conf`。

- 7. 重启树莓派使设置生效，然后进行测试。

## 对于指定为无线接入点的树莓派：

- 1. 安装 hostapd 作为接入点主机软件。

- 2. 主配置文件将是 `/etc/hostapd/hostapd.conf`。建议设置包括：

```
interface=wlan0
bridge=br0
driver=nl80211
ssid=PiNet
hw_mode=g
channel=7
wmm_enabled=0
macaddr_acl=0
```

```
auth_alg=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=YourPasswordHere
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```

- 3. 通过编辑 `/etc/default/hostapd` 配置 hostapd 以使用该配置文件。

- 4. 通过更改 `/etc/dhcpcd.conf` 并指定 `denyinterfaces wlan0`，防止无线网卡被默认网络管理器管理。

## 对于指定为 DHCP 服务器的树莓派：

- 1. 安装 isc-dhcp-server 作为 DHCP 服务器。

- 2. 主配置文件将是 `/etc/dhcp/dhcpd.conf` 和 `/etc/default/isc-dhcp-server`。

- 3. `/etc/dhcp/dhcpd.conf` 的示例模板是：

```
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.10 192.168.1.100;
  option domain-name-servers 192.168.1.1;
  option routers 192.168.1.1;
  default-lease-time 600;
  max-lease-time 7200;
}
```

- 4. 确保 DHCP 服务器配置为开机启动。

- 5. 使用 `cat /var/log/syslog | grep dhcp` 检查日志中的错误。

## 对于指定为 Web 服务器的树莓派：

- 1. 确保树莓派从 DHCP 服务器获取 IP 地址。此树莓派需要静态 IP（以便其他树莓派可以找到它来请求网页），因此 DHCP 服务器需要此树莓派的 MAC 地址，以便每次分配相同的 IP 地址。要从控制台查看 IP 地址，请使用命令 `ip a`。

- 2. 安装 nginx 作为 Web 服务器软件，并设置为开机自动启动。

- 3. 在 `/var/www/html` 处创建网页。

- 4. nginx 的主配置文件位于 `/etc/nginx` 中。

- 5. 如果 nginx 无法启动，可以使用 `sudo nginx -t` 检查配置错误。

- 6. `/var/www/html/index.html` 的示例 HTML 文件可能类似于：

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Welcome to Pi Web Server</title>
</head>
<body>
  <h1>Hello, Raspberry Pi Network!</h1>
  <p>This is a simple web page served from the Raspberry Pi web server.</p>
</body>
</html>
```

## 对于指定为代理服务器的树莓派：

- 1. 确保树莓派从 DHCP 服务器获取 IP 地址。此树莓派需要静态 IP（以便其他树莓派可以找到它来请求网页），因此 DHCP 服务器需要此树莓派的 MAC 地址，以便每次分配相同的 IP 地址。要从控制台查看 IP 地址，请使用命令 `ip a`。

- 2. 安装 squid 代理服务器软件，并设置为开机自动启动。

- 3. 主配置文件位于 `/etc/squid/squid.conf`。

- 4. 除了充当 Web 缓存外，由于所有流量都通过代理，它还可用作内容过滤器，例如，您可以阻止对给定 URL 的请求。这与防火墙方法相似，但功能不同。请调查如何使用 squid 阻止某些网站。

## 对于指定为 DNS 服务器的树莓派：

- 1. 确保树莓派从 DHCP 服务器获取 IP 地址。此树莓派需要静态 IP（以便其他树莓派可以找到它来请求网页），因此 DHCP 服务器需要此树莓派的 MAC 地址，以便每次分配相同的 IP 地址。要从控制台查看 IP 地址，请使用命令 `ip a`。

- 2. 当 DNS 服务器配置完成后，需要更新 DHCP 服务器，以便客户端知道要查询此计算机进行 DNS 解析。

- 3. 安装 bind9 作为 DNS 服务器软件，并确保其设置为开机启动。

- 4. 主配置文件将在文件夹 `/etc/bind` 中。

- 5. 要检查配置错误，请转到 `sudo named-checkconf` 和 `sudo named-checkzone myhome.local /etc/bind/zones/db.myhome.local`。

- 6. 用于创建自己的 DNS 域（将在内部网络上工作）的示例 ZONE 文件 `/etc/bind/db.myhome.local` 可能类似于：

```
$TTL 604800
@ IN SOA ns1.myhome.local. admin.myhome.local. (
3 ; Serial
604800 ; Refresh
86400 ; Retry
2419200 ; Expire
604800 ) ; Negative Cache TTL
;
@ IN NS ns1.myhome.local.
ns1 IN A 192.168.1.1
@ IN A 192.168.1.1
www IN A 192.168.1.2
```

## ATL 对齐链接

- **调研技能：**
  - 查找和选择合适的软件和硬件资源。
  - 理解文档，为特定角色配置每个树莓派。
  - 比较解决方案和不同方法或选项，以确定什么最适合项目要求。

- **思维技能：**
  - 解决设置新网络时出现的众多挑战，例如 IP 地址冲突、防火墙规则以及确保所有设备可以有效通信。
  - 批判性思维，以评估每个网络组件的有效性并排除故障。
  - 决策网络设计。

- **社交技能：**
  - 协作，在小组中共同分工、分享发现并相互支持。
  - 冲突解决，针对如何配置网络或解决问题的不同意见。
  - 责任分担，并依赖他人的贡献。

- **沟通技能：**
  - 技术写作，记录网络设置和配置步骤。
  - 口头沟通，向同伴或老师解释 DNS 或 DHCP 等复杂概念。

- **自我管理技能：**
  - 规划和组织，管理大型累积任务。
  - 适应性，应对意外问题。
  - 自我激励和主动性，超越基本设置，例如实施额外的网络服务或安全措施。

## 考试练习题

### 1 小型企业网络搭建

一家小型企业最近扩张，需要更新其网络基础设施以支持更多员工，并提供对资源的安全、高效访问。

- a. 识别一项可将办公室内多台计算机连接起来创建局域网（LAN）的网络硬件。[1]
- b. 该企业已为其网络选择星型拓扑。描述在小型企业环境中使用星型拓扑的一个优点。[2]
- c. 该公司在其内部网站上同时使用 HTTP 和 HTTPS 协议。描述 HTTP 和 HTTPS 之间的一个关键区别。[2]
- d. 在 TCP/IP 模型的上下文中，描述传输层的功能。[3]
- e. 网络架构同时包含客户端-服务器和点对点设置。就资源管理而言，比较这两种网络架构。[3]
- f. 该企业计划使用 IPv6。识别在不断发展的企业中使用 IPv6 相对于 IPv4 的一个优点。[1]
- g. 该企业正在决定使用光纤电缆还是无线传输来连接不同部门。讨论应考虑的两个因素。[2]
- h. 描述网络中的路由器如何使用动态路由来管理数据流量。[3]
- i. 该公司担心网络安全。描述一种常见的网络漏洞及其相应的对策。[3]
- j. 数据加密对该公司的运营至关重要。在数据安全的背景下，描述对称加密和非对称加密之间的区别。[3]
- k. 概述数字证书如何有助于网络安全。[2]

### 2 大学校园网络

一所大学校园网络需要在动态、高需求的环境中支持数千名用户。

- a. 说出连接分布在广阔区域内校园建筑所必需的一种网络设备。[1]
- b. 该大学使用混合网络拓扑。描述在大学校园环境中使用混合拓扑的一个好处。[2]
- c. DNS 服务器在大学网络中至关重要。描述 DNS 在网络操作中的作用。[2]
- d. 描述 TCP/IP 模型的互联层如何促进校园内不同建筑之间的连接。[3]
- e. 校园同时使用 IPv4 和 IPv6 寻址。就地址可用性概述这两种 IP 寻址类型。[2]
- f. 评估在学术建筑内进行数据传输时使用双绞线电缆与光纤电缆的情况。考虑成本和速度等因素。[3]
- g. 解释分组交换如何在繁忙的大学校园网络中实现高效的数据流量管理。[3]
- h. 描述应实施的一项网络安全措施，以保护学生成绩和其他敏感数据不被学生本人修改，同时仍允许他们访问校园网络。[2]
- i. 大学使用数字签名进行文档验证。描述数字签名如何增强安全性。[3]
- j. 概述证书颁发机构在大学网络安全框架中的应用。[2]

