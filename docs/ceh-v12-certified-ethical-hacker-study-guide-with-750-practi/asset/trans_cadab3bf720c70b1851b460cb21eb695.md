
一旦你启动 `wifiphisher`，它会列出所有在系统范围内的 SSID。这里是你选择要伪装的 SSID 以获取凭据的地方。你可以在 [Figure 10.10](#c10.xhtml#c10-fig-0109) 中看到此选择。正如屏幕上显示的，你需要向下滚动选择要伪装的 SSID，然后按回车确认。你可能已经注意到在前面的输出中，有一个无线接口将被用于 deauthentication 攻击。这意味着当 `wifiphisher` 运行时，它会向看起来已连接到真实接入点的系统发送 deauthentication 帧。这将迫使那些客户端重新认证，理想情况下它们会与你建立连接。

![FIGURE 10.10 wifiphisher SSID selection](images/c10f010.png)

[**FIGURE 10.10**](#c10.xhtml#R_c10-fig-0109) `wifiphisher` SSID 选择

在你选择要伪装的 SSID 后，`wifiphisher` 会询问你要使用哪种攻击类型。在 [Figure 10.11](#c10.xhtml#c10-fig-0119) 中，你可以看到用户将被展示的场景选项。

![FIGURE 10.11 wifiphisher attack template selection](images/c10f011.png)

[**FIGURE 10.11**](#c10.xhtml#R_c10-fig-0119) `wifiphisher` 攻击模板选择

所选模板将决定你从目标获得什么。OAuth 页面将让你收集凭据，而其他模板（包括浏览器插件）则会让你在目标计算机上安装一些代码。这可能是远程访问软件，例如。与许多其他事物一样，这取决于你在这类攻击中想要实现什么。

在无线领域，要使其有效工作需要许多环节配合，这意味着整个设置会以一种在用户感知上不易引起怀疑的方式运行，从而可能阻止用户让安全团队介入识别你的 rogue access point。使用自动化工具进行无线社交工程攻击通常更为合适。这并不意味着你必须始终使用手动方法进行其他社交工程攻击。还有其他自动化社交工程的方法。

## 自动化社交工程

由于钓鱼是野外最常见且最易实施的攻击之一，我们可以从自动化钓鱼攻击开始。我们将使用 Metasploit 来协助，更具体地说，我们将使用一个在 Metasploit 之上作为叠加的程序 —  — 社会工程工具包 (SET)。这是一个基于菜单的程序，利用 Metasploit 的模块和功能，但会自动整合它们，帮助你完成社会工程攻击所需的任务。下面的代码片段展示了 SET 的初始菜单。该程序功能强大，但我们这里只做简要浏览，而不会深入探讨全部功能。

**Social‑Engineer Toolkit 起始菜单**

```
   The Social-Engineer Toolkit is a product of TrustedSec.
 
           Visit: https://www.trustedsec.com
 
   It's easy to update using the PenTesters Framework! (PTF)
 Visit https://github.com/trustedsec/ptf to update all your tools!
 
 
  Select from the menu:
 
    1) Social-Engineering Attacks
    2) Penetration Testing (Fast-Track)
    3) Third Party Modules
    4) Update the Social-Engineer Toolkit
    5) Update SET configuration
    6) Help, Credits, and About
 
   99) Exit the Social-Engineer Toolkit
 
 set>
 
 
```

选择 **Social‑Engineering Attacks** 后会打开另一个菜单，这里需要输入菜单项的编号。整个程序多年来不断增长其功能。这一点在 **Social‑Engineering Attacks** 菜单的向量数量上表现明显，你可以在下面的列表中看到。你可能会注意到有两种钓鱼攻击向量：一种是大规模发送邮件，另一种是定向 spear phishing。区别在于预期的收件人数量。

**Social‑Engineer Toolkit 社交工程攻击**

```
 Select from the menu:
 
    1) Spear-Phishing Attack Vectors
    2) Website Attack Vectors
    3) Infectious Media Generator
    4) Create a Payload and Listener
    5) Mass Mailer Attack
    6) Arduino-Based Attack Vector
    7) Wireless Access Point Attack Vector
    8) QRCode Generator Attack Vector
    9) Powershell Attack Vectors
   10) Third Party Modules
 
   99) Return back to the main menu.
 
 
```

无论你选择哪一项，都可以向单个地址或多个地址发送。下面的代码片段展示了不同选项之间的差异。

**Spear‑phishing 向量**

```
    1) Perform a Mass Email Attack
    2) Create a FileFormat Payload
    3) Create a Social-Engineering Template
```

**Mass Mailer 向量**

```
     1.  Email Attack Single Email Address
     2.  Email Attack Mass Mailer
     
 
```

我们将重点观察 **Mass Email Attack** 向量，因为其基本步骤在不同的邮件攻击中是相同的。Mass Email Attack 允许我们使用文件格式漏洞。可用的 payload 是 Metasploit 中已有的文件格式 exploit，这些文件格式常被利用且成功率有希望。

**文件格式漏洞的 Payload**

```
            ********** PAYLOADS **********
 
     1) SET Custom Written DLL Hijacking Attack Vector (RAR, ZIP)
     2) SET Custom Written Document UNC LM SMB Capture Attack
     3) MS15-100 Microsoft Windows Media Center MCL Vulnerability
     4) MS14-017 Microsoft Word RTF Object Confusion (2014-04-01)
     5) Microsoft Windows CreateSizedDIBSECTION Stack Buffer Overflow
     6) Microsoft Word RTF pFragments Stack Buffer Overflow (MS10-087)
     7) Adobe Flash Player "Button" Remote Code Execution
     8) Adobe CoolType SING Table "uniqueName" Overflow
     9) Adobe Flash Player "newfunction" Invalid Pointer Use
    10) Adobe Collab.collectEmailInfo Buffer Overflow
    11) Adobe Collab.getIcon Buffer Overflow
    12) Adobe JBIG2Decode Memory Corruption Exploit
    13) Adobe PDF Embedded EXE Social Engineering
    14) Adobe util.printf() Buffer Overflow
    15) Custom EXE to VBA (sent via RAR) (RAR required)
    16) Adobe U3D CLODProgressiveMeshDeclaration Array Overrun
    17) Adobe PDF Embedded EXE Social Engineering (NOJS)
    18) Foxit PDF Reader v4.1.1 Title Stack Buffer Overflow
    19) Apple QuickTime PICT PnSize Buffer Overflow
    20) Nuance PDF Reader v6.0 Launch Stack Buffer Overflow
    21) Adobe Reader u3D Memory Corruption Vulnerability
    22) MSCOMCTL ActiveX Buffer Overflow (ms12-027)
          
 
```

文件格式告诉我们将如何利用系统。这将让我们在远程系统上运行任意代码；我们只需要确定那段任意代码是什么。我们的 payload 将基于我们选择的文件格式漏洞类型。如果选择列表中的第一种文件格式，则会得到一系列 payload，默认是 Meterpreter 内存注入。该 payload 会将 Meterpreter shell 发送回我们这边，前提是我们已设置好 handler。

钓鱼在社交工程中是可靠的攻击向量，但它并不是唯一的选择。你可能甚至不想获得目标系统的 shell 访问权限。幸运的是，SET 拥有许多其他功能，正如初始菜单所示。你甚至可以使用 SET 自动化无线攻击。虽然还有其他许多社交工程攻击方式，但这是一个强大的工具，利用 Metasploit 框架的 payload 与其他功能，极大地简化了你的工作。

## 总结

