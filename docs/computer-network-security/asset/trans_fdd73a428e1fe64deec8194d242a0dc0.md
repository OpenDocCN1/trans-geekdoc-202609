

## 6.5. 在所有 ASA 接口上启用此安全策略。

```
ASA1(config)#service-policy PMAP-IN-TO-OUT global
```

## 7. 测试防火墙配置。

- 确保可以从 PC1 向 PC2 发送 ping 请求。
- 确保无法从 Server1 向 PC1 发送 ping 请求。
- 确保可以从 PC1 访问 Server1 的 http 服务。
- 确保无法从 PC1 访问 Server1 的 ftp 服务。

## 练习 15

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_219_0.png)

要查看此图的彩色版本，请参见 www.iste.co.uk/sadiqui/computer.zip

## 寻址表

| Device | Interface | IP address | Subnet mask | Gateway |
|---|---|---|---|---|
| ASA1 | E0/0 (VLAN2) | 212.212.1.1 | /30 | - |
| ASA1 | E0/1 (VLAN1) | 192.168.1.1 | /24 | - |
| ASA1 | E0/2 (DMZ) | 192.168.10.1 | /24 | - |
| R1 | F0/0 | 212.212.1.2 | /30 | - |
| R1 | F0/1 | 192.168.2.1 | /24 | - |
| PC1 | NIC | 自动 | | |
| PC2 | NIC | 192.168.2.2 | /24 | 192.168.2.1 |
| Server0 | NIC | 192.168.2.3 | /24 | 192.168.2.1 |
| Server_http | NIC | 192.168.10.2 | /24 | 192.168.10.1 |
| Server_ftp | NIC | 192.168.10.3 | /24 | 192.168.10.1 |

## 目标

- 使用 CLI 配置 ASA 5505 防火墙。

## 所需软件

- Packet Tracer。

## 部分 A：建立基本设备配置

### 1. 配置基本设备设置。

### 1.1. 按拓扑图配置主机名。

### 1.2. 根据寻址表将 IP 地址应用于设备接口。

### 2. 创建指向公司内部网络的静态路由。

```
R1(config)#ip route 192.168.1.0 255.255.255.0 212.212.1.1
R1(config)#ip route 192.168.10.0 255.255.255.0 212.212.1.1
```

## 部分 B：使用 CLI 配置 ASA 5505 防火墙

### 1. 配置 ASA 设备的基本设置。

### 1.1. 配置主机名。

```
ciscoasa(config)#hostname ASA1
ASA1(config)#
```

### 1.2. 设置系统日期。

```
ASA1(config)#clock set 14:25:00 May 12 2018
```

### 1.3. 配置特权模式密码。

```
ASA1(config)#enable password 1234
```

### 1.4. 配置 Telnet 连接密码。

```
ASA1(config)#passwd Cisco123
```

### 2. 从内部网络配置对 ASA 的 Telnet 和 SSH 访问。

### 2.1. 从内部网络配置 Telnet 访问。

```
ASA1(config)#telnet 192.168.1.0 255.255.255.0 inside
```

```
ASA1(config)#telnet timeout 10
```

### 2.2. 配置对 ASA 的远程 SSH 访问。

```
ASA1(config)#crypto key generate rsa modulus 1024
```

警告：已定义名为 <Default-RSA-Key> 的 RSA 密钥对。
您确实要替换它们吗？[yes/no]: y
密钥对生成过程已开始，请稍候。

```
ASA1(config)# ssh 192.168.1.0 255.255.255.0 inside
```

```
ASA1(config)# ssh timeout 10
```

### 3. 配置 ASA 设备的接口。

### 3.1. 为内部网络配置 VLAN 1 逻辑接口，并将安全级别设置为 100。

```
ASA1(config)# interface vlan 1
ASA1(config-if)# nameif inside
ASA1(config-if)# ip address 192.168.1.1 255.255.255.0
ASA1(config-if)# security-level 100
```

### 3.2. 为外部网络配置 VLAN 2 逻辑接口，并将安全级别设置为 0。

```
ASA1(config)# interface vlan 2
ASA1(config-if)# nameif outside
ASA1(config-if)# ip address 212.212.1.1 255.255.255.252
ASA1(config-if)# security-level 0
```

### 3.3. 为 DMZ 网络配置 VLAN 3 逻辑接口。

```
ASA1(config)# interface vlan 3
ASA1(config-if)# nameif DMZ
ERROR: This license does not allow configuring more than 2 interfaces with nameif and without a "no forward" command on this interface or on 1 interface(s) with nameif already configured.
```

### 3.4. 解释显示此错误消息的原因。

### 3.5. 阻止内部网络 (vlan1) 与 DMZ (vlan3) 之间的任何流量。

```
ASA1(config-if)#no forward interface vlan 1
ASA1(config-if)#nameif DMZ
ASA1(config-if)# ip address 192.168.10.1 255.255.255.0
ASA1(config-if)# security-level 50
```

### 3.6. 将 ASA 端口分配给连接的 VLAN。

