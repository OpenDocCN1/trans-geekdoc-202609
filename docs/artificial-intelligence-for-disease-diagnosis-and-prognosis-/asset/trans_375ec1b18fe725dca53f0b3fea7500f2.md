

表 6.1 使用 COVIDx 数据集的 COVID-19 诊断架构比较研究

| 作者 | 年份 | 任务 | 病例数 | 预处理 | 架构 | 性能 |
|---|---|---|---|---|---|---|
| Gunraj 等人 [12] | 2021 | 地理范围和不透明度范围评分 | 396 | 随机平移 旋转 水平翻转 缩放 强度偏移 剪切 高斯噪声 | DNN | 地理范围 = 0.664 不透明度范围 = 0.635 均值 = 0.032 标准差 = 0.044 |
| Ebadi 等人 [15] | 2021 | 图像分类 | 12,943 | 裁剪 | DNN | N/A |
| Ambati 等人 [17] | 2021 | 图像分类 | 13,870 | N/A | CNN | 准确率 = 98.08% |
| Cherti 等人 [18] | 2021 | 小样本学习 图像分类 迁移学习 | 13,870 | 标准随机调整大小裁剪数据增强 | 预训练模型，ResNet 50 | 准确率 = 95.78% |
| Celaya 等人 [25] | 2021 | 医学图像分割 语义分割 | 13,870 | 随机反射 | CNN | 准确率 = 99.41% |
| Qi 等人 [19] | 2021 | 计算机断层扫描 (CT) COVID-19 诊断 决策制定 | 13,870 | N/A | ResNet50 | 准确率 = 86.46% |
| Yang 等人 [26] | 2021 | 联邦学习 | 13,870 | N/A | CNN | F1 = 94.54 +/- 0.21 |
| Ali 等人 [27] | 2021 | 分类 | 13,870 | 几何变换和颜色空间变换 | CNN | 准确率 = 95% |
| Li 等人 [20] | 2021 | 计算机断层扫描 (CT) | 19 | 翻转、平移、使用五个不同的随机角度旋转 | 基于补丁的卷积神经网络 | 准确率 = 97.89% |
| Hao 等人 [21] | 2021 | 主动学习 通用分类-表征学习 无监督表征学习 | 13,870 | 随机裁剪 随机翻转 色彩畸变 高斯模糊 随机灰度 | CNN-GP 混合模型 | 准确率 = 96% |
| Zhang 等人 [22] | 2021 | COVID-19 诊断 | 13,870 | N/A | CNN | 准确率 = 88% |
| Gunraj 等人 [10] | 2020 | COVID-19 诊断 | 13,870 | 平移 旋转 水平翻转 缩放 强度偏移 | CNN | N/A |
| Gunraj 等人 [11] | 2020 | 决策制定 | N/A | 裁剪框 抖动 旋转 水平和垂直剪切 水平翻转 强度 | DNN | 灵敏度 = 98.1% 阳性预测值 = 98.1% |
| Huang 等人 [28] | 2020 | 图像分类 | 217,000 | 颜色抖动变换 | DNN | 准确率 = 92.4% |
| Abbasi 等人 [29] | 2020 | 严重程度预测 | 13,870 | N/A | CNN | ROC = 0.99 ± 0.01; PR F1 = 0.99 ± 0.01; 0.98 |
| Hirano 等人 [30] | 2020 | 异常检测 COVID-19 诊断 COVID-19 图像分割 迁移学习 | 13,870 | 归一化图像 | CNN | ROC 曲线从 0.71 到 0.77 |
| Motamed 等人 [23] | 2020 | 异常检测 COVID-19 诊断 COVID-19 图像分割 迁移学习 | 13,870 | 增强 | CNN | AUC 0.54 到 0.71 |
| Li 等人 [31] | 2020 | 图像增强 | 13,870 | 自适应直方图均衡化 | CNN | 准确率 = 94.44% |
| Chowdhury 等人 [16] | 2020 | 图像分类 | 14,914 | 部分平移不变性 | CNN | 准确率 = 97% |
| Dev 等人 [32] | 2020 | 图像分类 | 13,870 | 旋转 平移 翻转 | CNN | 准确率 = 98.08% |
| Shoeibi 等人 [14] | 2020 | 图像分类 | 13,870 | N/A | CNN | N/A |
| Zhang 等人 [33] | 2020 | 图像检索 度量学习 | 13,870 | 水平翻转 透视 锐度 模糊 网格畸变 弹性变换 | CNN | 准确率 = 94% |
| Deepshikha 等人 [34] | 2020 | 异常检测 | 14,200 | GAN 生成器 | 迁移学习 | 准确率 = 70% |
| Sarosh 等人 [35] | 2020 | 生存预测 迁移学习 | 13,870 | GAN 增强 | CBB | 准确率 = 98% |
| Banerjee 等人 [36] | 2020 | COVID-19 诊断 | 1786 | 旋转，水平翻转 | CNN | 准确率 = 93% |

