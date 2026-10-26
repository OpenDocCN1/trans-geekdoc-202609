

其他攻击包括*女巫攻击*和*日蚀攻击*。在*女巫攻击*中，攻击者试图通过加入伪造节点来控制部分网络，这由一组节点完成。在*日蚀攻击*中，受害节点被攻击者从公共网络中隔离，受害节点所连接的IP地址被路由到攻击者的地址。研究表明，篡改网络节点可以造成网络拥塞，从而诱发网络上的其他多种攻击。

### 2.12 保障比特币网络安全

为保护比特币网络免受前述安全威胁，本节提出了多种应对措施。

为了应对*分布式拒绝服务（DDoS）攻击*，Johnson等人[15]提出了一种基于博弈的方法，让矿池通过提高计算成本相互竞争。通过该方法得出，较大的矿池比较小的矿池能获得更多激励。Eyal[16]也采用了类似的博弈方法，并指出较大的矿池通过网络中的自私行为获取了大部分激励。Bentov等人[17]提出了一种活动证明（PoA）协议来解决DDoS攻击。解决DDoS攻击的另一种方法是使用任意用户自定义的Web服务或像TOR这样的浏览器持续监控网络流量。

*时间劫持*是一种可能将网络分割成多个部分的致命攻击。为克服时间劫持攻击，提出了一系列技术，包括：(i) 为确定区块时间戳的上限，应使用系统时间而非网络时间；(ii) 应严格遵循可能的时间尺度；(iii) 应只使用受信任的对等节点。

为避免*日蚀攻击*，受信任节点的IP地址被单独存储。连接节点时基于节点的信任因素，任何恶意节点都会被禁止加入网络。有建议指出，对支付请求消息稍作修改即可降低退款攻击的概率。支付请求消息应添加一些客户信息，如注册邮箱、产品信息或送货地址。每个支付请求都有一个与密钥关联的唯一支付地址，该密钥将用于退款。然而，添加客户信息可能会损害用户隐私。Andrychowicz等人[18]提出了一种名为“新存款协议”的解决方案来应对*可塑性攻击*。建议将交易签名保存在单独的Merkle树中。

一般来说，由于担心恶意活动造成损失，大额比特币交易不会直接进行。在这种情况下，这些交易被拆分成多笔较小的交易，由于网络必须验证多笔交易，这最终会延迟完成过程。因此，为减少这种延迟，建议通过离线交易进行支付，即所谓的“微支付”。微支付通过一个名为“微支付通道”的单独通道进行。这些通道是比特币网络本身的一部分，但却是交易对手方进行交易的专用手段。

当对等节点在声明新区块的同时广播挖掘该区块所花的时间，*篡改攻击*就可以解决。这将使网络中的其他对等节点计算挖掘一个区块所需的平均时间。通过这种方式，可以确保网络中不会发生时间戳篡改或不必要的延迟。

除上述解决方案外，结合网络流量使用反洗钱（AML）法规和了解你的客户（KYC）政策，也能提高挖矿过程的质量。

## 结论

在比特币中，只需使用非结构化的P2P网络即可实现网络各部分之间的数据共享。比特币网络的安全性依赖于基于PoW的共识协议的效率，这些协议使区块链能够保持一致的状态。区块链的不一致性若被恰当利用，可能导致有效的双重支付。因此，比特币网络在规模、存储和带宽方面保持可扩展性非常重要，因为这能强化共识协议。全节点在P2P网络中处于活跃状态，有助于数据分发。相反，轻客户端使用SPV执行交易。但事实上，该网络仍然存在非结构化接口的普遍可扩展性问题，以及比特币协议本身所引发的问题。

## 参考文献

