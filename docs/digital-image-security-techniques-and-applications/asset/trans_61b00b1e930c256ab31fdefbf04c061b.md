
- 在可取消生物特征识别的基础上，开发跨传感器可操作的指纹模板保护方法仍有空间，这意味着可以在注册和验证阶段使用不同的传感器。
- 指纹模板保护方法可以进一步考虑最终安全指纹模板的尺寸进行开发，同时不影响所计算模板的性能和无对齐特性。生成小尺寸指纹模板的方法可用于为内存较小的消费设备提供安全访问控制。
- 文献中关于为部分指纹图像生成可取消指纹模板的研究并不多；因此，可以探索这一领域，以开发能够保护部分指纹模板的方法。

## 14.7 结论

由于生物特征识别系统相对于传统认证系统的优势，再加上兴趣的激增，这些系统在各种多功能应用中的使用得到了巨大的增长。与此同时，身份盗窃问题明显增加，这成为生物特征识别系统的一个重大安全隐患。在基于指纹生物特征识别系统中，通常包含细节点信息的用户模板存储在数据库中。文献中的研究已经充分证明，如果存储的模板被攻击者获取，就可以通过该模板重建指纹图像。因此，有必要在将原始指纹数据存储到数据库之前对其进行保护。为了保护指纹模板，文献中讨论了许多指纹模板保护方法。其中，可取消生物特征识别是指纹模板保护的一个类别，与其他类别相比，它被广泛讨论。本章全面介绍了可取消生物特征识别的工作原理，并简要讨论了最近在可取消生物特征识别领域保护指纹模板的研究进展。此外，还详细讨论了三种近期方法。这些方法提出了基于不可逆变换的指纹模板保护技术，并处理了指纹模板保护和指纹生物特征识别系统领域中的各种问题。未来，可以开发基于可取消生物特征识别的指纹模板保护方法，以提高包含低质量指纹图像的挑战性数据库的识别性能。将可取消生物特征识别与其他类别相结合的混合方法在文献中的研究较少；因此，可以进一步探索用于指纹模板保护方法的混合方法。此外，未来还可以开发支持传感器互操作性的可取消生物特征识别方法，以保护指纹模板。

## 参考文献