## 6.6 结论

COVID-19 是一种迅速发展的大流行病，在很短的时间内使世界上许多人的健康面临危险。它直接影响肺细胞，如果不能及早发现，可能导致永久性损伤，甚至死亡。专业人士使用 X 射线或 CT 图像以及 PCR 结果来准确检测该疾病。PCR 结果揭示的并非 COVID-19，而是另一种形式的肺部感染，例如呼吸道结核。DL 网络被用于对 COVID-19 识别进行广泛分析。讨论了用于诊断和预测 COVID-19 的公共数据库。使用了最新的 DL 方法来诊断、分割和预测 COVID-19 的传播。大型公共数据库的可用性是开发可靠且准确的 COVID-19 诊断系统面临的问题之一。我们相信，随着更多公共数据库的出现，研究人员将能够构建更好的 DL 模型，以可靠地检测和预测 COVID-19。因此，这将有助于开发性能最佳的范式。我们相信，数据模型的融合可以辅助诊断和预测性能。为了构建准确的模型，从 DL 架构中提取的特征可以与应用的 ML 相结合，以增强获得的分类结果。此外，构建合适的分割模型很困难，因为它需要专业人士勾勒肺部。因此，利用胸部 X 射线或 CT 的可视化过程来检测对这些病例准确诊断至关重要的最重要特征。未来，我们计划使用应用于 COVIDX 和其他更新收集的数据集的特征选择算法，以可靠且高效的准确性调查和可视化图像。

## 参考文献

