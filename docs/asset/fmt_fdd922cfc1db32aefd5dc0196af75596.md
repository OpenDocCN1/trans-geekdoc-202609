
![](img/f4c3bcc9f5332d57a8ec85a75075f8da_582_3.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_582_4.png)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_582_5.png)

图 19.7 使用心律失常 ECG 样本的原始和隐写 ECG。 (a) 原始正常 ECG 信号 (b) 原始正常 ECG 信号 (c) 隐写 ECG (d) 隐写 ECG (e) 隐写和原始 ECG 的放大视图 (f) 隐写和原始 ECG 的放大视图。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_583_0.png)

图 19.8 原始和隐写心电图信号的 PDF 绘图 – 正常 ECG 样例 1。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_583_1.png)

图 19.9 原始和隐写心电图信号的 PDF 绘图 – 正常 ECG 样例 2。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_584_0.png)

图 19.10 原始和隐写心电图信号的 PDF 绘图 – 心律失常 ECG 样例 1。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_584_1.png)

图 19.11 原始和隐写心电图信号的 PDF 绘图 – 心律失常 ECG 样例 2。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_585_0.png)

图 19.12 分数阶 (`α`) 对各种正常 ECG 样例均方误差 (`MSE`) 的影响。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_585_1.png)

图 19.13 分数阶 (`α`) 对各种正常 ECG 样例平均绝对误差 (`MAE`) 的影响。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_586_0.png)

图 19.14 分数阶 (`α`) 对各种正常 ECG 样例信噪比 (`SNR`) 的影响。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_586_1.png)

图 19.15 分数阶 (`α`) 对各种正常 ECG 样例峰值信噪比 (`PSNR`) 的影响。

值。`MSE` 和 `MAE` 的较低值在 `α` 较高时实现，这是理想的。而较高的 `α` 值会产生更好的 `SNR` 和 `PSNR`。在心律失常 ECG 数据库中观察到类似趋势。图 19.16 至 19.19 显示了使用不同 `α` 值对五个心律失常样本的 `MSE`、`MAE`、`SNR` 和 `PSNR` 的结果。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_587_0.png)

图 19.16 不同分数阶 (`α`) 下五个心律失常隐写 ECG 样本的均方误差评估。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_587_1.png)

图 19.17 不同分数阶 (`α`) 下五个心律失常隐写 ECG 样本的平均绝对误差评估。

如图 19.12 至 19.19 所示，当 `α` 在 0.75 到 0.95 之间变化时，所有参数的平均变化范围仅为 2% 至 5%（非常小）。在此可以在性能参数变化不大情况下获得 `α` 方面的额外灵活性。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_588_0.png)

图 19.18 不同分数阶 (`α`) 下五个心律失常隐写 ECG 样本的信噪比。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_588_1.png)

图 19.19 不同分数阶 (`α`) 下五个心律失常隐写 ECG 样本的峰值信噪比。

### 19.5.4 安全性和嵌入容量分析

传输端和接收端之间共享三个不同的参数：

- 加密密钥
- `FrFT` 变换阶数
- 密钥长度

当任何未经授权的人员尝试在任一共享参数变化的情况下访问数据时，将导致提取错误数据。要生成正确的数据，解码器端必须知道全部三个参数。变换阶数被用作秘密信息提取的密钥，因为使用错误的变换阶数很难重建原始秘密信息。这些参数从未通过不安全的互联网通道传输，并在传输端和接收端存储。

可以插入 ECG 样本中的位数称为嵌入容量。在所提出方案中，每个 `FrFT` 系数嵌入一个秘密数据位。可以插入的总位数计算为，

```
c = t_Sam × f_s × 2 (19.11)
```

其中，`t_Sam` 为 ECG 样本时间长度（秒），`f_s` 为 ECG 采样频率，`c` 为嵌入容量。ECG 覆盖样本时间的增加会提高嵌入容量。

所提出的基于 `FrFT` 的 ECG 隐写术方法与现有的最先进 ECG 隐写术算法进行了比较。表 19.4 显示了基于 `FrFT` 的 ECG 隐写术方法与其他现有技术的比较。为了公平比较，仅考虑基于变换的 ECG 隐写术算法。由表 19.4 可见，所提出的方法的 `FrPRD` 小于除 [10] 之外的所有其他方法。此外，`XOR` 加密的存在增强了

#### 表 19.4 基于分数傅里叶变换的 ECG 隐写术方法与其他现有技术的比较

| 方法 | 变换 | 安全分析 | 容量 | PRD（%） |
|---|---|---|---|---|
| [4] | Wavelet | 是 | 2.4 kB | 0.32 |
| [10] | DWT-SVD | 否 | — | 0.000059 |
| [12] | DWT-SVD | 否 | 3500 bits | 0.0031 |
| [13] | DWT-SVD | 否 | 3.07 kB | 0.06 |
| [14] | IWT | 否 | 324.3 kB for 30 min | 0.2241 |
| [17] | IWT | 是 | 2.4 kB | 0.2934 |
| [20] | FDCT | 是 | 512 Bytes | 0.0132 |
| [6] | DWT, DCT & DFT | 否 | 32 bits | — |
| Proposed | Fractional FT | 是 | 5400 Bytes | 0.0199 |

