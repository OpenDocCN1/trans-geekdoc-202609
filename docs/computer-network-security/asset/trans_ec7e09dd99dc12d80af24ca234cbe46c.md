
## Part B: 保护密码

在R1上

- 1. 设置最小密码长度为8个字符。
- 2. 为特权模式设置密码“Ci$c0ena”。
- 3. 配置控制台、辅助端口和虚拟访问线路。
  - 3.1. 将“Ci$c0con”设置为控制台端口密码，并将非活动间隔设置为5分钟。
  - 3.2. 将“Ci$c0vty”设置为VTY线路的密码，并将非活动间隔设置为2分钟。
  - 3.3. 禁用辅助端口。
- 4. 加密所有密码。

## Part C: 使用Cisco IOS配置站点到站点IPsec VPN

加密Server1和Server2之间的流量。

### 1. 在R1和R2上创建扩展ACL以识别“有趣流量”。

```
R1(config)# access-list 101 permit ip 192.168.0.0 0.0.255.255 192.168.2.0 0.0.255.255
R2(config)# access-list 101 permit ip 192.168.2.0 0.0.255.255 192.168.0.0 0.0.255.255
```

### 2. 创建IKE策略并配置第1阶段所需的设置。

### 2.1. IKE协议第1阶段的作用是什么？

### 2.2. 在R1上配置第1阶段所需的设置。

```
R1(config)# crypto isakmp policy 10
R1(config-isakmp)# authentication pre-share
R1(config-isakmp)# encryption aes 256
R1(config-isakmp)# hash sha
R1(config-isakmp)# group 5
R1(config-isakmp)# lifetime 3600
R1(config-isakmp)# end
```

### 2.3. 根据上述命令，填写以下表格：

| IKE第1阶段设置 |
|---|
| ISAKMP策略ID | |
| 身份验证方法 | |
| 加密算法 | |
| 加密密钥使用的位数 | |
| 哈希算法 | |
| Diffie-Hellman组 | |
| 安全关联的生存期 | |

### 2.4. 验证IKE策略的设置。

```
R1# show crypto isakmp policy
Global IKE policy
Protection suite of priority 10
encryption algorithm: AES - Advanced Encryption Standard
(256 bit keys).
Hash algorithm: Secure Hash Standard
Authentication method: Pre-Shared Key
Diffie-Hellman group: #5 (1536 bit)
Lifetime: 3600 seconds, no volume limit
```

### 2.5. 在R2上重复上述相同的配置。

### 3. 指定PSK共享密钥并识别VPN隧道另一端的IP地址。

在两台路由器上配置预共享密钥。
```
R1(config)# crypto isakmp key Tri123 address 192.168.10.2
R2(config)# crypto isakmp key Tri123 address 192.168.10.1
```

### 4. 创建第2阶段所需的IPsec策略。

### 4.1. IKE协议第2阶段的作用是什么？

### 4.2. 在R1上创建第2阶段所需的IPsec策略。

```
R1(config)# crypto ipsec transform-set 10 esp-aes 256 esp-sha-hmac
```

### 4.3. 根据上述命令，填写以下表格：

| IKE第2阶段设置 | |
|---|---|
| 转换集策略的标识符。 | |
| 使用的基本IPsec协议。 | |
| 加密算法 | |
| 加密密钥使用的位数。 | |
| 哈希算法 | |

注意.— 可以修改IPsec关联的生存期，使其不同于ISAKMP关联的生存期。可以使用以下命令：

```
R1(config)# crypto ipsec security-association lifetime seconds 1800
```

### 4.4. 验证转换集策略的设置。

```
R1# show crypto ipsec transform-set
Transform set 10: { esp-256-aes esp-sha-hmac }
will negotiate = { Tunnel, },
```

### 4.5. 在R2上重复相同的配置。

### 5. 创建加密映射并配置加密映射参数。

### 5.1. 在R1上创建加密映射。

```
R1(config)# crypto map carte_crypto1 10 ipsec-isakmp
R1(config-crypto-map)# match address 101
R1(config-crypto-map)# set peer 192.168.10.2
R1(config-crypto-map)# set transform-set 10
R1(config-crypto-map)# exit
```

### 5.2. 根据上述命令，填写以下表格：

