

## 扩展阅读

椭圆曲线密码学是一个迷人而复杂的主题，涉及大量数学知识。我没有讨论一些重要概念，例如点的阶、曲线的余因子、射影坐标、挠点以及求解 ECDLP 问题的方法。如果你对数学感兴趣，可以在 Henri Cohen 和 Gerhard Frey 所著的 *《椭圆与超椭圆曲线密码学手册》*（Chapman and Hall/CRC，2005 年）中找到这些及其他相关主题的信息。Joppe Bos、Alex Halderman、Nadia Heninger、Jonathan Moore、Michael Naehrig 和 Eric Wustrow 在 2013 年发表的综述“实践中的椭圆曲线密码学”也提供了图文并茂的介绍和实际示例（https://eprint.iacr.org/2013/734）。

## 第四部分
## 应用

各种实现已经登上了新闻头条——Heartbleed、BEAST、CRIME 和 POODLE 都是影响了数百万台 Web 服务器的漏洞。

注意：你可能会看到有人将 TLS 称为安全套接字层（SSL），这是其前身的名称。

2013 年，工程师们开始着手开发 TLS 1.3。正如你将在本章中学到的，TLS 1.3 摒弃了不必要和不安全的特性，并用当时最先进的算法取代了旧算法。其结果是更简单、更快且更安全的协议。

在探讨 TLS 1.3 的工作原理之前，我们先回顾一下 TLS 旨在解决的问题以及它存在的原因。

## 目标应用与需求

TLS 是 HTTPS 网站中的 S，浏览器地址栏中出现的挂锁图标表示页面是安全的。创建 TLS 的主要动机是通过对站点进行身份验证并加密流量来保护敏感信息（如个人数据、信用卡号和用户凭证），从而在电子商务或网上银行等应用中实现安全浏览。

TLS 还通过在客户端和服务器之间建立安全通道来帮助保护普遍的基于互联网的通信，确保传输的数据是机密、经过身份验证且未被修改的。

TLS 的安全目标之一是防止中间人攻击，即攻击者截获发送方的加密流量，解密流量以获取明文内容，然后重新加密并发送给接收方。TLS 通过使用证书和受信任的证书颁发机构对服务器（以及可选地对客户端）进行身份验证来阻止这些攻击，我们将在第 258 页的“证书与证书颁发机构”中讨论。

为了被广泛采用，TLS 还需要满足另外四个要求：效率、互操作性、可扩展性和通用性。对于 TLS，效率意味着与未加密连接相比，将性能损失降至最低。这对服务器（降低服务提供商的硬件成本）和客户端（避免可感知的延迟或减少移动设备的电池消耗）都有好处。协议需要具备互操作性，以便能在任何硬件和任何操作系统上运行。它需要可扩展，以便支持额外的特性或算法。而且它必须通用——即不绑定于特定应用。这与传输控制协议（TCP）类似，TCP 并不关心其上层使用的应用协议。

## TLS 协议套件

为了保护客户端与服务器之间的通信，TLS 由若干协议的多个版本组成，形成 TLS 协议套件。TLS 不是传输协议，通常位于传输协议（TCP）和应用层协议（如 HTTP 或 SMTP）之间，以保护通过 TCP 连接传输的数据。

TLS 也可以运行在*用户数据报协议（UDP）*传输协议之上，该协议用于需要对延迟要求极低的“无连接”传输，例如音频或视频流媒体和在线游戏。然而，与 TCP 不同，UDP 不保证传输或数据包的正确排序。因此，TLS 的 UDP 版本——*数据报传输层安全性（DTLS）*略有不同。有关 TCP 和 UDP 的更多信息，请参阅 Charles Kozierok 的 *《TCP/IP 指南》*（No Starch Press，2005 年）。

## TLS 和 SSL 协议家族

TLS 始于 1995 年，当时网景（Netscape）开发了 TLS 的前身——SSL 协议。SSL 远非完美，SSL 2.0 和 SSL 3.0 都存在安全缺陷。你绝不应该使用 SSL，而应始终使用 TLS——令人困惑的是，人们（包括安全专家）经常把 TLS 称为 SSL。

并非所有版本的 TLS 都是安全的。TLS 1.0（1999 年）是最不安全的版本，但它仍然比 SSL 3.0 安全。TLS 1.1（2006 年）好一些，但包含许多弱算法。TLS 1.2（2008 年）更好，但很复杂，只有在正确配置的情况下才能提供高安全性。此外，其复杂性增加了实现中出错的风险以及配置错误的风险。例如，TLS 1.2 支持 CBC 模式下的 AES，该模式常常容易受到填充预言机攻击。

