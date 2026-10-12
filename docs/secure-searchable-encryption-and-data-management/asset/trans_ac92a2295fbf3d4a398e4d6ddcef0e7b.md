

## FSG2^+

Fang 等人 [[36]](#03chap_03.xhtml#ref3_36) 提出了一种 PEKS 变体，其特点是不需要安全信道，并且还提供了抗 KGA（关键字猜测攻击）的安全性。在早期的方案中也实现了相同的目标，但它们需要随机预言机模型来证明其方案的安全性。而该方案则在标准模型下被证明是安全的。他们使用了 Gentry 的 IBE 方案 [[30]](#03chap_03.xhtml#ref3_30) 作为构建的底层加密技术。

## LLZ^+

最近，Lu 等人 [[37]](#03chap_03.xhtml#ref3_37) 提出了一种基于证书密码学和签密的可搜索公钥加密，以提供抗 KGA 安全性，同时消除了接收者与服务器之间对安全信道的需求。该方案不需要安全信道，也提供了抗 KGA 安全性。所提方案也在标准模型下被证明是安全的。

上述讨论方案的存储和计算成本的比较分析见 [表 3.3](#03chap_03.xhtml#tbl3_3)。

### 表 3.3 PEKS 及其扩展的存储和计算成本比较分析

| 方案 | 存储成本 | 计算成本 |
| --- | --- | --- |
| **PEKS: Boneh 等人** [[24]](#03chap_03.xhtml#ref3_24) | 加密索引：`1|G| + |{0,1}^(λ)|` | `1P + 2E + 2H` |
|  | 陷门：`1|G|` | `1E + 1H` |
|  | 搜索 | `1P + 1H` |
| **无安全信道 (SCF) PEKS** |  |  |
| **Baek 等人** [[27]](#03chap_03.xhtml#ref3_27) | 加密索引：`1|G| + |{0,1}^(λ)|` | `1P + 1E + 1E[T] + 2H` |
|  | 陷门：`1|G|` | `1E + 1H` |
|  | 搜索 | `1P + 2E + 1H` |
| **Gu 等人** [[28]](#03chap_03.xhtml#ref3_28) | 加密索引：`1|G| + |{0,1}^(λ)|` | `3E + 2H` |
|  | 陷门：`1|G|` | `1E + 1H` |
|  | 搜索 | `1P + 1H` |
| **Fang 等人** [[29]](#03chap_03.xhtml#ref3_29) | 加密索引：`2|G| + 2|G[T]|` | `3P + 3E + 3E[T] + 1H` |
|  | 陷门：`1|G| + 1|Z[p]|` | `2E` |
|  | 搜索 | `2P + 2E + 2E[T] + 1H` |
| **Rhee 等人** [[31]](#03chap_03.xhtml#ref3_31) | 加密索引：`1|G| + |{0,1}^(λ)|` | `7P + 2E + 2H` |
|  | 陷门：`1|G|` | `1E + 1H` |
|  | 搜索 | `1P + 1E + 1H` |
| **抗 KGA 的 PEKS** |  |  |
| **Tang 和 Chen** [[34]](#03chap_03.xhtml#ref3_34) | 加密索引：`1|G| + 1|G[T]|` | `1P + 2E` |
|  | 陷门：`1|G|` | `1E + 1H` |
|  | 搜索 | `1P` |
| **具有 KGA 安全性的 SCF-PEKS** |  |  |
| **Rhee 等人** [[35]](#03chap_03.xhtml#ref3_35) | 加密索引：`1|G| + |{0,1}^(λ)|` | `1P + 2E + 2H` |
|  | 陷门：`2|G|` | `3E + 2H` |
|  | 搜索 | `1P + 2E + 2H` |
| **Fang 等人** [[36]](#03chap_03.xhtml#ref3_36) | 加密索引：`|VK| + 1|G[1]| + 2|G[2]| + 2|G[T]| + |σ|` | `3P + 8E + 1H + 1𝒮` |
|  | 陷门：`1|G[1]| + 1|Z[p]|` | `1E` |
|  | 搜索 | `4P + 2E + 1E[T] + 1H + 1V` |
|  | 陷门：`1|G|` | `3E + 2H` |
|  | 搜索 | `1P + 1E[T] + 1H` |
| **Lu 等人** [[37]](#03chap_03.xhtml#ref3_37) | 加密索引：`1|G| + |{0,1}^(λ)|` | `1P + 3E + 1E[T] + 3H` |
|  | 陷门：`1|G|` | `3E + 2H` |
|  | 搜索 | `1P + 1E[T] + 1H` |

[表 3.3](#03chap_03.xhtml#tbl3_3) 中使用的符号见 [表 3.4](#03chap_03.xhtml#tbl3_4)。

### 表 3.4 比较分析中使用的符号及其说明

| 符号 | 说明 |
| --- | --- |
| `|G|`, `|G[T]|` | 对称双线性配对情况下，源群 (`G`) 和目标群 (`G[T]`) 元素的长度 |
| `|G[1]|`, `|G[2]|`, `|G[T]|` | 非对称双线性配对情况下，源群 (`G[1]`,`G[2]`) 和目标群 (`G[T]`) 元素的长度 |
| `|σ|` | 签名的长度 |
| `|VK|` | 验证密钥的长度 |
| `|{0,1}^(λ)|` | 长度为 `λ` 的二进制串，其中 `λ` 是特定方案的安全参数 |
| `|Z[p]|` | 素数阶 `p` 的整数群中元素的长度 |
| `|F[p]|` | 素数阶 `p` 的域中元素的长度 |
| `P` | 双线性配对运算 |
| `E`, `E[T]` | 源群和目标群中的指数运算 |
| `H` | 抗碰撞单向哈希函数 |
| `𝒮` | 签名运算 |
| `V` | 验证运算 |
| `Poly`, `k` | 次数为 `k` 的多项式 |

存储成本按大小和群元素数量计算。我们仅考虑加密算法和陷门算法的存储成本，因为在这些算法中我们需要存储其输出，即云服务器上的密文和用户设备上的陷门；搜索算法不计算此类成本。计算成本按算法执行的操作数量计算。搜索算法也计算在内。算法可能执行不同类型的操作，如哈希运算、指数运算、配对运算；其中配对运算开销最大。因此，我们应尽量构建配对运算次数为常数的方案。如果在搜索算法中能使配对运算次数为常数，则称该可搜索加密方案支持快速搜索。

## 3.4 章节小结

本章正式介绍了可搜索加密的概念，明确阐述了此类技术的必要性，以及如何利用该技术解决在不破坏机密性的前提下，从加密数据中实现机密性保护和期望信息的高效检索问题。我们还根据底层加密技术讨论了可搜索加密的两大类别，并探讨了这两类中的开创性工作。此外，还努力阐明在何种场景下，哪种底层加密技术能为用户提供更多益处。

# 参考文献

1.  J. Wu, L. Ping, X. Ge, Y. Wang, and J. Fu, "Cloud storage as the infrastructure of cloud computing," in *2010 International Conference on Intelligent Computing and Cognitive Informatics*, 2010, pp. 380–383.
2.  A. Omezzine, N. B. Ben Saoud, S. Tazi, and G. Cooperman, "Adaptive and concurrent negotiation for an efficient cloud provisioning," Int. J. High Perform. Comput. Netw, vol. 15, no. 3–4, pp. 145–157, 2019.
3.  K. Ren, C. Wang, and Q. Wang, "Security challenges for the public cloud," IEEE Internet Comput, vol. 16, no. 1, pp. 69–73, 2012.
4.  R.-C. Ziebell, J. Albors-Garrigos, K.-P. Schoeneberg, and M. R. P. Marin, "Adoption and success of e-HRM in a cloud computing environment: A field study," Int. J. Cloud Appl. Comput, vol. 9, no. 2, pp. 1–27, 2019.
5.  H. Vahdat-Nejad, S. O. Eilaki, and S. Izadpanah, "Towards a better understanding of ubiquitous cloud computing," Int. J. Cloud Appl. Comput, vol. 8, no. 1, pp. 1–20, 2018.
6.  P. Priyadarshinee, "Cloud computing adoption: Scale development, measurement and validation," Int. J. Cloud Appl. Comput, vol. 8, no. 1, pp. 97–116, 2018.
7.  R. L. Krutz, and R. D. Vines, *Cloud Security: A Comprehensive Guide to Secure Cloud Computing*. Wiley Publishing, 2010.
8.  O. O. Olakanmi, and A. Dada, "An efficient privacy-preserving approach for secure verifiable outsourced computing on untrusted platforms," Int. J. Cloud Appl. Comput, vol. 9, no. 2, pp. 79–98, 2019.
9.  S. Kaushik, and C. Gandhi, "Ensure hierarchal identity based data security in cloud environment," Int. J. Cloud Appl. Comput, vol. 9, no. 4, pp. 21–36, 2019.

