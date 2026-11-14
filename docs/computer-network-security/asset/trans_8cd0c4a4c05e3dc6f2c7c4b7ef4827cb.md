
![](img/6cc1cc8bbb23ba3014958aee841c4ff5_100_0.png)

## 图 5.1. 不同类型网络划分至独立区域

## 5.6.3. 应用于区域间流量的规则

路由流量时，会对 ZFW 应用以下规则：

- 必须先创建安全区域，然后才能为其分配接口；
- 一个接口可以分配给单个安全区域；
- 默认情况下，属于同一区域的接口之间允许流量；

必须预先配置安全策略，才能授权流量在两个区域之间传递。可采取三种操作：

- **放行**：允许流量从一个区域 transite 到另一个区域；
- **检查**：允许流量并检查返回流量；
- **丢弃**：删除流量；

除非明确禁止，否则任何指向路由器接口（“自身区域”）的流量均获授权。

## 5.6.4. 术语

ZFW 的访问策略需要三个基本组件：

- 类映射：允许根据某些条件识别流量；
- 策略映射：允许应用先前创建的“类映射”策略；
- 服务策略：允许定义应用先前创建的策略映射的位置。

## 5.6.5. 配置 ZFW

可按以下步骤依次配置 ZFW：

- 1) 创建区域；
- 2) 创建类映射以识别授权流量；
- 3) 创建策略映射以应用类映射；
- 4) 定义区域对；
- 5) 将策略映射应用到区域对；
- 6) 将接口分配给区域。

## 5.7. 创建区域

| Command | Description |
|---|---|
| Router(config)# zone security zone-name | 创建安全区域。 |

## 5.8. 创建类映射

| Command | Description |
|---|---|
| Router(config)# class-map type inspect { match-any | match-all } class-map-name | 创建类映射并定义这些选项。match-any：数据包必须满足其中一条匹配条件。match-all：数据包必须满足所有匹配条件。 |
| Router(config-cmap)# match protocol protocol | 根据协议定义匹配条件。 |

## 5.9. 创建应用类映射的策略映射

| Command | Description |
|---|---|
| Router(config)# policy-map type inspect policy-map-name | 创建策略映射并定义这些选项。 |
| Router(config-pmap)# class type inspect class-map-name | 将其与一个（或多个）类映射关联。 |
| Router(config-pmap-c)# {drop | inspect | pass } | 定义要执行的操作。 |

## 5.10. 定义区域对

| Command | Description |
|---|---|
| Router(config)# zone-pair security zone-pair-name source { source-zonename | self | default } destination { destination-zone-name | self | default } | 创建区域对，允许在两个区域之间应用单向“策略映射”。 |

## 5.11. 将策略映射应用到区域对

| Command | Description |
|---|---|
| Router(config-sec-zone-pair)# service-policy type inspect policymap-name | 将策略映射策略应用到区域对。 |

## 5.12. 将接口分配给区域

| Command | Description |
|---|---|
| Router(config)# interface type number<br>Router(config-if)# zone-member security zone-name | 将接口与特定安全区域关联。 |

## 5.13. 应用练习

练习 6.

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_103_0.png)

有关此图的彩色版本，请参见 www.iste.co.uk/sadiqui/computer.zip

### 寻址表

| 设备 | 接口 | IP 地址 | 子网掩码 | 网关 |
|---|---|---|---|---|
| R1 | G0/0 | 192.168.0.1 | /24 | – |
| | S0/0 | 192.168.100.1 | /30 | – |
| R2 | G0/0 | 192.168.1.1 | /24 | – |
| | S0/0 | 192.168.100.2 | /30 | – |
| | S0/1 | 192.168.200.1 | /30 | – |
| R3 | G0/0 | 192.168.2.1 | /24 | – |
| | S0/0 | 192.168.200.2 | /30 | – |
| PC1 | NIC | 192.168.0.2 | /25 | 192.168.0.1 |
| PC2 | NIC | 192.168.1.2 | /26 | 192.168.1.1 |
| PC3 | NIC | 192.168.2.4 | /24 | 192.168.2.1 |
| PC4 | NIC | 192.168.2.5 | /24 | 192.168.2.1 |
| ftp_server | NIC | 192.168.2.2 | /24 | 192.168.2.1 |
| http-server | NIC | 192.168.2.3 | /24 | 192.168.2.1 |

## 目标

- 保护密码；
- 配置 IPv4 ACL；
- 配置 IPv6 ACL。

## 要使用的软件

Packet Tracer.

## A 部分：建立基本设备配置。

