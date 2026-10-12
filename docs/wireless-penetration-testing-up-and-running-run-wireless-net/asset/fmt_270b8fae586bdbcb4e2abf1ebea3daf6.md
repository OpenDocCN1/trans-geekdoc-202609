
# WEP 破解实战步骤

## 1. 配置接入点
连接到我们的接入点 **Wireless Lab**，并导航至处理无线加密机制的设置部分，如 *[Figure 4.2](#c04.xhtml#fig4_2)* 所示。在我的接入点上将 **Security Options** 设置为 **WEP** 即可实现此目的。我们还需要调整 WEP 密钥的长度。我们已将 WEP 配置为使用 64 位密钥，如 *[Figure 4.2](#c04.xhtml#fig4_2)* 所示。我们将默认密钥设置为 **WEP Key 1**，并将 64 位 WEP 密钥值设置为十六进制的 `0123456789`。您可以将其更改为任何您想要的值。

![](images/Figure-4.2.jpg)

**Figure 4.2:** Netgear router setting

完成更改后，接入点现在应该能够使用 WEP 作为加密方法。让我们启动攻击者机器。

## 2. 启用监听模式
打开一个终端窗口并输入以下命令，然后按 *Enter* 键：

```
airmon-ng start wlan0
```

`wlan0` 接口将通过此命令在监听模式下启动。监听模式允许您的计算机监听通过无线网卡范围内的每个无线数据包。我们将能够使用此技术向无线网络注入数据包。结果如 *[Figure 4.3](#c04.xhtml#fig4_3)* 所示：

![](images/Figure-4.3.jpg)

**Figure 4.3:** airmon-ng command

## 3. 抓取数据包
然后按 *Enter* 键后输入以下命令：

```
airodump-ng wlan0
```

此命令开启无线接口的监听模式。结果如 *[Figure 4.4](#c04.xhtml#fig4_4)* 所示：

![](images/Figure-4.4.jpg)

**Figure 4.4:** airodump-ng command_1

## 4. 定向抓取握手包
按 *Enter* 键后输入以下命令：

```
airodump-ng -c 1 -w capture --bssid DC:EF:09:59:B1:1F wlan0
```

命令组件如下：

*   `-c`：指定信道
*   `-w`：指定写入文件
*   `–bssid`：指定无线接入点 MAC 地址

*[Figure 4.5](#c04.xhtml#fig4_5)* 是上一命令的输出：

![](images/Figure-4.5.jpg)

**Figure 4.5:** airodump-ng command_2

让我们将无线客户端连接到接入点并使用 WEP 密钥 `0123456789`。当客户端成功连接时，`airodump-ng` 应在屏幕上显示一条消息。

为了利用协议中的缺陷，我们需要大量使用相同密钥加密的数据包，这在繁忙网络场景中也是如此。因此，我们需要让网络产生更多数据包。我们将使用 `aireplay-ng` 实用程序来实现这一点。

## 5. 伪造认证关联
按 *Enter* 键后输入以下命令，如 *[Figure 4.6](#c04.xhtml#fig4_6)* 所示：

```
airplay-ng -1 1000 -q 10 -e ‘Wireless Lab’ -a DC:EF:09:59:B1:1F -h 00:11:22:33:44:55 wlan0 --ignore-negative-one
```

命令组件如下：

*   `-1`：每次突发的数据包数量
*   `-q`：保活包之间的秒数
*   `-e`：设置目标 AP SSID
*   `-a`：设置接入点 MAC 地址
*   `-h`：设置源 MAC 地址（`00:11:22:33:44:55` 为伪造的 MAC 地址）
*   `--ignore-negative-one`：解决 wlan0 固定信道问题

![](images/Figure-4.6.jpg)

**Figure 4.6:** aireplay-ng command_1

## 6. ARP 重放攻击
我们将使用 `aireplay-ng` 拦截无线网络上的 ARP 数据包并将其重新注入以模仿 ARP 应答。如 *[Figure 4.7](#c04.xhtml#fig4_7)* 所示，我们将在一个单独的窗口中运行 `aireplay-ng`。如果我们重复这些数据包几千次，将在网络上产生大量数据流量。即使 `Aireplay-ng` 没有访问 WEP 密钥的权限，它也可以根据数据包大小检测 ARP 数据包。因为 ARP 是固定头部协议，所以 ARP 数据包的大小可以很容易地估算，并用于识别它们，即使通信是加密的。我们将使用接下来要介绍的选项配合 `aireplay-ng`。`-3` 选项用于 ARP 重放，`-b` 选项用于我们网络的 BSSID，`–h` 选项用于伪造客户端的 MAC 地址。重放攻击仅对授权且已关联的客户端 MAC 地址有效，因此我们需要执行此操作，如 *Figure 4.7* 所示：

```
aireplay-ng -3 -b DC:EF:09:59:B1:1F -h 00:11:22:33:44:55 wlan0
```

![](images/Figure-4.7.jpg)

**Figure 4.7:** aireplay-ng command_2

## 7. 数据包积累
此时 `Airodump-ng` 也将开始记录大量数据包。捕获文件包含所有这些拦截的数据包。

## 8. 破解 WEP 密钥
让我们开始实际破解！在一个新窗口中，我们使用 `capture-01.cap` 选项运行 `aircrack-ng`。这将启动 `aircrack-ng` 程序，该程序将开始使用文件中的数据包破解 WEP 密钥。`Airodump-ng` 应收集 WEP 数据包，`aireplay-ng` 应执行重放攻击，`aircrack-ng` 应尝试根据收集的数据包破解 WEP 密钥，所有这些应同时进行。在本实验中，它们都在不同的窗口中打开。按 *Enter* 键后输入以下命令，如 *[Figure 4.8](#c04.xhtml#fig4_8)* 所示：

```
aircrack-ng capture-01.cap
```

![](images/Figure-4.8.jpg)

**Figure 4.8:** aircrack-ng command

破解密钥所需的数据包数量是不确定的；但通常在数十万或更多。在快速网络上（或使用 `aireplay-ng`），这不应超过 5–10 分钟。如果文件中当前的数据包数量不足，`aircrack-ng` 将暂停并等待收集更多数据包；然后重新启动破解过程。一旦收集并分析了足够的数据包，`Aircrack-ng` 应能够破解密钥。

如果您成功破解了网络密钥，恭喜您成功破解了一个 WEP 加密网络！如果不成功也不要担心。每个无线接入点和网络都是独特的。这还取决于您与接入点之间的信号强度以及使用的加密级别。

至关重要的是要理解 WEP 完全存在缺陷，`Aircrack-ng` 可以破解任何 WEP 密钥（无论多么复杂）。唯一的要求是 `aircrack-ng` 能够访问足够多的使用该密钥加密的数据包。

**注意：** 我们还可以使用上一章学到的 **Shared Key Authentication** 绕过方法来模拟对接入点的认证。如果合法客户端退出网络，这将很有用。这将允许我们在仍将重放数据包发送到网络的同时伪造认证和关联。

# WPA 和 WPA2 加密

**TKIP** 加密算法主要由 **WPA** 使用。**TKIP** 的创建目标是在不需要全新硬件的情况下升级 **WEP**。另一方面，**WPA2** 使用 **AES-CCMP** 加密技术，它比 **TKIP** 强大且健壮得多。

**WPA** 和 **WPA2** 都支持通过 **RADIUS** 服务器进行基于 **EAP** 的认证（企业版），或基于 **Pre-Shared Key**（**PSK**，预共享密钥）的认证模式（个人版）。

可以对 **WPA/WPA2 PSK** 使用字典攻击。此攻击需要客户端与接入点之间的四次 **WPA** 握手，以及常用口令的字典。然后我们可以尝试使用 `Aircrack-ng` 等工具破解 **WPA/WPA2 PSK** 密码。

四次握手如 *[Figure 4.9](#c04.xhtml#fig4_9)* 所示：

![](images/Figure-4.9.jpg)

**Figure 4.9:** WPA/WPA2 authentication diagram

**Pairwise Transient Key**（**PTK**，成对临时密钥）是使用 **PSK** 和其他五个参数计算得出的：网络 **SSID**、**Authenticator Nounce**（**ANonce**，认证者随机数）、**Supplicant Nounce**（**SNonce**，申请者随机数）、**Authenticator MAC address**（**Access Point MAC**，认证者 MAC 地址）和 **Supplicant MAC address**（**Wi-Fi Client MAC**，申请者 MAC 地址）。然后使用此密钥加密接入点和客户端之间的数据。
