
在受试者无关的评估设置下进行，旨在识别能够跨受试者泛化用于真实世界疾病检测应用的疾病特异性 ERP 特征。在六个数据集（PD-SIM、PD-ODD、ADHD-WMRI、SCPD、RLPD 和 AOPD）中，最佳方法的 F1 分数分别为 66.79%、67.37%、66.43%、74.33%、73.87% 和 69.26%。总体而言，没有单一的 ERP 范式在疾病检测中持续表现出明显优势。值得注意的是，三个较小的帕金森病数据集 SCPD、RLPD 和 AOPD 的性能相对高于两个较大的数据集 PD-SIM 和 PD-ODD。这种趋势可能归因于较小数据集中更平衡的数据分布，其中帕金森病患者和健康对照受试者的数量完全相等。在方法比较方面，顶级性能主要由从头训练的深度学习模型以及从基础模型检查点微调的模型实现。基于手动提取特征的两种方法从未达到顶级结果。此外，与 ERP 刺激类型分类不同，ERP 特异性特征在疾病检测中并不能始终优于通用 EEG 特征。在多个数据集中，ERP 特异性特征甚至表现更差，这表明这些数据集中的疾病相关信息可能与规范的 ERP 成分关联不紧密。

## D. 整体性能分析

为了在多个任务和评估指标上对不同方法进行全面比较，我们进一步分析了 15 种方法在 12 个数据集 × 3 个评估指标上的整体性能，共计 36 次评估。图 4 展示了每种方法在全部 36 次评估中的平均排名，以及每种方法在每次评估上的具体排名热力图。排名越低且蓝色越深表示性能越好。

我们观察到，从头训练的监督式深度学习模型在整体性能上持续优于其他方法。在所有评估方法中，EEGConformer 实现了最低的平均排名 3.96，表明其在多样化任务和评估指标上具有最稳定且具有竞争力的性能。继 EEGConformer 之后，ModernTCN、TimesNet、CBraMod 和 Medformer 构成顶级群体。值得注意的是，只有 CBraMod 属于基础模型类别，其余方法均是从头训练的。这表明现有基础模型可以部分迁移到 ERP 分类任务中。一个可能的解释是，目前的 EEG 基础模型很少在 ERP 特异性数据上进行预训练。大多数预训练资源由长序列自发 EEG 组成，且未纳入 ERP 特异性预处理步骤，例如基线校正或基于事件的试验分段。因此，预训练期间学习到的表征可能与 ERP 为中心的下游任务并不最优对齐。基于手动特征的方法整体性能始终最差。在两种手工特征方法之间，ERP 特异性特征相对优于通用 EEG 特征。这些结果凸显了手工统计和频域特征的局限性，它们难以在多样化的 ERP 范式和疾病条件下保持稳健性能，尤其是在受试者无关评估下。这表明，除了解释性或神经科学导向分析外，在以端到端性能为主要目标的真实世界应用中，手动特征提取的优势有限。

## E. Transformer 的 Patch 嵌入比较

**Transformer 嵌入方法比较（F1 分数）**

![](img/6b8a0cc86f73ccc8d474525448d82e6d_8_0.png)

*图 5：在现有 EEG Transformer 中常用的多变量、单变量和整体变量 token 嵌入之间的 F1 分数比较。所有其他 Transformer 组件保持相同。*

我们比较现有 EEG Transformer 模型中常用的三种 token 嵌入方法，以检验其对 ERP 数据分类的适用性。所有其他组件，包括自注意力模块、前馈网络和层归一化层，在各方法间保持相同。为了确保模型容量可比，多变量嵌入方法的 patch 长度设为 25，单变量嵌入方法设为 100。因此，多变量、单变量和整体变量 token 嵌入方法的总参数数分别为 0.864、0.818 和 0.822 百万。

所有结果均以表 IV 中的 F1 分数报告。单变量嵌入方法实现了最佳性能

