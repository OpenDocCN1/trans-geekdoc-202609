

# 结论

在本研究中，我们提出了一种名为 MCAD 的新方法，旨在利用 sMRI、FD-PET 和 CSF 生物标志物等多模态数据区分阿尔茨海默病（AD）和认知正常（CN）。由于 MRI 和 FD-PET 扫描中疾病相关的差异较小且尺寸不一，我们利用了基于空洞细粒度表示的编码器来学习多尺度特征。同时，CSF 编码器可以捕捉更丰富的信息表示。为了有效利用 AD 的跨模态相关信息，我们在基于图像块和 CSF 的细粒度表示的互信息（MI）中对模态交互进行建模。我们设计了一个确保模态对齐的目标函数，旨在从特征层面学习 AD 特征，这有助于多模态特征的有效融合并提高 AD 的诊断性能。在 ADNI 数据集上的实验结果表明，与其他竞争方法相比，我们的方法在 AD 分类任务中表现更好。广泛实验证明，学习多模态之间的细粒度交互为 AD 提供了关键信息。

# 声明

作者声明没有可能影响本文报道工作的竞争性财务利益或关系。

# 致谢

本文的研究得到了成都市重大科技应用示范项目（2019-YF09-0012-SN0）的支持。

# 参考文献

- 1. S. Swartz, V. Atharthi, A. Kaushik, A. Yardt, M. Nair, 阿尔茨海默病：发机制、诊断与治疗. Int. Nature Neurology (2014) 15:149-154.
- 2. L. Zhan, J. Jiao, W. Wang, Y. Zhou, J. Jahansadi, G. Prasad, J. M. C. Liu, C. Chen, Y. Zhang, Y. Wang, and G. Sheng, 深度学习用于阿尔茨海默病异常脑网络的检测. Front. in Neurology (2019) 10:668.
- 3. K. Zhang, Y. Wang, H. Li, J. Chen, G. Wang, and S. Dong, 用于识别阿尔茨海默病的多视图分类, 见阿尔茨海默病和认知障碍国际研讨会, 2021.
- 4. L. Lange, 阿尔茨海默病事实与数据, Alzheimer’s Medicine (2020) 16:100662.
- 5. V. G. Vaslagner, 脆弱的脑与网络-77: 老龄人类脑网络的结构变化. Nature Neurology (2013) 20:227-238.
- 6. H. Ha, J. Liu, L. Nguyen, J. Marshall, et al., 与 K. Riverter, G. Green, D. Green 相关疾病，阿尔茨海默病和衰老中的相关蛋白, Nature Res. (2020) 6:709-713.
- 7. J. White, E. Thieullen-Serre, M. Dias-Mera, J. Sanchez-Gutiérrez, A. Routier, S. Boutin, C. Meyer, S. Danis, S. Darrington, and N. Nicolas, 基于图的关联网络识别阿尔茨海默病的分类: International Medical Exp. Eval. (2016) 63:555.
- 8. M. Chen, 基于深度学习的阿尔茨海默病和轻度认知障碍的分类与预测: 综述, Curr Alzheimer Res. 17 (3) (2022) 297-309.

![](img/35eb289ac20da6b2112bd8090073aee2_12_0.png)

J. Chang

Computers in Biology and Medicine 162 (2023) 107050

