
6. 哪种认证方法基于周期性地请求客户端的哈希值？

7. 攻击模式（aggressive mode）中 IKE 阶段 1 包含几步？

8. PPTP 使用哪种加密算法？

9. WEP 的主要弱点是什么？

10. 哪种 Wi‑Fi 加密协议完全实现 802.11i？

1. Any user or computer to whom tickets can be assigned

2. Pass-the-hash

3. HMAC, SHA1, and SHA2

4. IKE phase 2

5. CHAP and EAP

6. CHAP

7. Three

8. MPPE

9. Reusing initialization vectors

10. WPA2

#### Endnotes

1. D. Downing, M. Covington, and C. Covington, *Dictionary of Computer and Internet Terms*, 10th Ed. (Barron’s Educational Series, 2009).

2. G. Pall and G. Zorn, “Microsoft Point-to-Point Encryption (MPPE) Protocol,” RFC 3078, [www.ietf.org/rfc/rfc3078.txt](http://www.ietf.org/rfc/rfc3078.txt).

3. IVPN, “PPTP vs. L2TP/IPSec vs. OpenVPN,” [www.ivpn.net/pptp-vs-l2tp-vs-openvpn](http://www.ivpn.net/pptp-vs-l2tp-vs-openvpn).

### 15

**Military Applications**

**In this chapter we will cover the following:**

![image](img/image00483.jpeg) NSA and cryptography

![image](img/image00483.jpeg) U.S. cryptography laws

![image](img/image00483.jpeg) How do other nations use cryptography

![image](img/image00483.jpeg) Cryptography and malware

![image](img/image00483.jpeg) The Onion Router

It may seem a bit odd to some readers to include a separate chapter specifically for military applications of cryptography. After all, isn’t the military the primary user of cryptography? Prior to the Internet and the advent of e-commerce, that was undoubtedly true. However, for the past several decades, banks, e-commerce web sites, and individuals sending e-mail or securing their hard drives all use cryptography. In fact, the civilian applications for cryptography are quite numerous. Most of the cryptography I have discussed thus far in this book is used for civilian purposes, although some of it (such as AES and GOST) is also used for military purposes.

In this chapter, we will specifically examine applications of cryptography that are exclusively (or nearly so) the domain of militaries, governments, and intelligence agencies. Although civilian organizations certainly have a need for secure communications, the need is more pressing in military and intelligence applications for two reasons. First, the stakes are much higher. Rather than money being lost or embarrassing data being leaked, lives might be lost. In the event of armed conflict, a breach of security could provide the opponent with a tactical or even strategic advantage. Second, the nature of the persons attempting to breach government security is far more serious. Militaries are not worried about solo hackers or similar threats so much as concerted efforts by trained intelligence personnel to breach their communication systems.

**Note**

- [军事与执法之间的界限有时会模糊，尤其是在处理恐怖组织时。其活动既由执法机构追查，也由军事和情报机构追查。国际犯罪组织同样属于情报机构和执法机构的管辖范围。在本章后半部分，我将讨论一些既属于刑事范畴又属于恐怖主义范畴的项目。]

#### NSA 和密码学

- 要讨论密码学的军事应用，就不可能不提及美国国家安全局（NSA）。在第 2 章中，你读到过 NSA 在冷战时期的简要历史。本节首先讨论 NSA 的现代密码学作用。

* * *

**安全分类**

- 本章中，你会看到标记为“秘密”或“绝密”的项目。理解这些术语的含义很重要。每个国家都有自己的安全分类体系，甚至美国的某些机构也有自己的分类体系。本章使用的术语指的是美国国防部的分类标准。

- 根据美国的分类层级，“秘密”和“绝密”有特定含义。最低分类是*confidential*，即信息若泄露可能会损害国家安全。 *Secret* 信息若泄露可能会造成严重损害国家安全。 *Top secret* 信息若泄露可能会导致特别严重的损害国家安全。此外还有一个等级：*Top Secret SCI*，即 *Sensitive Compartmented Information*。每种清单级别要求的调查程度不同。

- 对于 *secret* 清单，申请人需要进行完整的背景调查，包括刑事记录、工作经历和信用历史，并需向多个国家机构（如国土安全部、移民局、国务院等）进行检查。此类检查称为 National Agency Check with Law and Credit（NACLC）。就业背景调查会覆盖申请人过去七年的生活经历，并可能包括多次体检（polygraph）。

- *top secret* 清单要求更为严格。申请人需要进行 Single Scope Background Investigation（SSBI），这包括对申请人及其配偶的完整 NACL，调查期限至少十年。还需要由受过训练的调查员进行专题面谈。还需直接核实工作经历、受教育情况、出生和国籍，并提供至少四位参考人，其中至少两位会被调查员面谈。还需要进行多次体检。SSBI 每五年重复一次。

- *SCI* 清单仅在完成完整的 SSBI 后才会分配。 SCI 可能有自己的评估访问流程，因此无法提供标准化的说明。

- 在任何清单调查中，若出现问题，调查范围会扩大以解决这些问题。例如，若某项问题涉及申请人的受教育背景，但该教育经历已过去二十年，调查将被扩展以处理此问题。

* * *

##### NSA 加密标准

- 自 NSA 早期成立以来，该局一直负责美国政府的密码学工作。NSA 以两种方式定义密码算法：四种加密产品类型（编号 1 至 4）以及两种算法套件 — — Suite A 和 Suite B。^(1)

> **Note**
>
> 本章讨论的是受限设备和算法，但仅限于公开可得的内容。因此，你可能会发现这里的算法描述比书中前面章节的算法要模糊。出于显而易见的原因，书中无法在公开出版物中提供受限算法的完整描述。

###### Type 1 产品

- Type 1 产品是 NSA 认证用于机密用途的设备。通常包括受限制的硬件和算法，但在某些情况下，受限制硬件可能使用非受限的算法。

- **HAIPE** — — HAIPE（High Assurance Internet Protocol Encryption）设备可使用 Suite A 和 Suite B 算法。它常作为安全网关连接两个站点。HAIPE 本质上是政府增强版的 IPSec。

- HAIPE 基于 IPSec，并加入了若干增强功能。其中一种增强是能够提前共享密钥，从而加密组播数据。IPSec 使用安全关联（SA）建立安全隧道，而 HAIPE 则使用内部安全策略数据库。

- **HAVE QUICK** — — HAVE QUICK 是一种频率跳变算法，最初用于地面与空中 ultra high frequency（UHF）无线电通信。军用无线电通过跳频来规避干扰，使其非常难以被拦截。要使用 HAVE QUICK，双方必须事先同步准确的时间（Time of Day，TOD），并常用 Word of the Day（WOD）作为传输密钥。此外，双方还使用 NET 号来选择特定网络。HAVE QUICK 本身并不提供加密，但常与加密系统配合使用，以实现机密性并防止干扰。

- **SINCGARS** — — Single Channel Ground and Airborne Radio System（SINCGARS）是一套 VHF FM 波无线电，频率范围 30 ~ 87.975 MHz。美国军队及多个其他国家均在使用。它既支持单频模式，也支持频率跳变模式。早期 SINCGARS 设备未内置加密功能，需外接加密模块；后续版本则集成了内置加密单元。

- 产品系列从 1988 年的 RT‑1439 开始，随后还有 RT‑1523G、RT‑1730C（海军专用）以及 RT‑1702G（供步兵携带）。下图展示了其中一个系统示例 Figure 15-1。

![Images](img/image00726.jpeg)

* * *

**FIGURE 15-1    SINCGARS system**

###### Type 2 产品

- Type 2 产品是 NSA 认证用于“敏感但非机密”用途的设备。典型的 Type 2 算法包括 Key Exchange Algorithm（KEA）非对称对数和 Skipjack 块加密；典型的 Type 2 硬件例子包括 Fortezza、CYPRIS 等。

- **Fortezza Plus** — — Fortezza Plus 卡（也称 KOV‑14 卡）是一种 PC 卡，提供密码功能和密钥，用于安全终端设备的语音和数据加密。原始 Fortezza 加密卡包含安全令牌，每位用户均发放配有私钥的 Fortezza 卡，用于访问敏感数据。原始卡片采用 Skipjack 算法。

- Fortezza Plus 采用受限算法，用于安全终端的语音和数据加密。更为现代的改进是 KSV‑21，它向后兼容 Fortezza Plus 卡。下图展示了 Fortezza Crypto CardFigure 15-2。

![Images](img/image00727.jpeg)

* * *

**FIGURE 15-2    Fortezza Crypto Card**

###### Type 3 和 Type 4 产品

- Type 3 产品为非受限（公开）产品。书中迄今讨论的许多算法属于此类，包括数据加密标准（DES）、高级加密标准（AES）以及 SHA 等。

- **Suite A**

Suite A algorithms are unpublished, classified algorithms used for highly sensitive systems. Suite A algorithms include `MEDLEY`, `SAVILLE`, `BATON`, `WALBURN`, `JOSEKI`, and `SHILLELAGH`.

`SAVILLE`    The `SAVILLE` algorithm is often used in voice encryption. Although its details are classified, some indications suggest it may have a 128-bit key.

`BATON`    The `BATON` algorithm is classified. However, the publicly available standard `PKCS#11` has some general information about `BATON`. Public-Key Cryptography Standard (PKCS) 11 defines an API for cryptographic tokens such as those used in smart cards. `BATON` is a block cipher that uses a 128-block with a 320-bit key. It can also be used in electronic codebook (ECB) mode with a 96-bit block.

**Note**

Although this was mentioned earlier in this book, it is worth mentioning again that the NSA using classified documents is not in conflict with Kerckhoffs’s principle. To begin with, the NSA is the largest employer of mathematicians and cryptographers in the world. They can subject an algorithm to internal peer review that is quite exhaustive. Furthermore, Kerckhoffs teaches us that the security of a cryptographic mechanism should depend on only the secrecy of the key, not the secrecy of the algorithm. The key word being *depend*. The Suite A algorithms do not depend on the secrecy of the algorithm for security, but they do add a bit of additional security.

###### Suite B

Suite B algorithms are published, and `AES` is a perfect example of a Suite B.^(2) Suite B includes many algorithms you have already studied in previous chapters, which are all publicly available:

![image](img/image00484.jpeg)   **Advanced Encryption Standard**    If using a 128-bit key, `AES` is considered secure enough for secret information. If using a 256-bit key, `AES` is considered secure enough for top-secret information.

![image](img/image00484.jpeg)   **Elliptic Curve Digital Signature Algorithm** (`ECDSA`)

![image](img/image00484.jpeg)   **Elliptic Curve Diffie-Hellman** (`ECDH`)

![image](img/image00484.jpeg)   **Secure Hash Algorithm 2** (`SHA-2`, 256, 384, and 512)

![image](img/image00484.jpeg)   **Elliptic curve cryptography**    With a 384-bit key, `ECC` is considered secure enough for top-secret information.
