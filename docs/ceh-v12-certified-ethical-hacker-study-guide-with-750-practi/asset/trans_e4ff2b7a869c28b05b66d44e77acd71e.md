
Malware 是一个并非一次性完成的任务，大部分情况下尤其如此。这尤其适用于恶意软件的目的是为攻击者提供远程访问。攻击者希望恶意软件在登录/退出和重启后继续运行。攻击者可以使用多种技术确保软件始终运行。从启动过程开始，恶意软件可能在操作系统甚至尚未启动前就将自己安装并运行。这使其能够控制启动过程，并在任何防护措施生效前将其加载到内存中。启动前的恶意软件并不常见，但它是最危险的之一，因为它在任何反恶意软件程序启动前就已经运行，从而更难以被检测。

在 Windows 系统中，攻击者可能会使用 Windows 注册表添加键值，使软件在系统启动时自动启动。常用的注册表键有两个。第一个是 `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run`，它会在系统启动时启动软件。另一个是 `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run`，该键用于在用户登录时启动程序。该注册表键属于特定用户，因此恶意软件只会在该用户登录时启动，这限制了恶意软件仅限于该用户的权限。首选键是 `HKEY_LOCAL_MACHINE` 下的键，因为它会以机器级权限运行；但有时攻击者只有用户级权限。

另一种技术是计划任务（scheduled tasks）。这种持久化机制在类 Unix 操作系统以及 Windows 系统上都适用。在类 Unix 系统中，`cron` 是用于计划任务的常用设施。可能有不同的实现，但最终都是 `cron`。在 Windows 系统中，有 `at` 程序，它的工作方式类似于类 Unix 系统的计划任务。你可以设置程序在指定时间运行。在类 Unix 系统中，可能还有按小时、按天或按周运行的任务。

还有其他用于持久化的技术。MITRE ATT&CK 框架列出了所有已知的持久化机制，包括操作系统特定的技术（如 Windows Management Instrumentation（WMI）事件订阅）以及跨平台的技术（如启动脚本）。这些技术通常可以被检测，因此攻击者始终在寻找新的持久化技术。

**Summary**

Malware 是信息技术行业的严重问题，影响企业和个人。恶意软件作者通常占据上风。如果他们想保持领先，可以始终在防病毒程序之前将恶意软件植入系统。他们通常利用新恶意软件获得优势，并且可以不断修改恶意软件，使其更难被检测。

这就是恶意软件分析的作用所在。有两种分析方式。第一种是静态分析，它通过查看恶意软件的属性及其实际代码来进行。你可以查看文件的组成，包括 PE 文件中节段的数量和大小。静态分析还可以判断是否为打包可执行文件。一种方法是查看入口点。入口点在编译时确定，基于提供给程序的地址空间。该地址可以被标记，而不仅仅是一个地址。如果你看到入口点名为类似 "UPX" 的名称，你就会知道它已被打包，因为 UPX 是常见的打包工具。反汇编器有助于查看代码以及可执行文件的某些属性。

另一种分析方式是动态分析，即运行程序并观察恶意软件的行为。这必须小心进行，因为你不想感染自己的机器，也不想将网络中的其他系统暴露于潜在感染风险。在虚拟机中运行恶意软件可以帮助此目的，尽管某些恶意软件会识别它是否运行在虚拟机中并不会完全展开。你可以使用沙箱环境运行程序，也有沙箱会自动化分析。其中一个是 Cuckoo Sandbox，它可以安装在自己的硬件上，或在公开的在线安装中使用。使用调试器可以帮助进行动态检查，因为你可以控制程序的运行。

在你对目标组织进行测试时，你可能想使用恶意软件。由于你行为守法，你不想使用真正具有恶意目的的恶意软件。你可能想安装后门或测试操作员是否能够检测到恶意软件的存在。你可以通过编写自己的程序来实现，同时考虑目标平台、架构以及其他要求。Python 是流行的编程语言，但 Windows 系统可能没有像 macOS 或 Linux 那样预装 Python 解释器。Windows 系统通常预装有 PowerShell。使用像 C 这样的编译语言编写的程序通常更可靠，因为所有程序元素都可以在编译时完成，而不必依赖预先安装的库。

恶意软件通常会有相关的基础设施。你可能听说过僵尸网络（botnets）。僵尸网络是受感染系统的集合，拥有命令和控制（C2）系统，用于指示僵尸终端执行什么操作。即使没有完整的 C2 系统网络，也至少会有系统供受感染系统连接，以便攻击者进行远程控制。这是因为防火墙通常允许出站流量，而阻止入站流量。因此，最佳做法是从内部发起连接。内部发起连接时，需要一个服务器供内部系统连接。即使只有少数系统，这仍然是基础设施。

**Review Questions**

你可以在附录中找到答案。

1. 在僵尸网络中，用于告诉单个僵尸执行什么操作的系统叫什么？

   1. `C2 servers`

   2. `IRC servers`

   3. `HTTP servers`

   4. `ISC2 servers`

2. 蠕虫和病毒的主要区别是什么？

   1. `A worm uses polymorphic code.`

   2. `A virus uses polymorphic code.`

   3. `A worm can self‑propagate.`

   4. `A virus can self‑propagate.`

3. 静态分析相对于动态分析的一个优势是什么？

   1. `Malware is guaranteed to deploy.`

   2. `Dynamic analysis is untrustworthy.`

   3. `Static analysis limits your exposure to infection.`

   4. `Static analysis can be run in virtual machines.`

4. 你会使用 VirusTotal 做什么？

   1. `Checking your system for viruses`

   2. `Endpoint protection`

   3. `As a repository of malware research`

   4. `Identifying malware against antivirus engines`

5. 便携式可执行文件（PE 文件）中通常会包含哪两个部分？

   1. `Text and binary`

   2. `Binary and data`

   3. `Addresses and operations`

   4. `Text and data`

6. 你可以使用什么来生成自己的恶意软件？

   1. `Empire`

   2. `Metasploit`

   3. `Rcconsole`

   4. `IDA Pro`

7. 恶意软件打包工具的作用是什么？

   1. `To obscure the actual program`

   2. `To ensure that the program is all binary`

   3. `To compile the program into a tight space`

   4. `To remove null characters`

8. 恶意软件程序的多态代码的主要目的是什么？

   1. `Efficiency of execution`

   2. `Propagation of the malware`

   3. `Antivirus evasion`

   4. `Faster compilation`

9. 写恶意软件时不使用 Python 的一个原因是什么？

