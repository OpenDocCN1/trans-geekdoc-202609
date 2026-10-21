
### 表 9.4
分类算法的 OA 和 OP

| OA (%) | OP (%) |
|---|---|
| 99.949 | 99.924 |

结果中记录了一个来自全层烧伤的被误分类元素，该元素被错误预测为健康皮肤，如表 9.2 中单元格位置 [a, c] 所示。这种误分类可能是由于某些全层烧伤图像呈现蜡样外观所致，如图 9.8 所示。

如图 9.8 所示的全层烧伤与健康皮肤相比呈现白色、蜡样且有光泽。这种全层烧伤的光泽外观看起来像未受影响的皮肤图像；因此，这可能是结果中全层烧伤图像被单次误分类的原因。

分类的 OA 可通过对所有类别中正确分类数（TP）求和，然后除以所有分类的总数得到。

OA = (TP(H) + TP(S) + TP(F)) / Total samples  (9.6)

其中 TP(H) 为健康皮肤类别的真正例，TP(S) 为表浅表皮烧伤类别的真正例，TP(F) 为全层烧伤类别的真正例。公式 (9.6) 得到的结果在表 9.4 中给出。

分类算法的总体精度（OP）按公式 (9.7) 表达得到

OP = (TP(S) + TP(F)) / (TP(S) + TP(F) + FP)  (9.7)

![](img/5025594f89449de2a74e5b325b1e84ef_237_0.png)

## 图 9.8 健康与全层烧伤图像。

公式 (9.7) 中的 FP 表示被错误分类为正例的负例，结果在表 9.4 中给出。

## 9.6 结论

诊断烧伤的最终目标是提供即时评估，减少住院延误时间，避免因长期住院而可能获得的并发症，并防止因医疗设施不可用而导致生命损失。因此，使用 ML 算法来区分健康皮肤、表浅烧伤和全层烧伤。图像特征的提取使用预训练模型（ResNet101）进行，随后使用 SVM 分类器用于分类任务。结果显示性能准确率高达 99。本研究的一个有趣之处在于，特征提取模型是在物体识别和分类任务上训练的，但在应用于医学图像进行特征提取时似乎效果良好。ML 的应用可用于解决偏远地区医疗人员不足的问题，在这些地区，获取医疗设施和经验丰富的医疗从业者使患者面临困难情况。

本工作中研究的局限之一是未包含中度烧伤。这是因为我们手头缺乏此类数据。其次，研究是在高加索人患者（白皮肤人群）上进行的，值得纳入不同种族人群的数据，例如有色人种皮肤的烧伤图像。因此，这些为进一步研究提供了空间。

## 参考文献

