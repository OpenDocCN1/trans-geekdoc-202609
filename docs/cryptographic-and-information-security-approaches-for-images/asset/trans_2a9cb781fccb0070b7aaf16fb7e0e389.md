
依赖于 SVC 的层间预测关系以构建哈希链或嵌入水印。HAU 与 SVC 结构无关，因为 HAU 仅考虑基层码流的认证和 SVC 的基于内容特征，因此 HAU 对用户是透明的。

最后一列说明了通信开销。在我们的 SVC 实验中，GOP 大小为 8，编码的 SVC 序列具有三层（一层基层和两层增强层）。密码学认证 [46] 在每个 GOP 中添加 960 字节开销（即每个帧有 120 字节开销）。因此，该方案 [46] 的平均开销分别为质量和空间可伸缩性原始码流的 2.19% 和 2.62%。总体而言，如表 7.4 最后一列所示，HAU 产生最小的通信开销，除了在质量可伸缩性上的通信开销与密码学认证相似。此外，HAU 的通信开销是恒定的，但密码学认证 [46] 和基于水印的认证 [50] 的开销会随着增强层数量的增加而增加。例如，当 GOP 大小为 8 时，如果 SVC 序列包含多一个增强层，每个帧将携带 40 字节更多开销 [46]。

## 7.4.1.4 结论

提出了一种用于 SVC 的混合认证方案，名为 HAU，它分别使用密码学认证和基于内容的认证处理基层和增强层。密码学认证确保基层的完整性，而基于内容的认证使用提取的特征验证增强层。HAU 是安全的、SVC 格式透明的、通信开销轻量且计算复杂度低。分析和实验表明，HAU 对内容保持型操作具有鲁棒性，但对内容改变型操作敏感。

## 7.5 结论

本章强调了可伸缩视频编码的安全性。首先，它介绍了可伸缩视频编码的特性，包括时间、质量和空间可伸缩性。然后描述了安全需求，即安全性和完整性。其次，它分析和评估了可伸缩视频和图像的现有加密和认证方案，并发现现有的部分加密和现有的基于内容认证算法无法满足现实安全需求。此外，针对不同场景提出了两种加密方案，即码流加密和透明加密。此外，还基于可伸缩视频编码的结构设计了一种混合认证方案。

## 参考文献

