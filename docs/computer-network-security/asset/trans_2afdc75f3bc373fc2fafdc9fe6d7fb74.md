

### 9.3. 禁止来自网络“site 2”到 http-server 的 HTTP 流量。

```
R3(config-ext-nacl)# deny tcp 192.168.1.0 0.0.0.63 host 192.168.2.3 eq www
```

### 9.4. 允许与 http-server 的所有 IP 流量。

```
R3(config-ext-nacl)#permit ip any host 192.168.2.3
```

### 9.5. 显示 ACL_HTTP ACL 规则。

```
R3#sh IP access-lists ACL_HTTP
```

### 9.6. 将 ACL_HTTP ACL 应用到 G0/0/0 接口。

```
R3(config-if)# ip access-group ACL_HTTP out
```

### 9.7. 测试 ACL_HTTP ACL 的效果。

### 10. 在 R3 上，创建一个名为“ACL_FTP”的扩展 ACL，以满足以下安全要求：

- 允许从 PC2 到 ftp_server 的 FTP 访问；
- 阻止来自“site 1”网络到 ftp_server_http 的 FTP 流量；
- 允许与 ftp_server 的所有 IP 流量。

### 10.1. 显示 ACL_FTP ACL 规则。

### 10.2. 将 ACL_FTP ACL 应用到 G0/0 接口。

### 10.3. 测试 ACL_FTP ACL 的效果。

```
PC2:\>ftp 192.168.2.3
Trying to connect... 192.168.2.3
Connected to 192.168.2.3
220- Welcome to PT Ftp server
Username: cisco
331- Username ok, need password
Password: **** (cisco)
230- Logged in
(passive mode On)
ftp>
```

## 部分 D：配置 IPv6 ACL

### IPv6 寻址表

| 设备 | 接口 | IP 地址 | 网关 |
|---|---|---|---|
| R1 | G0/0 | 2001:DB8:AAAA:A::1/64 | – |
| | S0/0 | 2001:DB8:AAAA:D::1/64 | – |
| R2 | G0/0 | 2001:DB8:AAAA:B::1/64 | – |
| | S0/0 | 2001:DB8:AAAA:D::2/64 | – |
| | S0/1 | 2001:DB8:AAAA:E::1/64 | – |
| R3 | G0/0 | 2001:DB8:AAAA:C::1/64 | – |
| | S0/0 | 2001:DB8:AAAA:E::2/64 | – |
| PC1 | NIC | 2001:DB8:AAAA:A::2/64 | FE80::1 |
| PC2 | NIC | 2001:DB8:AAAA:B::2/64 | FE80::1 |
| PC3 | NIC | 2001:DB8:AAAA:C::4/64 | FE80::1 |
| PC4 | NIC | 2001:DB8:AAAA:C::5/64 | FE80::1 |
| ftp_server | NIC | 2001:DB8:AAAA:C::2/64 | FE80::1 |
| http-server | NIC | 2001:DB8:AAAA:C::3/64 | FE80::1 |

- 1. 创建一个与之前练习中相同拓扑的新模板

- 2. 在 R1、R2 和 R3 上配置基本参数。

- 2.1. 按拓扑图所示配置主机名。

- 2.2. 根据寻址表将 IP 地址应用到路由器接口。

注意：路由器的本地链路地址将设置为 FE80::1/64。

- 2.3. 将串行接口的时钟值设置为 128000。

- 3. 使用 OSPF 协议配置路由。

- 3.1. 在两台路由器上使用进程 ID 1 启用 OSPF。

- 3.2. 为 R1 设置 RID 为 1.1.1.1，为 R2 设置为 2.2.2.2，为 R3 设置为 3.3.3.3。

- 3.3. 将所有网络添加到 OSPF 协议。

- 3.4. 测试所有网络元素之间的连通性。

- 4. 在 R3 上，创建并激活一个名为“ACL_HTTP”的扩展 ACL，以满足第 1 部分中定义的所有安全要求。

写出要使用的命令：
......................................................................................
......................................................................................
......................................................................................

- 5. 在 R3 上，创建一个名为“ACL_FTP”的扩展 ACL，以满足第 1 部分中定义的安全要求。
......................................................................................
......................................................................................
......................................................................................

- 6. 测试所创建 ACL 的效果。

## 练习 7.

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_110_0.png)

### 寻址表

| 设备 | 接口 | IP 地址 | 子网掩码 | 网关 |
|---|---|---|---|---|
| R1 | G0/0 | 192.168.0.1 | /24 | – |
| | G0/1 | 192.168.1.1 | /24 | – |
| | S0/0 | 192.168.100.1 | /30 | – |
| | S0/1 | 192.168.200.1 | /30 | – |
| R2 | G0/0 | 192.168.10.1 | /24 | – |
| | S0/0 | 192.168.100.2 | /30 | – |
| R3 | G0/0 | 192.168.20.1 | /24 | – |
| | S0/0 | 192.168.200.2 | /30 | – |
| PC1 | NIC | 192.168.0.2 | /24 | 192.168.0.1 |
| PC2 | NIC | 192.168.10.2 | /24 | 192.168.10.1 |
| ftp_server | NIC | 192.168.1.2 | /24 | 192.168.1.1 |
| http-server | NIC | 192.168.1.3 | /24 | 192.168.1.1 |
| http2-server | NIC | 192.168.20.2 | /24 | 192.168.20.1 |