- [1] Maltoni, D.; Maio, D.; Jain, A. K.; Prabhakar, S. 指纹识别手册，第2版；Springer Publishing Company, Incorporated, 2009.
- [2] Ross, A. A.; Shah, J.; Jain, A. K. 从细节点重建指纹. In Proc. of SPIE Conf. on Biometric Technology for Human Identification; 2005; pp. 68–80.
- [3] Ross, A.; Shah, J.; Jain, A. K. 从模板到图像：从细节点重建指纹. IEEE Trans. Pattern Anal. Mach. Intell., 2007, 29 (4), 544–560.
- [4] Feng, J.; Jain, A. K. 指纹重建：从细节点到相位. IEEE Trans. Pattern Anal. Mach. Intell., 2010, 33 (2), 209–223.
- [5] Juels, A.; Wattenberg, M. 一种模糊承诺方案. In Proc. of Computer and Communications Security, Singapore; 1999; pp 28–36.
- [6] Baghel, V. S.; Prakash, S.; Agrawal, I. 一种保护指纹模板的增强型模糊金库. Multimed. Tools Appl., 2021, 80 (21), 33055–33073.
- [7] Gomez-Barrero, M.; Maiorana, E.; Galbally, J.; Campisi, P.; Fierrez, J. 基于同态加密的多生物特征模板保护. Pattern Recognit., 2017, 67, 149–163.
- [8] Ratha, N. K.; Connell, J. H.; Bolle, R. M. 增强基于生物特征的身份验证系统的安全性和隐私性. IBM Syst. J., 2001, 40 (3), 614–634.
- [9] Ratha, N. K.; Chikkerur, S.; Connell, J. H.; Bolle, R. M. 生成可取消指纹模板. IEEE Trans. Pattern Anal. Mach. Intell., 2007, 29 (4), 561–572.
- [10] Jain, A. K.; Nandakumar, K.; Nagar, A. 生物特征模板安全. EURASIP J. Adv. Signal Process., 2008, 2008.
- [11] Connie, T.; Teoh, A.; Goh, M.; Ngo, D. PalmHashing：一种用于可取消生物特征识别的新方法. Inf. Process. Lett., 2005, 93 (1), 1–5.
- [12] Teoh, A. B.; Ngo, D. C. BioPhasor：令牌补充的可取消生物特征识别. In Proc. of 9th International Conference on Control, Automation, Robotics and Vision; 2006; pp 1–5.
- [13] Jin, Z.; Jin, A. T. B. 基于细节点邻域分解的指纹模板保护. In Proc. of International Joint Conference on Biometrics (IJCB); 2011; pp 1–7.
- [14] Wang, S.; Deng, G.; Hu, J. 一种部分哈达玛变换方法用于设计包含二值生物特征表示的可取消指纹模板. Patt. Recogn., 2017, 61, 447–458.
- [15] Si, X.; Feng, J.; Yuan, B.; Zhou, J. 指纹稠密配准. Patt. Recogn., 2017, 63, 87–101.
- [16] Lee, W.; Cho, S.; Choi, H.; Kim, J. 针对小型指纹扫描仪的基于细节点和脊线形状特征的部分指纹匹配. Expert Syst. Appl., 2017, 87, 183–198.
- [17] Wang, S.; Yang, W.; Hu, J. 基于分区细节点对的无对齐可取消指纹模板设计. Patt. Recogn., 2017, 66, 295–301.
- [18] Moujahdi, C.; Bebis, G.; Ghouzali, S.; Rziza, M. 指纹外壳：指纹模板的安全表示. Patt. Recogn. Lett., 2014, 45, 189–196.
- [19] Jain, A.; Prasad, M. V. N. K. 一种使用动态聚类的指纹索引新方案. J. Reliab. Intell. Environ., 2016, 2, 159–171.
- [20] Ali, S. S.; Prakash, S. 增强型指纹外壳. In Proc. of SPIN 2015; 2015; pp. 801–805.
- [21] Ali, S. S.; Prakash, S. 使用显著细节点构建指纹外壳. In Proc. of COMPUTE 2017; ACM, 2017; pp. 91–98.
- [22] Ali, S. S.; Prakash, S. 三维安全指纹外壳. Patt. Recogn. Lett., 2019, 126, 68–77.
- [23] Ali, S. S.; Ganapathi, I. I.; Prakash, S. 使用坚固特征构建指纹外壳. J. Intell. & Fuzzy Syst., 2019, 36 (5), 4091–4104.
- [24] Ali, S. S.; Ganapathi, I. I.; Prakash, S. 指纹模板保护的鲁棒技术. IET Biometrics, 2018, 7 (6), 536–549.
- [25] Ali, S. S.; Ganapathi, I. I.; Prakash, S.; Consul, P.; Mahyo, S. 使用改进的细节点属性保护生物特征用户模板. Patt. Recogn. Lett., 2020, 129, 263–270.
- [26] Trivedi, A. K.; Thounaojam, D. M.; Pal, S. 用于指纹匹配系统的鲁棒且不可逆的指纹模板. Forensic Sci. Int., 2018, 288, 256–265.
- [27] Yang, W.; Wang, S.; Hu, J.; Zheng, G.; Valli, C. 基于指纹和手指静脉的可取消多生物特征识别系统. Pattern Recognit., 2018, 78, 242–251.
- [28] Ali, S. S.; Ganapathi, I. I.; Mahyo, S.; Prakash, S. 多项式金库：一种安全鲁棒的基于指纹的身份验证. IEEE Trans. Emerg. Top. Comput., 2019, 9, 612–625.
- [29] Trivedi, A. K.; Thounaojam, D. M.; Pal, S. 用于指纹生物特征识别的不可逆可取消指纹模板. Comput. & Secur., 2020, 90, 101690.
- [30] Lahmidi, A.; Minaoui, K.; Moujahdi, C.; Rziza, M. 使用不可逆细节点四面体的指纹模板保护. Comput. J., 2022, 65 (10), 2741–2754. https://doi.org/10.1093/comjnl/bxab111
- [31] Lahmidi, A.; Moujahdi, C.; Minaoui, K.; Rziza, M. 关于指纹模板保护方案构思的方法论：可靠性的思考. EURASIP J. Inf. Secur., 2022, 2022 (1), 1–13.
- [32] Yang, W.; Wang, S.; Shahzad, M.; Zhou, W. 基于特征自适应随机投影的可取消生物特征认证系统. J. Inf. Secur. Appl., 2021, 58, 102704.
- [33] Bedari, A.; Wang, S.; Yang, J. 基于两阶段特征变换的物联网隐私保护指纹认证系统. IEEE Trans. Ind. Informatics, 2022, 18 (4), 2745–2752.
- [34] Baghel, V. S.; Ali, S. S.; Prakash, S. 采用配对极坐标结构计算安全且无对齐的指纹模板. IEEE Trans. Ind. Informatics, 2023, 19 (2), 1947–1956.
- [35] Baghel, V. S.; Prakash, S. 面向消费电子设备的使用DFT生成安全指纹模板. IEEE Trans. Consum. Electron., 2022, 69 (2), 118–127. https://doi.org/10.1109/TCE.2022.3217234

