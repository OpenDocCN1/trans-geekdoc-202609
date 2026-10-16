
Wi‑Fi Protected Setup（WPS）是一种无线标准，可实现对安全无线接入点（AP）的简单连接。WPS 的缺点在于其注册 PIN 的实现会让人轻松连接到无线网络，从而便于对使用 WPA/WPA2 PSK 锁定整个系统的攻击。正如我们多年来在安全方面所看到的，一切都是一种权衡。

![remember](images/remember.png)WPS 设计用于家庭无线网络的消费者使用。如果你的无线环境像我所看到的大多数情况，它很可能包含消费级无线接入点（路由器），这些设备易受此攻击。

WPS 攻击相对简单，使用较老的开源工具 Reaver（[`https://code.google.com/p/reaver-wps`](https://code.google.com/p/reaver-wps)）即可。Reaver 通过对 WPS PIN 进行暴力破解来工作。我使用的是商业版 Reaver Pro（[`www.reaversystems.com`](http://www.reaversystems.com)），在公司停止销售前我已经获得了它。你可以通过以太网或 USB 将测试系统连接到 Reaver Pro。如图 10-10 所示，Reaver Pro 的界面非常直观。

![ FIGURE 10-10:  The Reaver Pro startup window.](images/9781119485476-fg1010.png)

[FIGURE 10-10:](#c10.xhtml#rc10-fig-0010)  Reaver Pro 启动窗口。

假设你能在 Amazon 或 eBay 找到它，使用 Reaver Pro 很简单。你只需按照以下步骤操作：

1. **通过将测试系统插入 PoE LAN 网络连接，将其与 Reaver Pro 设备相连。**

   你会通过 DHCP 从 Reaver Pro 设备获取 IP 地址。

2. **打开浏览器，访问 http://10.9.8.1，并使用 reaver/foo 作为用户名和密码登录。**

3. **在主界面，点击菜单按钮。**

   将出现无线网络列表。

4. **在列表中选择你的无线网络，然后点击“分析”。**

5. **让 Reaver Pro 运行并完成其任务。**

   如图 10-11 所示，这是整个过程。

![ FIGURE 10-11:  Using Reaver Pro to determine that Wi-Fi Protected Setup is enabled.](images/9781119485476-fg1011.png)

[FIGURE 10-11:](#c10.xhtml#rc10-fig-0011)  使用 Reaver Pro 确认 Wi‑Fi Protected Setup 已启用。

如果你想让 Reaver Pro 自动破解 WPS PIN，请点击“配置”并将 WPS PIN 设置打开。WPS PIN 破解可能需要几分钟到几小时，但如果成功，Reaver Pro 将返回 WPA PSK，或提示无线网络距离太远或启用了入侵锁定。

我对 Reaver Pro 的使用结果参差不齐，取决于运行它的电脑以及被测试的无线 AP。不过，如果你想找出并修复无线安全漏洞，它仍然是值得尝试的攻击手段。

### 针对 WPS PIN 漏洞的防范措施

这一安全修复极为直接：禁用 WPS。如果必须保留 WPS，至少在 AP 上配置 MAC 地址控制。虽然此防护并非万无一失，但已好于无防护！更新的消费级无线路由器也为 WPS PIN 提供了入侵锁定功能。当系统检测到 WPS PIN 破解尝试时，会在一定时间内锁定这些尝试，这是一种很好的保护措施。在企业环境中防止 WPS 攻击的最佳做法是根本不要使用低端无线路由器。

###  rogue（隐蔽）无线设备

请警惕未经授权的 AP 以及已连接到你网络的未经授权的无线客户端，这些都是让攻击者社交工程诱导用户连接到恶意网络/系统的常见手段。

![warning](images/warning.png)此外，请确保教育用户在办公室外安全使用 Wi‑Fi。向他们传达连接未知 Wi‑Fi 的危害，并定期、持续地提醒他们。否则，他们的系统可能被入侵或感染恶意软件，当他们再次连接到你的网络时，问题就归他们。

通过 NetStumbler 或客户端管理软件，你可以检测出不属于你网络的 AP 和自组网（peer‑to‑peer）设备。你也可以使用无线网络分析工具（如 Omnipeek、CommView for WiFi）的网络监控功能。

请寻找以下 rogue AP 的特征：

*   **异常 SSID**，包括流行的默认 SSID，如 `linksys`、`free public wifi`。

*   **不在你网络中的 MAC 地址**。查看 MAC 地址的前三字节（前六位数字），它们指示设备厂商。你可以在 [`http://standards.ieee.org/develop/regauth/oui/public.html`](http://standards.ieee.org/develop/regauth/oui/public.html) 进行 MAC 地址厂商查找，以获取不确定的 AP 信息。

*   **弱无线信号**，这可能表明 AP 被隐藏或位于建筑内部或外部。

*   **与你网络通信的无线信道不同**，即使用了与网络主要信道不同的信道。

*   **Wi‑Fi 客户端的吞吐量下降**，这可能是隐蔽 AP 的迹象。

在图 10-12 中，NetStumbler 发现了两个潜在的未经授权 AP。最显眼的是 SSID 为 `BI` 和 `LarsWorld` 的两个，它们分别运行在不同信道、不同速率上，并且由不同的硬件厂商制造。如果你知道你的无线网络应运行什么（你当然知道），未经授权的系统就会显而易见。

![ FIGURE 10-12:  NetStumbler showing potentially unauthorized APs.](images/9781119485476-fg1012.png)

[FIGURE 10-12:](#c10.xhtml#rc10-fig-0012)  NetStumbler 显示潜在的未经授权 AP。

NetStumbler 有一项局限性：它无法检测到将 SSID 广播（probe response）关闭的 AP。像 CommView for WiFi 这类商业无线分析工具以及开源工具 Kismet 不仅会检测到 AP 的探测响应（如 NetStumbler 所做），还会捕获其他 802.11 管理帧，如关联响应和 beacon。这些管理帧使得 Kismet 能够发现隐藏的 Wi‑Fi。

如果 Linux 环境不是你喜欢的，且你仍想快速简便地查找隐藏 AP，可以创建客户端到 AP 的重新连接场景，使用去认证（deauthentication）包迫使 SSID 广播。详细步骤请参考我与同事 Peter T. Davis 合著的《Hacking Wireless Networks For Dummies》（Wiley）一书。

最安全、最可靠的查找隐藏 AP 的方法是搜索 802.11 管理帧。你可以在像 Omnipeek 这样的无线分析工具中配置捕获过滤器，只捕获 802.11 管理帧，如图 10-13 所示。

![ FIGURE 10-13:  You can configure Omnipeek to detect APs that don’t broadcast their SSIDs.](images/9781119485476-fg1013.png)

[FIGURE 10-13:](#rc10-fig-0013)  你可以在 Omnipeek 中配置捕获过滤器，以检测不广播 SSID 的 AP。

图 10-14 显示如何使用 CommView for WiFi 发现异常网络主机。在图 10-14 中，Technico 和 Netgear 系统出现在列表中，但该网络仅使用 Ubiquiti 硬件。

![ FIGURE 10-14:  Using CommView for WiFi to spot wireless systems that don’t belong.](images/9781119485476-fg1014.png)

[FIGURE 10-14:](#rc10-fig-0014)  使用 CommView for WiFi 发现不属于该网络的无线系统。

我的测试网络相对较小，但足以说明“异常系统”如何脱颖而出。