- 1. C. Wearn, K. C. Lee, J. Hardwicke, A. Allouni, A. Bamford, P. Nightingale, and N. J. B. Moiemen, “激光多普勒成像与热成像在烧伤深度评估中的前瞻性比较评价研究,” Burns, vol. 44, no. 1, pp. 124–133, 2018.
- 2. A. D. Gilbert, E. Rajha, C. El Khuri, R. B. Chebl, A. Mailhac, M. Makki, and M. El Sayed, “黎巴嫩三级医院急诊科烧伤患者流行病学,” Burns, vol. 44, no. 1, pp. 218–225, 2018.
- 3. P. Brassolatti, P. S. Bossini, H. W. Kido, M. C. D. Oliveira, L. Almeida-Lopes, L. M. Zanardi, M. A. Napolitano, L. R. d. S. de Avó, F. M. Araújo-Moreira, and N. A. Parizotto, “光生物调节与细菌纤维素膜在治疗大鼠三度烧伤中的应用,” Journal of Tissue Viability, vol. 27, no. 4, pp. 249–256, 2018.
- 4. R. Kandiyali, J. Sarginson, L. Hollén, F. Spickett-Jones, and A. Young, “五岁以下儿童小面积烧伤及烧伤后意外疾病的管理——英国医疗体系中的成本研究,” Burns, vol. 44, no. 1, pp. 188–194, 2018.
- 5. S. Wall, N. Allorto, R. Weale, V. Kong, and D. Clarke, “低收入中等收入国家烧伤创面护理的伦理问题,” AMA Journal of Ethics, vol. 20, no. 6, p. 570, 2018.
- 6. D. McGill, K. Sørensen, I. MacKay, I. Taggart, and S. Watson, “烧伤深度评估：激光多普勒成像与视频显微镜的前瞻性盲法比较,” Burns, vol. 33, no. 7, pp. 833–842, 2007.
- 7. A. D. Jaskille, J. C. Ramella-Roman, J. W. Shupp, M. H. Jordan, and J. C. Jeng, “烧伤深度评估技术批判性综述：第 II 部分。激光多普勒技术综述,” Journal of Burn Care & Research, vol. 31, no. 1, pp. 151–157, 2010.
- 26. U. Sarwar, M. Javed, and W. A. Dickson, “评估覆盖复杂彩色纹身的烧伤深度时的诊断挑战,” Journal of Plastic, Reconstructive & Aesthetic Surgery, vol. 67, no. 7, pp. e186–e187, 2014.
- 27. F. Musumeci, C. Rottondi, A. Nag, I. Macaluso, D. Zibar, M. Ruffini, and M. Tornatore, “机器学习技术在光网络中应用概述,” IEEE Communications Surveys & Tutorials, Vol. 21(2), pp. 1383–1408, 2018.
- 28. Z. Al-Kassim, and Memon, Q., “为瘫痪人士设计低成本眼球追踪键盘,” Computers & Electrical Engineering, Vol. 58, pp. 20–29, 2017.
- 29. Memon, Q., “更智能的医疗保健协作网络,” Building Next-Generation Converged Networks: Theory and Practice, 2013, pp. 451–476.
- 30. J. Deng, W. Dong, R. Socher, L.-J. Li, K. Li, and L. Fei-Fei, “ImageNet：一个大规模分层图像数据库,” in Computer Vision and Pattern Recognition, 2009. CVPR 2009. IEEE Conference on, 2009, pp. 248–255, Miami, USA
- 31. K. Simonyan and A. Zisserman, “用于大规模图像识别的非常深的卷积网络,” arXiv preprint arXiv:1409.1556, 2014.
- 32. W. Nash, T. Drummond, and N. Birbilis, “深度学习在材料降解研究中的综述,” NPJ Materials Degradation, vol. 2, no. 1, p. 37, 2018.
- 33. R. Yamashita, M. Nishio, R. K. G. Do, and K. Togashi, “卷积神经网络：概述及其在放射学中的应用,” Insights into Imaging, vol. 9, pp. 1–19, 2018.
- 34. S. Sakib, N. Ahmed, A. J. Kabir, and H. Ahmed, “卷积神经网络概述：其架构与应用,” 2018110546 (doi: 10.20944/preprints201811.0546.v1), 2018.
- 35. O. Russakovsky, J. Deng, H. Su, J. Krause, S. Satheesh, S. Ma, Z. Huang, A. Karpathy, A. Khosla, and M. Bernstein, “ImageNet 大规模视觉识别挑战赛,” International Journal of Computer Vision, vol. 115, no. 3, pp. 211–252, 2015.
- 36. W. Nash, T. Drummond, and N. Birbilis, “深度学习在材料降解研究中的综述,” NPJ Materials Degradation, vol. 2, no. 1, p. 37, 2018.
- 37. A. M. Bukar and H. Ugail, “基于面部侧视图的自动年龄估计,” IET Computer Vision, vol. 11, no. 8, pp. 650–655, 2017.
- 38. J. Yosinski, J. Clune, Y. Bengio, and H. Lipson, “深层神经网络中的特征可迁移性如何？,” in Advances in Neural Information Processing Systems, 27, pp: 3320–3328, 2014.
- 39. A. Krizhevsky, I. Sutskever, and G. E. Hinton, “使用深度卷积神经网络的 ImageNet 分类,” in Advances in Neural Information Processing Systems, 2012, pp. 1097–1105.
- 40. C. Szegedy, W. Liu, Y. Jia, P. Sermanet, S. Reed, D. Anguelov, D. Erhan, V. Vanhoucke, and A. Rabinovich, “用卷积更深层次地学习,” in Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, Boston, MA, 2015, pp. 1–9.
- 41. K. He, X. Zhang, S. Ren, and J. Sun, “用于图像识别的深度残差学习,” in Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, Las Vegas, NV, 2016, pp. 770–778.
- 42. A. S. Razavian, H. Azizpour, J. Sullivan, and S. Carlsson, “即插即用的 CNN 特征：识别的惊人基线,” in Computer Vision and Pattern Recognition Workshops (CVPRW), 2014 IEEE Conference on, Columbus, OH, 2014, pp. 512–519.
- 43. H. Xue, Q. Yang, and S. Chen, SVM: 支持向量机: Chapman & Hall/CRC: London, UK, 2009.
- 44. V. Jakkula, “支持向量机（SVM）教程,” in School of EECS, Washington State University, vol. 37, 2006.
- 45. R. Kohavi, “用于准确性估计和模型选择的交叉验证与自助法的研究,” in IJCAI, vol. 14, pp. 1137–1145, 1995.
