

| 排名 | 大学 | 学生 | 分数 |
|---|---|---|---|
| - | ESNA de Bretagne | 75 | 3019 |
| - | Hochschule Niederrhein | 446 | 2719 |
| - | Radboud University | 35 | 2329 |
| 4 | ENSIBS | 122 | 2284 |
| 5 | FAU Erlangen-Nuremberg | 38 | 2262 |
| 6 | Bradley University | 80 | 2154 |
| 7 | Western Governors University | 347 | 2146 |
| ▲ 8 | University of Maryland Global Campus | 202 | 2069 |

**图 10.6** 某黑客 CTF 网站的大学排名（2024年2月24日）。

学习针对不同 Linux 和 Windows 系统的不同利用技术非常有益。随着时间推移，当你遇到想要入侵的系统时，你的经验会帮助你。还有一些其他资源可以用于攻击侧。VulnHub（现由 Offensive Security 拥有，该公司也是 OSCP 考试供应商）允许你下载虚拟机，你可以在自己的系统上运行并攻击它们。我喜欢这种方式，因为更多的工作需要你自己完成，比如配置操作系统和网络，确保你的机器能够通信。

实际上，我当时正在为一次会议做研究，并尝试做一场关于入侵物联网（IoT）和监控与数据采集（SCADA）设备的现场演示。我在 VulnHub 网站上找到了一些不错的虚拟机，在完成一些额外操作后，我能够让它们运行起来并完成配置，然后能够利用它们。该网站允许你免费下载虚拟机。有时你可以找到教程来指导你如何攻陷这些机器。随着时间积累的经验将有助于提升你的黑客技能。

![](img/181571ad74cba0e6a2f38fcd2658651e_301_0.png)
**图 10.7** 虚拟机资源。

对于 Hack The Box 和 VulnHub，社区都有参与。你可以上传自己的虚拟机，或提供关于如何攻陷这些机器的演练指南（除非它们是 Hack The Box 上的活跃机器）。通过解释过程并确保你所采取的步骤可重现来进行演练，是渗透测试的关键部分，也有助于提升你的报告撰写技能。下面是我能够利用的一个模拟人行横道信号灯的虚拟机示例。该虚拟机从 VulnHub 获取，名为 TinySploit ARM，它使用快速模拟器（QEMU）模拟基于 ARM 的设备，并且是免费开源的。我也采用过另一种方式，在搭载 Silicon 芯片的 Mac 上使用 UTM 和 QEMU 来模拟基于 Intel 的中央处理器（CPU）。

![](img/181571ad74cba0e6a2f38fcd2658651e_301_1.png)
**图 10.8** TinySploit ARM。

这次攻击的一个有趣之处在于，我找到了一个可用于针对人行横道信号灯的漏洞利用程序，但该程序在我当时拥有的最新版 Kali 上无法运行，因为该漏洞利用程序是用 Python 2 编写的，而我的 Kali 使用的是 Python 3。因此，我没有花时间用早期版本的 Python 重写该漏洞利用程序，而是给朋友打了个电话（老电视剧的梗），并让 ChatGPT（https://chat.openai.com/）将我找到的漏洞利用程序转换，使其能在 Python 3 中运行。我不记得它是否完美，但经过一点编辑，我让它成功运行了。我懂得阅读（和编辑）代码，但自从我为 Atari 或 Texas Instruments (TI)-82 图形计算器编写初学者通用符号指令码（BASIC）程序以来，我并没有真正做过太多编程。当然，使用人工智能（AI）并利用 ChatGPT 帮助你冲过终点线是完全可以的。在我看来，使用 AI 工具是一个很好的补充，只是不要陷入总是依赖它来完成工作的境地。

```
write this for python3:
#!/usr/bin/env python

from pwn import *

LHOST = [192,168,150,100]
LPORT = 4444
RHOST = '192.168.150.128'
RPORT = 8080
BAD_CHARS = '\x00\x20'

shellcode = '\x01\x10\x8f\xe2\x11\xff\x2f\xe1\x01\x21\x48\x1c\x52\x40\xff\x27\x1a\x37\x01\xdf\x83\x4'
shellcode += p16(LPORT, endian='big')
```

**图 10.9** ChatGPT 助手。

说到 Kali，你需要的一件事是为你的攻击机器准备一个好的 Kali 虚拟机。有些人使用 Parrot、AthenaOS、Exegol 或其他 Linux 变体。Kali 的相关文档非常丰富，所以如果你是渗透测试或网络安全的新手，使用预配置的 Kali Linux 虚拟机将是一个不错的选择。你可以在这里下载：https://www.kali.org/get-kali/#kali-virtual-machines

![](img/181571ad74cba0e6a2f38fcd2658651e_302_0.png)
**图 10.10** Linux。