安全级别。就嵌入容量而言，该方法能够嵌入 5400 字节的数据（一秒 ECG 样本），与 [4,12,17] 相比更高。

### 19.5.5 ECG 隐写术在 eHealthcare 系统中的应用

近年来生物医学设备的进步加速了对可穿戴传感器及其在远程健康监测系统和健身监测中的商业应用的兴趣。远程患者健康监测系统的典型架构被称为 eHealthcare 系统，如图 19.20 所示，用于观察、检查和记录患者的生理参数。在 eHealthcare

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_590_0.png)

图 19.20 使用 ECG 隐写术的 eHealthcare 系统示意图。

应用中，信息和通信技术被引入以远程增强医疗保健系统 [39]。诸如排队等待和旅行时间等困难可通过 eHealthcare 系统轻松解决，这有助于患者的居家医疗服务。e-Health 结合了医学信息学、公共卫生和商业三个不同领域，利用互联网提供健康服务和信息。

如 eHealthcare 架构所示，ECG 样本使用可穿戴身体传感器采集（此外还可以采集和传输血压和血糖水平等其他信号），传感器观测值通过蓝牙传输到患者的智能手机。ECG 隐写术在智能手机中实现，以将患者秘密数据和其他生理信息嵌入到覆盖 ECG 信号中。隐写 ECG 信号最终通过互联网以最少的开销位传输到 eHealthcare 服务器（或医院服务器）。

在 eHealthcare 服务器处，接收到隐写 ECG，并将原始 ECG 以及患者数据存储以供将来使用。只有拥有密钥的授权医生和行政人员，包括护理人员，才有权查看 ECG 信号并访问秘密信息。所说明的架构也可用于不同的应用，如两家医院之间的医疗数据共享。所提出的方法确保了高水平的安全性，同时对 ECG 信号的劣化最小。

## 19.6 摘要

本章提出了基于分数傅里叶变换的用于嵌入患者个人和医疗记录的安全且鲁棒的 ECG 隐写术技术。为了增强安全性并允许授权访问患者的个人数据，使用了 `XOR` 加密。该方法使用八种不同的性能指标在两个数据库上进行评估：（a）正常 MIT-BIH ECG 和（b）心律失常 MIT-BIH ECG。所提出技术在隐写 ECG 中引入了最小失真。该方案实现了零比特误码率、高安全性、高容量和低复杂度。观察到该方法不可感知，以零误码率提取所有信息，且隐写 ECG 信号可用于诊断。分数阶参数的使用在系统性能无显著变化的情况下为该方法增加了灵活性。还介绍了基于 ECG 隐写术的 eHealthcare 系统架构。

## 参考文献

