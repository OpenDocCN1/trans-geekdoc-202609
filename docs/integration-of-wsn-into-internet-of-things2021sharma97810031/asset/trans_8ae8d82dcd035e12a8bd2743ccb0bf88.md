
用于提供服务的原语和信任根，这些服务原本可通过公钥原语实现。这样做的优势在于，设备约束在很大程度上决定了解决方案的性质，代价是互操作性降低。在面向互联网的协议（如 CoAP 和 6LoWPAN）中，一旦标准化工作取得足够进展，易受攻击的 PKC 解决方案很可能会被淘汰，转而采用 PQC 算法。在此情境下，除非在标准中定义，否则混合模型将不太可行。

## 5.6 结论与未来工作

在本章中，我们探讨了在考虑量子增强攻击（QEA）潜在途径的前提下，将无线传感器网络（WSN）集成到物联网（IoT）中所必须解决的安全挑战。我们涵盖了现代轻量级密码学的现状、量子计算的潜力，以及抗量子安全算法开发的进展。选择新密码算法的主要风险在于存在未预见的漏洞的可能性。宝贵的研发资源可能被投入到那些突然被证明不安全的解决方案中。这就是为什么必须仔细审查面向 WSN 的抗量子解决方案的原因。对潜在提案进行审计和审查可以降低忽视隐藏威胁的可能性。与后量子密码学（PQC）相关的大多数领域刚刚开始被探索。密码分析、侧信道攻击、协议设计和实现优化代表了在短期和中期需要大量工作的领域。本文提供的分析的最终目标是展示，一些后量子算法似乎满足被认为可接受的 WSN 应用条件，即使处于早期阶段。一旦某些算法被标准化，其实现很有可能会得到改进以达到更高效的解决方案。另一种可能性是，新的 WSN 设备将适应新的安全要求及其强加的相关开销。这可能导致最终用户的货币成本增加。如果应用程序可以承担这项成本，那么需求很可能会支持受限设备设计的新方向。我们的研究结果表明，NIST 后量子候选算法中入选标准化进程第二轮的一些算法表现出适用于 IoT 和 WSN 的有希望的特性。值得注意的是，即使考虑到技术差异，它们的计算时间也与轻量级密码学解决方案的可接受延迟相差不大。关于存储要求，有一些竞争性方案与大多数商用传感器节点（motes）的内存可用性非常契合。有兴趣将 PQC 替代方案用于 IoT 和 WSN 的研究人员可以从这些算法入手。

创建高效的后量子算法实现将在 WSNs 采用这些算法以及将该技术集成到量子支持的 IoT 中发挥重要作用。未来研究可以探索在商用 WSN 设备上实现后量子算法的替代方案，以便通过实验更好地量化可用性和成本，相关指标包括服务质量、侧信道足迹和能耗概况。或者，片上系统（SoC）方法也可以作为高效加速 PQC 算法的可行平台进一步研究。

## 所属机构与资助

Carlos Andres Lara-Nino 和 Miguel Morales-Sandoval 隶属于 CINVESTAV 塔毛利帕斯校区。Arturo Diaz-Perez 隶属于 CINVESTAV 瓜达拉哈拉校区。该工作得到 CONACyT 在拨款编号 336750 下及 CINVESTAV 的支持。该工作还通过项目编号 281565 由“Fondo Sectorial de Investigación para la Educación”（墨西哥 CONACyT 教育部门研究基金）提供资助。

## 参考文献

