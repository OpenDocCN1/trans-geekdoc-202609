

本章讨论了传输安全空间中的三个具体问题：验证数据、保护数据不被检查以及保护用户隐私。对于网络工程师而言，了解传输安全的工作原理以及传输安全系统中的薄弱点如何与网络设计相互作用的理论，往往比了解实际安全机制的细节更为重要。正因如此，本章的重点在于提供更坚实的理论基础，即“如何思考传输安全”，而不是传输安全的实际实现。对传输安全感兴趣并希望更深入探索的读者，建议查阅本章末尾的“Further Reading”部分。

总体而言，传输安全只是网络工程所需整体安全中的一小部分；[第 21 章](#ch21.xhtml#ch21)，“[Security: A Broader Sweep](#ch21.xhtml#ch21)”，从网络和系统两个层面探讨了更广泛的安全主题。

### Further Reading

Bauer, Kevin, Damon McCoy, Dirk Grunwald, Tadayoshi Kohno, and Douglas Sicker. “Low-Resource Routing Attacks Against Tor.” In *Proceedings of the 2007 ACM Workshop on Privacy in Electronic Society*, 11–20. WPES ’07. New York, NY, USA: ACM, 2007. doi:10.1145/1314333.1314336.

Brockners, Frank, Shwetha Bhandari, Sashank Dara, Carlos Pignataro, John Leddy, Stephen Youell, David Mozes, and Tal Mizrahi. “Proof of Transit.” Internet-Draft. Internet Engineering Task Force, March 2017. [https://datatracker.ietf.org/doc/html/draft-brockners-proof-of-transit-03](https://datatracker.ietf.org/doc/html/draft-brockners-proof-of-transit-03).

Davies, Joshua. *Implementing SSL / TLS Using Cryptography and PKI*. 1st edition. Hoboken, NJ: Wiley, 2011.

Ducklin, Paul. “What Your Encrypted Data Says about You.” *Naked Security*, March 18, 2016. [https://nakedsecurity.sophos.com/2016/03/18/what-your-encrypted-data-says-about-you/](https://nakedsecurity.sophos.com/2016/03/18/what-your-encrypted-data-says-about-you/).

Ferguson, Niels, and Bruce Schneier. *Practical Cryptography*. 1st edition. New York: Wiley, 2003.

Ferguson, Niels, Bruce Schneier, and Tadayoshi Kohno. *Cryptography Engineering: Design Principles and Practical Applications*. 1st edition. Indianapolis, IN: Wiley, 2010.

Katz, Jonathan, and Yehuda Lindell. *Introduction to Modern Cryptography*. 2nd edition. Boca Raton, FL: Chapman and Hall/CRC, 2014.

Kaufman, Charlie, Paul E. Hoffman, Yoav Nir, Pasi Eronen, and Tero Kivinen. *Internet Key Exchange Protocol Version 2 (IKEv2)*. Request for Comments 7296. RFC Editor, 2014. doi:10.17487/RFC7296.

Matte, Célestin, Mathieu Cunche, Franck Rousseau, and Mathy Vanhoef. “Defeating MAC Address Randomization Through Timing Attacks.” In *Proceedings of the 9th ACM Conference on Security #38; Privacy in Wireless and Mobile Networks*, 15–20. WiSec ’16. New York, NY: ACM, 2016. doi:10.1145/2939918.2939930.

Narayanan, Arvind, Joseph Bonneau, Edward Felten, Andrew Miller, and Steven Goldfeder. *Bitcoin and Cryptocurrency Technologies: A Comprehensive Introduction*. Princeton, NJ: Princeton University Press, 2016.

Paar, Christof, Jan Pelzl, and Bart Preneel. *Understanding Cryptography: A Textbook for Students and Practitioners*. 1st edition. Heidelberg; New York: Springer, 2010.

Piper, Fred, and Sean Murphy. *Cryptography: A Very Short Introduction*. 1st edition. Oxford; New York: Oxford University Press, 2002.

Rescorla, Eric, and Tim Dierks. *The Transport Layer Security (TLS) Protocol Version 1.2*. Request for Comments 5246. RFC Editor, 2008. doi:10.17487/RFC5246.

Schneier, Bruce. *Applied Cryptography: Protocols, Algorithms and Source Code in C*. 1st edition. Indianapolis, IN: Wiley, 2015.

Shimeall, Tim. “Traffic Analysis for Network Security: Two Approaches for Going Beyond Network Flow Data.” *SEI Blog*, September 16, 2016. [https://insights.sei.cmu.edu/sei_blog/2016/09/traffic-analysis-for-network-security-two-approaches-for-going-beyond-network-flow-data.html](https://insights.sei.cmu.edu/sei_blog/2016/09/traffic-analysis-for-network-security-two-approaches-for-going-beyond-network-flow-data.html).

Silva, John Edward. “An Overview of Cryptographic Hash Functions and Their Uses.” SANS Institute, January 15, 2013. [https://www.sans.org/reading-room/whitepapers/vpns/overview-cryptographic-hash-functions-879](https://www.sans.org/reading-room/whitepapers/vpns/overview-cryptographic-hash-functions-879).

Sobers, Rob. “The Definitive Guide to Cryptographic Hash Functions (Part 1).” *Varonis Blog*, August 2, 2012. [https://blog.varonis.com/the-definitive-guide-to-cryptographic-hash-functions-part-1/](https://blog.varonis.com/the-definitive-guide-to-cryptographic-hash-functions-part-1/).

———. “The Definitive Guide to Cryptographic Hash Functions (Part II).” *Varonis Blog*, August 14, 2012. [https://blog.varonis.com/the-definitive-guide-to-cryptographic-hash-functions-part-ii/](https://blog.varonis.com/the-definitive-guide-to-cryptographic-hash-functions-part-ii/).

Stallings, William. *Cryptography and Network Security: Principles and Practice*. 7th edition. Boston, MA: Pearson, 2016.

Vanhoef, Mathy, Célestin Matte, Mathieu Cunche, Leonardo S. Cardoso, and Frank Piessens. “Why MAC Address Randomization Is Not Enough: An Analysis of Wi-Fi Network Discovery Mechanisms.” In *Proceedings of the 11th ACM on Asia Conference on Computer and Communications Security*, 413–24. ASIA CCS ’16. New York, NY: ACM, 2016. doi:10.1145/2897845.2897883.

### Review Questions

1. 中间人攻击被视为一个主要的安全弱点，但在许多情况下，系统被有意放置在加密数据流的路径中。中间的系统充当代理，在数据通过系统时对其进行解密和重新加密。找出这种系统的至少一个用例，并解释此类系统的积极和消极方面。

2. 作为数据残留的一个例子，研究网络浏览器指纹的概念。描述该概念、其准确性以及可用的缓解措施。

3. 哈希和加密算法有很多相似之处，也有一些不同之处。描述这些相似之处和不同之处。

4. 找到至少一种使用多轮加密的加密系统。为什么选择这个轮数？加密系统是否建议为更高安全性使用更多轮数？

5. 近年来，公证人的概念变得更难设计和实现。描述此类系统可能面临的一些挑战，以及这些挑战可能如何克服。

6. MAC 地址随机化在 IPv4 和 IPv6 中的实现是否不同？有哪些不同之处，为什么存在这些差异？

7. 调查 IPsec。它与 TLS 有何不同？它在协议栈的哪一层进行加密，可用的操作模式有哪些？

# PART II
## The Control Plane

构建单个数据包处理设备\[md\]路由器（或第三层交换机，现在通常仅称为交换机，这让几乎所有人都感到困惑）是最常见的例子\[md\]一直是到目前为止的重点。现在是时候开始连接路由器了。考虑 [Figure P2-1](#part2.xhtml#p2fig01) 中的网络。

![Image](graphics/p2fig01.jpg)

**Figure P2-1** *Topology Discovery*

运行在主机 A 上的应用程序需要从运行在 F 上的进程获取一些信息。设备 B、C、D 和 E 当然是数据包处理器（路由器）。为了在主机 A 和 F 之间转发数据包，路由器 B 将被要求转发数据包到 F，即使它未连接到 F；同样，路由器 C 和 D 将需要转发数据包到 A 和 F，即使它们也未连接到这两个主机。

