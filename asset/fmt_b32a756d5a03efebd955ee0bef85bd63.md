
Pass the hash is a hacking technique used to access networks that use Microsoft NT LAN Manager (NTLM) as their authentication protocol. With pass the hash, the hacker first compromises a Windows system and then performs a hashdump of the SAM database. The hashdump contains all of the password hashes for each of the user accounts on that system. The hacker can then use those hashes in a pass-the-hash attack to move laterally throughout the network and authenticate to the next system. The benefit of this type of attack from a hacker’s perspective is that the hacker does not need to crack the user passwords; they can simply pass the hash value of the password to another system on the network when authenticating. As a mitigation technique for pass the hash, you can enforce Kerberos authentication in order to remove the risk of this attack.

### Amplification（信号放大）

Amplification is the process of increasing the strength of a signal so that communication can occur. A hacker may amplify the signal on their wireless card so that they can reach greater distances with wireless. This means that the hacker may not need to be physically close to a network in order to connect to that network if they have amplified their signal. Keep in mind, from a security point of view, you should lower the power on your wireless access point to force someone to be close to your access point in order to connect (inside the facility).

### Spam（垃圾邮件）

Spam is sending the same unsolicited e-mail message to a number of people. Spam messages are typically sent in hopes that the receiver of the spam message will buy a product or service from the sender of the message.

Most e-mail servers now have spam filters in place that help protect the system from receiving a large number of unsolicited e-mail messages.

### Privilege Escalation（权限提升）

Privilege escalation is a popular attack that involves someone who has user-level access to a system being able to elevate their privileges to gain administrative access to the system. Privilege escalation normally occurs due to a vulnerability within software running on the system or within the operating system itself. It is important to keep the system and application patched in order to remove any known vulnerabilities, which will help prevent privilege escalation.

### Port Scanning Attacks（端口扫描攻击）

Another popular network attack is known as port scanning or a port scanning attack. With a port scanning attack, the hacker runs software on the network that does a port scan against the system, which indicates to the hacker what ports are open. Once the hacker finds out what ports are open, they can then try to exploit the ports to gain access to the system.

A number of different types of port scans can be used; the following list details three of the most popular:

#### TCP connect scan（TCP 连接扫描）

With a TCP connect scan, shown in Figure 4-9, the hacker performs a TCP three-way handshake with each port on the system. The concept is that if the hacker can do a three-way handshake with a port, then the port must be open.

![Image](img/f0162-01.jpg)

**FIGURE 4-9** Performing a TCP connect scan

#### SYN scan (half-open scan)（SYN 扫描/半开放扫描）

The TCP connect scan is easily detected on a network because of the three packets sent between the hacker and the system being scanned; therefore, the SYN scan was created. With the SYN scan, the hacker sends a SYN message but doesn’t send the ACK as the third phase of the three-way handshake after receiving an ACK/SYN from the victim’s system. The goal here is to avoid detection by creating less traffic. This scan is also known as a half-open scan or a stealth scan.

#### XMAS scan（XMAS 扫描）

In an XMAS scan, a packet is sent to each port with the PSH, URG, and FIN flags set in the packet. The term *XMAS scan* comes from the fact that you have three of six flags enabled, which is like turning on a bunch of lights on a Christmas tree. Note that this is also called an XMAS attack.

---

## EXERCISE 4-2: Performing a Port Scan（执行端口扫描）

![Images](img/video.jpg)

In this exercise, you will use Kali Linux to do some port scanning on the `10.0.0.0` network. Ensure that Windows 10 VM, ServerA VM, and Kali Linux are started.

## 实验步骤

1. 进入 Linux VM 并打开终端（命令提示符）。通常可以通过右键单击桌面并选择 **New Terminal** 来完成。

2. 要对 `10.0.0.1` 系统执行 TCP 连接扫描，请输入：

```
nmap -sT 10.0.0.1
```

