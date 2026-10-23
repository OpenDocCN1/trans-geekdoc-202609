
需要用点标记细胞。另一种近期的方法侧重于减少对训练数据需求的，是超分辨率方法的开发，该方法旨在主要利用低分辨率训练数据（通常辅以稀疏的高分辨率训练数据）来预测高分辨率标签 [153]。在这些方法中生成训练数据涉及对补丁进行标记以指示每个补丁中不同细胞的密度，并辅以点标注。

mIHC 和 mIF 的出现及其与数字病理学和深度学习方法在定量 IHC 解读方面的自然结合，有可能解决挑战，使这种来自多个生物标志物的丰富信息能够常规用于提供临床上有用的预后和预测信息 [29–31,42,136,142,148]。人们似乎对能够探究并量化肿瘤微环境中不同类型免疫细胞之间相互作用性质的方法，以通过识别关键免疫调节细胞来提供有用的预后信息，抱有越来越少的怀疑和日益增长的热情。利用 mIHC 和人工智能在新辅助和辅助治疗环境中对患者进行靶向免疫治疗分层，从而识别出具有临床可操作性的见解的潜力太重要而不可忽视 [42,130]。因此，如果 mIHC 和 mIF 要被临床采用，开发新方法绝对是必要的。如果以及当这些方法成为能够支持临床决策以指导治疗并提供预后信息的成熟方法时，严格的评估、测试和验证无疑是必需的。由于最近出现了几种商业化的 mIF 和 mIHC 方法，这些方法被纳入主流转化癌症研究的未来前景看起来非常光明。

## 厂商平台

深度学习算法也已进入商业平台。用于分析免疫浸润的商业软件包括 Genie Spectrum（Aperio ePathology Solutions, Vista, CA）[154,155]、Image-Pro Plus 3.0（Media Cybernetics, Silver Spring, MD）[156]、Halo（Indica Labs, Corrales, NM）[151]、ImageJ [157]、VMscope（VMscope GmbH, Berlin, Germany）slide explorer [2]、Vectra/inForm（PerkinElmer, Waltham, MA, USA）[158]、SlidePath（Leica Biosystems, Wetzlar, Germany）[159]、Tissue Studio（Definiens, Munich, Germany）[146]、Author AI（Visiopharm Corporation, Westminster, CO, USA）等，还有许多其他软件。一种商业化的图像分析软件平台 WebMicroscope 也被用于（1）识别含有 TIL 的组织区域以及（2）计数每个区域中的淋巴细胞数量 [160]，作者观察到在精原细胞瘤中 TIL 密度与疾病复发具有预后相关性。PaigeAI 和 PathAI 也是公司示例，它们宣传能够在 H&E WSI 中进行区域表征和细胞识别的组合，作为其各自开发深度学习应用以提供更准确诊断努力的一部分。

## 结论

人工智能正迅速承担起阐明和表征肿瘤免疫相互作用的关键角色。支持构建详细空间图的深度学习驱动计算算法似乎是表征肿瘤微环境中一般肿瘤免疫相互作用的相对直接的方法，这可能对预测治疗反应和临床结局非常有帮助。因此，未来几年内先进数字病理学和深度学习应用的利用可能会非常迅速增长。本章主要集中于描述我们生成癌症免疫图能力快速进步背后的方法，以及可组合使用以提供多种潜在有用信息从而实现精准医疗的新兴方法。目前，利用复杂的 TME 解释癌症免疫动力学具有挑战性，但数字病理学和深度学习方法预测、mIHC 和 mIF 定量分析、临床结局和治疗反应之间的疾病部位特异性相关性正在被积极研究，以发现生物标志物并阐明肿瘤与免疫之间的复杂关系，从而帮助推进我们治疗癌症的能力。尽管患者特异性肿瘤-免疫相互作用的绘制仍处于早期阶段，但关于这些方法产生的空间形态学和分子模式定量分析的研究关键下一阶段令人着迷，并有望具有临床适用性。最后但同样重要的是，数字病理学和深度学习方法的强大之处还在于能够并行对数千至数十万例病例的 WSI 进行这些计算分析，而无需额外的组织、时间和资源。也可以完全设想，对特定部位疾病的小亚组进行 mIF 和 mIHC 分析可用于识别可推广的关系，这些关系可与更大集合中 H&E WSI 中的更高通量标准 Pathomics 分析相关联，以进一步深入了解肿瘤生物学。希望这些发展能够导致可在病理科实施的工作流程，作为常规诊断外科病理学的实用临床决策支持工具。因此，我们希望本章的结尾能作为一个开端，帮助想象一个未来，即 incoming 组织样本的 WSI 由自动化算法分析，这些算法执行诊断筛查、定量 mIHC panel 中生物标志物的表达、提供预后信息、帮助识别治疗靶点并预测治疗反应。