我推荐在 Windows 或 Linux 上使用 VMware Workstation，在 Mac 上使用 VMware Fusion，这些软件自 2024 年起已免费。你可以通过以下链接为 Windows、Linux 或 Mac 下载：https://www.vmware.com/products/desktop-hypervisor.html。请注意，它仅限非商业用途免费。我建议人们使用它而不是 Oracle VirtualBox 的主要原因是，如果你所在组织的 IT 部门拥有 vSphere 和 Elastic Sky X Integrated (ESXi) 服务器，熟悉 VMware 将非常有益。熟悉 VMware Workstation (Player) 的网络和配置，可以让你更轻松地过渡到企业环境中的 VMware vSphere 工作。

![](img/181571ad74cba0e6a2f38fcd2658651e_303_0.png)
**图 10.11** VMware vSphere。

我已经使用 VMware 超过 20 年，有人引用过我的话，说“这是我用过的最具变革性的软件”。如果没有 VMware Workstation，我对网络安全的理解以及对操作系统和网络概念的熟悉程度绝不会是今天这个样子。使用 VMware，你可以学习安装、配置、组网、入侵、执行应急响应以及进行取证分析。快照功能非常有用，它可以在操作系统完全按照你的要求配置好后、在你做出更改之前保存一个状态点。

![](img/181571ad74cba0e6a2f38fcd2658651e_303_1.png)
**图 10.12** – VMware 快照。

诚然，Oracle VirtualBox 和 Microsoft Virtual PC 确实具备与 VMware Workstation 类似的功能。但我确实发现 Linux 操作系统在 VMware Workstation 上运行得更好。

如果你是黑客新手，我们可以利用 VMware 的仅主机（Host-only）功能，确保扫描和漏洞利用不会离开你的系统。你实际上可以断开无线网络或以太网连接（如果你有的话），但仍然可以使用 VMware 的仅主机模式。请确保你在攻击时使用仅主机模式，以确保你的攻击被限制在本地。

![](img/181571ad74cba0e6a2f38fcd2658651e_305_0.png)
**图 10.15** VMware 仅主机模式。

安装 VMware Workstation 时，有三种模式：

- 仅主机（Host-Only）：虚拟机只能与该机器上处于仅主机模式的其他虚拟机通信。
- NAT（网络地址转换）：可访问互联网和其他 NAT 虚拟机。
- 桥接（Bridged）：可访问物理网络适配器。

当你安装 VMware Workstation 时，你的 Windows 机器默认会有两个额外的网络接口卡：VMnet1（属于仅主机网络的一部分）和 VMnet8（属于 NAT 网络的一部分）。你的以太网或无线适配器将对应你的桥接网络。这将允许你连接到宿主机（即安装操作系统的主机）。这两个 VMnet 接口都有一个以 .1 结尾的私有互联网协议（IP）地址。这些网络的网关是 .2，动态主机配置协议（DHCP）服务器是 .254。这些地址 .1、.2 和 .254 在这些虚拟网络上是保留的。

![](img/181571ad74cba0e6a2f38fcd2658651e_305_1.png)
**图 10.16** VMware VMnet 适配器。

如果你点击“编辑”->“虚拟网络编辑器”，你可以调整 NAT 和仅主机模式的 IP 网络。我更喜欢为 VMware 选择自己的静态 IP 地址。我不喜欢使用看起来很随机的 IP 地址，因为如果我们记住我们正在 ping、扫描和利用的 IP 地址，就更容易练习我们的技能。对于在教室中使用 VMware Workstation 教学的教师来说，这些 IP 地址可能会在您的各种安装中随机分配，而当班上的每个人都有不同的 IP 地址集时，教学（无论是新手还是经验丰富的学习者）就会变得困难。我还经常带着笔记本电脑外出做演示，而我连接的 Wi-Fi 网络通常提供 10.0.0.0/8 地址。许多家庭网络使用 192.168.1.0/24 子网，基于这两个原因，我选择使用 172.16.0.0/12 范围内的网络地址。当你在这里进行更改时，它们会影响宿主机上的 VMnet1 和 VMnet8 适配器。它们会自动更新为这些寻址方案，所以不要手动更改它们。我关闭了仅主机连接的 DHCP，因为我喜欢手动设置 IP。由于我经常利用 NAT 网络上可用的互联网，所以我为该接口保留 DHCP 服务器，但通常仍然手动设置虚拟机 IP 地址，将网关设置为 .2，通常将域名系统（DNS）服务器设置为 8.8.8.8（Google DNS）。虽然其中一些可能看起来微不足道，但如果你静态地设置东西，并为受害机器使用易于记忆的地址（如 172.16.100.100 而不是像 192.168.39.138 这样的地址），你将花更多时间学习，更少时间进行故障排除和检查 IP 地址。

## 私有 IP 地址范围

```
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
```

![](img/181571ad74cba0e6a2f38fcd2658651e_306_0.png)
**图 10.17** VMware Workstation 的 IP 子网。

当你开始网络安全之旅时，你应该从仅主机模式并使用扁平网络开始。扁平网络攻击更容易理解和实施。正如你从下面的示例中看到的，我更喜欢使用易于记忆的漂亮静态 IP 地址，