- 1. R. P. Feynman, “底部大有可为,” Resonance, vol. 16, p. 890, 2011 年 10 月.
- 2. D. Deutsch, “量子理论、丘奇-图灵原理与通用量子计算机,” 伦敦皇家学会学报 A：数学、物理与工程科学, vol. 400, no. 1818, pp. 97–117, 1985.
- 3. P. W. Shor, “量子计算机上的质因数分解和离散对数多项式时间算法,” SIAM 评论, vol. 41, pp. 303–332, 1999 年 6 月.
- 4. L. Chen, S. Jordan, Y.-K. Liu, D. Moody, R. Peralta, R. Perlner, and D. Smith-Tone, “后量子密码学报告,” http://nvlpubs.nist.gov/nistpubs/ir/2016/NIST.IR.8105.pdf.
- 5. D. J. Bernstein 和 T. Lange, “后量子密码学,” 自然, vol. 549, pp. 188–194, 2017 年 9 月.
- 6. Z. Liu, J. Weng, Z. Hu, 和 H. Seo, “面向嵌入式设备的高效椭圆曲线密码学,” ACM 嵌入式计算系统事务, vol. 16, pp. 1–53, 2016 年 12 月 18 日.
- 7. Z. Liu, X. Huang, Z. Hu, M. K. Khan, H. Seo, 和 L. Zhou, “面向物联网安全的新兴椭圆曲线族：ECC 成熟之时,” IEEE 可靠与安全计算事务, vol. 14, no. 3, pp. 237–248, 2016.
- 8. E. Wenger, 基于 ATMega 的面向椭圆曲线密码学的专用指令集轻量级处理器, pp. 1–15. Berlin, Heidelberg: Springer, 2013.
- 9. S. Sinha Roy, K. Jarvinen, 和 I. Verbauwhede, 面向 Koblitz 曲线的轻量级协处理器：包含仅 4300 个门的标量转换的 283 位 ECC, pp. 102–122. Berlin, Heidelberg: Springer, 2015.
- 10. B. Koziol, R. Azarderakhsh, 和 M. Mozaffari-Kermani, 低资源且快速的二进制 Edwards 曲线密码学, pp. 347–369. Cham: Springer International Publishing, 2015.
- 11. J. Bosmans, S. S. Roy, K. Jarvinen, 和 I. Verbauwhede, “面向 256 位 NIST 素数场椭圆曲线密码学的微型协处理器,” 在 2016 年第 29 届 VLSI 设计国际会议和 2016 年第 15 届嵌入式系统国际会议 (VLSID) 上, Kolkata, pp. 523–528, 2016 年 1 月.
- 12. T. Yalcin, “面向 IoT 应用的紧凑型 ECDSA 引擎,” 电子学报, vol. 52, no. 15, pp. 1310–1312, 2016.
- 13. M. Varchola, T. Guneysu, 和 O. Mischke, “MicroECC：一种轻量级可重构椭圆曲线加密处理器,” 在 2011 年可重构计算与 FPGA 国际会议上, Cancun, pp. 204–210, 2011 年 11 月.
- 14. D. B. Roy, P. Das, 和 D. Mukhopadhyay, 指尖上的 ECC：GF(p) 中轻量级 ECC 设计的单指令方法, pp. 161–177. Cham: Springer International Publishing, 2016.
- 15. C. A. Lara-Nino, A. Diaz-Perez, 和 M. Morales-Sandoval, “面向 IoT 的基于二进制 Edwards 曲线的能效/面积高效标量乘法,” 传感器, vol. 19, no. 3, p. 720, 2019.
- 16. L. K. Grover, “数据库检索快速量子力学算法,” 在 *第二十八届 ACM 计算理论研讨会论文集, STOC’96* 中, ACM, New York, NY, pp. 212–219, 1996.
- 17. M. A. Nielsen 和 I. L. Chuang, *量子计算与量子信息*. New York, NY: Cambridge University Press, 2000.
- 18. M. Dyakonov, “反对量子计算的论点,” IEEE Spectrum, 2018 年 11 月.
- 19. M. A. Barreno, 量子计算机下的密码学未来. 博士论文, Dartmouth College. Computer Science, 2002 年 7 月.
- 20. J. Hsu, “CES 2018：英特尔 49 量子比特芯片瞄准量子霸权,” IEEE Spectrum, 2018 年 1 月.
- 21. S. Bravyi, D. Gosset, 和 R. König, “浅层电路中的量子优势,” *科学*, vol. 362, no. 6412, pp. 308–311, 2018.
- 22. J. Kelly, “Bristlecone，Google 新型量子处理器预览.” [在线], 2018 年 3 月. https://ai.googleblog.com/2018/03/a-preview-of-bristlecone-googles-new.html.
- 23. C. Cheng, R. Lu, A. Petzoldt, 和 T. Takagi, “量子世界中的物联网安全,” *IEEE 通信杂志*, vol. 55, pp. 116–120, 2017 年 2 月.
- 24. C. Bormann, M. Ersue, 和 A. Keränen, “受限节点网络术语.” RFC 7228, 2014 年 5 月.
- 25. B. Driessen, T. Güneysu, E. B. Kavun, O. Mischke, C. Paar, 和 T. Pöppelmann, “IPSecc：一种轻量级可重构 IPSec 核心,” 在 *2012 年可重构计算与 FPGA 国际会议* 上, Cancun, pp. 1–7, 2012 年 12 月.
- 26. S. Ray, R. Nandan, 和 G. Biswas, “面向互联网应用的基于 ECC 的 IKE 协议设计,” *Procedia Technology*, vol. 4, pp. 522–529, 2012. 计算机、通信、控制与信息技术第二届国际会议 (C3IT-2012), 2012 年 2 月 25–26 日.
- 27. A. Capossele, V. Cervo, G. De Cicco, 和 C. Petrioli, “将安全作为 CoAP 资源：面向 IoT 的优化 DTLS 实现,” 在 *2015 年 IEEE 国际通信会议 (ICC)* 上, London, pp. 549–554, 2015 年 6 月.
- 28. M. Mosca, “量子计算机时代的网络安全：我们准备好了吗?,” *IEEE 安全与隐私*, vol. 16, pp. 38–41, 2018 年 9/10 月.
- 29. Z. Liu, K. R. Choo, 和 J. Grossschadl, “使用基于格的密码学保护后量子物联网中的边缘设备,” *IEEE 通信杂志*, vol. 56, pp. 158–162, 2018 年 2 月.
- 30. E. Berlekamp, R. McEliece, 和 H. van Tilborg, “关于某些编码问题的固有难解性 (简讯),” *IEEE 信息论事务*, vol. 24, pp. 384–386, 1978 年 5 月.
- 31. D. J. Bernstein, J. Buchmann, 和 E. Dahmen, *后量子密码学*. New York, NY: Springer Publishing Company, Incorporated, 第 1 版, 2008.
- 32. H. Zhu, “肖尔算法破解或未破解的密码学中使用的计算假设调查.” 硕士论文, McGill University 计算机科学学院, Montréal, Canada, 2001.
- 33. D. Jao 和 L. De Feo, *从超奇异椭圆曲线同源性构建抗量子密码系统*, pp. 19–34. Berlin, Heidelberg: Springer, 2011.
- 34. L. Chen, D. Moody, 和 Y.-K. Liu, “后量子密码学 – 提案征集.” [在线], 2017 年 1 月. https://csrc.nist.gov/Projects/Post-Quantum-Cryptography/Post-Quantum-Cryptography-Standardization/Call-for-Proposals.
- 35. T. Oder, J. Speith, K. Holtgen, 和 T. Güneysu, “迈向签名方案 Falcon 的实用微控制器实现,” 2019. 技术报告, Ruhr-University Bochum. https://www.ei.ruhr-uni-bochum.de/media/esecg/veroeffentlichungen/2019/01/25/falcon_paper.pdf.