- 1. S. Nakamoto, “Bitcoin: A peer-to-peer electronic cash system,” Technical Report, 2008 [Online]. Available: https://bitcoin.org/bitcoin.pdf.
- 2. Bitcoin. “Bitcoin developer documentation.” 2014 [Online]. Available: https://bitcoin.org/en/developer-documentation.
- 3. github.com/freewil/bitcoin-testnetbox
- 4. A. Miller et al., “Discovering bitcoin’s public topology and influential nodes,” Technical Report, May 2015 [Online]. Available: https://cs.umd.edu/projects/coinscope/coinscope.pdf.
- 5. T. Bamert, C. Decker, L. Elsen, R. Wattenhofer, and S. Welten, “Have a snack, pay with bitcoins,” in Proc. 13th IEEE Int. Conf. Peer Peer Comput. (P2P’13), September 2013, pp. 1–5.
- 6. D. Kaminsky. “Black OPS of TCP/IP, Black Hat USA.” August 2011.[Online]. Available: http://dankaminsky.com/2011/08/05/bo2k11/.
- 7. P. Koshy, D. Koshy, and P. McDaniel, “An analysis of anonymity in bitcoin using P2P network traffic,” in Proc. Financial Cryptography and Data Security: 18th Int. Conf., FC 2014, March 2014, pp. 469–485.
- 8. R. Dingledine, N. Mathewson, and P. Syverson, “Tor: The second-generation onion router,” in Proc. 13th USENIX Secur. Symp. (USENIX Security’04), August 2004, pp. 303–320.
- 9. S. T. Ali, P. McCorry, P. H.-J. Lee, and F. Hao, “Zombiecoin: Powering next-generation botnets with bitcoin,” in Proc. 2nd Workshop Bitcoin Res. (BITCOIN’15), January 2015, pp. 34–48.
- 10. Vinced. “Namecoin—A distributed naming system based on bitcoin.” April 2011. [Online]. Available: https://bitcointalk.org/index.php?topic=6017.0.
- 11. J. Warren, “Bitmessage: A peer-to-peer message authentication and delivery system,” Technical Report, November 2012 [Online]. Available: https://bitmessage.org/bitmessage.pdf.
- 12. J. Szefer and R. B. Lee, “Bitdeposit: Deterring attacks and abuses of cloud computing services through economic measures,” in Proc. 13th IEEE/ACM Int. Symp. Cluster Cloud Grid Comput. (CCGRID’13), May 2013, pp. 630–635.
- 13. A. Schwartz. “Squaring the triangle: Secure, decentralized, human-readable names,” January 2011 [Online]. Available: http://www.aaronsw.com/weblog/squarezooko
- 14. M. Apostolaki, A. Zohar, and L. Vanbever, “Hijacking Bitcoin: Routing attacks on cryptocurrencies,” in Proc. IEEE Symp. Security Privacy (SP), San Jose, CA: IEEE, 2017, pp. 375–392.
- 15. B. Johnson, A. Laszka, J. Grossklags, M. Vasek, and T. Moore, “Gametheoretic analysis of DDoS attacks against Bitcoin mining pools,” in Proc. Financ. Cryptography Data Security FC Workshops BITCOIN WAHC, Heidelberg, Germany: Springer, 2014, pp. 72–86.
- 16. I. Eyal, “The miner’s dilemma,” in Proc. IEEE Symp. Security Privacy (SP), San Jose, CA: IEEE Comput. Soc., 2015, pp. 89–103.
- 17. I. Bentov, C. Lee, A. Mizrahi, and M. Rosenfeld, “Proof of activity: Extending Bitcoin’s proof of work via proof of stake [extended abstract],” SIGMETRICS Perform. Eval. Rev., vol. 42, no. 3, pp. 34–37, December 2014.
- 18. M. Andrychowicz, S. Dziembowski, D. Malinowski, and Ł. Mazurek, “On the malleability of Bitcoin transactions,” in Proc. Financ. Cryptography Data Security FC Int. Workshops BITCOIN, WAHC, Wearable, Heidelberg, Germany: Springer, 2015, pp. 1–18.

![](img/115a7d47166d21dfa1d1dc5986da244b_54_0.png)

## 3 区块链技术

### *免信任系统*

*Sathya A.R.*  
ICFAI Foundation for Higher Education  
(Deemed to be University)

*Ajay Kumar Jena*  
KIIT (Deemed to be University)

### 目录

- 3.1  引言 ........................................................................................................ 38
- 3.2  历史 .................................................................................................................... 38
- 3.3  区块链技术概述 ........................................................................ 39
  - 3.3.1  区块的结构 .......................................................................................... 40
  - 3.3.2  创世区块 .............................................................................................. 42
- 3.4  区块链的类型 .................................................................................................. 43
  - 3.4.1  公有区块链 ............................................................................................... 43
  - 3.4.2  私有区块链 .............................................................................................. 43
  - 3.4.3  联盟区块链 ....................................................................................... 44
- 3.5  区块链的性质 ............................................................................................ 44
  - 3.5.1  去中心化 ....................................................................................................... 44
  - 3.5.2  透明性 .......................................................................................................... 45
  - 3.5.3  不可篡改性 ............................................................................................................. 45
  - 3.5.4  持久性 ........................................................................................................... 45
  - 3.5.5  匿名性 ............................................................................................................. 45
  - 3.5.6  可审计性 ............................................................................................................ 45
- 3.6  交易与数字签名 ............................................................................. 45
- 3.7  Merkle树 ................................................................................................................. 46
- 3.8  SHA-256 ...................................................................................................................... 47
- 3.9  区块链如何工作 ................................................................................................ 47
- 3.10  区块链开源实现 ......................................................................... 48
  - 3.10.1  比特币 .................................................................................................................. 49
  - 3.10.2  以太坊 .............................................................................................................. 49
  - 3.10.3  超级账本 .......................................................................................................... 49
  - 3.10.4  Corda ................................................................................................................... 50
- 3.11  测试网 ....................................................................................................................... 50
  - 3.11.1  持续发展 .................................................................................... 50
  - 3.11.2  防止中断 ........................................................................................... 50
- 3.12  支付验证 .................................................................................................. 51

