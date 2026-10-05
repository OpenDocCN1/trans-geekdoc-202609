
# 202 • 网络安全与密码学

消息 (5)：请求服务：此消息由 C 发往应用服务器 V 以获取服务。

$C\rightarrow V: Ticket_c || Authenticator_v$
$Authenticator_{c^2} = E_{Kr,c}[ID || AD]$

$Authenticator_{c^2}$ 使用 C 和 V 共享的密钥 $K_{r,c}$加密。这将确保 V 消息已从 C 处获取：如果两者匹配，则向 V 验证该用户。现在 V 向 C 发回一条消息 ($TS_s+1$)，其中 $TS_s$ 是在消息 5 中接收到的。这是 C 和 V 的相互认证。

消息 (6)：应用服务器到客户端：此消息由应用服务器在响应请求时发送 C。

$V\rightarrow C: E_{Kr,c}[TS_s+1]$

# 9.5.1 跨域 Kerberos

不同的组织拥有自己的 Kerberos 域（Realms）。

但一个域内的客户端可能想要访问其他域的服务器。同样，一个域内的服务器可能为其他域的客户端提供服务，这些客户端通过它们自己的域 Kerberos 进行认证。如果用户在域“A”的客户端工作站 $C$ 登录并打算访问域“B”中的远程服务器 $V$，请求处理如下：

- 1. 客户端向本地 TGS 请求访问票据。该请求包含了在工作站 $C$ 登录的用户 ID，$ID_{tgs}$ 以及时间戳 $TS_{tgs}$。

- 2. 本地 AS 发布 Ticket$_{tgs}$ 和用于 C 与本地 TGS 通的会话密钥 $K_{c,tgs}$。Ticket$_{tgs}$ 使用 AS 和本地 TGS 共享的密钥 $K_{as,tgs}$加密。因此，只有本地 TGS 可以打开票据。会话密钥 $K_{c,tgs}$ 用于 C 和本地 TGS 之间的通信。

- 3. 现在，客户端工作站向本地 TGS 请求访问域“B”中远程 TGS 的票据。该请求包含了 $ID_{tgrem}$、Ticket$_{tgs}$ 和 $Authenticator_{c^1}$。

- 4. 本地 TGS 发布票据和会话密钥 $K_{cgs}$。票据使用本地 TGS 与远程 TGS 共享的密钥 $K_{tgs}$加密，以便远程 TGS 可以打开票据。会话密钥 $K_{cgs}$ 用于 C 和远程 TGS 之间的通信，即 TGS$_{rem}$。

图 9.2 展示了认证序列（Kerberos 版本 4）。消息 (1) 和 (2) 每个会话交换一次，消息 (3) 和 (4) 根据“服务类型”交换，消息 (5) 和 (6) 根据服务会话交换。

![](img/d3b56042c756fbcc01ff06f1b9f530_427_0.png)

图 9.2 认证序列图（Kerberos 版本 4）。

- 5. 现在，客户端工作站向 TGS$_{rem}$ 请求访问域“B”中远程服务器 $V_{rem}$ 的票据。该请求包含了 $ID_{rem}$、$Ticket_{rem}^{rem}$ 和 $Authenticator_{c^2}^{rem}$。

- 6. TGS、票据和会话密钥 $K_{c,rem}^{rem}$——票据使用 TGS 和 V 共享的密钥 $K_{rem}^{rem}$加密。会话密钥 $K$ 用于 C 和应用服务器 $V_{rem}$ 之间的通信。

- 7. 客户端工作站向域“B”中的 $V_{rem}$ 请求请求提供所需的服务。该请求包含了 $Ticket_{rem}$ 和 $Authenticator_{c^3}$。Authenticator 包含了时间戳 $TS_s$。

- 8. 最后，$V_{rem}$ 通过向 C 发送 $(TS_s+1)$ 也向 C 验证自身。此消息使用 $K_{rem}^{rem}$加密。图 9.3 展示了认证序列。（img/d3b56042c756fbcc01ff06f1b9f530_428_0.png）

图 9.3 认证序列图。

# 9.5.2 Kerberos 版本 5 认证序列

消息 1 从客户端到认证服务器 (AS) 的认证服务请求 (KRB_REQ)
$C\rightarrow AS: Options || ID_e || Realm_e || ID_{tgs} || Times || Nounce_e$

其中
- Options：客户端为从 AS 请求的票据授予据 (TGT) 指定的选项
- FORWARDABLE：票据是可以转发的
- PROXYABLE：票据是可以代理的，等

认证服务器的响应将反映在 Flag 中：
- ID_e：客户端 ID。
- Realm_e：客户端所在域。
- ID_{tgs：TGS ID。
- Times：时间。
- Nounce_e：防止重放的随机数

消息 2 从 AS 发往客户端的认证服务回复 (KRB_REP)，用于获取票据授予据 (TGT) 和用于 C 与本地 TGS 通的会话密钥 $K_{c,tgs}$。
$AS\rightarrow C: Flags || Ticket_{tgs} || E_{as,tgs} [ Times || Realm_e]$

Flag 包含了 Ticket$_{tgs}$ 的可用选项，如转发、代理。Time 表示有效期，开始时间可以提前生效。

消息 3 从 C 发往 TGS 的票据授予服务请求 (KRB_TGS_REQ)，用于获取服务票据和用于 C 与应用服务器 V 通的会话密钥 $K_{c,s}$。
$C\rightarrow TGS: Options || ID_e || Times || Nounce_e || Ticket_{tgs} || Authenticator_{c^1}$

消息 4 从 TGS 发往客户端的票据授予服务回复 (KRB_TGS_REP)，用于传递服务票据和用于 C 与 V 通的会话密钥 $K_{c,t}$。
$TGS\rightarrow C: Flags_e || ID_e || Ticket_e || E_{c,s}[K_{c,t} || Times || Nounce_s || Realm_s || ID_s]$

Flag 包含了 Ticket$_e$ 的可用选项。Time 表示有效期。

消息 5 从 C 发往应用服务器的服务请求 (KRB_AP_REQ)，用于获取服务。
$C\rightarrow V: Options || Ticket_e || Authenticator_{c,s}$
$Authenticator_{c,s} = E_{K_{c,s}}[ID_c || Realm_s || Sub-Key || Seq#s]$

消息 6 应用服务器发往客户端的服务回复 (KRB_AP_REP)，用于相互认证。
$V\rightarrow C: E_{K_{c,s}}[TS_s || Seq#s]$

# 9.5.3 Kerberos V4 与 Kerberos V5 的区别

Kerberos V4 存在以下环境和技术限制，这些限制在 Kerberos V5 中已成功克服：

- 1. **加密算法**：Kerberos V4 仅允许使用 DES加密。但 Kerberos V5 允许使用其他加密算法；密文上的标签指示所使用的算法。

- 2. **通信协议**：Kerberos V4 仅使用 IP 地址进行通信；但 Kerberos V5 允许使用其他网络地址协议；标签指示所使用的网络地址协议。

- 3. **消息字节序协议**：Kerberos V4 使用小端或大端格式，并将其附加在消息上；但在 Kerberos V5 中，结构使用抽象语法表示 (ASN.1) 和基本编码规则 (BER) 定义，提供了无歧义的字节序。
