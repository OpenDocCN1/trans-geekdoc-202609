
**FIGURE 13.6** 通过对二值分割图像体积应用 3D 生长算法，可视化自动分割 MRA 数据。患者 C 第 0 天（左上），患者 C 第 700 天（右上），患者 D 第 0 天（左下），患者 D 第 700 天（右下）。这些结果展示了这些患者的脑血管结构随时间变化（圆圈标记）。

**TABLE 13.3** 患者 A、B、C、D 的血压测量值

| 患者 | 第 0 天收缩压 | 第 0 天舒张压 | 第 0 天 MAP | 第 700 天收缩压 | 第 700 天舒张压 | 第 700 天 MAP |
| --- | --- | --- | --- | --- | --- | --- |
| A | 120 | 80.5 | 93.7 | 103.5 | 66.5 | 78.8 |
| B | 130.5 | 83 | 98.8 | 143.5 | 94 | 110.5 |
| C | 118 | 80.5 | 93 | 105.3 | 69 | 81.1 |
| D | 114 | 84.5 | 94.3 | 120 | 88 | 98.7 |

## 13.4 讨论

平均累积分割算法的灵敏度为 0.997 ± 0.008，特异性为 0.9998 ± 0.001。这种高精度的表现表明，使用手动输入来初始化自动分割具有明显的好处。单独使用手动分割在实际医疗环境中过于耗时，而仅使用自动分割方法则无法提供足够的准确性来划分和量化直径小于 10 μm 的脑小动脉（arteriolar）血管。所提议的分割算法结合了手动分割的精度与自动化、时间更节约的优势，能够在保持高精度的同时，最大程度地减少所需的时间和努力。

我们方法的高灵敏度和特异度能够准确地将血管与周围脑组织区分，从而实现脑血管变化的量化。PDF 显示了从第 0 天到第 700 天血管直径的总体变化。在 Willis 环（circle of Willis）下方，PDF 与系统血压（BP）之间存在统计学相关性（*P* = 0.0007），表明血压升高（即 CPP 增加）与平均血管直径下降及 PDF 减小相关。BP 和 MAP 测量与大多数患者在 Willis 环下方的非侵入性平均 PDF 直径测量相吻合良好。由于已假设脑部变化会在系统性高血压出现之前发生 [9,10,26]，我们的方法可能成为一种工具，用于在结合其他方法（如认知测试）的情况下，及早开展或优化系统性高血压（HBP）的管理。该发现很重要，因为它表明血压升高导致的血管重塑在诊断性必然性高血压（essential hypertension）出现之前就已经发生。本研究中选取的个体明确具有前高血压的血压值，该方法可用于确定脑血管重塑与脑小血管病变之间的关系，而脑小血管病变在高级高血压中已知会伴随中风和痴呆的风险 [27,28]。PDF 与 MAP 的相关性与患者性别无关。Willis 环上方血管的 PDF 差异在统计学上与年龄相关，表明老年患者的脑血管可能出现收缩，这可能使其中风风险更高。

在患者 C 和 D 中，CDF 的变化未能与 MAP 的变化相关，这可能提示脑血流自调功能受损，可能是由于脑血管重塑所致 [5,26]。这三维脑血管重建显示在第 0 天至第 700 天之间存在显著的血管变化。这些结果可能表明，仅凭系统血压来开具药物治疗可能无法提供最佳的医疗管理。CDF 与 MAP 之间的相关性缺失可能提示血管改变以及脑血管不良事件的更高风险，这需要更频繁的监测和/或优化医疗管理，即使系统血压和 MAP 正常。结合 BP 与 CDF 的变化可能有助于降低不良事件的发生率。

所提方法采用 MRA，直接可视化整体脑血管解剖结构，并且对小血管的分辨率高于多普勒超声，后者主要评估血流或在其视野内单一或少数血管的特性。MRA 是获取小脑血管准确三维结构所必需的成像方式。常规使用所提 MRA 方法进行筛查成本较高。其临床重要性在于难治性高血压（treatment-resistant hypertension），该病症目前仍缺乏深入理解 [29]。最近一项研究提供了令人信服的数据，表明此类患者可能存在血管异常（如 Willis 环畸形），而我们的技术可以轻易检测到 [30]。其他研究也提出，此类高血压可能是因脑血管受脑干血压调节区域的压迫所致 [31]。这些异常一旦被发现，就能指导临床治疗，而目前的药物剂量尚未解决这些问题。此外，有家族史或临床史导致高血压风险升高的患者，也可以通过本方法进行筛查，以在疾病发病前检测血管变化并管理高血压，尽管检测血管变化和管理高血压的成本较高。