### 1. 配置基本设备设置。

- 1.1. 按拓扑配置主机名。
- 1.2. 根据寻址表将 IP 地址应用到设备接口。
- 1.3. 将串行接口的时钟值设置为 128 000。

### 2. 使用 OSPF 协议配置路由。

- 2.1. 在两台路由器上启用 OSPF，进程 ID 使用值 1。
- 2.2. 将 RID 值设置为 R1 的 1.1.1.1、R2 的 2.2.2.2 和 R3 的 3.3.3.3。
- 2.3. 将所有网络添加到 OSPF 协议。
- 2.4. 测试所有网络元素之间的连通性。

## B 部分：保护密码

- 1. 设置最小密码长度为 8 个字符。
- 2. 为特权模式设置密码“Ci$c0ena”。
- 3. 配置控制台、辅助端口和虚拟访问线路。
- 3.1. 将“Ci$c0con”设置为控制台端口密码，并将非活动间隔设置为 5 分钟。
- 3.2. 将“Cis$c0vty”设置为 VTY 线路的密码，并将非活动间隔设置为 2 分钟。
- 3.3. 禁用辅助端口。
- 4. 加密所有密码；

```
R1(config)# service password-encryption
```

## C 部分：配置 IPv4 ACL

- 1. 审查编号扩展 ACL 的有效编号范围。
- 2. 在 R3 上，创建一个编号扩展 ACL，以授权来自 PC1 站对 http-server 的访问。为此，使用以下选项创建 ACL：
  - 扩展列表编号为 100
  - 要定义的操作为 permit；
  - 要使用的协议为 TCP；
  - 源为 IP 地址为 192.168.0.2 的主机（PC1）；
  - 目标为 IP 地址为 192.168.2.2 的主机（http-server）；
  - 要使用的端口为 80。

编写要使用的 ACL：

- 3. 向已创建的扩展 ACL 添加一条规则，以拒绝来自“站点 2”网络对 http-server 的访问。为此，按以下选项配置 ACL 100：
  - 要定义的操作为 deny；
  - 要使用的协议为 TCP；
  - 源为网络地址为 192.168.1.0 / 26 的网络（站点 2）；
  - 通配符掩码通过从网络掩码中减去掩码 255.255.255.255 获得：
  255.255.255.255 – 255.255.255.192 = 0.0.0.63
  - 目标为 IP 地址为 192.168.2.3 的主机（http-server）；
  - 要使用的端口为 80。

编写要使用的命令：

- 4. 向之前的 ACL 添加一条规则，允许与 http-server 的所有 IP 流量。为此，按以下选项配置 ACL 100：
  - 要定义的操作为 permit；
  - 要使用的协议为 IP；
  - 要使用的源为 any；
  - 目标为 IP 地址为 192.168.2.3 的主机（http-server）。

编写要使用的命令：

- 5. 向之前的 ACL 添加一条规则，允许拒绝 PC1 和 PC4 之间的 ICMP 流量。为此，按以下选项配置 ACL 100：
  - 要定义的操作为 permit；
  - 要使用的协议为 ICMP；
  - 要使用的源为 IP 地址为 192.168.0.2 的主机（PC1）；
  - 目标为 IP 地址为 192.168.2.4 的主机（PC4）。

编写要使用的命令：

- 6. 将访问控制列表 100 应用到 G0/0 接口。

编写要使用的命令：

注释。—— 通常，扩展 ACL 应放置在源附近。但是，由于 ACL 100 影响来自两个网络“站点 1”和“站点 2”的流量，最佳位置应为接口 G0/0 的输出方向。

- 7. 测试先前创建的 ACL。
  - 检查是否可以从 PC1 访问 http 服务。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_107_0.png)
  - 检查是否无法从 PC2 访问 http 服务。
  - 检查是否可以从 PC2 向 http-server 发送 ping 请求。
  - 检查是否无法从 PC1 向 PC3 发送 ping 请求。
  - 检查是否可以从 PC1 向 PC4 发送 ping 请求。

- 8. 删除创建的 ACL。

```
R3(config)# no access-list 100
```

- 9. 在 R3 上，创建并测试名为“ACL_HTTP”的扩展 ACL，以满足先前所述的安全要求。

- 9.1. 创建扩展 ACL。

```
R3(config)# ip access-list extended ACL_HTTP
R3(config-ext-nacl)#
```

- 9.2. 允许从 PC1 到 http-server 的 http 访问

```
R3(config-ext-nacl)# permit tcp host 192.168.0.2 host 192.168.2.3 eq www
```