| 加密映射的设置 |
| :--- |
| 加密映射的名称 | |
| ISAKMP策略ID | |
| 有趣流量的ACL标识符 | |
| VPN隧道另一端的IP地址 | |
| 转换集策略的标识符 | |

### 5.3. 在R2上重复上述相同的配置。

### 6. 将加密映射应用于R1和R2的相应接口。

```
R1(config)# interface S0/0
R1(config-if)# crypto map carte_crypto1
R2(config)# interface S0/0
R2(config-if)# crypto map carte_crypto2
```

### 7. 验证VPN隧道设置。

### 7.1. 验证加密映射设置。

```
R1# show crypto map
Crypto Map carte_crypto1 10 ipsec-isakmp
Peer = 192.168.10.2
Extended IP access list 101
access-list 101 permit ip 192.168.0.0 0.0.255.255 192.168.2.0 0.0.255.255
Current peer: 192.168.10.2
Security association lifetime: 4608000 kilobytes/3600 seconds
PFS (Y/N): N
Transform sets={
10,
}
Interfaces using crypto map carte_crypto1:
Serial0/0
```

### 7.2. 显示ISAKMP和IPsec安全关联。

```
R1# show crypto isakmp sa
IPv4 Crypto ISAKMP SA
dst   src   state   conn-id slot status

IPv6 Crypto ISAKMP SA
R1# show crypto ipsec sa
interface: Serial0/0/0
Crypto map tag: carte_crypto1, local addr 192.168.10.1
protected vrf: (none)
local ident (addr/mask/prot/port): (192.168.0.0/255.255.255.0/0/0)
remote ident (addr/mask/prot/port): (192.168.2.0/255.255.255.0/0/0)
current_peer 192.168.10.2 port 500
PERMIT, flags={origin_is_acl ,}
...
```

### 7.3. 在Server2、PC1和Server1之间发送ping，并再次显示ISAKMP和IPsec安全关联。

```
Router# show crypto isakmp sa
IPv4 Crypto ISAKMP SA
dst   src   state   conn-id slot    status
192.168.10.2 192.168.10.1 QM_IDLE   1033 0 ACTIVE
```

### 7.4. 将两台路由器之间的串行链路替换为FastEthernet（或以太网）链路，并添加Sniffer以捕获两台路由器之间交换的帧。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_202_0.png)

注意.— FastEthernet接口的IP地址必须与串行接口的IP地址相同。

### 7.5. 将加密映射应用于R1和R2的相应接口。

```
R1(config)# interface F0/2
R1(config-if)# crypto map carte_crypto1
R2(config)# interface F0/1
R2(config-if)# crypto map carte_crypto2
```

### 7.6. 在Server 2和Server 1之间ping，并解释Sniffer捕获的IPsec帧。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_203_0.png)

### 7.7. 为什么只为Server2和Server1之间的流量创建了安全关联，而没有为PC1和Server1之间的流量创建安全关联？

注意.— 如果在保存配置后重启其中一台路由器，也可以捕获ISAKMP帧。

## 学习高级防火墙

本章将重点介绍以下主题：

- 思科ASA防火墙：
  - ASA型号，
  - ASA设备的使用模式，
  - ASA 5505概述；
- 使用CLI配置ASA：
  - ASA许可证类型，
  - 配置接口，
  - 配置DHCP服务，
  - 配置ACL，
  - 配置NAT服务，
  - 配置AAA；
- 使用CCP和ASDM图形工具配置思科设备；
- TMG 2010防火墙。

### 10.1. 思科ASA防火墙

### 10.1.1. 简介

思科ASA（自适应安全设备）是一种结合防火墙、防病毒、入侵防御系统（IPS）和VPN功能的安全设备。

它因此提供了广泛的技术和解决方案，用于有效的网络安全。

### 10.1.2. ASA型号

ASA有不同型号。所有型号都提供高级防火墙和VPN功能。型号之间最大的区别在于每个型号可以管理的最大流量以及接口的数量和类型。ASA型号根据组织的要求选择，例如流量、每秒最大连接数和公司预算。

ASA设备还支持虚拟化环境。这些环境运行与物理设备相同的软件，以提供相同的安全功能。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_205_0.png)

图10.1 不同的ASA型号¹

注意.— 本章将限于研究ASA 5505型号和防火墙功能。

### 10.1.3. ASA设备的使用模式

- 路由器模式：
- 这是常规的部署模式；
