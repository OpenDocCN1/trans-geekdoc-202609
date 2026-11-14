

| 命令 | 描述 |
|---|---|
| Router(config)# aaa group server radius group-name | 对现有 RADIUS 主机服务器进行分组并使用它们。 |
| Router(config-sg-radius)# server ip-address [ auth-port port-number ] [ acct-port port-number ] | 为组服务器配置 RADIUS 服务器的 IP 地址。 |
| Router(config)# aaa group server tacacs+ group-name | 将现有 TACACS+ 主机服务器分组在一起。 |
| Router(config-sg-tacacs+)# server server-ip | 为组服务器配置 TACACS+ 服务器的 IP 地址。 |

## 4.3. AAA 授权

AAA 授权策略定义了用户在路由器或网络上的访问参数。

| 命令 | 描述 |
|---|---|
| Router(config)# aaa authorization { exec | network | commands level } { default list-name } { method1 [ method2 ...]} | 定义在访问以下模式时使用的授权策略：- exec，允许用户在此模式下运行命令；- network，设置与网络相关的授权访问请求，例如 PPP；- commands，为特定特权级别设置授权命令。 |

## 4.4. AAA 可追溯性

AAA 可追溯性使得可以在事件日志中记录用户执行的所有操作。通过这样做，可以查询日志以验证用户操作或识别给定操作的作者，以便在出现问题时迅速介入。AAA 支持六种不同的可追溯性类型：系统、网络、exec、commands、连接和资源。

## 4.5. 应用练习

练习 5.–

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_87_0.png)

要查看此图的彩色版本，请参阅 www.iste.co.uk/sadiqui/computer.zip

### 寻址表

| 设备 | 接口 | IP 地址 | 子网掩码 | 网关 |
| :--- | :--- | :--- | :--- | :--- |
| R1 | G0/0 | 192.168.0.1 | /24 | – |
| | S0/0 | 192.168.2.1 | /30 | – |
| R2 | S0/0 | 192.168.2.2 | /30 | – |
| PC1 | NIC | 192.168.0.2 | /24 | 192.168.0.1 |
| AAA 服务器 | NIC | 192.168.0.3 | /24 | 192.168.0.1 |

### 目标

- 保护密码；
- 保护控制平面；
- 使用 AAA 保护管理访问。

### 使用的软件

Packet Tracer。

### 部分 A：配置基本设备设置。

### 1. 配置基本设备设置。

- 1.1. 按拓扑图所示配置主机名。
- 1.2. 根据寻址表将 IP 地址应用到设备接口。
- 1.3. 为串行接口设置时钟值为 128 000。

### 2. 使用 EIGRP 配置路由。

- 2.1. 在两台路由器上启用 EIGRP，SA ID 使用值 1。
- 2.2. 为 R1 设置 RID 值为 1.1.1.1，为 R2 设置 RID 值为 2.2.2.2。
- 2.3. 将所有网络添加到 EIGRP。
- 2.4. 测试所有网络元素之间的连通性。

### 部分 B：保护密码

- 1. 设置最小密码长度为 8 个字符。
- 2. 为特权模式设置密码“Ci$c0ena”。
- 3. 配置控制台、辅助端口和虚拟访问线路。
- 3.1. 将“Ci$c0con”设置为控制台端口密码，并将非活动间隔设置为 5 分钟。
- 3.2. 在 VTY 线路上设置密码“Ci$c0vty”，并将非活动间隔设置为 2 分钟。
- 3.3. 禁用辅助端口。
- 4. 加密所有密码。

```
R1(config)# service password-encryption
```

### 部分 C：保护控制平面

为 EIGRP 配置 MD5 身份验证。

- 1. 在 R1 上配置 EIGRP 密钥。

```
R1(config)#key chain EIGRP-SECRET
R1(config-keychain)# key 1
R1(config-keychain-key)# key-string Ci$eigrp
```

- 2. 在 R2 上重复相同的配置。
- 3. 实施 EIGRP 身份验证。