3. 要对 `10.0.0.1` 执行 TCP 连接扫描并指定扫描端口 21、25 和 80，请输入：

```
nmap -sT -p 21,25,80 10.0.0.1
```

4. 这些端口中哪些在该系统上是开放的？

________________________________________________________________________________

5. 要对 `10.0.0.1` 执行 SYN 扫描并指定扫描端口 21、25 和 80，请输入：

```
nmap -sS -p 21,25,80 10.0.0.1
```

6. TCP 连接扫描和 SYN 扫描有什么区别？

________________________________________________________________________________

________________________________________________________________________________

7. 要对整个 `10.0.0.0` 网络执行 SYN 扫描并指定扫描端口 21、25 和 80，请输入：

```
nmap -sS -p 21,25,80 10.0.0.0/24
```

## 其他网络攻击

不同类型的网络攻击层出不穷；以下是一些你应为 Security+ 认证考试熟悉的其他劫持及相关攻击：

- **Pharming（域名劫持/重定向攻击）** 如前所述，*pharming* 是某些人用来指代针对 DNS 或 hosts 文件的攻击的术语，此类攻击会将用户导向错误的网站。

- **Antiquated protocols（过时协议）** 过时协议是指在开发时未考虑安全性、且通常现已有安全版本取代的协议。例如 TCP/IP 协议套件中的大多数协议，如 `HTTP`、`FTP`、`SMTP` 和 `POP3`。你将在 第 12 章 了解这些协议的安全版本。

- **Session hijacking（会话劫持）** 会话劫持是指黑客将通信双方中的一方踢出通信，并冒充该方参与对话。黑客通常通过拒绝服务攻击使一方断开连接。

- **Null sessions（空会话）** 空会话是指在不提供任何凭据的情况下连接到 Windows 系统。一旦连接成功，如果系统未加固，攻击者便可枚举该系统。通过枚举，黑客可能收集用户、组和共享文件夹列表。以下命令用于与 Windows 系统建立空会话：

```
net use \\10.0.0.1\ipc$ "" /u:""
```

- **Domain name kiting（域名滥用/域名踢踏）** 在域名滥用中，黑客利用允许的五天宽限期免费获取域名。五天宽限期结束时，他们取消该域名，然后再次免费获取五天。他们持续重复此过程以免费占用该域名。

- **Malicious insider threat（恶意内部威胁）** 恶意内部威胁是指公司内部人员故意破坏或泄露公司数据。恶意内部威胁也可能是实施欺诈活动的人员（应对措施包括利用职责轮换和最小权限概念）。

- **Transitive access (attack)（传递访问/攻击）** 传递攻击发生在用户收到指向另一个 Windows 共享文件夹的超链接并点击该链接时。这会强制用户系统将 Windows 用户账户凭据传递给远程系统以尝试认证。问题在于，如果黑客使用嗅探器和密码破解工具，便可尝试破解账户密码。

- **Client-side attacks（客户端攻击）** 客户端攻击是通过客户端系统软件中的漏洞对系统发起的攻击。许多客户端攻击源自互联网应用程序，如 Web 浏览器和即时通讯应用。

- **Watering hole attack（水坑攻击）** 水坑攻击是指黑客确定目标可能访问的网站，然后通过在其中植入病毒或恶意代码来攻陷这些网站。当你访问该网站（你信任的网站）时，便会感染病毒。

- **Typo squatting/URL hijacking（拼写劫持/URL 劫持）** 拼写劫持也称为 URL 劫持，它利用用户在浏览器地址栏输入 URL 时可能出现拼写错误的事实。黑客建立一个 URL 与热门网站极其相似、但包含预期拼写错误的网站，将粗心的输错者引导至黑客的网站。

> **考试提示：** 请记住，水坑攻击是指黑客感染目标受害者常访问的网站。当预期受害者访问该网站时，恶意代码执行并感染他们。

## 恶意代码或脚本执行