### 目标

配置基于区域的防火墙。

### 使用的软件

Packet tracer.

### 部分 A：建立基本设备配置。

- 1. 配置基本设备设置。

- 1.1. 按拓扑图所示配置主机名。

- 1.2. 根据寻址表将 IP 地址应用到设备接口。

- 1.3. 将串行接口的时钟值设置为 128000。

- 2. 使用 OSPF 协议配置路由。

- 2.1. 在路由器上使用进程 ID 1 启用 OSPF。

- 2.2. 为 R1 设置 RID 值为 1.1.1.1，为 R2 设置为 2.2.2.2，为 R3 设置为 3.3.3.3。

- 2.3. 将所有网络添加到 OSPF 协议。

- 2.4. 测试所有网络元素之间的连通性。

### 部分 B：配置基于区域的防火墙

- 1. 回顾 DMZ 区域的定义。

- 2. 在 R1 上创建安全区域。

- 2.1. 创建名为 IN-ZONE 的内部区域。

```
R1(config)# zone security IN-ZONE
R1(config-sec-zone)# exit
```

- 2.2. 创建名为 DMZ-ZONE 的 DMZ 区域。

```
R1(config)# zone security DMZ-ZONE
R1(config-sec-zone)# exit
```

- 2.3. 创建名为 OUT-ZONE 的外部区域。

```
R1(config)# zone security OUT-ZONE
R1(config-sec-zone)# exit
```

- 2.4. 创建名为 HEAD-ZONE 的外部区域。

```
R1(config)# zone security HEAD-ZONE
R1(config-sec-zone)# exit
```

- 3. 创建 Class-Maps 以识别授权流量。

- 3.1. 创建 CMAP-IN-TO-DMZ Class-Map。

```
R1(config)# class-map type inspect match-any CMAP-IN-TO-DMZ
```

- 3.2. 允许 http、ftp 和 icmp 协议。

```
R1(config-cmap)# match protocol http
R1(config-cmap)# match protocol ftp
R1(config-cmap)# match protocol icmp
R1(config-cmap)# exit
R1(config)# exit
```

- 3.3. 创建 CMAP-IN-TO-HEAD Class-Map。

```
R1(config)# class-map type inspect match-any CMAP-IN-TO-HEAD
```

- 3.4. 允许 http 和 icmp 协议。

```
R1(config-cmap)# match protocol http
R1(config-cmap)# match protocol icmp
R1(config-cmap)# exit
R1(config)# exit
```

- 3.5. 创建 CMAP-OUT-TO-DMZ Class-Map。

```
R1(config)# class-map type inspect match-any OUT-TO-DMZ
```

- 3.6. 仅允许 http 协议。

```
R1(config-cmap)# match protocol http
R1(config-cmap)# exit
R1(config)# exit
```

- 4. 创建 Policy-Maps 以将访问规则应用到 Class-Map。

- 4.1. 回顾应用于区域间流量的三条规则的定义。

- - 通过：................................................................................

- - 检查：

- - 丢弃：

- 4.2. 创建 Policy-Map 以将 Class-Map CMAP-IN-TO-DMZ 应用。

```
R1(config)# policy-map type inspect PMAP-IN-TO-DMZ
R1(config-pmap)# class type inspect CMAP-IN-TO-DMZ
R1(config-pmap-c)# pass
```

- 4.3. 同样，创建以下 Policy-Maps：

- - 针对 Class-Map CMAP-OUT-TO-DMZ 的 PMAP-OUT-TO-DMZ；
- - 针对 Class-Map CMAP-IN-TO-HEAD 的 PMAP-IN-TO-HEAD。

- 5. 定义区域对。

- 5.1. 在 IN-ZONE 和 DMZ-ZONE 之间创建一个应用 PMAP-IN-TO-DMZ 策略的区域对。

```
R1(config)# zone-pair security IN-to-DMZ source IN-ZONE destination DMZ-ZONE
R1(config-sec-zone-pair)# service-policy type inspect PMAP-IN-TO-DMZ
```

- 5.2. 同样，创建以下区域对：

- - OUT-to-DMZ，应用 PMAP-OUT-TO-DMZ 策略；
- - IN-to-HEAD，应用 PMAP-IN-TO-HEAD 策略。

- 6. 将接口分配到区域。

```
R1(config)# interface G0/0
R1(config-if)# zone-member security IN-ZONE
R1(config)# interface G0/1
R1(config-if)# zone-member security DMZ-ZONE
R1(config)# interface S0/0
R1(config-if)# zone-member security OUT-ZONE
R1(config)# interface S0/1
R1(config-if)# zone-member security HEAD-ZONE
```

- 7. 验证 R1 的配置。

使用 “show running-config” 命令，验证配置的所有参数。

- 8. 测试防火墙的配置。

- – 确保可以从 PC1 和 PC2 访问 http-server。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_115_0.png)

- – 检查是否只能从 PC1 访问 http2-server。

- – 检查是否只能从 PC1 访问 ftp-server 服务。

```
PC1> ftp 192.168.1.3
```

- – 检查是否可以从 PC1 向 http-server 发送 ping 请求。

- – 检查是否无法从 PC2 向 http-server 发送 ping 请求。

- – 检查是否可以从 PC1 向 PC2 发送 ping 请求。

