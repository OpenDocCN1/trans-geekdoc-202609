
介绍所使用的协议，然后逐步介绍相关的威胁。随后讨论最佳实践，然后是加密。

## 34.3.1 协议基础

### 34.3.1.1 音频流协议：RTP 和 UDP。

实时传输协议（RTP）是一种基于数据包的通信协议，为几乎所有 VoIP 架构提供了基础。RTP 的一部分是可用于重建音频流的定时和数据包序列信息。与 TCP 类似，用户数据报协议（UDP）是第 4 层网络通信协议。这两种协议都提供了从一个网络地址到另一个网络地址所需的基本数据包寻址。在处理 VoIP 时，数据包的传输时间至关重要。TCP 和 UDP 都会给组织的网络通信增加开销。这种开销会导致通信延迟增加。UDP 增加的开销较少，因为它提供的包错误检查相对较少。折中之处在于 UDP 有助于更快地传输数据包，但也会导致更多数据包丢失。有观察表明，在一次 VoIP 通话中分散的 10% 的数据包丢失对大多数用户来说几乎无法察觉。然而，使 VoIP 安全的所有功能也会增加延迟。增加的延迟意味着更多丢失或丢弃的数据包，进而导致不愉快或不可接受的用户体验。最终，慢数据包就是丢失的数据包。

### 34.3.1.2 信令协议：SIP 和 H.323。

会话初始协议（SIP）是一种用于在用户之间建立交互式多媒体会话的协议。除 VoIP 外，它还用于视频会议和在线游戏。SIP 似乎是建立 VoIP 通话最常见被接受的形式。安全 SIP（SSIP）在第 34.5.1 节中讨论。与 SIP 类似，H.323 可用于视频会议或 VoIP 通话设置。虽然 SIP 似乎是新安装的标准，但在对旧模拟通信设备有大量投资的大型企业级安装中，仍可能发现 H.323 的使用。

简而言之，VoIP 通话的基础包括以下细节。VoIP 客户端应用程序，无论是在个人电脑还是专用手持设备上，都使用 SIP 或 H.323 来建立通话。这种通话设置是控制参数的交换，可能包括要使用的加密和压缩算法。这称为“信令”。一旦通话建立，VoIP 客户端使用 RTP 开始对语音数据进行分包。RTP 数据包被纳入 UDP 数据包中，后者添加寻址和排序信息。UDP 数据包在接收站按序列号收集和排序。一些系统使用“抖动缓冲区”来组装和存储数据包。然后终端 VoIP 客户端读取抖动缓冲区并将 RTP 数据包转换回语音。

## 34.3.2 VoIP 威胁。

虽然不是详尽的列表，但这些攻击代表了使用 VoIP 时可能遇到的一些漏洞：

- 互联网电话垃圾信息（SPIT）
- 窃听
- 服务盗用
- 中间人攻击

### 34.3.2.1 SPIT。

大多数用户已经习惯于每天在收件箱中发现 10 或 20 条（或 100 或 200 条）垃圾邮件。每天收到相同数量的语音邮件的想法导致了令人反感的缩写

问题开始出现。防火墙在将 SIP 流量在互联网之间传递时没有问题，因为 VoIP 设备的内部地址存储在转换表中。然而，SIP 信令传递了用户 VoIP 设备的私有地址。这意味着网络外部的设备试图将 RTP/UDP 音频流发送到一个虚构的 IP 地址。本质上，NAT 阻止了 VoIP 的正常运行。

常用了一些变通方法。有时 NAT 设备可以配置为提供 VoIP 支持。有时 VoIP 设备可以配置为通过其他开放端口工作，占用 HTTP 等常见协议，不幸的是，这通常会产生意想不到的副作用。或者可以在 NAT 的两侧使用 VoIP 代理服务器以促进穿越。每个解决方案各自带来自己的安全问题，应仔细处理；这些问题包括外部代理服务器的后果或在其他协议上创建异常流量，如在占用示例中所述。

## 34.5 加密。

加密在通信安全中发挥着关键作用。有关加密的一般介绍，请参阅本手册第 7 章；有关公钥加密的更多详细信息，请参阅第 37 章。

### 34.5.1 安全 SIP。

传输层安全（TLS）由互联网工程任务组（IETF）发起，用于保护和加密跨越公共网络的数据通信。其目的是取代安全套接层（SSL），成为广泛接受的数据通信安全形式。该协议由“握手”和“记录”组成。TLS 设计为应用程序无关，以便开发人员可以选择自己的方式启动 TLS 会话。