- [12] Ruizhe Zheng, Lingyan Mao, Dingding Han, Tian Luo, Yi Wang, Jing Ding, and Yuguo Yu. FAPEX: Fractional amplitude-phase expressor for robust cross-subject seizure prediction. 39th International Conference on Neural Information Processing Systems, 2025.
- [13] Yihe Wang, Nadia Mammone, Darina Petrovsky, Alexandros T. Tzallas, Francesco C. Morabito, and Xiang Zhang. ADformer: A multi-granularity spatial-temporal transformer for EEG-based Alzheimer's detection. arXiv preprint arXiv:2409.00032, 2024.
- [14] Josh Achiam, Steven Adler, Sandhini Agarwal, Lama Ahmad, Ilge Akkaya, Florencia Leoni Aleman, Diogo Almeida, Janko Altenschmidt, Sam Altman, Shyamal Anadkat, et al. GPT-4 technical report. arXiv preprint arXiv:2307.08774, 2023.
- [15] Gemini Team, Petko Georgiev, Ving Ian Lei, Ryan Burnell, Libin Bai, Anmol Gulati, Garrett Tanzer, Damien Vincent, Zhufeng Pan, Shibo Wang, et al. Gemini 1.5: Unlocking multimodal understanding across millions of tokens of context. arXiv preprint arXiv:2403.05530, 2024.
- [16] Maxime Oquab, Timothée Darcet, Théo Moutakanni, Huy Vo, Marc Szafraniec, Vasil Khalidov, Pierre Fernandez, Daniel Haziza, Francisco Massa, Alaaeldin El-Nouby, et al. DINOv2: Learning robust visual features without supervision. arXiv preprint arXiv:2304.07193, 2023.
- [17] Wei-Bang Jiang, Li-Ming Zhao, and Bao-Liang Lu. Large brain model for learning generic representations with tremendous EEG data in BCI. arXiv preprint arXiv:2405.18765, 2024.
- [18] Guangyu Wang, Wenchao Liu, Yuhong He, Cong Xu, Lin Ma, and Haifeng Li. EEGPT: Pretrained transformer for universal and reliable representation of EEG signals. Advances in Neural Information Processing Systems, 37:39249–39280, 2024.
- [19] Jiquan Wang, Sha Zhao, Zhiling Luo, Yangxuan Zhou, Haiteng Jiang, Shijian Li, Tao Li, and Gang Pan. CBraMod: A criss-cross brain foundation model for EEG decoding. arXiv preprint arXiv:2412.07236, 2024.
- [20] Ibtehaaj Hameed, Danish M. Khan, Syed Muneeb Ahmed, Syed Sabeeb Aftab, and Hammad Fazal. Enhancing motor imagery EEG signal decoding through machine learning: A systematic review of recent progress. Computers in Biology and Medicine, 185:109534, 2025.
- [21] Katerina D. Tzimourta, Nikolaos Giannakeas, Alexandros T. Tzallas, Loukas G. Astrakas, Theodora Afrantou, Panagiotis Ioannidis, Nikolaos Grigoriadis, Pantelis Angelidis, Dimitrios G. Tsalikakis, and Markos G. Tsipouras. EEG window length evaluation for the detection of Alzheimer's disease over different brain regions. Brain Sciences, 9(4):81, 2019.
- [22] Katerina D. Tzimourta, Theodora Afrantou, Panagiotis Ioannidis, Maria Karatzikou, Alexandros T. Tzallas, Nikolaos Giannakeas, Loukas G. Astrakas, Pantelis Angelidis, Evripidis Glavas, Nikolaos Grigoriadis, et al. Analysis of electroencephalographic signals complexity regarding Alzheimer's disease. Computers & Electrical Engineering, 76:198–212, 2019.
- [23] N. N. Kulkarni and V. K. Bairagi. Extracting salient features for EEG-based diagnosis of Alzheimer's disease using support vector machine classifier. IETE Journal of Research, 63(1):11–22, 2017.
- [24] Joseph N. Mak, Dennis J. McFarland, Theresa M. Vaughan, Lynn M. McCane, Philippa Z. Tusi, Debra J. Zeitlin, Eric W. Sellers, and Jonathan R. Wolpaw. EEG correlates of P300-based brain–computer interface (BCI) performance in people with amyotrophic lateral sclerosis. Journal of Neural Engineering, 9(2):026014, 2012.
- [25] Xiaou Li, Yuning Yan, and Wenshi Wei. Identifying patients with poststroke mild cognitive impairment by pattern recognition of working memory load-related ERP. Computational and Mathematical Methods in Medicine, 2013(1):658501, 2013.
- [26] Bruce Wallace, Frank Knoefel, Rafik Goubran, Rocío A. López Zunini, Zhaofen Ren, and Aaron Maccosham. EEG/ERP: Within episodic assessment framework for cognition. IEEE Transactions on Instrumentation and Measurement, 66(10):2525–2534, 2017.
- [27] Francisco J. Fraga, Tiago H. Falk, Paulo A. M. Kanda, and Renato Anghinah. Characterizing Alzheimer's disease severity via resting-awake EEG amplitude modulation analysis. PLoS ONE, 8(8):e72240, 2013.
- [28] Luke Tait, George Stothart, Elizabeth Coulthard, Jon T. Brown, Nina Kazanina, and Marc Goodfellow. Network substrates of cognitive impairment in Alzheimer's disease. Clinical Neurophysiology, 130(9):1581–1595, 2019.
- [29] Markus Waser, Heinrich Garn, Reinhold Schmidt, Thomas Benke, Peter Dal-Bianco, Gerhard Ransmayr, Helena Schmidt, Stephan Seiler, Günter Sanin, Florian Mayer, et al. Quantifying synchrony patterns in the EEG of Alzheimer's patients with linear and non-linear connectivity markers. Journal of Neural Transmission, 123:297–316, 2016.
- [30] Lucas R. Trambaiolli, Ana C. Lorena, Francisco J. Fraga, Paulo A. M. Kanda, Renato Anghinah, and Ricardo Nitrini. Improving Alzheimer's disease diagnosis with machine learning techniques. Clinical EEG and Neuroscience, 42(3):160–165, 2011.
- [31] Magali T. Schmidt, Paulo A. M. Kanda, Luis F. H. Basile, Helder Frederico da Silva Lopes, Regina Baratho, Jose L. C. Demario, Mario S. Jorge, Antonio E. Nardi, Sergio Machado, Jéssica N. Ianof, et al. Index of alpha/theta ratio of the electroencephalogram: a new marker for Alzheimer's disease. Frontiers in Aging Neuroscience, 5:60, 2013.
- [32] Xiaokun Liu, Chunlai Zhang, Zheng Ji, Yi Ma, Xiaoming Shang, Qi Zhang, Wencheng Zheng, Xia Li, Jun Gao, Ruofan Wang, et al. Multiple characteristics analysis of Alzheimer's electroencephalogram by power spectral density and Lempel–Ziv complexity. Cognitive Neurodynamics, 10:121–133, 2016.
- [33] Paulo Afonso Medeiros Kanda, Lucas R. Trambaiolli, Ana C. Lorena, Francisco J. Fraga, Luis Fernando I. Basile, Ricardo Nitrini, and Renato Anghinah. Clinician's road map to wavelet EEG as an Alzheimer's disease biomarker. Clinical EEG and Neuroscience, 45(2):104–112, 2014.
- [34] Heinrich Garn, Markus Waser, Manfred Deistler, Thomas Benke, Peter Dal-Bianco, Gerhard Ransmayr, Helena Schmidt, Guenter Sanin, Peter Santer, Georg Caravias, et al. Quantitative EEG markers relate to Alzheimer's disease severity in the prospective dementia registry Austria (PRODEM). Clinical Neurophysiology, 126(3):505–513, 2015.
- [35] Hamed Azami, Steven E. Arnold, Saeid Sanei, Zhuoqing Chang, Guillermo Sapiro, Javier Escudero, and Anoopum S. Gupta. Multiscale fluctuation-based dispersion entropy and its applications to neurological diseases. IEEE Access, 7:68718–68733, 2019.
- [36] Lucie Tylová, Jaromír Kukal, Václav Hubata-Vacek, and Oldřich Vyšata. Unbiased estimation of permutation entropy in EEG analysis for Alzheimer's disease classification. Biomedical Signal Processing and Control, 39:424–430, 2018.
- [37] Shixin Peng, Ruyi Xu, Xin Yi, Xin Hu, Lili Liu, and Leyuan Liu. Early screening of children with autism spectrum disorder based on electroencephalogram signal feature selection with L1-norm regularization. Frontiers in Human Neuroscience, 15:656578, 2021.
- [38] Raja Majid Mehmood, Muhammad Bilal, S. Vimal, and Seong-Whan Lee. EEG-based affective state recognition from human brain signals by using Hjorth-activity. Measurement, 202:117738, 2022.
- [39] Zhangjing Deng, Haoying Bai, Shijing Wu, Jiani Wu, Boyuan Xia, Yingxi Chen, Yurou He, Shuyu Li, and Yang Lü. Diagnosis of Alzheimer's disease via machine learning approaches with integrated resting-state EEG and ERP characteristics. Cognitive Computation, 17(6):166, 2025.
- [40] Vernon J. Lawhern, Amelia J. Solon, Nicholas R. Waytowich, Stephen M. Gordon, Chou P. Hung, and Brent J. Lance. EEGNet: A compact convolutional neural network for EEG-based brain–computer interfaces. Journal of Neural Engineering, 15(5):056013, 2018.
- [41] Eduardo Santamaria-Vazquez, Victor Martinez-Cagigal, Fernando Vaquerizo-Villar, and Roberto Hornero. EEG-Inception: A novel deep convolutional neural network for assistive ERP-based brain-computer interfaces. IEEE Transactions on Neural Systems and Rehabilitation Engineering, 28(12):2773–2782, 2020.
- [42] Qi Xin, Shaohai Hu, Shuaiji Liu, Ling Zhao, and Yu-Dong Zhang. An attention-based wavelet convolution neural network for epilepsy EEG classification. IEEE Transactions on Neural Systems and Rehabilitation Engineering, 30:957–966, 2022.
- [43] Jin Xie, Jie Zhang, Jiayao Sun, Zheng Ma, Liuni Qin, Guanglin Li, Huihui Zhou, and Yang Zhan. A transformer-based approach combining deep learning network and spatial-temporal information for raw EEG classification. IEEE Transactions on Neural Systems and Rehabilitation Engineering, 30:2126–2136, 2022.
- [44] N. Kasthuri, R. Ramyea, V. S. Arunprasshath, S. Abhineeth, and S. Bharathraj. EEG Conformer model based epileptic seizure prediction using deep learning. In 2024 15th International Conference on Computing Communication and Networking Technologies (ICCCNT), pages 1–7. IEEE, 2024.
- [45] Di Wu, Siyuan Li, Jie Yang, and Mohamad Sawan. Neuro-BERT: Rethinking masked autoencoding for self-supervised neurological pretraining. arXiv preprint arXiv:2204.12440, 2022.
- [46] Yi Ding, Neethu Robinson, Chengxuan Tong, Qiuhao Zeng, and Cuntai Guan. LGNet: Learning from local-global-graph representations for brain-computer interface. IEEE Transactions on Neural Networks and Learning Systems, 35(7):9773–9786, 2023.
- [47] Jing Jin, Ruitian Xu, Ian Daly, Xueqing Zhao, Xingyu Wang, and Andrzej Cichocki. MOCNN: A multiscale deep convolutional neural network for ERP-based brain-computer interfaces. IEEE Transactions on Cybernetics, 54(9):5565–5576, 2024.
- [48] Yiyu Gui, Mingzhi Chen, Yuqi Su, Guibo Luo, and Yuchao Yang. EEGMamba: Bidirectional state space model with mixture of experts for EEG multi-task classification. arXiv preprint arXiv:2407.20254, 2024.
