

| 命令 | 描述 |
|---|---|
| router(config)#interface interface-type router(config-if)#ip ospf authentication message-digest | 配置每接口身份验证。 |
| router(config-if)#ip ospf message-digest-key key-id md5 key | 定义身份验证设置。 |

- 要配置每区域 MD5 身份验证，请执行以下操作：

| 命令 | 描述 |
|---|---|
| router(config-router)#area area-id authentication message-digest | 配置每区域身份验证。 |
| router(config)#interface interface-type router(config-if)#ip ospf message-digest-key key-id md5 key | 定义身份验证设置。 |

## 2.7.4. 配置 EIGRP 协议身份验证

要为 EIGRP 配置 MD5 身份验证，必须执行以下操作：

- 配置一个密钥串；
- 在密钥串下配置一个密钥 ID；
- 为密钥 ID 指定密码；
- 为密钥指定接受时间和过期时间（可选）。

请执行以下操作：

| 命令 | 描述 |
|---|---|
| router(config)#key chain name-of-key-chain | 密钥串可用于配置多个密钥，这些密钥随后可用于执行安全身份验证。例如，这样可以为给定密钥配置有效期，或在有限时间内使用一系列轮换密钥，以降低密钥被攻破的可能性。 |

| 命令 | 描述 |
|---|---|
| router(config-keychain)#key key-id | 创建一个密钥并进入密钥配置模式。 |
| router(config-keychain-key)#key-string key-string | 配置一个密钥字符串。 |
| router(config)#interface interface-type router(config-if)#ip authentication key-chain eigrp as-number key-chain-name | 配置使用特定密钥串进行身份验证。 |
| router(config-if)#ip authentication mode eigrp as-number md5 | 配置使用 MD5 身份验证。 |

注意 - EIGRP 仅支持 MD5 身份验证。

## 2.7.5. 配置 RIP 身份验证

要为 RIP 配置 MD5 身份验证，请执行以下操作：

| 命令 | 描述 |
|---|---|
| router(config)#key chain name-of-key-chain | 创建密钥串。 |
| router(config-keychain)#key key-id | 创建一个密钥并进入密钥配置模式。 |
| router(config-keychain-key)#key-string key-string router(config-keychain-key)#end | 配置一个密钥字符串。 |
| router(config)#interface interface-type router(config-if)#ip rip authentication key-chain key-chain-name | 配置使用特定密钥串进行身份验证。 |
| router(config-if)#ip rip authentication mode md5 | 配置使用 MD5 身份验证。 |

## 2.8. 应用练习

### 练习 1。

### 拓扑结构

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_41_0.png)

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_42_0.png)

### 寻址表

| 设备 | 接口 | IP 地址 / 子网掩码 | 操作系统 (GNS3) | 网关 |
|---|---|---|---|---|
| R1 | G0/0 | 192.168.0.1/24 | c2600-adventerprisek9-mz.124-1 | - |
| PC1 | NIC | 192.168.0.2/24 | Windows 7 | 192.168.0.1 |

### 目标

- 保护密码。
- 实施连接限制。
- 分配管理角色。

### 使用的软件

- Packet Tracer。
- 或 GNS3。

### 部分 A：建立基本设备配置

- 1.1. 按照拓扑结构中指示的内容配置主机名。
- 1.2. 根据寻址表将 IP 地址应用于设备接口。

### 部分 B：保护密码

- 1. 设置最小密码长度为 8 个字符。

```
R1(config)# security passwords min-length 8
```

- 2. 配置特权模式的密码。

  - 2.1. 为该模式定义明文密码。

```
R1(config)# enable password Ci$c0123
```

- 2.2. 能否从“show run”命令中读取此密码？

- 2.3. 为特权模式设置加密密码。

```
R1(config)# enable secret Ci$c0ena
```

- 2.4. 能否从“show run”命令中读取此密码？

- 3. 配置控制台端口、辅助端口和虚拟访问线路。

  - 3.1. 配置控制台端口密码，并将非活动间隔设置为 5 分钟。

```
R1(config)# line console 0
R1(config-line)# password Ci$c0con
R1(config-line)# exec-timeout 5 0
R1(config-line)# login
R1(config-line)# logging synchronous
```

  - 3.2. 在 VTY 线路上配置密码，并将非活动间隔设置为 2 分钟。