安全 SIP 是一种旨在通过加密的 TLS 通道发送 SIP 信令消息的机制。SSIP 会话由 SIP 客户端联系 SIP 代理并请求 TLS 会话启动。代理返回一个证书，SIP 客户端随后对其进行验证。然后客户端和代理交换该会话的加密密钥。如果通话目的地是另一个网络段，SIP 代理将联系该段并协商顺序 TLS 会话，因此 SIP 消息在整个过程中都受到 TLS 保护。

### 34.5.2 安全实时协议。

安全实时协议（SRTP）是对 RTP 的增强，为 VoIP 音频流提供加密、身份验证和完整性。高级加密标准（AES）最初是一种分组密码；SRTP 将 AES 纳入数据流，其实现方式将其用作流密码。

加密很好，但它并不能保护用户或组织免受重放攻击。SRTP 使用哈希消息认证码（HMAC-SHA1）算法提供身份验证和完整性检查。MAC 是使用加密哈希函数结合私钥计算的。SRTP 使用美国国家安全局设计的五种安全哈希算法（SHA）之一。这五种算法均符合联邦信息处理标准（FIPS）中设定的要求。

### 34.5.3 会话边界控制。

到目前为止，已经确定了影响 VoIP 部署的若干问题。会话边界控制（SBC）是一组服务，解决与安全、QoS、NAT 穿越和网络互操作性相关的 VoIP 问题。SBC 收集实时带宽统计信息，可用于分配维持所需 QoS 所需的网络资源。SBC 还将支持多种 NAT-T 算法，允许呼叫在保持内部资源匿名性的同时被路由到公共网络。同时，SBC 可以同时容纳 SIP 和 H.323。这允许必要的信令协议转换以连接这两种类型的网络。

## 34.6 结语。

VoIP 为企业用户提供了扩展的功能和更低的成本，但管理人员必须将安全考虑集成到所有此类系统的架构和实施中，以防止拦截、欺骗和拒绝服务攻击。此外，技术人员必须监控这一快速变化领域的进展，以了解新的攻击方法和对策。

## 34.7 延伸阅读

- Boyter, B. “Voice-over-IP 嗅探攻击”，2003，www.giac.org/certified_professionals/practicals/gcih/0442.php（网址已失效）。
- Collier, M., and D. Endler. Hacking Exposed 统一通信与 VoIP 安全秘诀与解决方案，2nd ed. McGraw-Hill Osborne Media, 2013.
- Davidson, J., J. Peters, and B. Gracely. Voice over IP 基础. Indianapolis, IN: Cisco Press, 2000.
- Endler, D., and M. Collier. Hacking Exposed—VoIP：Voice Over IP 安全秘诀与解决方案. New York: McGraw-Hill Osborne Media, 2007. 另请参阅相关网站，www.hackingVoIP.com
- Kuhn, D. R., T. J. Walsh, and S. Fries. “VoIP 系统的安全考虑。” NIST Special Publication 800-58, 2005. http://csrc.nist.gov/publications/nistpubs/800-58/SP800-58-final.pdf
- Long, T. “窃听 IP 电话呼叫。” GIAC Security Essentials Certification Practical Assignment, 2002. www.sans.org/reading_room/whitepapers/telephone/318.php
- Miller, W. 无线 Mesh 网络安全：概述. Death and Blind Media, 2013
- Molitor, A. “部署具有 IP 电话应用的动态 Voice over IP 防火墙”，2000. http://cnscenter.future.co.kr/resource/rsc-center/vendor-wp/aravox/aravox_deploying_dynamic.pdf（网址已失效）。
- Molitor, A. “使用特定技术、全面策略和 VoIP 兼容防火墙保护 VoIP 网络”，2000. http://cnscenter.future.co.kr/resource/rsc-center/vendor-wp/aravox/aravox_specifictechniques.pdf（网址已失效）。
- Porter, T., B. Baskin, L. Chaffin, M. Cross, J. Kanclirz, A. Rosela, C. Shim, and A. Zmolek. 实用 VoIP 安全. Rockland, MA: Syngress, 2006.
- Thalhammer, J. “VoIP 电话系统中的安全。” 硕士论文，Institute for Applied Information Processing and Communications at the Graz University of Technology, Graz, Austria, 2002; www.iaik.tugraz.at/teaching/11_diplomarbeiten/archive/thalhammer.pdf（网址已失效）。
- Thermos, P., and A. Takanen. 保护 VoIP 网络：威胁、漏洞和对策. Boston, MA: Addison-Wesley, 2007.
- Verma, P. K., and L. Wang. Voice over IP 网络：服务质量、定价和安全. Springer, 2013.
- VOIP Security Alliance 白皮书：www.voipsa.org/Resources/whitepapers.php
