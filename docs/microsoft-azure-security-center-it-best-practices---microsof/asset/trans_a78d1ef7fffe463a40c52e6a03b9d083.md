

- **活跃显著问题 (Active Critical Notable Issues)**：显著问题是关键事件。在身份语境下，它们是关键身份事件。此计数器反映了需要立即关注的活跃显著问题。
- **活跃警告显著问题 (Active Warning Notable Issues)**：这与之前的计数器相同，针对的是中优先级问题而非关键问题。

身份与访问仪表板中的“失败日志”部分让人目了然日志失败的主要原因。

当用户身份验证失败时，Windows 会生成一个名为事件 4625 的事件。要调查特定登录失败的原因，请点击“失败区域 (Failed Logon Regions)”部分中的登录。参见图 4-34，事件 4625窗口显示了失败原因。（参见“失败信息”部分。）

![](img/4b11e95292819ab1a383a41ef73aedb4_100_0.png)

**图 4-34** 事件 4625 的描述

事件 4625 对话框中可用信息可能根据失败原因而异。表 8-1 列出了失败的一些最常见原因。

| 错误代码 (状态/子状态) | 描述 |
|---|---|
| 0xC000006D | 用户名未知或密码错误。 |
| 0xC0000234 | 账户锁定。 |
| 0xC0000072 | 账户当前禁用。 |
| 0xC0000193 | 指定的用户帐户已过期。 |
| 0xC0000071 | 密码过期。 |

**表 8-1** 登录失败的常见原因

> 提示 登录失败原因的完整列表，请参 https://aka.ms/AccountLogon。

在查看事件 4625 时，请注意“登录 (Logon)”字段。如果此字段设置为 3，意味着登录尝试来自网络。在这种情况下，你还会看到一个带有相应 IP 地址的 IPAddress 字段。如果 LogonType 设置为 5，意味着登录尝试来自某个源或进程。Process 字段将包含进程名称。列表 4-1 显示的代码包含了事件 4625 的全部内容，该事件在登录请求失败时生成，并出现在尝试访问的计算机上。

# 列表 4-1 事件 ID 4625

```
Log Name: Security
Source: Microsoft-Windows-Security-Auditing
Date: 2/19/2019 9:08:29 AM
Event ID: 4625
Task Category: Logon
Level: Information
Keywords:Audit Failure
User: N/A
Computer: ARCOS
Description:
An account failed to log on.
Subject:
Security ID: NULL SID
Account Name: -
Account Domain: -
Logon ID: 0x0
Logon Type: 3
Account For Which Logon Failed:
Security ID: NULL SID
Account Name:
YURIDBVT01$
Account Domain: NORTHAMERICA
Failure Information:
Failure Reason:
Unknown user name or bad password.
Status:
0xC000006D
Sub Status: 0xC0000064
Process Information:
Caller Process ID: 0x0
Caller Process Name: -
Network Information:
Workstation Name: YURIDBVT01
Source Network Address: 192.168.1.254
Source Port: 53407
```

Detailed Authentication Information:
Logon Process: Ntlmsp
Authentication Package: NTLM
Transited Services: -
Package Name (NTLM only): -
Key Length: 0

- **主体字段 (Subject fields)**：主体字段指示请求登录的本地系统帐户。这最常见的是一个服务（例如 Server 服务）或本地进程（例如 Winlogon.exe 或 Services.exe）。
- **登录字段 (Logon field)**：登录类型字段指示请求的登录类型。最常见的类型是 2（交互式）和 3（网络）。
- **进程信息字段 (Process Information fields)**：进程信息字段指示系统上的哪个帐户和进程请求了登录。
- **网络信息字段 (Network Information fields)**：网络信息字段指示远程登录请求源。工作站名称 (Workstation Name) 并不总是可用，某些情况下可能会留空。
- **身份验证信息字段 (Authentication Information fields)**：身份验证信息字段提供了此登录请求的详细信息：
- **传递服务 (Transited Services)**：传递服务指示哪些中间服务参与了此登录请求。
- **包名 (Package Name)**：包名指示在 NTLM 协议中使用了哪种子协议。
- **密钥长度 (Key Length)**：密钥长度指示生成的会话密钥的长度。如果没有请求会话密钥，则长度为 0。

# 列表 4-2 事件 ID 4625

```
<Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">
<System>
<Provider Name="Microsoft-Windows-Security-Auditing" Guid="54849625-5478-4994-A5BBA-3E30B2C8C00" />
<EventID>4625</EventID>
<Version>0</Version>
<Level>1</Level>
<Task>12544</Task>
<Opcode>0</Opcode>
<Keywords>0x8010000000000000</Keywords>
<TimeCreated SystemTime="2019-02-19T15:08:29.580371002Z" />
<EventRecordID>60107528</EventRecordID>
<Correlation />
<Execution ProcessID="724" ThreadID="16256" />
```
<Channel>Security</Channel>
<ARGOS/></Computer>
<Security />
<System-id />
<EventData>
<Data Name="SubjectUserId">S-1-0-0</Data>
<Data Name="UserName">--</Data>
<Data Name="SubjectDomain">--</Data>
<Data Name="SubjectLogId">0x0</Data>
<Data Name="TargetUserId">S-1-0-0</Data>
<Data Name="TargetUserName">YURIDBV01</Data>
<Data Name="TargetDomainName">NORTHAMERICA</Data>
<Data Name="Status">0xC000006D</Data>
<Data Name="FailureReason">Unknown user name or bad password.</Data>
<Data Name="Sub Status">0xC0000064</Data>
<Data Name="Logon Type">3</Data>
<Data Name="Process Name">Ntlmsp</Data>
<Data Name="Authentication Package">NTLM</Data>
<Data Name="Transited Services">--</Data>
<Data Name="Package Name">--</Data>
<Data Name="Key Length">0</Data>
</EventData>
</Event>
```

