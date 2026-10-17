
深度学习方法被用于指静脉识别。然而，由于系统在非公开数据集上进行训练和测试 (Radzi and Bakhteri, 2016; R. Arya et. al., 2021)，结果并不理想。从原始图像中提取特征时，部分信息会因多种因素而丢失。为提升鲁棒性，作者采用全连接 CNN 模型恢复指静脉的丢失模式，实现良好的验证性能 (Zoph and Le, 2017)。CNN 模型相较于其他技术更为复杂且不轻量。研究者为指静脉识别开发了轻量化模型 (Hong, Lee, and Park, 2017)。传统的图像分割方法与 CNN 结合以提升识别性能。指静脉像素信息的标签由系统自动分配。CNN 模型被训练并测试以预测指静脉像素信息。针对分割图像中缺失像素，开发了一个特殊的 CNN 模块 (IEEE and IEEE, 2017)。提出了一种 CNN‑监督离散哈希指静脉识别过程，以降低模板尺寸至 250 bytes 并显著提升匹配速度 (P. Sharma et al., 2018)。过时的指静脉识别方法易被黑客破解，因为其使用的是明文模板 (Qin and El‑yacoubi, 2017)。作者提出 FVR‑DLRP，以安全且高效的方式生成可撤销的指静脉模板。传统的指静脉识别系统普遍受遮光和错位问题影响。从图像中提取特征是深度 CNN 的复杂且繁琐过程 (Y. Liu et al., 2018)。为改善这些问题，研究者提出了一种强健的 CNN 模型，误差率为 0.396，数据集质量高 (Hong, Lee, and Park, 2017)。所有公开的指静脉数据集图像数量均较少。

尽管用于指静脉的 CNN 模型准确率更高，但其训练过程仍存在挑战 (W. Liu et al., 2017)。该模型已成功用于指静脉识别 (Simonyan, 2019)。为解决小训练数据集的问题，提出了一种轻量 CNN，利用相似度测量网络 (Qin and El‑yacoubi, 2018)。提出了密集网络用于指静脉识别 (FVR)，能够去除图像噪声并结合多张图像进行识别与特征提取。系统计算成本较高 (Song, Kim, and Park, 2019)。尽管所有方法均在公开数据集上测试，但在实际应用中仍表现不佳。开发了一种基于深度的独立 CNN 模型，结构简单但对特征不明显的图像识别效果较差 (Tang et al., 2019)。CNN‑CO 通过本地描述子对 ImageNet 模型进行预训练，实际表现优于所有传统系统 (Y. U. Lu, 2019)。提出了一种基于轻量级 Siamese 网络的指静脉认证模型，图像采集时会丢失特征信息。利用 GCNet 与多尺度特征解决此问题，系统在三个公开数据集上测试，但特征提取模块仍需通过调整 CNN 宽度和基数进行改进 (Fang, Ma, and Li, 2023)。训练和测试参数因隐蔽的神经网络结构而复杂。虽然准确率达 99.98 %，但仍需要轻量化的 FVR 模型 (Wang and Shi, 2022)。双重稀疏表示分类被开发用于 FVR，精度低于其他模型且求解稀疏系数耗时，因为所有训练样本均基于字典矩阵 (Fang et al., 2022)。需优化字典选择以提升性能 (Fang et al., 2022)。指静脉识别采用椭圆 PDCNN（高级版 PDK），性能最佳；前十层取自 MobileNet，其余层取自 SqueezeNet，使网络能够压缩以提高性能 (Li et al., 2023)。

CNN 模型提升了 FVR 的识别性能，但这种进步需要改进特征提取模块并防御安全攻击，且 CNN 模型本身并不轻量。

## FVR 系统的安全性

当前时代，各系统的安全面临信息丢失和受保护数字资产被盗的重大风险。在选择生物信息用于任何应用前，应牢记以下几点以增强安全性。首先，应用中使用的所有技术阶段必须在数据隐私和保护方面安全可靠。尽管生物特征技术面临多种安全攻击，但它仍被视为安全的现实世界系统。

### 指静脉模板保护

模板保护通过特征提取从图像中生成精确或相关信息 (Kumar, 2019)。这种唯一的精确信息可区分不同个体。模板方案分为两类：(a) 生物密码系统 (Kaur, Kumar, and Singh, 2023)，将密码学密钥方法与生物特征方案相结合；(b) 可撤销模板 (Manisha, 2020)。在此领域，生物特征模板被扭曲，使原始数据对入侵者不可得，同时仍可进行身份识别。CNN 模型用于提高 FVR 精度时的模板生成可行 (Yin, Zhang, and Liu, 2021)。模板生成如 Figure 5.2 所示。

指静脉模板的安全由密码基于的密钥导出函数提供，生成名为 FVR‑DLRP 的密钥。即使密码被破解，信息仍然安全；但该系统在假接受率 (FAR) 上精度较低，导致 FAR 攻击并降低真接受率 (GAR) (Y. Liu et al., 2018)。

![Figure 5.2 Template generation](`img/fig5_2_C.jpg`)

Figure 5.2 Template generation