```
R1(config)#interface s0/0
R1(config-if)# ip authentication mode eigrp 1 md5
R1(config-if)# ip authentication key-chain eigrp 1 EIGRP-SECRET
```

- 4. 在 R2 上重复相同的配置。

### 5. 验证 R1 和 R2 之间是否已建立 EIGRP 邻居链路。

```
R1#show ip eigrp neighbors
EIGRP-IPv4 Neighbors for AS(1)
H Address Interface Hold Uptime SRTT RTO Q
Seq
(sec) (ms) Cnt Num
0 192.168.2.2 s0/0 12 00:01:10 2000 5000 0 2
```

### 6. 验证身份验证是否已使用 MD5 加密执行。

```
R1#debug eigrp packets
*Mar 2 13:06:02.998: EIGRP: received packet with MD5 authentication, key id = 1
```

### 部分 D：使用 AAA 保护管理访问

### 1. 回顾使用 AAA 管理访问的优势。

### 2. 使用本地数据库为访问控制台配置本地 AAA 身份验证。

### 2.1. 激活 AAA 服务。

```
R1(config)# aaa new-model
```

### 2.2. 配置身份验证方法，仅使用本地数据库。

```
R1(config)# aaa authentication login default local none
```

### 2.3. 创建密码为“@dmin012”的 Admin 用户。

```
R1(config)#username Admin privilege 15 secret @dmin012
R1(config)#exit
R1#exit
```

### 2.4. 通过 Telnet 连接到 Admin 账户。

### 3. 使用本地数据库为 Telnet 创建 AAA 身份验证配置文件。

3.1. 删除旧身份验证模式的配置。

```
R1(config)# no aaa authentication login default local none
```

3.2. 为路由器 Telnet 访问创建身份验证名称。

```
R1(config)# aaa authentication login TELNET_CON local
```

注.— “local” 参数用于在与“AAA”服务器连接失败时使用本地数据库。

3.3. 定义 Telnet 访问的身份验证名称。

```
R1(config)# line vty 0 4
```

```
R1(config-line)# login authentication TELNET_CON
```

3.4. 通过控制台连接到 Admin 账户。

```
PC1> telnet 192.168.0.1
```

3.5. 如何仍然可以连接到 R1？

### 4. 使用本地 AAA 服务器配置身份验证。

4.1. 在 AAA 服务器上：

- 激活 AAA 服务；
- 创建客户端“R1”，密码为“R@duis00”；
- 创建客户端“R2”，密码为“R@duis01”；
- 为客户端 R1 定义 IP 地址 192.168.0.1，为客户端 R2 定义 IP 地址 192.168.2.2；
- 将 AAA 服务器类型设置为 RADIUS；
- 创建两个用户：u1，密码为“P@ssuser1”；u2，密码为“P@ssuser2”。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_92_0.png)

### 4.2. 配置路由器以使用 AAA 服务器。

```
R1(config)# radius-server host 192.168.0.3 key R@duis00
R1(config)# aaa authentication login TELNET_CON group radius
local
```

### 4.3. 使用 Admin 账户通过 Telnet 连接到 R1。

```
PC1> telnet 192.168.0.1
```

### 4.4. 为什么现在无法再连接到 R1？

### 4.5. 使用 u1 账户通过 Telnet 连接到 R1。

### 4.6. 配置 R2 以使用 AAA 身份验证。

```
R2(config)# radius-server host 192.168.0.3 key R@duis01
R2(config)# aaa authentication login TELNET_CON group radius
local
R2(config)# line vty 0 4
R2(config-line)# login authentication TELNET_CON
```

### 4.7. 使用相同的 u1 账户通过 Telnet 连接到 R2。

```
PC1> telnet 192.168.2.2
```

### 4.8. 使用 AAA 服务器的优势是什么？

................................................................................................................

注.— 在本练习中，我们仅限于 AAA 身份验证。但是，读者可以通过添加与 AAA 授权和 AAA 可追溯性相关的部分来了解更多信息，例如使用 Cisco Secure ACS 服务器。