- 1. D. L. Goeckel, 利用过时衰落估计的时变信道自适应编码。*IEEE 通信汇刊*, 47(6): 844–855, 1999.
- 2. V. K. Goyal, 多描述编码：压缩遇见网络。*IEEE 信号处理杂志*, 18(5): 74–93, 2001.
- 3. H. Schwarz, D. Marpe, and T. Wiegand, H.264/AVC 标准可伸缩视频编码扩展概述。*IEEE 电路与系统视频技术汇刊*, 17(9): 1103–1120, 2007.
- 4. M. Wien, H. Schwarz, and T. Oelbaum, SVC 性能分析。*IEEE 电路与系统视频技术汇刊*, 17(9): 1194–1203, 2007.
- 5. ITU-T, I. J. 1, 通用视听服务高级视频编码, ITU-T and ISO/IEC JTC 1 Recommendation H.264 and ISO/IEC 14496-10 (MPEG-4) AVC, 2005.
- 6. W. Li. MPEG-4 视频标准中细粒度可伸缩性概述。*IEEE 电路与系统视频技术汇刊*, 11(3): 301–317, 2001.
- 7. H. Sohn, W. De Neve, and Y. M. Ro. 使用 JPEG XR 的可伸缩监控视频感兴趣区域置乱。*ACM 多媒体*, pp. 861–864, 2009.
- 8. H. Sohn, W. De Neve, and Y. M. Ro. 视频监控系统中的隐私保护：JPEG XR 中子带自适应置乱分析。*IEEE 电路与系统视频技术汇刊*, 21(2): 170–177, 2011.
- 9. C. Yuan, B. B. Zhu, Y. Wang, S. Li, and Y. Zhong. MPEG-4 FGS 的高效且完全可伸缩加密。*ISCAS (2)*, pp. 620–623, 2003.
- 10. B. B. Zhu, C. Yuan, Y. Wang, and S. Li. MPEG-4 细粒度可伸缩性的可伸缩保护。*IEEE 多媒体汇刊*, 7(2): 222–233, 2005.
- 11. Z. Shahid, M. Chaumont, and W. Puech. 通过扫描模式置乱对二元可伸缩 H.264/AVC 增强层进行选择性和可伸缩加密。*ICIP*, pp. 1273–1276, 2009.
- 12. G. Algin and E. Tunali. H.264 SVC 编解码器的可伸缩视频加密。*视觉通信与图像表示杂志 (JVCIR)*, 22(4): 353–364, 2011.
- 13. A. Tosun and W. Feng. MPEG 视频流的高效多层编码与加密。*IEEE 国际多媒体与博览会 (I)*, pp. 119–122, 2000.
- 14. C. Li, X. Zhou, and Y. Zhong. 可伸缩视频编码的 NAL 层加密。*PCM*, pp. 496–505, 2008.
- 15. C. Li, C. Yuan, and Y. Zhong. 可伸缩视频编码的分层加密。*第 2 届国际图像与信号处理大会*, pp. 1–4, 2009.
- 16. W. Zeng and S. Lei. 数字视频的高效频域选择性置乱。*IEEE 多媒体汇刊*, 5(1): 118–129, 2003.
- 17. F. Liu and H. Koenig. 视频加密算法综述。*计算机与安全*, 29(1): 3–15, 2010.
- 18. B. Zhu, M. Swanson, and S. Li. 可伸缩多媒体的加密与认证：现状与挑战。*Internet Multimedia Management Systems V*, 5601: 157–170, 2004.
- 19. X. Liu and A. Eskicioglu. 分发网络中多媒体内容的选择性加密：挑战与新方向。 在 *第 2 届 IASTED 通信、互联网和信息技术国际会议* 上, pp. 527–533, 2003.
- 20. H. Yu. 无线多媒体访问可伸缩加密概述。*Internet Quality of Service*, 5245: 24–34, 2003.
- 21. S. Lian. *多媒体内容加密：技术与应用*. Boca Raton, FL: CRC Press, pp. 121–130, 2008.
- 22. T. Kunkelmann and U. Horn. 基于数据划分和可伸缩编码的视频加密 - 比较。*IDMS*, pp. 95–106, 1998.
- 23. T. Stutz and A. Uhl. H.264 AVC/SVC 加密综述, *IEEE 电路与系统视频技术汇刊*, 22(3): 325–339, 2012.
- 24. R. L. Rivest. RC4 加密算法. RSA Data Security, Inc., March 12, 1992.
- 25. S.-W. Park and S.-U. Shin. H.264/可伸缩视频编码 (SVC) 中加密与水印的组合方案。 在 *智能交互多媒体新方向* 中. Springer, Berlin, Germany, pp. 351–361, 2008.
- 26. 联合可伸缩视频模型软件, http://ip.hhi.de/imagecomg1/savce/downloads/svc-reference-software.htm.
- 27. A. Skodras, C. Christopoulos, and T. Ebrahimi. JPEG 2000 静态图像压缩标准。*IEEE 信号处理杂志*, 18(5): 36–58, 2001.
- 28. Z. Zhao and P. Liang. H.264/AVC FME 模式减少的统计分析。*IEEE 电路与系统视频技术汇刊*, 21(1): 53–61, 2011.
- 29. S. Ma, W. Gao, D. Zhao, and Y. Lu. H.264/AVC 中量化方案的研究及其在码率控制中的应用。 在 *多媒体信息处理进展, PCM* 上, pp. 192–199, 2004.
- 30. T. Ebrahimi and C. Horne. MPEG-4 自然视频编码 - 概述。*信号处理：图像通信*, 15(4–5): 365–385, 2000.
- 31. I. E. Richardson. *H.264 高级视频压缩标准*, 2nd ed. Chichester, UK: Wiley, 2010.
- 32. A. Mansouri, A. M. Aznaveh, F. Torkamani-Azar, and F. Kurugollu. H.264 压缩域中低复杂度的视频水印。*IEEE 信息取证与安全汇刊*, 5(4): 649–657, 2010.
- 33. J. S. Park and H. J. Song. H.264/AVC 编码器的选择性帧内预测模式决策。*世界科学与工程技术学院*, 13: 51–55, 2006.
- 34. 亚利桑那州立大学：视频轨迹库. http://trace.eas.asu.edu/index.html.
- 35. CAVIAR 团队：欧盟资助的 CAVIAR 项目/IST 2001 37540. http://homepages.inf.ed.ac.uk/rbf/CAVIAR/.
- 36. C. Y. Lin and S. F. Chang. MPEG 视频认证的问题与解决方案。 在 *SPIE 多媒体内容安全与水印国际会议* 上, Vol. 3657, pp. 54–56, 1999.
- 37. S. Shahabuddin, R. Iqbal, S. Shirmohammadi, and J. Zhao. 用于 H.264 视频认证的压缩域时域自适应鲁棒水印。 在 *IEEE 国际多媒体与博览会 (ICME)* 上, pp. 1752–1755, 2009.
- 38. P. Yin and H. H. Yu. MPEG 视频认证的半脆弱水印系统。 在 *IEEE 语音、声学和信号处理国际会议 (ICASSP)* 上, Vol. 4, pp. IV-3461–IV-3464, 2002.
- 39. J. G. Apostolopoulos and S. J. Wee. 支持无需解密转码的安全可伸缩流。 在 *IEEE 图像处理国际会议论文集* 中, pp. 437–440, 2001.