基于硬矿工指纹验证方案的深度卷积神经网络（Deep CNN）被提出，其性能优于商用指纹静脉识别系统。该方法还加快了完整的训练过程。巨大的模板尺寸需要巨大的存储空间（Huang et al., 2017）。使用了 Gabor 滤波器，基于轻量级 CNN 构建了指纹静脉认证系统，并结合监督离散哈希以改进指纹静脉图像。尽管经过上述步骤，该方法仍降低了模板尺寸并提升了指纹静脉识别的性能。训练时间与识别结果之间的关系没有得到彻底测量（Xie and Kumar, 2019）。基于指纹和指纹静脉生物数据集开发了融合系统，并应用了特征层面的融合。该系统的数据匹配性能和安全性更高（Yang et al., 2018）。基于深度 CNN 的 BDD-FVR 系统采用了深度卷积神经网络。该系统与 ML-ELM 结合形成 FVR 系统，既提供模板的隐私保护，也提供模板的安全性；在入侵者篡改模板的情况下，模板会独立执行撤销操作，然后通过用户特定密钥生成新的模板版本（Yang et al., 2019）。采用了加权最小二乘回归以改进模板生成，它能够最小化验证错误，但基于一个假设，而同一图像数据的类内距离非常小（Qin, 2019）。针对 CIRF 的可撤销生物特征方案被提出，并引入了基于 CIRF 的低秩近似索引方案，以解决过高的计算开销问题。低秩近似生物特征图像被用于加速 CIRF 的计算，同时在傅里叶域中使用最小生成树表示法对低秩矩阵进行表示。研究者证明了所提方法在保护相关生物信息方面的可靠性（Murakami et al., 2019）。提出了模板保护方案以对齐图像。IoM 哈希用于实现 FVR 所需的隐私和安全（Kirchgasser et al., 2020）。CNN 模型为模板提供了安全性以解决呈现攻击问题，但模板仍面临对抗样本攻击，且缺乏轻量级特征提取模块（Ren et al., 2021）。当前技术已能够解决人工神经网络中指纹静脉模式识别的各种问题。问题在于谁可以为 prob 和 gallery 图像提供良好的匹配，以及是否需要准备并生成指纹静脉的轻量级模型（Yin, Zhang, and Liu, 2021）。

### Security attacks

另一方面，受限系统负责安全攻击。攻击者生成假生物特征模板并以不同层次修改它们，指纹静脉面临各种安全攻击相关问题，时而引入各种安全措施及其补丁来修复系统（Tome and Vanoni, 2014）。

提出了可转移的深度卷积网络来处理呈现攻击。研究者在现有 Alex-Net 基础上增加了七层，以克服过拟合问题。使用了两种不同打印机生成指纹静脉的伪影。改进后的系统能够处理指纹静脉的 PAD（防伪造攻击）。可转移的深度学习神经网络仍需面对视频呈现攻击（Raghavendra et al., 2017）。为数据模板安全发展了另一种机制，但仍在模板存储和模板匹配过程中面临安全漏洞。基于模板的 FVR 具有呈现攻击防护能力，但仍存在对抗攻击相关问题（Ren et al., 2021）。Yimin Yin 等人（Yin, Zhang, and Liu, 2021）提供的综述详细指出了指纹静脉 CNN 方法中的所有安全漏洞。系统已发展以应对冒充攻击，并以最短的注册时间验证身份。在 CNN 训练前，使用 MC-CLAHE 方法处理指纹静脉图像，但系统仅对数据库提供安全保护（Safie, Zarina, and Khalid, 2023）。已开发多种基于 CNN 的模板模型。它们对安全攻击提供了中等防御能力，但模板基于的 FVR 系统的安全问题仍然存在。Table 5.3 展示了与 CNN、模板及 FVR 安全相关的最新文章。

Table 5.3 Recent articles related to the CNN and template security of FVR

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
| `Double weighted group sparse representation classification` || PolyU \[\], FV-USM, SDUML-HMT || 该系统在 FV\_USM 上的性能最佳，达到了 97.0-95.88- 88.72% 的准确率，超过了三种不同模型的变体 || 稀疏系数计算耗时较长，需要改进以提高系统的准确率 || International Journal of Machine Learning and Cybernetics (Springer May-2022) || (Fang et al., 2022) |
| `Multimodal approach based on CNN (RESNET, AlexNet, VGG-19)` || CASIA-WebFace, SDUMLA-FV, FV-USM || 99.98% || 模型应保持轻量化 || Sensors (MDPI Aug-2022) || (Wang and Shi, 2022) |
| `MC-CLAHE (CNN- AlexNet)` || FV-USM || AUC=0.78–0.91 || 仅提供对数据库的安全保护 || International Journal of Online and Biomedical Engineering (iJOE 2023) || (Safie, Zarina, and Khalid, 2023) |

*   Rohit, A., and Jalal, A. S. (2021). Presentation attack detection system for fake iris: A review. Multimedia Tools Appl., 80, 15193–15214.

*   Al-khafaji, Ruaa S. S. and Al-tamimi, M. S. H. (2022). Vein biometric recognition methods and systems: A review. Adv. Sci. Technol. Res. J., 16(1), 36–46.

*   Patrizio, C. and La Rocca, D. (2014). Brain waves for automatic biometric-based user recognition. IEEE Trans. Inform. Foren. Sec., 9(5), 782–800. [`doi.org/10.1109/TIFS.2014.2308640`](https://doi.org/10.1109/TIFS.2014.2308640).