```
ASA1(config)# interface e0/1
ASA1(config-if)# switchport access vlan 1
ASA1(config-if)# no shutdown
ASA1(config-if)# interface e0/0
ASA1(config-if)# switchport access vlan 2
ASA1(config-if)# no shutdown
ASA1(config-if)# interface e0/2
ASA1(config-if)# switchport access vlan 3
ASA1(config-if)# no shutdown
```

### 3.7. 使用 sh interface ip brief、sh ip address 和 sh switch vlan 命令检查配置和端口分配。

### 4. 在 ASA 上配置 DHCP 服务。

### 4.1. 为公司内部网络配置 DHCP 服务。

```
ASA1(config)#dhcpd address 192.168.1.5-192.168.1.100 inside
Warning, DHCP pool range is limited to 32 addresses, set address range as: 192.168.1.5-192.168.1.36
ASA1(config)# dhcpd dns 192.168.1.1
```

### 4.2. 在内部网络上启用 DHCP 服务。

```
ASA1(config)# dhcpd enable inside
```

### 4.3. 检查 PC1 是否已接收到有效的 IP 地址。

注意：在内部网络上，DHCP 服务默认在 ASA 服务中启用。

### 5. 为 ASA 配置默认静态路由。

```
ASA1(config)#route outside 0.0.0.0 0.0.0.0 212.212.1.2
```

### 6. 修改应用于 ASA 的默认安全策略。

### 6.1. 创建 Class-Map 以识别授权流量。

```
ASA1(config)#class-map CMAP-IN-TO-OUT
```

### 6.2. 显示 "match" 命令的可用选项。

```
ASA1(config-cmap)#match ?
```

### 6.3. 选择默认流量。

```
ASA1(config-cmap)#match default-inspection-traffic
```

```
ASA1(config-cmap)#exit
```

### 6.4. 创建 Policy-Map 以应用访问规则。

```
ASA1(config)#policy-map PMAP-IN-TO-OUT
ASA1(config-pmap)#class CMAP-IN-TO-OUT
ASA1(config-pmap-c)#inspect icmp
ASA1(config-pmap-c)#inspect ftp
ASA1(config-pmap-c)#inspect http
ASA1(config-pmap-c)#exit
```

### 6.5. 在所有 ASA 接口上启用此安全策略。

```
ASA1(config)#service-policy PMAP-IN-TO-OUT global
```

### 7. 在 ASA 上配置 NAT 服务。

### 7.1. 配置 PAT 服务以允许内部网络访问 Internet。

```
ASA1(config)# object network inside-internet
ASA1(config-network-object)# subnet 192.168.1.0 255.255.255.0
ASA1(config-network-object)# nat (inside,outside) dynamic interface
ASA1(config-network-object)# end
```

### 7.2. 配置静态 NAT 服务以允许从 Internet 访问 DMZ 区域中的服务器。

```
ASA1(config)# object network dmz-server-http
ASA1(config)# host 192.168.10.2
ASA1(config)# nat (dmz,outside) static 212.212.1.10
ASA1(config)# object network dmz-server-ftp
ASA1(config)# host 192.168.10.3
ASA1(config)# nat (dmz,outside) static 212.212.1.11
```

### 8. 配置 ACL 以定义授权访问。

### 8.1. 创建 ACL 以授权访问 DMZ 服务器。

```
ASA1(config)# access-list outside-dmz extended permit ip any host 192.168.10.2
ASA1(config)# access-list outside-dmz extended permit tcp any host 192.168.10.2 eq www
ASA1(config)# access-list outside-dmz extended permit ip any host 192.168.10.3
ASA1(config)# access-list outside-dmz extended permit tcp any host 192.168.10.3 eq ftp
```

### 8.2. 在外部接口上激活 ACL

```
ASA1(config)# access-group outside-dmz in interface outside
```

### 9. 测试防火墙配置。

### 9.1. 使用 show running-config 命令检查 ASA 防火墙配置。

### 9.2. 测试以下要素：

- 确保可以从 PC1 访问 Server0 的 http 服务；
- 确保可以使用 IP 地址 212.212.1.10 从 PC2 访问 Server_http 的 http 服务；
- 确保可以使用 IP 地址 212.212.1.11 从 PC2 访问 Server_ftp 的 FTP 服务。

### 9.3. 显示已执行的 NAT 转换。

```
ASA1#sh xlate
```

## 10.3. 使用图形工具配置 Cisco 元素

### 10.3.1. CCP 概述

Cisco Configuration Professional (CCP) 是一款图形工具，可在不使用 Cisco IOS CLI 命令的情况下，便于配置、监控和故障排除 Cisco 路由器。

CCP 有两个版本：

- CCP：这是一个完整版本，用于通过安装在主机上的应用程序来组织和管理多个路由器；
- CCP Express：这是 CCP 的轻量版本，可在路由器的闪存中使用。它允许对设备进行基本配置。

### 10.3.2. ASDM 概述

Cisco Adaptive Security Device Manager (ASDM) 是一款 Java 图形工具，允许配置、监控和故障排除 Cisco ASA 系统。

### 10.3.3. 使用 CCP 和 ASDM

完成练习 16。