你将在 第 15 章 了解应用程序攻击与安全，以及可在系统上执行的不同类型恶意代码。本节仅介绍攻击者可用来创建恶意脚本的一些常见脚本环境：

- **PowerShell** PowerShell 是 Windows 系统的脚本环境，使用 cmdlet。cmdlet 是采用 `verb-noun`（动词-名词）格式的 PowerShell 命令（例如，使用 `get-service` 获取系统上运行的服务列表）。你可以创建扩展名为 `.ps1` 的 PowerShell 脚本文件。

- **Python** Python 是最流行的脚本环境之一，用于自动化系统任务和执行网络测试。例如，管理员常使用 Python 编写自己的端口扫描器。Python 脚本文件使用 `.py` 扩展名。

- **Bash** Bash 脚本在 Linux 环境中创建，常用于执行 Linux 系统的定期维护任务。Bash shell 脚本文件包含一系列按顺序运行的 Linux 命令，脚本文件扩展名为 `.sh`。

- **Macros（宏）** 宏是应用程序的一项功能，可记录你的操作步骤，以便通过运行宏重复执行这些步骤。大多数应用程序中的宏环境除可录制步骤外，还可使用语言语法进行编程。攻击者常创建包含恶意宏的文件，并通过电子邮件发送给受害者，受害者打开文件时宏即运行，在系统上执行恶意操作。

- **Visual Basic for Applications (VBA)** Visual Basic for Applications 是 Microsoft Office 套件的宏编程语言。例如，你可以在 Excel 中使用 VBA 自动操作电子表格。

## 预防网络攻击

面对如此多类型的网络攻击，你可以采取多种措施加以防范。首先，确保已部署物理安全控制，防止未经授权的人员进入设施并连接到网络。

此外，在交换机上实施安全功能，例如禁用交换机上未使用的端口。如果端口被禁用，黑客尝试连接未使用端口时将无法使用。还应在交换机上实施端口安全功能；即启用端口时，将特定 MAC 地址与该端口关联。这将确保没有人能从交换机断开一台工作站并用未经授权的系统替换它。

及时为系统打补丁，以免受已知漏洞利用。同时，确保更新网络硬件（如交换机和路由器）的固件，以消除固件中的已知漏洞。

最后，让所有员工了解不同类型的攻击，如 `vishing`（语音钓鱼）、`pharming`、`spam`（垃圾邮件）和 `spim`（即时消息垃圾邮件）等。员工的安全意识越强，你的环境就越安全。

### 认证目标 4.03

### 了解密码攻击

一个非常重要且需要熟悉的攻击类型是密码攻击。密码攻击是指黑客试图破解存储在系统上的用户账户密码。本节将讨论不同类型的密码攻击，以及如何防止密码攻击在您的环境中发生。请注意，这些也被称为 `cryptographic attacks`（加密攻击），这是您在 Security+ 考试目标中找到它们的分类术语。

![Image](img/exam.jpg)

**您应该了解不同类型的密码攻击。**

#### 密码攻击的类型

密码攻击主要有三种类型：字典攻击、暴力破解攻击和混合攻击。您将在本节中了解这些密码攻击类型，以及密码喷射、彩虹表和明文密码等其他密码攻击概念。

![Images](img/video.jpg)**要查看密码破解攻击的示例，请查看随书附带的在线资源中包含的视频。**

##### 字典攻击

字典攻击涉及黑客使用一个程序，该程序在一个文本文件中包含常用用户名列表，在另一个文件中包含语言字典中的单词列表，这些单词将被尝试作为密码。字典文件通常包含一种语言的所有单词，可以从互联网上下载。图 4-10 显示了一个名为 NetBIOS 身份验证工具 (NAT) 的字典攻击工具及其示例用户列表文件和密码列表文件。

![Image](img/f0167-01.jpg)

图 4-10  

使用 NAT 进行字典攻击