```
R1(config)# line vty 0 4
R1(config-line)# password Ci$c0vty
R1(config-line)# exec-timeout 2 0
R1(config-line)# login
```

  - 3.3. 禁用辅助端口。

```
R1(config)# line aux 0
R1(config-line)# no exec
```

  - 3.4. 通过 Telnet 从 PC1 访问 R1。

```
PC1> telnet 192.168.0.1
```

- 4. 加密所有密码。

  - 4.1. 使用“密码加密服务”命令加密控制台和 VTY 密码。

```
R1(config)# service password-encryption
```

- 4.2. 能否从“show run”命令中读取控制台和 VTY 密码？

### 部分 C：实施连接限制

- 1. 配置登录警告横幅。

  - 1.1. 使用“motd”命令为未授权用户配置警告。

```
R1(config)# banner motd $ Access strictly forbidden for unauthorized persons $
R1(config)# exit
```

  - 1.2. 从命令“show run”中，配置文件中字符“$”被什么替换了？

### 部分 D：保护对 VTY 线路的访问

- 1. 配置 SSH 连接。

使用以下选项配置 SSH 连接：

- 域名：tri.local；
- 用户名：sshadmin，密码：Ci$c0ssh；
- RSA 加密密钥为 1024 位；
- 使用的 SSH 版本为版本 2；
- 等待时间为 90s；
- 登录尝试次数为 3 次；
- 授权 SSH 和 Telnet 会话。

- 2. 配置连接参数。

  - 2.1. 使用“login block-for”命令配置：如果在 30 秒内两次连接尝试失败，则停止连接 60 秒。

```
R1(config)# login block-for 60 attempts 2 within 30
```

  - 2.2. 使用“Login delay”命令配置连续连接尝试之间 5 秒的延迟。

```
R1(config)# login delay 5 (GNS3)
```

  - 2.3. 每次连接尝试成功时，向事件日志添加一条条目。

```
R1(config)# login on-success log
```

或：

```
R1(config)# login on-success log every 1 (GNS3)
```

  - 3. 创建两个新用户帐户，使用秘密密码。

```
R1(config)# username user01 secret user01pass
R1(config)# username user02 secret user02pass
```

- 4. 从 Telnet 会话连接到 R1。

  - 4.1. 从 PC1 建立到 R1 的 Telnet 会话。

```
PC1> telnet 192.168.1.1
```

  - 4.2. 是否要求您输入用户帐户？为什么？

............................................................................

  - 4.3. 定义 VTY 线路使用本地定义的登录帐户。

```
R1(config)# line vty 0 4
R1(config-line)# login local
```

  - 4.4. 从 PC1 重新建立到 R1 的 Telnet 会话。

```
PC1> telnet 192.168.1.1
```

  - 4.5. 尝试使用错误的用户 ID 或密码登录两次。第二次失败尝试后，PC1 上会显示什么消息？

............................................................................

  - 4.6. 第二次不成功的连接尝试后，R1 控制台上会显示什么消息？

............................................................................

- 4.7. 从 PC1，尝试在 60 秒内建立另一个到 R1 的 Telnet 会话。Telnet 连接尝试后，PC1 上会显示什么消息？

- 4.8. Telnet 连接尝试后，R1 路由器上显示了什么消息？

- 5. 仅通过使用 SSH 协议限制到 R1 的连接。

  - 5.1. 配置 VTY 线路仅使用 SSH 协议。

```
R1(config)# line vty 0 4
R1(config-line)# transport input ssh
R1(config-line)# exit
```

  - 5.2. 从 PC1，尝试建立另一个 SSH 和 Telnet 会话到 R1。

### 部分 E：分配管理角色

- 1. 配置特权级别。

  - 1.1. 使用以下选项创建一个新用户帐户：
    - 帐户名称：“SshUser”；
    - 加密密码：‘SshUpa $$’；
    - 特权级别 10。

```
R1(config)# username SshUser privilege 10 secret SshUpa $$
```

  - 1.2. 为特权级别 10 配置密码“Priv10P $”。

```
R1(config)# enable secret level 10 Priv10P$
```

  - 1.3. 在 exec 模式下允许此特权级别使用“ping”命令。

```
R1(config)# privilege exec level 10 ping
```

  - 1.4. 在 exec 模式下允许此特权级别使用“ssh”命令。

```
R1(config)# privilege exec level 10 ssh
```