分割算法及血管和 BP 变化（CDF 与 PDF）指标并不局限于脑血管，这些方法同样可用于量化其他对血压敏感的器官（如肾脏）的血管变化。

## 13.5 Limitations

尽管我们的分割算法在自动分割方法上有显著提升，但仍受到 MRI 机器分辨率的限制。CDF 直径（Figure 13.5）从 0.5 mm 开始，因为距离图计算是基于血管边缘的半径，而 MRA 成像的每像素代表 0.25 mm。低于 0.5 mm 的数值无法被准确表示，导致血管直径小于 10 μm（在 Willis 环上方）的统计分析精度下降。

研究期间，受试者使用了多种非处方药物和保健品，这些药物引起的血压变化应当很小。不过，仍需要更大的样本量来确定其与高血压进展之间的 definitive 关系。虽然假设升高的 CPP 会在系统性高血压之前出现，但必然性高血压的成因仍是多因素的拼图，尚未完全阐明。尽管存在这些局限性，我们的方法仍对理解与高血压相关的脑病理具有重要意义，无论该病理是先于临床高血压出现，还是随之而来。

## 13.6 Conclusion

- [脑血管变化](https://wiki.example.org/feynmans_learning_method)可通过非侵入性的 MRA 图像分析获得。脑血管变化与大脑环状动脉以下的平均动脉压（MAP）相关。改进的分割算法结合 CDF 和 PDF 的计算，可指示脑血管和脑灌注压力的变化，这可能成为临床医生优化高血压（HBP）医疗管理的有用工具。除血管系统 [32, 33, 34, 35, 36, 37, 38, 39, 40, 41]，本工作还可应用于医学影像的其他多种领域，如前列腺 [42, 43, 44]，肾脏 [45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72]，心脏 [73, 77, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89]，肺 [90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100, 101, 102, 103, 104, 105, 106, 107, 108, 109, 110, 111, 112, 113, 114, 115, 116, 117, 118, 119, 120, 121, 122, 123, 124, 125, 126, 127, 128, 129, 130, 131, 132, 133, 134, 135, 136, 137]，大脑 [138, 139, 140, 141, 142, 143, 144, 145, 146, 147, 148, 149, 150, 151, 152, 153, 154, 155, 156, 157, 158]，视网膜 [159, 160, 161, 162, 163]，膀胱 [164]，以及伤害预测 [165] 以及一些非医学应用 [166, 167, 168, 169, 170, 171]。

## References

1. C. f. d. Control. *About Underlying Cause of Death, 1999–2015*, 2015. Available: `http://wonder.cdc.gov/ucd-icd10.html`

2. S. Kulkarni, I. O’Farrell, M. Erasi, and M. Kochar, “Stress and hypertension,” *WMJ: Official Publication of the State Medical Society of Wisconsin*, vol. 97, no. 11, pp. 34–38, 1998.

3. S. Mohan and N. R. Campbell, “Salt and high blood pressure,” *Clinical Science*, vol. 117, no. 1, pp. 1–11, 2009.

4. M. J. Sarnak et al., “Kidney disease as a risk factor for development of cardiovascular disease,” *Circulation*, vol. 108, no. 17, pp. 2154–2169, 2003.

5. C. Iadecola and R. L. Davisson, “Hypertension and cerebrovascular dysfunction,” *Cell Metabolism*, vol. 7, no. 6, pp. 476–484, 2008.

6. E. J. Van Dijk et al., “The association between blood pressure, hypertension, and cerebral white matter lesions,” *Hypertension*, vol. 44, no. 5, pp. 625–630, 2004.

7. M. Willmot, J. Leonardi-Bee, and P. M. Bath, “High blood pressure in acute stroke and subsequent outcome,” *Hypertension*, vol. 43, no. 1, pp. 18–24, 2004.

8. J. N. Barnes et al., “Aortic hemodynamics and white matter hyperintensities in normotensive postmenopausal women,” *Journal of Neurology*, vol. 264, no. 5, pp. 938–945, 2017.

9. J. R. Jennings et al., “Prehypertensive blood pressures and regional cerebral blood flow independently relate to cognitive performance in midlife,” *Journal of the American Heart Association*, vol. 6, no. 3, p. e004856, 2017.

10. J. R. Jennings 和 Y. Zanstra，“大脑是高血压的关键吗？” *Neuroimage*，第 47 卷，第 3 期，第 914–921 页，2009。

11. L. J. Launer 等，“血管因素与早期大脑健康的多种测量：CARDIA 大脑 MRI 研究，” *PLoS One*，第 10 卷，第 3 期，第 e0122138 页，2015。

12. R. J. Van der Geest 和 J. H. Reiber，“心脏 MRI 中的量化方法，” *Journal of Magnetic Resonance Imaging*，第 10 卷，第 5 期，第 602–608 页，1999。

13. A. A. Amini、J. Chen 和 Y. Wang，“用于确定心血管力学的成像与分析，”在 *Biomedical Imaging: From Nano to Macro, 2007. ISBI 2007. 4th IEEE International Symposium on* 中，IEEE，2007，第 692–695 页。

14. K. Van Everdingen、C. Klijn、L. Kappelle、W. Mali 和 J. Van der Grond，“颈动脉闭塞患者的 MRA 流量量化，” *Stroke*，第 28 卷，第 8 期，第 1595–1600 页，1997。

15. A. C. Chung 和 J. A. Noble，“利用瑞利分布的统计三维血管分割，”在 *International Conference on Medical Image Computing and Computer-Assisted Intervention* 中，Springer，1999，第 82–89 页。

16. A. El-Baz 等，“精确的三维磁共振血管造影分割，” *IEEE Transactions on Biomedical Engineering*，第 59 卷，第 7 期，第 2019–2029 页，2012。

17. D. L. Wilson 和 J. A. Noble，“自适应算法用于时飞 MRA 数据的分割，” *IEEE Transactions on Medical Imaging*，第 18 卷，第 10 期，第 938–945 页，1999。

18. G. Gimel’farb、A. A. Farag 和 A. El-Baz，“高斯混合物线性组合的期望-最大算法，”在 *Pattern Recognition, 2004. ICPR 2004. Proceedings of the 17th International Conference on* 中，IEEE，2004，第 3 卷，第 422–425 页。

19. N. D. Forkert 等，“脑血管结构的方向依赖级集分割，”在 *SPIE Medical Imaging* 中，International Society for Optics and Photonics，2011，第 79623S–79623S-8 页。

20. M. Holtzman-Gazit、R. Kimmel、N. Peled 和 D. Goldsher，“体积医学图像中薄结构的分割，” *IEEE Transactions on Image Processing*，第 15 卷，第 2 期，第 354–363 页，2006。

21. C. Xu 和 J. L. Prince，“蛇形、形状和梯度向量流，” *IEEE Transactions on Image Processing*，第 7 卷，第 3 期，第 359–369 页，1998。

22. A. R. Webb，*Statistical Pattern Recognition*，John Wiley & Sons，纽约，美国，2003。

23. M. Sabry、C. B. Sites、A. A. Farag、S. Hushek 和 T. Moriarty，“快速自动人类脑血管三维体积分割的方法，”在 *CARS 2002 Computer Assisted Radiology and Surgery* 中，Springer，2002，第 382–387 页。

24. K. Suzuki，“利用地质活动轮廓级集算法对器官进行电脑分割，”在 *Multi Modality State-of-the-Art Medical Image Segmentation and Registration Methodologies* 中，Springer，2011，第 103–128 页。

25. Y. Itai、H. Kim、S. Ishikawa、S. Katsuragawa 和 K. Doi，“开发一种体素匹配技术，大幅降低胸部 CT 的减法图像中减法伪影，” *Journal of Digital Imaging*，第 23 卷，第 1 期，第 31–38 页，2010。

26. J. R. Jennings 和 A. F. Heim，“从大脑到行为：高血压对认知与情感的调节，” *International Journal of Hypertension*，第 2012 卷，2012。

27. P. B. Gorelick 等，“血管对认知障碍和痴呆的贡献，” *Stroke*，第 42 卷，第 9 期，第 2672–2713 页，2011。

28. C. Iadecola 等，“高血压对认知功能的影响：美国心脏协会科学声明，” *Hypertension*，第 68 卷，第 6 期，第 e67–e94 页，2016。

29. P. K. Whelton 等，“2017 ACC/AHA/AAPA/ABC/ACPM/AGS/APhA/ASH/ASPC/NMA/PCNA 高血压成人预防、检测、评估和管理指南：美国心脏协会临床实践指南任务力量报告，” *Journal of the American College of Cardiology*，第 24430 页，2017。

30. E. A. Warnert 等，“高血压是大脑的自我保护吗？”， *Circulation Research*，第 CIRCRESAHA. 116.309493，2016。

31. E. I. Levy、A. M. Scarrow 和 P. J. Jannetta，“微血管减压在高血压治疗中的应用：综述与更新，” *World Neurosurgery*，第 55 卷，第 1 期，第 2–10 页，2001。
