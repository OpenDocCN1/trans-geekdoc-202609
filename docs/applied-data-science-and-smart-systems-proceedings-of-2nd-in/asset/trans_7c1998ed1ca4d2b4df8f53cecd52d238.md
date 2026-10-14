
[Figure 5.2 Template generation](#ch5.xhtml#R_fig5_2)

基于硬矿工指纹验证方案的深度卷积神经网络（Deep CNN）被提出，其性能优于商用指纹静脉识别系统。该方法还加快了完整的训练过程。巨大的模板尺寸需要巨大的存储空间（Huang et al., 2017）。使用了Gabor滤波器，基于轻量级CNN构建了指纹静脉认证系统，并结合监督离散哈希以改进指纹静脉图像。尽管经过上述步骤，该方法仍降低了模板尺寸并提升了指纹静脉识别的性能。训练时间与识别结果之间的关系没有得到彻底测量（Xie and Kumar, 2019）。基于指纹和指纹静脉生物数据集开发了融合系统，并应用了特征层面的融合。该系统的数据匹配性能和安全性更高（Yang et al., 2018）。基于深度CNN的BDD-FVR系统采用了深度卷积神经网络。该系统与ML-ELM结合形成FVR系统，既提供模板的隐私保护，也提供模板的安全性；在入侵者篡改模板的情况下，模板会独立执行撤销操作，然后通过用户特定密钥生成新的模板版本（Yang et al., 2019）。采用了加权最小二乘回归以改进模板生成，它能够最小化验证错误，但基于一个假设，而同一图像数据的类内距离非常小（Qin, 2019）。针对CIRF的可撤销生物特征方案被提出，并引入了基于CIRF的低秩近似索引方案，以解决过高的计算开销问题。低秩近似生物特征图像被用于加速CIRF的计算，同时在傅里叶域中使用最小生成树表示法对低秩矩阵进行表示。研究者证明了所提方法在保护相关生物信息方面的可靠性（Murakami et al., 2019）。提出了模板保护方案以对齐图像。IoM哈希用于实现FVR所需的隐私和安全（Kirchgasser et al., 2020）。CNN模型为模板提供了安全性以解决呈现攻击问题，但模板仍面临对抗样本攻击，且缺乏轻量级特征提取模块（Ren et al., 2021）。当前技术已能够解决人工神经网络中指纹静脉模式识别的各种问题。问题在于谁可以为prob和gallery图像提供良好的匹配，以及是否需要准备并生成指纹静脉的轻量级模型（Yin, Zhang, and Liu, 2021）。

### Security attacks

另一方面，受限系统负责安全攻击。攻击者生成假生物特征模板并以不同层次修改它们，指纹静脉面临各种安全攻击相关问题，时而引入各种安全措施及其补丁来修复系统（Tome and Vanoni, 2014）。

提出了可转移的深度卷积网络来处理呈现攻击。研究者在现有Alex-Net基础上增加了七层，以克服过拟合问题。使用了两种不同打印机生成指纹静脉的伪影。改进后的系统能够处理指纹静脉的PAD（防伪造攻击）。可转移的深度学习神经网络仍需面对视频呈现攻击（[Raghavendra et al., 2017](#ch5.xhtml#ref5_34)）。为数据模板安全发展了另一种机制，但仍在模板存储和模板匹配过程中面临安全漏洞。基于模板的FVR具有呈现攻击防护能力，但仍存在对抗攻击相关问题（Ren et al., 2021）。Yimin Yin等人（Yin, Zhang, and Liu, 2021）提供的综述详细指出了指纹静脉CNN方法中的所有安全漏洞。系统已发展以应对冒充攻击，并以最短的注册时间验证身份。在CNN训练前，使用MC-CLAHE方法处理指纹静脉图像，但系统仅对数据库提供安全保护（[Safie, Zarina, and Khalid, 2023](#ch5.xhtml#ref5_37)）。已开发多种基于CNN的模板模型。它们对安全攻击提供了中等防御能力，但模板基于的FVR系统的安全问题仍然存在。[Table 5.3](#ch5.xhtml#tab5_3)展示了与CNN、模板及FVR安全相关的最新文章。

[Table 5.3 Recent articles related to the CNN and template security of FVR](#ch5.xhtml#R_tab5_3)

| Method || Datasets || Performance parameters || Improvements/need to improve || Journal || Ref. |
| --- | --- | --- | --- | --- | --- |
| **Deep CNN** || DS1, DS2 & DS3 || EER - DS1=0.42%, DS2= 1.41% & DS3= 2.14% || Improvement of vein pattern matching || IEEE International Conference on Identity, Security and Behavior Analysis (IEEE-2017) || (Huang et al., 2017) |
| **Deep learning & random projection** || FV\_NET64 || GAR=91.2% FAR=0.3% || Enhancement the revocability of the template || Soft Computing (Springer-2018) || (Y. Liu et al., 2018) |
| **EP-DFT** || FVC2002 DB2, FVC2004 DB2, FV-HMTD || EER=0.45% || Enhancement of non-revocability of templates || Pattern Recognition (Elesvier-2018) || (Yang et al., 2018) |
| **CNN and supervised discrete hashing** || Two session databases || EER=0.0887 || Reduced the template size || Pattern Recognition Letters (Elesvier-2019) || (Xie and Kumar, 2019) |
| **BDD-ML-ELM** || SDUMLA, MMCBNU\_6000 & UTFVP || CIR=93.09%, 98.70%, 98.61%, respectively (datasets) || New non invertible templates for finger vein || IEEE Transactions on Industrial Informatics (IEEE-2019) || (Yang et al., 2019) |
| **Weighted least square regression** || HKPU & FV-USM || EER=1.28, 1.43, respectively (datasets) || Improvement in enrolment template for finger vein || MDPI (Information-2019) || (Qin, 2019) |
| **Correlation-invariant random filtering** || N || Genuine template identification=164.7 || Fast and secure biometric identification 7 No leakage of information of the template || Pattern Recognition Letters (Elesvier-2019) || (Murakami et al., 2019) |
| **Self-attention mechanism (SAC) Siamese network** || FV-USM, MMCBNU\_6000, SDUMLA-HMT || Recall is best over SDUMLA= 0.9944 F1 Score is best over FV\_USM=0.9925 EER is best over MMCBNU\_6000= 0.0012 || Need to improve the feature extraction module by changing the width and cardinality of the network models || Infrared Physic and Technology (Elsevier Dec-2020) || (Fang, Ma, and Li, 2023) |
| **RSA for template protection using CNN** || SDMLA, MMCBNU\_6000, HKPU, FV-USM || Scheme A is best over HKPU=99.03% and Scheme B is best over FV\_USM=99.18% || The feature extraction method is not lightweight and the system is not able to handle the adversarial sample attack and presentation attack || Knowledge Based System (Elsevier May-2021) || (Ren et al., 2021) |
| **Survey on ANN for finger vein** || SDUMLA-HMT, FV-USM, HKPU, MMCBNU\_6000, UTFVP, THU- FVFDT, SCUT, IDIAP || Performance summary of all CNN methods for finger vein || Need to generate the light weight models, solve the problem of mismatching of gallery and prob image, dynamic finger vein extraction || Computer Vision and Pattern Recognition (Springer Aug-2022) || (Yin, Zhang, and Liu, 2021) |