- [10] Wang, L., B. Liu, J. Shen, S. Wu, A. Di; 基于 2D 卷积网络的多模态多集成学习架构用于阿尔茨海默病诊断, Biol. Med. 126 (2021) 106420
- [11] A. Drazga, D. Altomare, C. Festari, J. Arbizu, S. Ortiz, E. Kerholz, P. Nester, F. Agosto, F. Nobilli, et al.; 18F-FDG PET 用于高风险患者阿尔茨海默病的预测, Eur. J. Nucl. Med. Imaging. 95 (2018) 1487–1496
- [12] S. Karakas, A. Volcker, V. Myrkers, et al.; 阿尔茨海默病生物标志物的识别, Acta Neurolrol. 117 (3) (2017) 591–607
- [13] A. Ashbery, F. Fisher, K. Chen, N. Aartveld, L. Lopez, T. Quicker, R. Caseli, P.N. Talbot, E.M. Reiman; 临床前痴呆的研究与预测, Nat. Aging Res. 9 (7) (2021) 791–798
- [14] X. Ma, B. Li, H. Hu, Y. Wang; 基于聚类进化融合结果的阿尔茨海默病多模态数据分析, IEEE J J. Bioinf. Inf Health. 24 (2020) 107512
- [15] W. Lin, Q. Ma, D. Wang; 多中心基于结构 MRI 分析的阿尔茨海默病诊断, Front. Hum. 8 (2021) 66933
- [16] S. Spavano, L. Dammag, A. Pian, N. Tocci, A.D., et al.; 用于阿尔茨海默病分类的参数高效深度学习方法, NeuroImage. 253 (2022) 11903
- [17] K. Wajid, A. Feijoo, J. Mervey, E. Fenema-Notte, D. Habler; MRI、PET 和 CSF 的模态融合用于阿尔茨海默病的诊断, J. Alzheimers Dis. 19 (3) (2022) 340–357
- [18] Y. Wang, and J. Liu; 阿尔茨海默病和轻度认知障碍的多模态分类, Neurosciences. 55 (5) (2022) 851–865
- [19] C. Zhang, and Y. Wang; 使用集成学习对 MRI、CSF 和 APOE 生物标志物进行多模态融合, Scientific Reports. 12 (2022) 5333
- [20] F. Sabahi, M. Ahmed; 基于深度学习的阿尔茨海默病早期诊断, Medical Science. 30 (2022) 10652
- [21] X. Liu, and Y. Wang; 基于模型的阿尔茨海默病多模态预测, 2021 IEEE International Conference on Data Mining (ICDM), pp. 1270–1275
- [22] Y. Zhang and Y. Wang; 使用多模态融合的阿尔茨海默病诊断, Comput. Biol. Med. 148 (2022) 10391
- [23] Y. Chen, J. Wang, E. Cao, H. Meijer, D. Hajler; 用于真实应用的阿尔茨海默病鲁棒深度学习预测模型, 2022, arxiv preprint:2213.0964
- [24] C. Himerowicz, V. Singh, G. Xu, S. Johnson, A.; 用于人群的多模态深度学习以进行阿尔茨海默病早期诊断, Neurosciences. 95 (2022) 5711–5729
- [25] D. Kushain, Y. Yan, P. Habib, L. Sen, Y. Chen, A. Wu, T. Agra, R., J. Wang.; 使用循环网络和深度学习的阿尔茨海默病早期诊断, IEEE/Trans. Comput. Biol. 2 (2022)
- [35] C. Han, L. Liu, J. Shen, D. Xu; 用于结构 MRI 联合注意和阿尔茨海默病诊断的高层次卷积网络, IEEE Trans. Neural. Learn. Math. 32 (4) (2020) 880–893
- [36] J. Zheng, X. Heng, X. Xu, Y. Li, J. Wang, A.; 用于阿尔茨海默病早期诊断的多模态注意力卷积网络, J. Neural. Eng. 19 (4) (2022) 04630
- [37] Q. Wang, Y. Chen, J. Li, Q. Hu, Y. Wang, A.; 用于阿尔茨海默病早期诊断的注意力增强网络, Biomarkers. 12 (11) (2022) 4215
- [38] Q. Sun, P. Joshi, M. Liu, C. Xu, X. Zhou, K. Karajardi, G. Chang, A. S, B. Byer, D. Shu, et al.; 用于阿尔茨海默病分类的卷积网络的评估与验证, Nature Communications. 11 (2020) 1920–1923
- [39] X. Ma, Y. Guo, L. Chen, R. Duan, A., et al.; 使用局部注意力网络的阿尔茨海默病多模态分类, Fusion 67 (2023) 53–67
- [40] C. B. Jack, Jr., M. A. Bertolotti, N. Fox, T. Ganderbauer, D. Harvey, R. B. Johnson, P. Birn, L. White, C. Ward, et al.; 阿尔茨海默病影像倡议: Res. J. Soc. Res. 27 (6) (2008) 685–691
- [41] Y. R. Jung, Z. Gu, B. Kim, Y. Lee, et al.; 用于阿尔茨海默病早期诊断的多模态深度学习, Scientific Reports. 11 (2021) 15543
- [42] K. Bashmakter, M. Han, L. Y. Yang, et al.; 使用多模态数据的阿尔茨海默病分类深度学习方法, Scientific Reports. 11 (2021) 15544
- [43] E. Fernandez, B. Gullot, J. Sampler-Ganzier, J. Wen, S. Bertani, A., M. Barcoux, T. Fagnani, A. Villard, M. Godinger, D. Habler, R.; 第21 届国际医学成像研讨会 (ISBI), pp. 189–193
- [44] Y. Wang, J. Liu, and R. Richardson; 用于自动检测阿尔茨海默病的卷积神经网络设计, Machine Learning for Health 11, 2020
- [45] K. Zhang and Y. Wang; 多模态自注意力网络用于痴呆, 2023
- [46] A. Doshoyts, L. Bayer, A. Kolokoliev, V. Semenin, X. Zaitsev, T. Unterterich, D. Medinhint, M. Godinger, G. Gelley, et al.; 用于阿尔茨海默病分类的注意力网络, 2020, arxiv preprint:2019.0961
- [47] A. Vawanna, N. Senrath, N. Parmar, J. Jha, et al.; 用于阿尔茨海默病分类的深度交叉编码网络, Adv. Neural. Med. Phys. 30 (2021) 073
- [48] T. Han, M. Bansal; 用于阿尔茨海默病分类的深度交叉编码网络, 2019, arxiv preprint:1912.0648
- [49] D. J. Kim, B. Park; 基于多模态生成对抗网络的阿尔茨海默病早期诊断, IEEE J. Bioinf. Health. 25 (2023) 7119–7128
- [50] J. Chen, M. Zheng, W. Xu, Y. Li, T. Wang, B. Zhou; 用于阿尔茨海默病诊断的多模态深度卷积网络, Neuroimage 168 (2023) 119552
- [51] J. Wang, S. Wang, Y. Yang, W. Wang, D. Treichler, R. Multihler; 用于视觉问答和定位的多模态双线性池化学习, 2023, arxiv preprint:2316.0184
- [52] V. Thomas, M. El-Ahmed, M. Hassandadeh, M. Wang; 用于阿尔茨海默病早期检测的多模态深度学习模型, Sci. Rep. 11 (1) (2021) 1–13