TLS 1.2 从早期 TLS 版本中继承了数十个特性和设计选择，这些使得它在安全性和性能方面并非最优。为了清理这个烂摊子，密码学工程师重新设计了 TLS——只保留好的部分并增加安全特性。结果是 TLS 1.3，一次彻底改进，简化了臃肿的设计，使其更安全、更高效、更简单。从本质上讲，TLS 1.3 是成熟的 TLS。

## TLS 概览

TLS 有两个主要协议：*握手协议*（或简称*握手*）确定双方共享的密钥；*记录协议*描述如何使用这些密钥来保护数据。TLS 处理的数据包称为*记录*。TLS 定义了一种数据包格式，用于封装来自高层协议的数据，以便传输给另一方。

握手从客户端发起与服务器的安全连接开始。客户端发送一条名为 ClientHello 的初始消息，其中包含它想要使用的密码算法的参数。服务器检查此消息及其参数，然后以 ServerHello 消息作为响应。一旦客户端和服务器处理完彼此的消息，它们就可以使用通过握手协议建立的会话密钥来交换加密数据，正如你将在第 263 页的“TLS 握手协议”中看到的那样。

## 证书与证书颁发机构

TLS 握手中最关键的一步，也是 TLS 安全的核心，是*证书验证步骤*，服务器在此步骤中使用证书向客户端进行身份验证。

*证书*本质上是一个公钥，附带该密钥的签名以及相关信息（包括域名）。例如，当连接到 *https://www.google.com* 时，你的浏览器会从某个网络主机接收证书，然后验证该证书的签名，签名内容大致是“我是 *google.com*，我的公钥是 [key]。”如果签名验证通过，该证书及其公钥就是*可信的*，浏览器便会继续建立连接。（有关签名的详细信息，请参阅第 10 章和第 12 章。）

浏览器通过*证书颁发机构（CA）*获知验证签名所需的公钥，该机构本质上是一个硬编码在浏览器或操作系统中的公钥。该公钥对应的私钥（即其签名能力）属于一个受信任的组织，该组织确保其颁发的证书中的公钥归属于声明这些公钥的网站或实体。也就是说，CA 充当*可信第三方*。如果没有 CA，就无法验证 *google.com* 提供的公钥确属 Google，而不是来自某个实施中间人攻击的窃听者。

例如，清单 13-1 展示了当你使用 OpenSSL 命令行工具发起到 *www.google.com* 的 443 端口（用于基于 TLS 的 HTTP 连接（HTTPS）的网络端口）的 TLS 连接时会发生什么。

```text
$ openssl s_client -connect www.google.com:443
CONNECTED(00000003)
---
Certificate chain
 0 s:CN = www.google.com
   i:C = US, O = Google Trust Services LLC, CN = GTS CA 1C3
 1 s:C = US, O = Google Trust Services LLC, CN = GTS CA 1C3
   i:C = US, O = Google Trust Services LLC, CN = GTS Root R1
 2 s:C = US, O = Google Trust Services LLC, CN = GTS Root R1
   i:C = BE, O = GlobalSign nv-sa, OU = Root CA, CN = GlobalSign Root CA
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIEiDCCA3CgAwIBAgIQNjVv7ypW9IQhAa7P69MzzANBgkqhkiG9w0BAQsFADBC
MQswCQYDVQQGEwJVUzEiMCAGA1UEChMZRT2vZ1lFRydXN0IFNlcnZpY2VzIExM
QzETMBEGA1UEAxMKR1RTIENBIFDmAzAeFw0yMzA5MDQwODIzMjJaFw0yNDEwODIz
ODIzMjhaMBkxFzAVBgNVBAMTDnd3dy5nb29nbGUuY29tMRkwFwYDVQQpZCjocaQIYI
KoZIh0NAQ0DgQAgENEMwVAYoTRTboW5ZxbUbX:/Z+EvcEi5OsZQZvP/xyyVIaURm4
AoJer9IJ0/6Iq62oAfDXUgrdBKpSzJzaeFCaqqOCAmg wggJkMA4GA1UdDwEB/wQE
AwIHgDATBgNVHSUEDDAKBggrBgEFBQcDATAMBgNVHRMBAf8EAjAAMB0GA1UdDgQW
BBRnwQnVC8ok1e6YPIbQWjB+XFpPRjAfBgNVHSMEGDAWgBSKdH+vhc3ulc09nNDi
RhTzcTUdJzBqBggrBgEFBQcBAQR eMFwwWyIKwYBBQUHMAKGG2hOdHA6Ly9vY3Nw
LnBra5nb29nL2doczFjMZAxBggrBgEFBQcYB1YhaHR0cDovL3Bra5Sn b29nL3Jl
cG8yV2YvdHMvZ3RwMzlzLmRlciJAZBgNVHREEGDAWggR5d3d3Lm google.com
BgNVHSAEGjAYMAgG BmeDBAECATAMBgorBgEEAdZ5AgUDMwGA1UdHwQ1MDMwMaAv
-----END CERTIFICATE-----
```

