

![](images/Figure-13.25.jpg)

**图 13.25：** 使用潜艇互换将资金从通道移动到链上

同样的方法可用于通过互换提供商从链上添加资金，只需按相反方向执行上述过程即可。

下面是使用 Lightning Loop 将资金从链上移动到通道我的一侧的示意图：

![](images/Figure-13.26.jpg)

**图 13.26：** 使用潜艇互换将资金从链上移动到通道

# 多路支付或 MPP

闪电网络不适合通过通道网络转移大额价值。这是因为要通过通道网络转移价值，只能选择发送方一侧有足够余额的通道，而大容量通道很少见。因此，如果需要转移大额价值，很难在发送方和接收方之间构建路由。为了克服这个问题，闪电网络软件有时会将价值拆分到多个通道上，并为每个拆分的价值寻找单独的路由。这被称为**多路支付**。

通过下面的插图可以理解这一点：

![](images/Figure-13.27.jpg)

**图 13.27：** 多路支付

在上图中，Alice 想要向 Bob 发送 100 m![](images/Bitcoin.jpg)，但没有可用的路由来转移它。为了实现这一点，Alice 将金额拆分为 20 m![](images/Bitcoin.jpg)、30 m![](images/Bitcoin.jpg) 和 50 m![](images/Bitcoin.jpg)，然后通过不同的路由发送。这样，Bob 就可以在无需进行链上交易的情况下离线接收 100 m![](images/Bitcoin.jpg)。

# 最终用户体验

当我们使用闪电网络支付服务时，我们需要创建一个通道，只要通道的收款方一侧有余额，我们就可以向对等方支付任意多次。

为了发送或接收付款，我们需要在我们的节点和网络中的其他几个节点之间建立通道。这需要通道管理，可能涉及以下活动：

*   创建一个通道，资金在我们这边、对等方那边，或两边都有。
*   创建零确认通道（turbo channels），或等待 3-6 个确认后再接受或发送付款。
*   主动平衡通道，以便既能发送也能接收付款。
*   保持网络拓扑最新，或使用蹦床节点来寻找最佳路由。
*   使用瞭望塔服务以防止被对等方欺骗。
*   协作或单方面关闭通道，并监控比特币区块链上的通道关闭/违约事件。

这看起来可能很吓人，但许多闪电网络钱包在内部处理所有这些事务，用户体验是无缝的。

# 闪电钱包

闪电钱包是比特币钱包，也能开启和管理通道。钱包可能会通过允许用户分配资金和管理通道来赋予用户更多控制权，也可能对用户隐藏所有复杂性，使体验无缝衔接。钱包可能是托管型的，资金由钱包控制，用户只需登录并批准交易。另一方面，在非托管钱包中，创建钱包的种子和密钥掌握在用户手中。

由于闪电钱包正在创建和管理通道，它们也被称为**闪电节点**。

以下是一些流行的闪电钱包：

*Zap 钱包、Muun 钱包、BlueWallet、Breez 钱包、Wallet of Satoshi、Bitcoin Lightning Wallet (BLW)、Éclair Mobile 等。*

# 闪电发票

你已经了解到，当 Alice 从 Bob 那里购买咖啡时，Bob 会生成一个秘密哈希，以便 Alice 进行支付。为了实现这一点，Bolt 11 解释了 Bob 需要与 Alice 共享的消息结构，这被称为闪电发票。

在这里，我们从商户应用程序生成了一个闪电发票，并使用一个开源应用程序对其进行了解码。以下是该应用程序的屏幕截图：

![](images/Figure-13.28.jpg)

**图 13.28：** 闪电发票信息

我们可以看到它包含的所有信息，这将帮助 Alice 创建一笔交易，并通过一个通道发送，付款将通过该通道路由并到达 Bob。

请求的字符串只是 Bob 与 Alice 分享的二维码。所以 Alice 去 Bob 的咖啡店。Bob 通过在手机钱包中显示二维码来请求付款。Alice 用她的手机钱包扫描二维码并进行支付。这在一分钟内就完成了。

以下是闪电网络支付的示意图：

![](images/Figure-13.29.jpg)

**图 13.29：** 闪电网络支付

# LNURL

LNURL 是建立在闪电网络之上的第三层。它更进一步，允许你使用闪电网络创建通道、发送和接收付款，甚至将其用于网站身份验证。

LNURL 支付链接可重复使用，因此不需要在每次购买时重新扫描发票。LNURL 涉及一个服务器，当扫描二维码时，扫描应用程序会联系 LNURL 服务器以执行所需的服务。这样，发票的发送无需用户交互即可发生。

这使得闪电网络不仅可用于支付，还可用于身份验证。LNURL 用于实现一些其他服务，具体请参阅以下 URL：

[https://github.com/fiatjaf/lnurl-rfc](https://github.com/fiatjaf/lnurl-rfc)

LNURL Auth 就是由 LNURL 启用的一项服务，它允许你使用闪电钱包登录网站。

我们将使用以下网站来演示 LNURL Auth：

[https://lightninglogin.live/login](https://lightninglogin.live/login)

以下是 LNURL：

![](images/Figure-13.30.jpg)

**图 13.30：** 用于登录网站的 LNURL Auth

这解码为以下内容：

`lightNING:LNURL1DP68GURN8GHJ7MRFVA58GMNFDENKCMM8D9HZUMRFWEJJ7MR0VA5KU0MTXY7N2WTRX4JNYENXVVMXZVTZV43RWCN9XPSKVDECXY6NWEPHXG6KVCNYXEJRXWRPXVUNSVFK893K2CF5XENRXVNRVEJKVCFSVVURYDPCXCN8GCT884KX7EMFDCSMESJ7`

我们使用一个在线应用程序对其进行解码，获得了以下 URL：

[https://lightninglogin.live/login?k1=59c5e2ffc6a1beb7be0af78157d725fbd6d38a398169cea46f32cfefa0c82486&tag=login](https://lightninglogin.live/login?k1=59c5e2ffc6a1beb7be0af78157d725fbd6d38a398169cea46f32cfefa0c82486&tag=login)

支持 LNURL 身份验证服务的钱包将能够与 LNURL 服务器协调以进行身份验证并登录服务器。简单扫描二维码即可让用户登录网站，他们将不需要任何传统的登录方式。

# 商户集成

闪电网络钱包允许任何实体店只需安装一个移动钱包即可接受付款。对于在线业务，BTCPay 服务器提供了闪电钱包与在线支付网页的轻松集成。BTCPay 是一个开源项目。还有其他的，如 WooCommerce 或 CoinGate，也提供闪电网络集成。

# 社交媒体集成

Twitter 最近与 Strike 钱包集成。截至目前，任何拥有 Strike 钱包的人都可以通过闪电网络通道接收比特币，任何拥有闪电钱包的人都可以发送比特币。这意味着人们可以在全球范围内协作并因服务获得报酬。此外，社会服务组织可以直接联系在暴政政权下工作的人们，通过直接向他们支付比特币来提供帮助。

Telegram 也有闪电网络机器人 `LNTXBOT`，可用于支付或请求付款。

# 交易所采用

一些交易所迅速采用了闪电网络。印度交易所 Zebpay 就是其中之一。全球有许多交易所也支持使用闪电网络将比特币与其他货币或加密货币进行兑换。一些流行的交易所包括 Bitfinex、Strike、OKEx、CashApp、Paxful 等。

