

求解并求斜率：

$s = \begin{cases} \dfrac{y_2 - y_1}{x_2 - x_1} \mod p & \text{if } P \neq Q & \text{Addition} \\ \dfrac{3x_1^2 + a}{2y_1} \mod p & \text{if } P = Q & \text{Doubling} \end{cases} \tag{6.21}$

**注意：** 这是 ECC 遵循的最重要属性之一，该结果将在寻找密钥时使用。

## ECC 的工作原理

### 第一阶段：设置

- 1. Alice 和 Bob 约定共同的 ECC 方程，假设为：
- $E: y^2 = x^3 + a x + b,$
- 以及该曲线上的素元 $(x_p, y_p)$

### 第二阶段：协议

- 1. Alice 生成其私钥： $a = K_{pr A} \in \{2,3,\dots,\#E -1\}$ 其中 $E$ 为群的基数。
- 2. Bob 生成其私钥： $b = K_{pr B} \in \{2,3,\dots,\#E -1\}$ 其中 $E$ 为群的基数。
- 3. Alice 和 Bob 使用以下方法生成其公钥：
- $A = K_{\text{pub }A} = a.P = (x_A, y_A) \tag{6.22}$
- $B = K_{\text{pub }B} = b.P = (x_B, y_B) \tag{6.23}$
- 4. 现在 Alice 和 Bob 将生成：
- $a.B = (X_{AB}, Y_{AB}) \tag{6.24}$
- $b.A = (X_{AB}, Y_{AB}) \tag{6.25}$
- 5. 消息 m 假设为视频，可以通过 AES 使用 $X_{AB}$ 作为密钥进行加密。
- $$C = AES_{X_{AB}}(m) \tag{6.26}$$
- 6. 解密将使用相同的 $X_{AB}$ 进行
- $$m = AES^{-1}_{X_{AB}}(C) \tag{6.27}$$

**注意：** 对于计算 $a.P$、$b.P$、$a.B$ 和 $b.A$，我们将使用公式 6.21。

## 6.3.1 ECC 相对于 RSA 的优势

以下为 ECC 相对于 RSA 的优势。

### 6.3.1.1 安全性

子指数攻击在 RSA 中被识别出来，这是因为其加法运算的快速计算。在 ECC 中，由于点加法计算成本高，难以进行子指数攻击。因此，使 RSA 密钥对安全所需的位数相对于使 ECC 密钥配对安全所需的位数呈指数增长。Jurisic 和 Menezes [46] 研究表明，要使 RSA 安全，需要 1024 位模数，而 ECC 仅需 160 位模数（表 6.6）。

表 6.6 RSA 和 ECC 的密钥大小与破解时间比较

| RSA 密钥大小（位） | ECC 密钥大小（位） | 破解时间（MIPS-年） |
|---|---|---|
| 512 | 106 | $10^4$ |
| 768 | 132 | $10^8$ |
| 1024 | 160 | $10^{11}$ |
| 2048 | 210 | $10^{20}$ |
| 21000 | 600 | $10^{78}$ |

### 表 6.7 RSA 和 ECC 比较

| 功能 | ECC-163 位（毫秒） | RSA-1024 位（毫秒） |
|---|---|---|
| 密钥生成 | 3.8 | 4708.3 |
| 签名 | 2.1(ECNRA) | 228.4 |
|  | 3.0(ECDSA) |  |
| 验证 | 9.9(ECNRA) | 12.7 |
|  | 10.7(ECDSA) |  |

### 6.3.1.2 空间

由于 ECC 在密钥尺寸较小的情况下可提供类似 RSA 的安全性，因此芯片上的晶体管数量也比芯片上 RSA 加密系统少。然而，两个 SoC（片上系统）的带宽消耗将相同，但对于较短的消息；ECC SoC 因其速度快而表现更好。

### 6.3.1.3 效率

ECC 和 RSA 可以通过在 RSA 中使用较小的指数来加快运行速度，这会直接影响其安全性，或通过在 ECC 中预先存储结果来加快运行速度，这会直接影响空间需求。ECC 背后的公司 Certicom 研究了快速 ECC 和改进 RSA 的影响（表 6.7）。

## 练习

练习 6.1：Hill 密码——一种多字母替换密码，使用 Z₂₆ 中的 m × m 可逆矩阵作为密钥。Hill 密码包含两个步骤：
步骤 1：将消息编码为 m 个 Z₂₆ 整数的序列块。
步骤 2：分别使用与秘密矩阵的乘积加密每个块。

使用已知明文攻击恢复以下消息的 m 和秘密密钥。
消息：conversation
加密消息：HIARRTNUYTUS

练习 6.2：维吉尼亚密码——一种多字母表替换密码，使用字母密钥加密消息。使用维吉尼亚密码，用密钥“books”加密单词“knowledge”。

练习 6.3：数据加密算法（DES）——一种用于电子数据加密的对称密钥算法。DES 有多种操作模式，如 ECB、CFB、CBC、OFB，这些模式在从明文块生成密文块方面有所不同。详细解释所有模式，并为每种模式绘制加密和解密的框图。

练习 6.4：证明如果对手可以替换一个密文块，则 b_i 和 b_{i+1} 的解密保持不变，而其余块的解密会发生变化。

练习 6.5：并非所有 DES 密钥都是强密钥。如果 DES_k 是对合，则存在弱密钥，其中 k 为密钥。给出 DES 的四个弱密钥。

练习 6.6：图像分割使用不同类型的算子来识别图像中的边缘。写出每个算子的优缺点，并说明特定算子使用的条件。

练习 6.7：写出图像中块选择和像素选择技术的优缺点。

练习 6.8：写出空间域图像加密技术和频域技术使用的条件。给出一些支持你答案的现实生活例子。

练习 6.9：写出在两点之间传输监控视频所需的步骤。包括视频的加密、传输和解密步骤。对以下两种场景使用的技术给出适当的理由：
场景 1：监控视频先完全存储然后传输（非实时）。
场景 2：监控视频加密后实时传输，无中间数据存储单元。

练习 6.10：ECC 相对于 RSA 有各种优势，包括小密钥尺寸的鲁棒性、更快的密钥生成等。讨论 ECC 相对于 RSA 的缺点，并给出一些支持你答案的例子。

## 参考文献

- 1. Ibn Wahshiyya 对古埃及象形文字字母的翻译。 [online]. 可用： https://en.wikipedia.org/wiki/Egyptian_hieroglyphs#/media/File:Ibn_Wahshiyya%27s_985_CE_translation_of_the_Ancient_Egyptian_hieroglyph_alphabet.jpg （访问日期 2017 年 10 月 30 日）。
- 2. A. A. Soofi, I. Riaz, 和 U. Rasheed, 用于数据安全增强的维吉尼亚密码, Int. J. Sci. Technol. Res., 5(3), 141–145, 2016.
- 3. B. A. Mohammed Haris, Playfair 密码不同修改的综述论文, Int. J. Adv. Res. Comput. Sci., 8(5).
- 4. M. Rahman, A. Nordin, A. F. A. Abidin, 和 M. K. Yusof, 密码学：经典 Hill 密码的新方法, Int. J. Secur. Appl., 7(2), 179–190, 2013.
- 5. V. Laforet, 《霍比特人》。 [online]. 可用： https://gizmodo.com/5969817/the-hobbit-an-unexpected-masterclass-in-why-48-fps-fails.
- 6. K. Jalesh 和 S. Nirmala, 增强图像信息内容安全性的混合方法, 收录于 Multimedia Processing, Communication and Computing Applications: Proceedings of the First International Conference, ICMCCA, 2012 年 12 月 13–15 日。 P. P. Swamy 和 D. S. Guru, 编。 New Delhi, India: Springer, 2013, pp. 169–180.
- 7. N. A. Flayh, R. Parveen, 和 S. I. Ahson, 基于小波的部分图像加密, 收录于 2009 IEEE International Multimedia, Signal Processing and Communication Technologies, Aligarh, India, 2009, pp. 32–35.
- 8. A. K. Yekkala, N. Udupa, N. Bussa, 和 C. E. V. Madhavan, 图像轻量级加密, 收录于 2007 Digest of Technical Papers International Conference on Consumer Electronics, 2007, pp. 1–2.
- 9. R. Munir, 基于 Arnold 猫映射置换的选择性图像加密算法的鲁棒性分析, Proc. 3rd Makassar Int. Conf. Electr. Eng. Informatics, pp. 1–5, 2012.
- 10. R. Krishnamoorthi 和 P. D. S. K. Malarchveli, 使用基于正交多项式的变换的灰度图像选择性组合加密, Int. J. Comput. Sci. Netw. Secur., 8(5), 195–204, 2008.
- 11. Y. V Subba Rao, A. Mitra, 和 S. R. Mahadeva Prasanna, 具有伪随机序列的部分图像加密方法, 收录于 Information Systems Security: Second International Conference, ICISS 2006, Kolkata, India, December 19–21. A. Bagchi 和 V. Atluri, 编。 Berlin, Germany: Springer, 2006, pp. 315–325.
- 12. M. A. A. Steffi 和 D. Sharma, 图像和视频部分加密的比较研究, Int. J. Mod. Eng. Res., 1(1), 179–185, 2011.
- 13. Y. Ou, C. Sur, 和 K. H. Rhee, 用于医学成像的基于区域的选择性加密, 收录于 Frontiers in Algorithmics: First Annual International Workshop, FAW 2007, Lanzhou, China, August 1–3.
- 14. W. Zhang, K. Wong, H. Yu, 和 Z. Zhu, 利用位分布固有特征的对称彩色图像加密算法, Commun. Nonlinear Sci. Numer. Simul., 18(3), 584–600, 2013.
- 15. H. T. Panduranga 和 S. K. NaveenKumar, 医学和卫星图像的选择性图像加密, Int. J. Eng. Technol., 5(1), 115–121, 2013.
- 16. S. Bahrami 和 M. Naderi, 使用轻量级流加密算法的图像加密, Adv. Multimed., 2012, 1–8, 2012.
- 17. J.-Y. Oh, D.-I. Yang, 和 K.-H. Chon, 基于 AES 的医学信息选择性加密算法, Healthc. Inform. Res., 16(1), 22, 2010.
- 18. A. Wong 和 W. Bishop, 具有生物特征认证的向后兼容、多级感兴趣区域（ROI）图像加密架构, Int. Conf. Signal Process. Multimed. Appl., 324–329, 2007.
- 19. F. Dufaux, S. J. Wee, J. G. Apostolopoulos, 和 T. Ebrahimi, JPEG 2000 中用于安全成像的 JPSEC, 收录于 Applications of Digital Image Processing XXVII, A. G. Tescher, 编。 SPIE, November 2004.
- 20. P. Kumar 和 P. K. Pateriya, 用于选择性图像加密的 RC4 增强算法方法, Int. J. Comput. Sci. Commun. Networks, 2(2), 181–189, 2012.
- 21. Z. Brahimi, H. Bessalah, A. Tarabet, 和 M. K. Kholladi, 医学图像传输的 JPEG2000 编码流新选择性加密技术, 收录于 2008 5th International Multi-Conference on Systems, Signals and Devices, 2008, pp. 1–4.
- 22. H. A. Younis, T. Y. Abdalla, 和 A. Y. Abdalla, 基于小波压缩数字图像部分加密的矢量量化技术, Iraqi J. Electr. Electron. Eng., 5(1), 74–89, 2009.
- 23. K. Kuppusamy 和 K. Thamodaran, 使用 PSO 的优化部分图像加密方案, 收录于 International Conference on Pattern Recognition, Informatics and Medical Engineering (PRIME-2012), 2012, pp. 236–241.
- 24. R. E. L. Metzler 和 S. S. Agaian, 使用快速形状自适应变换的选择性区域加密, 收录于 2010 IEEE International Conference on Systems, Man and Cybernetics, 2010, pp. 1763–1770.
- 25. S. Sasidharan 和 D. S. Philip, 具有小波变换和 RC4 的快速部分加密方案, Int. J. Adv. Eng. Technol., 1(4), pp. 322–331, 2011.
- 26. N. Taneja, B. Raman, 和 I. Gupta, 静态视觉数据的组合域加密, Multimed. Tools Appl., 59(3), 775–793, 2012.