## 参考文献

- [1] Denkert C, et al. 肿瘤相关淋巴细胞作为乳腺癌新辅助化疗反应的独立预测因子。Journal of Clinical Oncology 2010;28(1):105–13.
- [2] Denkert C, et al. 乳腺癌中肿瘤浸润淋巴细胞的标准化评估：国际免疫肿瘤生物标志物工作组的环形研究结果。Modern Pathology 2016;29(10):1155–64.
- [3] Hendry S, et al. 评估实体瘤中的肿瘤浸润淋巴细胞：面向病理学家的实用综述以及国际免疫肿瘤生物标志物工作组提出的标准化方法：第二部分：黑色素瘤、胃肠道癌、非小细胞肺癌和间皮瘤、子宫内膜和卵巢癌、头颈部鳞状细胞癌、生殖泌尿系统癌以及原发性脑肿瘤中的 TIL。Advances in Anatomic Pathology 2017;24(6):311–35.
- [4] Salgado R, et al. 乳腺癌中肿瘤浸润淋巴细胞（TILs）的评估：2014 年国际 TILs 工作组建议。Annals of Oncology 2015;26(2):259–71.
- [5] Gurcan MN, et al. 组织病理学图像分析：综述。IEEE Reviews in Biomedical Engineering 2009;2:147.
- [6] Irshad H, et al. 数字组织病理学中细胞核检测、分段和分类的方法：综述——现状与未来潜力。IEEE Reviews in Biomedical Engineering 2014;7.
- [7] Kothari S, et al. 用于全切片图像定量分析的病理成像信息学。Journal of the American Medical Informatics Association: JAMIA 2013;20(6):1099–108.
- [8] Madabhushi A, Lee G. 数字病理学中的图像分析和机器学习：挑战与机遇。Medical Image Analysis 2016;33:170–5.
- [9] Xing F, Yang L. 数字病理学和显微镜图像中稳健的细胞核/细胞检测和分割：综合综述。IEEE Reviews in Biomedical Engineering 2016;9:234–63.
- [10] Amgad M, et al. 结构化众包实现组织学图像的卷积分割。Bioinformatics 2019;35.
- [11] Amgad M, et al. 用于乳腺癌肿瘤浸润淋巴细胞表征的联合区域和细胞核分割。In: Medical imaging 2019: digital pathology. International Society for Optics and Photonics; 2019.
- [12] Cooper L, et al. 不同染色组织病理学图像的基于特征配准：计算机化滤泡性淋巴瘤预后应用。Computer Methods and Programs in Biomedicine 2009;96(3):182–92.
- [13] Cooper LA, et al. 来自癌症基因组图谱的泛癌见解：病理学家的视角。The Journal of Pathology 2018;244(5):512–24.
- [14] Cooper LA, et al. 肿瘤微环境强烈影响胶质母细胞瘤的主转录调节因子和基因表达类别。American Journal Of Pathology 2012;180(5):2108–19.
- [15] Cooper LA, et al. 用于疾病亚型识别和表征的综合形态学分析。Journal of the American Medical Informatics Association 2012;19(2):317–23.
- [16] Cooper LA, et al. 胶质母细胞瘤中的形态学特征和基因组相关性。IEEE International Symposium on Biomedical Imaging 2011:1624–7.
- [17] Gajewski TF, Schreiber H, Fu YX. 肿瘤微环境中的先天性和适应性免疫细胞。Nature Immunology 2013;14(10):1014–22.