- 1. F. Hu, M. Jiang, M. Wagner, and D.-C. Dong. Privacy-preserving tele-cardiology sensor networks: Toward a low-cost portable wireless hardware/software codesign. *IEEE Transactions on Information Technology in Biomedicine*, 11(6):619–627, 2007.
- 2. S. Katzenbeisser and F. Petitcolas (编者). *用于隐写术和数字水印的信息隐藏技术。* Artech House, Norwood, MA, 第1版, 2000.
- 3. W.-B. Lee and C.-D. Lee. 用于 HIPAA 隐私/安全法规的密码密钥管理解决方案。 *IEEE 生物医学信息技术汇刊*, 12(1):34–41, 2008.
- 4. A. Ibaida and I. Khalil. 用于保护床旁系统患者机密信息的小波基 ECG 隐写术。 *IEEE 生物医学工程汇刊*, 60(12):3322–3330, 2013.
- 5. R. Horspool and W. Windels. ECG 压缩的 LZ 方法。 在 *IEEE 第七届计算机医学系统研讨会论文集*，页 71–76。 IEEE, 1994.
- 6. S.-T. Chen, Y.-J. Guo, H.-N. Huang, W.-M. Kung, K.-K. Tseng, and S.-Y. Tu. 通过变换域量化方案在 ECG 信号中隐藏患者机密数据。 *医学系统杂志*, 38(6):54, 2014.
- 7. A. Ibaida, I. Khalil, and D. Al-Shamary. 为医疗保健信息系统在 ECG 信号中嵌入患者机密数据。 在 *2010 IEEE 工程医学与生物学年会*，页 3891–3894, IEEE, 2010年8月.
- 8. D. Awasthi and S. Madhe. 使用小波变换对隐写术中加密的 ECG 信号的分析。 在 *2015 年第 2 届电子与通信系统国际会议 (ICECS)*，页 718–723, IEEE, 2015年2月.
- 9. D. Awasthi and S. Madhe. 使用百分比残差差 (PRD) 测量评估基于小波的 ECG 隐写系统。 在 *2015 年通信与信号处理国际会议 (ICCSP)*，页 559–563, IEEE, 2015年4月.
- 10. S. E. Jero and P. Ramu. 一种鲁棒的 ECG 隐写方法。 在 *2016 年第 10 届医学信息与通信技术国际研讨会 (ISMICT)*，页 1–3, IEEE, 2016年3月.
- 11. D. Meghani and S. Geetha. 在电子医疗保健系统中保护患者数据的 ECG 隐写术。 在 *ACM 女性研究研讨会 2016 论文集, WIR'16*，页 66–70, ACM, 2016.
- 12. S.E. Jero, P. Ramu, and S. Ramakrishnan. 基于离散小波变换和奇异值分解的 ECG 隐写术用于安全患者信息传输。 *医学系统杂志*, 38(10):132, 2014.
- 13. E. Jero, P. Ramu, and R. Swaminathan. 使用连续蚁群优化的 ECG 隐写术不可感知性-鲁棒性权衡研究。 *专家系统与应用*, 49(Supplement C):123–135, 2016.
- 14. W. Wu, B. Liu, W. Zhang, and C. Chen. 基于直方图偏移和阈值的 ECG 信号可逆数据隐藏。 在 *2015 年第 2 届普适医疗保健未来信息与通信技术国际研讨会 (Ubi-HealthTech)*，页 1–5, IEEE, 2015年5月.
- 15. S. Singh and V. Kumar. 使用高级加密标准在 ECG 隐写术中保护患者机密数据。 在 *通信与计算系统*，页 821–826。 CRC Press, Boca Raton, FL.
- 16. H.-J. Shiu, B.-S. Lin, C.-H. Huang, P.-Y. Chiang, and C.-L. Lei. 使用盲可逆隐写术保护在线数字生理信号的隐私。 *生物医学计算机方法与程序*, 151(Supplement C):159–170, 2017.
- 17. K. PremChandran and K. Krishnakumar. 使用整数小波变换的 ECG 隐写术。 在 2015 年计算机通信与信息学国际会议 (ICCCI)，页 1–5, IEEE, 2015年1月.
- 18. C.A. Liji, K.P. Iniradevi, and K.K. Anish Babu. 基于整数到整数小波变换的 ECG 隐写术用于保护患者机密信息。 Procedia Technology, 24(Supplement C):1039–1047, 2016.
- 19. S. S. Patel and S. V. Sankpal. 使用 XOR 密码加密和 ECG 隐写术的安全患者数据传输。 在 2016 年电气、电子与优化技术国际会议 (ICEEOT)，页 1311–1315, IEEE, 2016年3月.
- 20. S.E. Jero, P. Ramu, and S. Ramakrishnan. 使用曲线波变换的 ECG 隐写术。 Biomedical Signal Processing and Control, 22(Supplement C):161–169, 2015.
- 21. S. E. Jero and P. Ramu. 基于曲线波的 ECG 隐写术用于数据安全。 Electronics Letters, 52(4):283–285, 2016.
- 22. C.-Y. Yang and W.-F. Wang. 基于系数对齐的有效心电图隐写术。 Journal of Medical Systems, 40(3):66, 2015.
- 23. H. Wang, W. Zhang, and N. Yu. 基于 ECG 可逆数据隐藏的患者机密信息保护。 Multimedia Tools and Applications, 75(21):13733–13747, 2016.
- 24. A. McBride and F. Kerr. 关于 Namias 的分数阶傅里叶变换。 IMA Journal of Applied Mathematics, 39(2):159–175, 1987.
- 25. V. Namias. 分数阶傅里叶变换及其在量子力学中的应用。 IMA Journal of Applied Mathematics, 25(3):241–265, 1980.
- 26. J. Lang. 基于保实多参数分数阶傅里叶变换和混沌置换的图像加密。 Optics and Lasers in Engineering, 50(7):929–937, 2012.
- 27. P. Singh, B. Raman, and M. Misra. 基于 SVD 和分数阶傅里叶变换的安全图像共享方案。 Signal Processing: Image Communication, 57(Supplement C):46–59, 2017.
- 28. D. Bhalke, C. Rama Rao, and D. Bormane. 使用基于分数阶傅里叶变换的 MFCC 特征和反向传播神经网络的自动乐器分类。 Journal of Intelligent Information Systems, 46(3):425–446, 2016.
- 29. X.J. Zhang, Y. Shen, S.Y. Li, and H.Y. Zhang. 分数阶傅里叶变换域中的医学图像配准。 Optik-International Journal for Light and Electron Optics, 124(12):1239–1242, 2013.
- 30. T. Nagashima, G. Cincotti, T. Murakawa, S. Shimizu, M. Hasegawa, K. Hattori, M. Okuno et al. 使用分数阶傅里叶变换的全光正交时/频域复用传输信号的峰均功率比降低。 Optics Communications, 402(Supplement C):123–127, 2017.
- 31. L.-L. Tang, C.T. Huang, J.-S. Pan, and C.-Y. Liu. 基于分数阶傅里叶变换的双水印算法。 Multimedia Tools and Applications, 74(12):4397–4413, 2015.
- 32. M.-Y. Zhai. 基于分数阶傅里叶变换的地震数据去噪。 Journal of Applied Geophysics, 109(Supplement C):62–70, 2014.
- 33. G. Moody and R. Mark. MIT-BIH 心律失常数据库的影响。 IEEE Engineering in Medicine and Biology Magazine, 20(3):45–50, 2001.