- 1. J. Wu, J. Liu, S. Li, Z. Peng, Z. Xiao, X. Wang, R. Yan, J. Luo. “COVID-19 患者各种生物样本中核酸的检测与分析.” Travel Medicine and Infectious Disease, 37 (2020): 101673.
- 2. T. Corse, L. Dayan, S. Kersten, F. Battaglia, S. R. Terlecky, and Z. Han, “既有免疫系统受损的 COVID-19 患者的临床结局：病例报告综述,” Int. J. Med. Sci., vol. 17, no. 18, pp. 2974–2986, 2020, doi: 10.7150/ijms.50537.
- 3. D. Wu, T. Wu, Q. Liu, and Z. Yang, “SARS-CoV-2 疫情：我们所知道的,” Int. J. Infect. Dis., vol. 94, pp. 44–48, 2020, doi: 10.1016/j.ijid.2020.03.004.
- 4. S. Elmuogy, N. A. Hikal, and E. Hassan, “COVID-19 CT 扫描图像分类的高效技术,” vol. 40, pp. 5225–5238, 2021, doi: 10.3233/JIFS-201985.
- 5. E. Hassan, M. Shams, N. A. Hikal, and S. Elmuogy, “基于迁移学习的植物幼苗分类,” 2021 国际电子工程会议 (ICEEM), pp. 1–7, 2021.
- 6. O. M. Elzeki, M. Shams, S. Sarhan, M. A. Elfattah, and A. E. Hassanien, “COVID-19：一种用于分类的新型深度学习计算机辅助模型,” PeerJ Comput. Sci., vol. 7, pp. 1–33, 2021, doi: 10.7717/peerj-cs.358.
- 7. A. Sedik 等人, “部署机器学习和深度学习模型以实现高效的数据增强 COVID-19 感染检测,” Viruses, vol. 12, no. 7, pp. 1–29, 2020, doi: 10.3390/v12070769.
- 8. P. Ghamisi 等人, “光谱-空间高光谱图像分类的新前沿：基于数学形态学、马尔可夫随机场、分割、稀疏表示和深度学习的最新进展,” in IEEE Geoscience and Remote Sensing Magazine, vol. 6, no. 3, pp. 10–43, Sept. 2018.
- 9. K. M. Hosny, M. A. Kassem, and M. M. Foaud, “使用深度学习和迁移学习进行皮肤癌分类,” 2018 年第九届开罗国际生物医学工程会议 CIBEC 2018 - 论文集, pp. 90–93, 2019, doi: 10.1109/CIBEC.2018.8641762.
- 10. H. Gunraj, L. Wang, and A. Wong, “胸部 X 射线图像,” Front. Med., vol. 7, pp. 1–12, 2020, doi: 10.3389/fmed.2020.608525.
- 11. H. Gunraj, L. Wang, and A. Wong, “COVIDNet-CT：一种用于从胸部 CT 图像中检测 COVID-19 病例的定制深度卷积神经网络设计,” Front. Med., vol. 7, pp. 1–12, 2020, doi: 10.3389/fmed.2020.608525.
- 12. H. Gunraj, A. Sabri, D. Koff, and A. Wong, “COVID-Net CT-2：通过更大、更多样化的学习，用于从胸部 CT 图像中检测 COVID-19 的增强型深度神经网络,” pp. 1–15, 2021, [在线]。可用：http://arxiv.org/abs/2101.07433.
- 13. A. Wong 等人, “COVID-Net S：通过训练和验证深度神经网络对胸部 X 射线的地理范围和不透明度范围评分来进行计算机辅助严重程度评估，以评估 SARS-CoV-2 肺部疾病严重程度,” 2020, [在线]。可用：http://arxiv.org/abs/2005.12855.
- 14. Shoeibi, A., Khodatars, M., Alizadehsani, R., Ghassemi, N., Jafari, M., Moridian 等人. 使用深度学习技术自动检测和预测 COVID-19：一篇综述. arXiv 预印本 arXiv:2007.10785.
- 15. A. Ebadi, P. Xi, A. Maclean, S. Tremblay, S. Kohli, and A. Wong, “COVIDx-US - 用于 AI 驱动的 COVID-19 分析的开放访问超声成像数据基准数据集,” pp. 1–12, 2021.
- 16. N. K. Chowdhury, M. A. Kabir, M. M. Rahman, and N. Rezoana, “ECOVNet：基于 EfficientNet 的用于从胸部 X 射线中检测 COVID-19 的深度卷积神经网络集成,” 2020, doi: 10.7717/peerj-cs.551.
- 17. A. Ambati and S. R. Dubey, “AC-CovidNet：用于胸部 X 射线图像中 COVID-19 识别的注意引导对比 CNN,” 2021, [在线]。可用：http://arxiv.org/abs/2105.10239.
- 18. M. Cherti and J. Jitsev, “大规模预训练对自然和医学图像中全样本和小样本迁移学习的影响,” pp. 1–18, 2021, [在线]。可用：http://arxiv.org/abs/2106.00116.
- 19. X. Qi, J. L. Nosher, D. J. Foran, and I. Hacihaliloglu, “基于胸部 X 射线图像的 COVID-19 诊断多特征半监督学习,” vol. 2019, pp. 1–11, 2021, [在线]。可用：http://arxiv.org/abs/2104.01617.

